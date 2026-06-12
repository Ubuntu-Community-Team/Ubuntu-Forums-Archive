---
title: "Authentication window dissapears too fast to click"
date: 2010-12-23
forum: New to Ubuntu
---

### Post by vanhecke on 2010-12-23
Hi,

I use Ubuntu since 8.10, and loving it. 
Now I have 10.10 running and have the following issue: when I update the system (update manager > install updates), I'm ask to authenticate. The authentication window shows up but immediately registers an authentication failure.
The window starts "shaking" as if I entered the wrong password and closes again. The whole action takes less than 0.2 seconds. I had a lucky screenshot taken in order to read the text on the authentication window.
The same happens in the Ubuntu software center and when I want to change global time settings (which I do often because I'm traveling a lot).

All other authentication windows behave normal. 

I've been searching the fora, but couldn't find an issue just like mine. 

Thanks for any ideas on this one.

---

### Post by vanhecke on 2010-12-23
Found at least a workaround.

It works by changing the menu entry (system > preferences > main menu) of the update manager "sudo /usr/bin/update-manager" (add the sudo).

---

### Post by miegiel on 2010-12-23
> **vanhecke said:**
> Found at least a workaround.

It works by changing the menu entry (system > preferences > main menu) of the update manager "sudo /usr/bin/update-manager" (add the sudo).

Since *update-manager* is graphical, it's better to use *gksudo* than *sudo*. Sudoing a graphical app can seriously mess up the configuration of that app. See for example the posts of people who got problems after running *sudo firefox*.

---

### Post by coffeecat on 2010-12-23
@vanhecke, a long shot this, but check it out anyway. Press alt-F2 and run 'gconf-editor'. Now go to apps > gksu. Is the 'sudo-mode' box ticked? If not, tick it. If it's not ticked then you will encounter authentication problems elsewhere as well.

---

### Post by masuch on 2011-09-16
I still have this error.
It is wrongly affected many other application than update-manager.
In this bug report - it should be solved, but not for me:
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/704667](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/704667)
Can anybody confirm does it work ?

---

### Post by nothingspecial on 2011-09-16
Please don't post the same issue in multiple threads.

Thread closed.

---

