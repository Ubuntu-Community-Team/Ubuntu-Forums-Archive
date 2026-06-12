---
title: "Ubuntu 11.04 doesn't boot anymore"
date: 2011-05-29
forum: New to Ubuntu
---

### Post by Kennin on 2011-05-29
My PC doesn't boot Ubuntu anymore. I suddenly get a BIOS screen only, with a login and pw request. When I enter those, I get 

[INDENT][FONT=Courier New][username]@[username]-desktop:~$[/FONT]_

[/INDENT]How do I get my sweetie up'n runnin' again, please? I use the newest Ubuntu 11.04 or someting like that... Nutty Narwale if I mistake not.

Thanks for helping!

Oh, an please be aware that I am an abolute Ubuntu n00b! I still am trying to figure out the to me odd disk management. :(

---

### Post by TeoBigusGeekus on 2011-05-29
Any enlightening error message after you give
```
startx
```
?

---

### Post by Kennin on 2011-05-29
THX!!! I'll give that a shot, first thing tomorrow!

---

### Post by corncob on 2011-05-29
See if pressing [CTRL][ALT][F7] does anything.

---

### Post by Kennin on 2011-05-30
[Startx] as well as [ctrl] [alt] [f7] make it very clear... my nvidia drivers are pooched. Any n00b way to get them fixed again, without having to reinstall my entire baby (and thus losing my data)? 

Please tell me there is...

---

### Post by corncob on 2011-05-30
I have no personal experience here but its been said elsewhere on the forum to go to System Settings > Hardware > Additional Drivers and install the Nvidia driver.  If its already there, remove it and reinstall it.  I guess you'll have to use the live CD to try to do this -- don't know if it will work.

---

### Post by Kennin on 2011-05-30
Thx, but without the proper command lines, I won't be able to do that, alas. No idea how that's supposed to work.

---

### Post by Kennin on 2011-05-31
Isn't "System Settings > Hardware > Additional Drivers" in the GUI? I cannot access the GUI as Ubuntu won't start. If you can navigate there without the GUI, I need to know how to get there, an how to actually reinstall the NVIDIA drivers, as I have no clue how to do that.

Right now I'm making a boot disk to install Ubuntu, perhaps I can boot from the CD and get the repair up and running from there.

---

### Post by corncob on 2011-05-31
Sorry, I had forgotten you didn't have a GUI.  I do think its possible from the command line as somebody had helped me with a similar problem.  That was years ago though and I can't find the thread.

---

### Post by Kennin on 2011-05-31
I did it! I managed to get it fixed!!! Without any more help, even!!!!

1. I pushed "esc" after the first BIOS screen, where Ubuntu is supposed to start.
2. I used the menu to startup "graphics recovery mode" to start up in Ubuntu 10.x.
3. I used the menu "system - admin - additional drivers" menu.
4. I activated the NVIDIA drivers. 
5. I restarted.
6. I jumped up, shouting TADAAAAAA!!!!

Thanks for helping, people! I appreciate it! Without the "startX" and "ctrl+alt+f7" tips, I couldn't possibly have found the solution!

---

