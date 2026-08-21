# Чеклист за покупка на апартамент

Един статичен HTML файл ([index.html](index.html)) — списък с апартаменти + формуляр по чеклиста
от `Cheklist_novo_stroitelstvo.docx`. Няма build стъпка, няма зависимости.

Данните се пазят като файл `data/apartments.json` **в самия repo**, чрез GitHub REST API —
това е "базата данни". Записва се нов commit при всяко Save/Delete.

## Setup (веднъж)

1. Пусни тук `git init`, commit и push към нов GitHub repo (виж по-долу).
2. Settings → Pages → Source: `main` branch, `/ (root)`. Изчакай да се появи линк.
3. Отвори сайта → ⚙ Настройки → въведи:
   - GitHub потребител/организация и repo име
   - Branch (`main`)
   - Personal access token: [github.com/settings/tokens?type=beta](https://github.com/settings/tokens?type=beta) →
     "Generate new token" → ограничи го само до този repo → права **Contents: Read and write**.

Токенът се пази само в `localStorage` на твоя браузър и се използва единствено за директни
заявки от страницата към `api.github.com`. Не го споделяй и не го пускай на чужд компютър.

```bash
git init
git add index.html README.md
git commit -m "Apartment checklist app"
git branch -M main
git remote add origin https://github.com/<user>/<repo>.git
git push -u origin main
```

## Ограничения (съзнателно, за простота)

- Всички записи са в един JSON файл → ако редактираш от два таба/устройства едновременно,
  по-късният Save ще презапише по-ранния (git conflict модел за един файл, не за много малки).
  За личен чеклист с десетки апартаменти това е достатъчно.
- Токенът е видим в localStorage/devtools на браузъра, който го въведеш. Ползвай само на
  твой личен компютър.
