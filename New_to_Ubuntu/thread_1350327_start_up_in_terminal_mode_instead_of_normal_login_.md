---
title: "start up in terminal mode instead of normal login page"
date: 2009-12-09
forum: New to Ubuntu
---

### Post by .Daniel. on 2009-12-09
Hello i'm absolutely new on ubuntu and here in the forum, I got a problem and hope you help me to solve it, 
the problem came after i install ATI driver and restart the system. now i just boot in terminal mode and i can't see the login page. it comes as : 

Ubuntu 9.10 (name) tty1
(name) login: 
password:
last login:
and some information

I've just switched to this page once to change the login page before, and it was by using ctrl,alt,f1 and switch back by alt,f7... but now it's coming right after start up and as i said i'm completely new on it and don't new any useful command to switch back to the normal login view. and also i'm not sure that the installing the graphic driver caused this mess. maybe it's something else...

I have searched to find any answer or solution but nothing yet.
I appreciated if someone help me out here...
Thanks in advance.

---

### Post by shakabra on 2009-12-09
try the command ```
startx
```.

---

### Post by .Daniel. on 2009-12-09
hello shakabra thanks for the quick replay, 
I have tried that already but i got error and it said  unable to connect to X server...

---

### Post by ukripper on 2009-12-09
Reboot and keep holding shift then grub will show up, while at grub screen select the second option which is a recovery mode. You can fix xserver from there. we go from there.

---

### Post by .Daniel. on 2009-12-09
Thanks for respond, ok i reboot my system, held down the shift as soon as the system start running, but the page just stopped until i stop holding shift, then the grub showed up and i chose the second option (recovery mode), 
I had 6 options: 
resume , clean , dpkg , grub , netroot , root
im not sure bt i think none of those options will solve it, i didn't find the way to fix the xserver yet.

---

### Post by philinux on 2009-12-09
Installing the ati driver will have reconfigured xorg.conf. Easiest way to get back to the desktop is to delete or rename this file.

Reboot and use the recovery option. At the the command prompt.

```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Then use the reboot command.

---

### Post by .Daniel. on 2009-12-09
> **philinux said:**
> Installing the ati driver will have reconfigured xorg.conf. Easiest way to get back to the desktop is to delete or rename this file.

Reboot and use the recovery option. At the the command prompt.

```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Then use the reboot command.

Thank you So much! It solved my problem perfectly...

---

### Post by lotharmat on 2009-12-09
> **.Daniel. said:**
> Thank you So much! It solved my problem perfectly...


Please can you mark the thread as 'solved' (thread tools above) This will help other people know that this solution could help them too

---

