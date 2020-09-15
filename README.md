# play_with_git

Git репозиторий создан для поиграться с ветками, коммитами, откатами и вот этим вот всем.

для простоты будем использовать только локальный репозиторий и удаленный origin
1. привязал удаленный репозиторий.
git remote add origin ссылка на этот репозиторий
в нем уже был файл README.md
в локальном репозитории сделал:
git add .
git commit -m "start commit"
git push origin master
и тут была ошибка >>>>>

To github.com:rudinandrey/play_with_git.git
 ! [rejected]        master -> master (non-fast-forward)
error: failed to push some refs to 'git@github.com:rudinandrey/play_with_git.git'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. Integrate the remote changes (e.g.
hint: 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.

это означает нужно сделать сначала git pull origin master

это сделает:

git fetch origin master

git merge origin/master 

но не все так просто, git ругнется, что: fatal: refusing to merge unrelated histories

это что-то типа отказ от объединения несвязанных историй.

но есть параметр, --allow-unrelated-histories

By default, git merge command refuses to merge histories that do not share a common ancestor. This option can be used to override this safety when merging histories of two projects that started their lives independently. As that is a very rare occasion, no configuration variable to enable this by default exists and will not be added.

переведем корявым гугловским переводчиком:

По умолчанию команда git merge отказывается объединять истории, не имеющие общего предка. Этот параметр можно использовать для отмены этой безопасности при объединении историй двух проектов, которые начали свою жизнь независимо. Поскольку это очень редкий случай, конфигурационная переменная для включения этого по умолчанию не существует и не будет добавлена.

Достаточно редкий случай. Скорее всего потому что чаще пользуются git pull. Ладно примем во внимание и пойдем дальше.

создали git checkout -b dev новую ветку.

добавили в файл index.html какой то текст. и сделал git add . && git commit -m "..." && git push origin dev 

в удаленном репозитории создалась ветка origin/dev которую github сразу предложил слить в master, но мы этого делать пока не будем.

