<p align="center"><strong>Практическая работа №4. Работа с системой контроля версий Git</strong></p>

**Проект:** «Планировщик учебных задач», версия 1.0.

**Удалённый репозиторий:** https://github.com/zane-code26/student-planner

**1. Создание проекта и подключение GitHub**

Создана отдельная папка student-planner и выполнена команда `git init -b main`.
Настроены данные автора коммитов. В README.md записаны название, описание,
возможности и версия проекта. В tasks.md добавлены три учебные задачи.
Файлы добавлены командой `git add`, затем создан первый коммит.

На GitHub создан пустой репозиторий student-planner. Локальная копия подключена
через `git remote add origin`, основная ветка отправлена командой
`git push -u origin main`. Проверены `git remote -v`, `git branch -vv`
и отслеживание origin/main.

**2. Работа в ветках**

| Ветка | Что сделано |
|---|---|
| main | Основная ветка с итоговым результатом. |
| feature/new-features | В tasks.md добавлены приоритеты и сроки задач. |
| docs/project-description | В README.md добавлены целевая аудитория и порядок использования. |

Обе рабочие ветки созданы от исходной main. Для каждой доработки выполнены
отдельный коммит и `git push -u origin <имя ветки>`.

**3. Значимые коммиты**

| Коммит | Результат |
|---|---|
| [`097fba5`](https://github.com/zane-code26/student-planner/commit/097fba5307a4efcfa9ac12ff9f1f94dfded530d9) | Созданы README.md, tasks.md и три исходные учебные задачи. |
| [`49e85a2`](https://github.com/zane-code26/student-planner/commit/49e85a2f197ab1e4ecb004c8d88f63e524bf8334) | Добавлены две возможности: приоритеты и сроки выполнения. |
| [`a06a432`](https://github.com/zane-code26/student-planner/commit/a06a432ffa6ead6565e24e9682bd07dc8cdfed92) | Описаны целевая аудитория и порядок использования. |
| [`7f75755`](https://github.com/zane-code26/student-planner/commit/7f75755739671932ed3defc7de362cde52539f84) | В main первая задача заменена подготовкой презентации. |
| [`1c8387f`](https://github.com/zane-code26/student-planner/commit/1c8387f75bcdd7ab6b07608473044f23f9fe0591) | В feature/new-features та же задача заменена подготовкой отчёта. |
| [`8e3e451`](https://github.com/zane-code26/student-planner/commit/8e3e45195097c6db9e721086819f91057b250999) | Разрешён конфликт первой задачи в tasks.md. |
| [`52700cd`](https://github.com/zane-code26/student-planner/commit/52700cd77fc12edbf82e799fcf5ad20cdd4190d5) | Ветка новых возможностей объединена с main. |
| [`3c47af0`](https://github.com/zane-code26/student-planner/commit/3c47af0d58c3863042020b921321e0d7ca51db47) | Ветка документации объединена с main. |

**4. Создание и разрешение конфликта**

В двух ветках независимо изменена одна и та же первая строка списка задач.
В main она стала «Подготовить презентацию по информатике», а в
feature/new-features — «Подготовить отчёт по практике».

При выполнении `git merge main` из ветки feature/new-features действительно
возник конфликт. Git вывел:

```text
Auto-merging tasks.md
CONFLICT (content): Merge conflict in tasks.md
Automatic merge failed; fix conflicts and then commit the result.
```

Команда `git status --porcelain` показала `UU tasks.md`.
Файл отредактирован вручную: оставлена одна согласованная задача
«Подготовить презентацию по информатике», маркеры конфликта удалены.
Две новые возможности планировщика сохранены.

Результат добавлен командой `git add tasks.md` и зафиксирован отдельным
коммитом `8e3e451`. У этого коммита два родителя:
`1c8387f` и `7f75755`.

После этого в main объединены сначала feature/new-features, затем
docs/project-description. Итог отправлен на GitHub.

**5. Проверка результата**

Выполнены `git fetch origin` и `git pull --ff-only origin main`.
Последняя команда сообщила `Already up to date.`.
История проверена через `git log --graph --oneline --decorate --all`,
локальные и удалённые ветки — через `git branch -a`.

В итоговой main присутствуют обе доработки. В tasks.md нет маркеров конфликта.
Команда `git diff main origin/main` не показывает различий.
После итоговой отправки `git status` показывает синхронизацию с origin/main
и чистый рабочий каталог: `nothing to commit, working tree clean`.

Отчёт REPORT.md добавлен отдельным коммитом в main и отправлен на GitHub.
В архиве сохранена папка .git с полной историей работы.
