---
title: "programs not working"
date: 2011-04-02
forum: New to Ubuntu
---

### Post by Greth Rain on 2011-04-02
hi everyone, i once again have come for help...

recently, i downgraded my gdm so that i could use themes and change the look of the login screen. however after that, some programs (games) give me the following error:

greth@greth-laptop:~$ desmume
Command 'desmume' is available in '/usr/games/desmume'
The command could not be located because '/usr/games' is not included in the PATH environment variable.
desmume: command not found
greth@greth-laptop:~$

please explain why this happens and how to fix it...

---

### Post by ankspo71 on 2011-04-03
Hi, 
Can you post the output of this command?:
```
cat /etc/environment
```

It should look like this:
```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
```

I have a feeling this file got modified or removed.

Here are similar posts:
[http://ubuntuforums.org/showthread.php?t=1442849](http://ubuntuforums.org/showthread.php?t=1442849)
[http://ubuntuforums.org/showthread.php?t=1636537](http://ubuntuforums.org/showthread.php?t=1636537)

---

### Post by rosencrantz on 2011-04-03
Add the line
export PATH=$PATH:/usr/games
to the .bashrc file in your home directory. (this adds /usr/games to your program search path) Log out and in again.

---

### Post by Greth Rain on 2011-04-03
hi, i now have an even larger problem...
after a while of using the comp, i get an error saying cannot open program, input/output error.
after, this, the gnome panel on top disappears, although docky stays. then, nothing loads. openofffice shows the splash screen for a millisecond and then disappeaers. terminal gives the input/output error. no program loads at all!
also, no keyboard shortcut works. crtl+alt+L to lock screen or crtl+alt+del to give the shutdown dialog all give an error showing the equivalent command for terminal saying to check if the command is right!

[EDIT]:

now, everything is deteriorating fast...
sometimes, ubuntu fails to boot giving a message that X server failed to initialize or something like that.
worse, i got two bluescreens on windoze after that. now, 66.6% of the time, ubuntu fails to boot with the x server message.
please help! i really DO NOT want to reformat and reinstall ubuntu or worse, my entire comp...
also, I have my user data on a separate partition from the root system partition. is it possible to reinstall ubuntu by formatting and then using the existing root partition for the system files and the existing partition for user without deleting any data on the user partition?

---

