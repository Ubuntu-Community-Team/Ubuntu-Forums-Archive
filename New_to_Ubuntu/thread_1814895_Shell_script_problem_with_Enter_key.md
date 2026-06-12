---
title: "Shell script problem with Enter key"
date: 2011-07-30
forum: New to Ubuntu
---

### Post by zhanglini on 2011-07-30
Hi I have a sync/backup shell script that had been working for a while and all of a sudden it is acting weird.  
Basically I am trying to sync /home to /home on an external drive but somehow  the script creates a new /home (with some spaces, or maybe an "Enter" sign).
The following is my code:```

#!/bin/sh
sudo rsync -rtpogv --progress --delete --exclude=/guest --exclude=/lost+found --exclude=/xxx/.gvfs --exclude=/xxx/.cache --exclude=/*/firefox/"Crash Reports" --exclude=/*/firefox/*/Cache --exclude=/*/firefox/*/minidumps -u -l -H /home  /media/Shared/home(note: no space here, but "Pressed Enter" to go to next line!!!)
sudo rm -R /media/Shared/etc/
sudo cp -R /etc/ /media/Shared/etc/
```
It seems the terminal is interpreting the "Enter" here as a character something.
Can somebody help?
I use Ubuntu 10.04

---

### Post by hakermania on 2011-07-30
hello :)
A small thought:
```

#!/bin/sh
sudo rsync -rtpogv --progress --delete --exclude=/guest --exclude=/lost+found --exclude=/xxx/.gvfs --exclude=/xxx/.cache --exclude=/*/firefox/"Crash Reports" --exclude=/*/firefox/*/Cache --exclude=/*/firefox/*/minidumps -u -l -H /home  /media/Shared/home/;
sudo rm -R /media/Shared/etc/;
sudo cp -R /etc/ /media/Shared/etc/;

```**;** shows where exactly the commands end and won't take any newline characters

---

### Post by zhanglini on 2011-07-30
That works!  wow it is THAT easy, I really need to learn some scripting.
Thank you @Haker!

---

### Post by hakermania on 2011-07-30
> **zhanglini said:**
> That works!  wow it is THAT easy, I really need to learn some scripting.
Thank you @Haker!

You're welcome :)
And yes, a little bit of scripting helps ;)

---

