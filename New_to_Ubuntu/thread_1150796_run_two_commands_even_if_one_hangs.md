---
title: "run two commands even if one hangs"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by PGScooter on 2009-05-06
Hi, I am trying to launch my screensaver with one command (so they I can put it in an alias):
```

gnome-screensaver & gnome-screensaver-command activate

```
I thought that this command would do the trick, but the second command is never executed.

I need to run gnome-screensaver because otherwise I cannot run the command to activate the screensaver: ```
gnome-screensaver-command activate
``` However, if gnome-screensaver is already running and I try to run it again I get the following error message which hangs and so the second command is never executed. 
```

jackal@compy:~$ 
** (gnome-screensaver:14339): WARNING **: screensaver already running in this session

```


thanks

---

### Post by mcduck on 2009-05-06
You can just separate the commands with a semi-colon if you want to run them regardless if the first command exits correctly or not.

```
gnome-screensaver; gnome-screensaver-command activate
```


"command1; command2" will first run command1, then command2
"command1 & command2" will run command1 and then command2 (starting command2 immediately instead of waiting for command1 to finish first)
"command1 && command2" will first run command 1, and if it exits without errors then run command2
"command1 || command2" will first run command1, and only if it fails, run command2.

---

### Post by ScaryBob on 2009-05-06
How about:
```
gnome-screensaver & gnome-screensaver-command activate &
```

---

### Post by sisco311 on 2009-05-06
an "elegant" solution: :)

```
pidof gnome-screensaver || gnome-screensaver && gnome-screensaver-command activate
```

---

### Post by PGScooter on 2009-05-06
thank you for all of the replies! It works perfectly now.

For reference purposes, I made a mistake in my original post. The correct command is ```
gnome-screensaver-command --activate
```
(note the -- before the "activate").

Thanks!

---

