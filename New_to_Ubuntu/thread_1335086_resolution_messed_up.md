---
title: "resolution messed up"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by garage jack on 2009-11-23
hi everyone. i'm new to ubuntu and this time i messed up my resolution. to be able to play torment on my machine, i had to decrease color depth to 16, and after that when i restarted my computer, not only that i wasn't able to play the game, i couldn't open my terminal to fix my mistake, i couldn't revert color depth to its original value in xorg.conf (access denied), couldn't open synaptic or any other application coz my screen would got frozen every time. would someone help me, please?

---

### Post by ukripper on 2009-11-23
ok when you boot normally and reach your login screen. Can you press CTRL + ALT +F1 and then put you username there and password. After that try to access your xorg.conf using below command ```
sudo nano /etc/X11/xorg.conf
```. Change your 16 depth there and save and exit. Reboot

Does it work now?

---

### Post by garage jack on 2009-11-23
it says unknown command when i type in sudo nano..

---

### Post by ukripper on 2009-11-23
> **garage jack said:**
> it says unknown command when i type in sudo nano..

```
sudo vi /etc/X11/xorg.conf
```

try this

---

### Post by garage jack on 2009-11-23
same thing.

---

### Post by garage jack on 2009-11-23
when i try to type in sudo gedit/etc/x11/xorg.conf it displays me some warning: can't show display or something like that

---

### Post by ukripper on 2009-11-23
> **garage jack said:**
> when i try to type in sudo gedit/etc/x11/xorg.conf it displays me some warning: can't show display or something like that

What you get when you run this:
```
cat /etc/X11/xorg.conf
```

make sure you type exactly the same as above. it is case sensitive

There is space between cat and /etc and X is capital in X11

---

### Post by garage jack on 2009-11-23
oh man, thank you very much! the first sudo nano.. was enough, i was being stupid whole time not typing it right, x in lower case and without space between sudo nano and the rest of the bunch. thanks again!

---

### Post by ukripper on 2009-11-23
no problem. Happens to everyone, we overlook things which we think is unlikely to happen.

---

