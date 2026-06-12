---
title: "changing the grub menu question"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by Proto Blaze on 2011-01-23
i want to make some of the grub options invisible at the menu... like the safe modes and stuff like that... i just want the options to be windows, ubuntu, and mint... how do i do that?

---

### Post by Quackers on 2011-01-23
Details here
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
Or there is a new GUI tool - details here 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

---

### Post by garvinrick4 on 2011-01-23
> **Proto Blaze said:**
> i want to make some of the grub options invisible at the menu... like the safe modes and stuff like that... i just want the options to be windows, ubuntu, and mint... how do i do that?
Here is what needs editing and link is instructions.
```
gksudo gedit /etc/default/grub
```[Grub2 - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Grub2#/etc/default/grub") 

#Remember any changes you need to 
```
sudo update-grub 
```for them to take effect.

---

### Post by Proto Blaze on 2011-01-24
thank you :-D

---

### Post by Quackers on 2011-01-24
You're welcome :-)
Please mark the thread as solved using the Thread Tools near the top of the page. Thanks.

---

