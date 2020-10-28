*Thanks to [jcsalterego](https://github.com/jcsalterego) for the idea and who's already implemented the same thing for [bash](https://github.com/jcsalterego/historian)*

### Backup and Restore ZSH history

- Simple python script that can backup and restore your zsh history file to a sqlite db
- Dedups commands, and prepends any commands that were in the db but not in the history file
- Accepts a max length parameter
    - This does not truncate your existing file
    - If max length is <= than the size of your existing file, no new commands will be added to your history file
    - Otherwise, it will pull commands based on their timestamps until max length is reached

### Running it

```
usage: ./src/hist.py [-h] [-p PATH] [-d DBNAME] [-m MAXLINES] [-b] [-r]

Backup/Restore zsh history

optional arguments:
  -h, --help               show this help message and exit
  -p PATH,      --path     PATH  path to ZSH history    (default $HOME/.zsh_history)
  -d DBNAME,    --dbname   DBNAME SQLite db path        (default $HOME/.zsh_hist_backup.db)
  -m MAXLINES,  --maxlines MAXLINES max size of history file (default no limit)
  -b, --backup
  -r, --restore
```

Backup:

```
./src/hist.py -b
```

Restore:
```
./src/hist.py -r
```

### Restoring history every time you open a shell

- Just add the restore command to your ~/.zshrc file! (with the path from $HOME of course)

### Backing up your DB

- I've scheduled a launchd task on my mac to push my db to git every evening. [Here's](https://github.com/rchakra3/Utils/tree/master/scripts/zsh_backup) a link to the scripts


***Feedback and comments welcome!***
