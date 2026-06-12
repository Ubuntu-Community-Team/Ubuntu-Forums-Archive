---
title: "how to run script file from desktop icon?"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by candtalan on 2008-12-10
I have written a simple script file  using rsync (to backup  bookmarks and thunderbird) and if I use nautilus file manager to open it - choose run in terminal - it works. :-)

I would like it to run in a terminal and that the terminal stays visible after it has finished running (to be closed manually), and also that it can be run by double clicking onto a desktop icon.

I would be grateful for some wisdom here...
tia

---

### Post by northern lights on 2008-12-10
If you'd put```
gnome-terminal -e /home/USER/yourscript.sh
```as the launcher's "command" entry, it would launch a terminal and execute your script. Unfortunately close the terminal right after though. The "-e" option makes *gnome-terminal* execute what comes after.

As for the terminal staying open, I have no idea off hand as to how to do it via the launcher, however you could extend your script by```
read -p "Close terminal (y/n)?"
[ "$REPLY" == "y" ] || exit
```and it would wait for you to hit "y".

---

### Post by aharown07 on 2009-09-18
Look here: [http://www.ax697.org/writing-a-basic-ubuntu-script-200786.html](http://www.ax697.org/writing-a-basic-ubuntu-script-200786.html)

Very helpful

---

### Post by kerry_s on 2009-09-18
```
**xterm -hold -e /path/to/script**
```

---

