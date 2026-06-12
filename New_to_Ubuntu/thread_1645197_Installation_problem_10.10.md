---
title: "Installation problem 10.10"
date: 2010-12-14
forum: New to Ubuntu
---

### Post by Lemuel111 on 2010-12-14
Hi folks. I updated Ubuntu from 10.04 to 10.10 last night but half way through the installation the system crashed. I pressed and held the power button to shut down. I then turned on and this is the message I got:-
"Install problem. The configuration defaults  for GNOME power manager have not been installed correctly. Please consult computer administrator"
I've tried loading another older version in GRUB menu inc. recovery mode and the same error message comes up. Can anyone help?  Thanks.

---

### Post by fatharraxman on 2010-12-14
ctrl+alt+f2 
sudo apt-get install  gnome-power-manager

---

### Post by sikander3786 on 2010-12-14
Make sure you are not running out of disk space.

Press Ctrl + Alt + F1 at login screen, log into tty1 and,

```
df -h
```

---

### Post by Lemuel111 on 2010-12-14
It won't accept my original password.

---

### Post by Lemuel111 on 2010-12-14
Sorry it's saying incorrect login not password. What will my login be?

---

### Post by sikander3786 on 2010-12-14
The one that you created? Or will be the same as your /home directory.

```
ls /home
```

---

### Post by Lemuel111 on 2010-12-22
Thanks for everyone's help on that. Problem sorted after following your directions. Cheers. :D

---

