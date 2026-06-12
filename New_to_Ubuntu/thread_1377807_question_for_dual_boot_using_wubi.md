---
title: "question for dual boot using wubi"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by D4matricks on 2010-01-10
I have 9.10 ubu karmic koala right now, and i am planning to dual boot.
so since wubi is for xp, vista, and things, i need to install xp on my comp.
so my question is, if i just insert my xp cd in my drive, ubuntu will go away??

---

### Post by sailthesea on 2010-01-10
If you use the XP install CD Yes it will write over Ubuntu and then you will have to use Wubi to install Ubuntu within XP

 I would ask why you want to do this? Wubi is not the best way to install Ubuntu

---

### Post by tom.swartz07 on 2010-01-10
> **D4matricks said:**
> I have 9.10 ubu karmic koala right now, and i am planning to dual boot.
so since wubi is for xp, vista, and things, i need to install xp on my comp.
so my question is, if i just insert my xp cd in my drive, ubuntu will go away??

I dont quite understand what youre trying to accomplish?

Do you want to have XP AND Ubuntu on your computer? You dont need to use WUBI for that- You could Dual Boot. Windows shouldnt touch Ubuntu when it installs

Just install XP and follow the instructions here: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by D4matricks on 2010-01-11
its because i am a computer noob xD. 
from what i hear, wubi will do the dual boot for me.

---

### Post by listerdl on 2010-01-11
I have a dual boot windows 7 and ubuntu 910 that even share the same folders, so if you are in windows you can access your documents and folders in ubuntu.

It is really easy. Simply make four partitions, one for windows on NTFS one for linux on ext4 and then storage and a swap parition.

Check out this tutorial it works a treat: [http://www.lifehacker.com.au/2009/11/boot-windows-7-and-ubuntu-in-perfect-harmony/](http://www.lifehacker.com.au/2009/11/boot-windows-7-and-ubuntu-in-perfect-harmony/)

The above tutorial worked very well for me aside from ubuntu 910 being very problematic and not allowing any souind through speakers.....annoying but i will solve it everntually...

Personally I prefer the hard coded dual boot, i.e. parition for each OS.

---

### Post by garvinrick4 on 2010-01-11
what does your "sudo fdisk -l" without quotes say and that is small L.  Will give you drive
partitions. Post it here. Should be able to add XP with very little trouble in nice dual boot.

---

