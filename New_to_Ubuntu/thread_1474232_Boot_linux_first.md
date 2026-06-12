---
title: "Boot linux first"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by Bob Appleby on 2010-05-05
I very seldom use Windows and would like to have linux boot automatically once the computer is turned on without having to wait for the choice to appear. I there an easy way to have linux as the first choice?

---

### Post by raymondh on 2010-05-05
> **Bob Appleby said:**
> I very seldom use Windows and would like to have linux boot automatically once the computer is turned on without having to wait for the choice to appear. I there an easy way to have linux as the first choice?

It's been a while since I've participated in the forum.  Hope this helps.

[https://help.ubuntu.com/community/Grub2#Boot](https://help.ubuntu.com/community/Grub2#Boot) Display Behavior
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Best,

Raymond

---

### Post by cap10Ibraim on 2010-05-06
I have Grub2 , so I use this application startup manager 
really easy with UI you can choose the OS and waiting time 
you can get it from the synaptic package manager

---

### Post by QIII on 2010-05-06
If you are using GRUB2, give this a read:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

If you are using legacy GRUB, 

```
gksudo gedit /boot/grub/menu.lst
```Find the line that says "timeout 3" (or whatever the value is now) and change it to "timeout 1".  That will give you one second.  I don't recommend going any less than that, because if you are not fast on the trigger you can sometimes play hell trying to get the GRUB menu up if you really want to use it.

I can't recommend SUM, because I am not convinced all the bugs are really worked out just yet.

---

