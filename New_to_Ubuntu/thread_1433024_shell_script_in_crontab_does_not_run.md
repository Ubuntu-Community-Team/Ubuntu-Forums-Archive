---
title: "shell script in crontab does not run"
date: 2010-03-18
forum: New to Ubuntu
---

### Post by jmcgee on 2010-03-18
from crontab -l:
```
16 3 * * * bash /home/mythuser/bulkcat.sh
```

the contents of that script:


```
#!
# Source mysql.txt to find out db information
if [ -f $HOME/.mythtv/mysql.txt ]; then
        . $HOME/.mythtv/mysql.txt
else
        echo "Couldn't locate mysql.txt"
        exit 1
fi

function update_dir {
        RATED_DIR="$1"
        SHOWLEVEL="$2"
        if [ ! -d "$RATED_DIR" ]; then
                echo "No such directory: $RATED_DIR"
                exit 1
        fi
        echo "UPDATE  videometadata SET showlevel=$SHOWLEVEL  WHERE filename LIKE '$RATED_DIR/%' ;" | mysql -u $DBUserName --password=$DBPassword -D $DBName -h $DBHostName
}

update_dir "/mnt/bigboy/myth/video/level4" 4
update_dir "/mnt/bigboy/myth/video/level1" 1
```


I can run the command from terminal just fine, it just doesn't run from crontab.  I originally had it in crontab with bash at start, that didn't work, either.  

any thoughts?
thanks.

---

### Post by spiderbatdad on 2010-03-18
entirely unsure, but looking at crontab I see PATH. Have you added the file location to path? Other thoughts include the -u option explained in the crontab manpage.

---

### Post by DaithiF on 2010-03-18
Hi,
1. make sure script is executable: 
```
chmod +x bulkcat.sh

```2. change your crontab entry to:
```
16 3 * * * /home/mythuser/bulkcat.sh > /home/mythuser/bulkcat.log 2>&1

```3. change the first line of the script to:
```
#!/bin/bash

```(while testing, set the cron minutes / hours to a time a couple of minutes ahead, so you don't have to wait a day between tests.  once its run, post whatever ends up in /home/mythuser/buikcat.log

---

### Post by bodhi.zazen on 2010-03-18
cron runs with a minimal shell and minimal environmental variables set.

Use the full path to your files, ie /home/user and NOT $HOME

Same with commands

/bin/foo not foo

---

### Post by jmcgee on 2010-03-20
OK, I added 

```
#!/bin/bash
```

to start of script, but no difference.

Then I added full path to home directory in the script and it did it's job as intended from cron!  Maybe I needed to do both.  Nothing shows up in log but maybe nothing is output if it run correctly.
thanks all.

---

