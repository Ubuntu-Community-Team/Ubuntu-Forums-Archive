---
title: "How to edit GRUB bot list in ubuntu 10.04"
date: 2010-12-15
forum: New to Ubuntu
---

### Post by lordmonkeyu on 2010-12-15
Hello,
How can I edit the GRUB boot list in ubuntu 10.04 ? because there is no file like :
```
/boot/grub/menu.lst
```
which I used in previous versions to do it

---

### Post by oldos2er on 2010-12-15
10.04 uses grub2. Some properties of grub2 can be configured in the file /etc/default/grub, others in various files in /etc/grub.d/* 

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by frank002 on 2010-12-15
The file you want to edit is /boot/grub/grub.cfg. Dont forget to do a sudo chown to change permission to yourself to edit file and then change back to make root the owner. As always, be careful when editing this file. Good luck.

---

### Post by wojox on 2010-12-15
> **frank002 said:**
> The file you want to edit is /boot/grub/grub.cfg. Dont forget to do a sudo chown to change permission to yourself to edit file and then change back to make root the owner. As always, be careful when editing this file. Good luck.

No, that's not a good idea.

---

### Post by Bucky Ball on 2010-12-15
+1. Don't go that way.

You should be editing /etc/default/grub then when finished you need to run 'update-grub' from memory. There is absolutely NO reason to chown anything and as mentioned, that is clumsy and not a good idea.

I advise having a good read of the links provided earlier as grub2 is quite different.

---

### Post by Quackers on 2010-12-15
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by Bucky Ball on 2010-12-15
> **Quackers said:**
> [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Hey, quackers. That link was provided already in post #2. ;)

---

### Post by Quackers on 2010-12-15
It's ok, I've just cleaned my glasses. I can see now :-)

---

### Post by Bucky Ball on 2010-12-15
> **Quackers said:**
> It's ok, I've just cleaned my glasses. I can see now :-)

lol

---

