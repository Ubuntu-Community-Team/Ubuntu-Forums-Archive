---
title: "forgot to update-burg"
date: 2010-09-19
forum: New to Ubuntu
---

### Post by 29732 on 2010-09-19
anyway, i forgot to update burg after installing the newer linux image and now i cant boot onto the new ubuntu and the older linux kernel just says linfrmad (or whatever) and asks me for input
im on ubuntu live cd so i need to know how to update burg(not grub) on my already installed ubuntu
thanks, 
29732

---

### Post by andrewthomas on 2010-09-19
> **29732 said:**
> anyway, i forgot to update burg after installing the newer linux image and now i cant boot onto the new ubuntu and the older linux kernel just says linfrmad (or whatever) and asks me for input
im on ubuntu live cd so i need to know how to update burg(not grub) on my already installed ubuntu
thanks, 
29732
 It is the same as grub.  Just substitute burg for grub in the commands from here
 
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by jtarin on 2010-09-19
[How to]("http://www.sourceslist.eu/blog/linux-blog/burg-manager-installing-and-configuring-burg-has-never-been-so-easy/")

---

### Post by 29732 on 2010-09-19
```
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo update-burg
sudo: update-burg: command not found
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt/home
ubuntu@ubuntu:~$ sudo burg-install --root-directory=/mnt/ /dev/sda
sudo: burg-install: command not found
ubuntu@ubuntu:~$ sudo burg-install --root-directory=/mnt/ /dev/sda
sudo: burg-install: command not found
ubuntu@ubuntu:~$ 

```
](*,)

---

### Post by 29732 on 2010-09-19
what the hell, installed grub
now reinstaling burg 
but thanks :D

---

### Post by jtarin on 2010-09-19
Do you have the Live CD? Yes then boot to the Gnome desktop and use [this guide]("https://help.ubuntu.com/community/Grub2#Reinstalling from LiveCD") to access you Ubuntu install. Scroll down to Sub-topic "METHOD 3 - CHROOT". Follow the instructions up to #7 to mount your Ubuntu install as root.Then try to update.

---

### Post by basec0m on 2010-11-13
Cleaned up some old kernels, forgot to "update-burg", no boot.

Just wanted to confirm that the suggestion by jtarin worked for me.
Just substitute "update-burg" for update-grub if you are running burg.

---

### Post by Reduced_Oxygen on 2011-10-03
None of those links help?!?!?

---

### Post by Reduced_Oxygen on 2011-10-03
Wait nm

---

