---
title: "New to Linux Ubuntu"
date: 2010-03-15
forum: New to Ubuntu
---

### Post by billwyatt on 2010-03-15
Hi
 
I am new to Linux, I have a PC with 3 HDD 
 
1 40gb with Ubuntu on it
2 20gb
3 SATA 200gb
 
Is there a way to move /home to the 20gb without reinstalling?
How do I setup that all 3 HDD are mounted at startup
 
I will be installing Ubuntu Server onto the 200gb drive later.
 
Thanks:D

---

### Post by finku on 2010-03-15
When you say move /home, do you to relocate /home or just use the 20GB as an additional storage for your home? (gparted might help if the 20GB drive is still unformatted)

For the mounted part, you need to edit your fstab - google should do the trick here.

---

### Post by billwyatt on 2010-03-15
relocate /home
I have formated it Ext4

---

### Post by finku on 2010-03-15
This should help [http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)

---

### Post by derekeverett on 2010-03-15
If I understand what your asking correctly.. it is simply a matter of mounting your 20gb partition and then copying your home folder into it.

You would need to modify your fstab if you want that partition to mount automatically at boot time.

---

### Post by billwyatt on 2010-03-15
All working now thanks for all you help

---

