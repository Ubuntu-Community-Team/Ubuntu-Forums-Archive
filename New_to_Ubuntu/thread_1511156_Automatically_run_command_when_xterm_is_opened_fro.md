---
title: "Automatically run command when xterm is opened from Gnome?"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by k4o on 2010-06-16
I run Ubuntu 9.10 at work and if I hit alt+f2 to run "xterm" I always need to load my profile with the command ". ~/.profile" -- is there any way I can have this done automatically if I run xterm?

Thanks :)

---

### Post by Chesamo on 2010-06-16
You want the command to be ```
xterm -e ~/.profile
``` If you want, create a Launcher with that command. Alt+F2 doesn't have shortcuts, I'm afraid.

---

### Post by k4o on 2010-06-16
Chesamo,

Thanks!  That launcher command does not work though.. it starts up then immediately closes.

What am I screwing up? :(

---

### Post by Zeike on 2010-06-16
What shell are you using?  Bash?  (If you don't know you can run 'echo $SHELL' to find out) In that case your profile should probably be .bash_profile instead.

Either way, 'profile' files are normally only called when starting a login shell.  A standard xterm session isn't usually configured to be a login session.

The file .bashrc will be called whenever any interactive bash shell is started.  You can put the commands you need in there, or alternatively you can add something like 'source .profile' to the end of .bashrc.

[QUOTE=man bash]```

**FILES**
       /bin/bash
              The bash executable
       /etc/profile
              The systemwide initialization file, executed for login shells
       /etc/bash.bashrc
              The systemwide per-interactive-shell startup file
       /etc/bash.bash.logout
              The systemwide login shell cleanup file, executed when  a  login
              shell exits
       ~/.bash_profile
              The personal initialization file, executed for login shells
       ~/.bashrc
              The individual per-interactive-shell startup file
       ~/.bash_logout
              The  individual  login shell cleanup file, executed when a login
              shell exits
       ~/.inputrc
              Individual readline initialization file
```
[/QUOTE]

---

### Post by k4o on 2010-06-16
> **Zeike said:**
> or alternatively you can add something like 'source .profile' to the end of .bashrc.

Using Bash.

I put 'source .profile' at the end of .bashrc and now it just sits in some sort of infinite loop that I need to end with CTRL+C to even use my command prompt.

EDIT: Fixed it, had some rogue lines in my .profile file (given to me by a coworker).
Thanks guys!

---

