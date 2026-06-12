---
title: "how to retain ubuntu and uninstall windows Xp"
date: 2011-02-10
forum: New to Ubuntu
---

### Post by dragon1111 on 2011-02-10
Hi...i installed ubuntu 10.10 alongside Windows Xp but my computer boots directly into ubuntu...Now that i'm really happy with ubuntu i want to get rid of Windows Xp from my computer for good...How do i do that considering it boots directly into ubuntu? Plz help :???:

---

### Post by theozzlives on 2011-02-10
> **dragon1111 said:**
> Hi...i installed ubuntu 10.10 alongside Windows Xp but my computer boots directly into ubuntu...Now that i'm really happy with ubuntu i want to get rid of Windows Xp from my computer for good...How do i do that considering it boots directly into ubuntu? Plz help :???:

do:
```
sudo apt-get install gparted
```
delete your NTFS partition and resize your Ubuntu partition (prolly ext4) to take up the free space. BE SURE you backup EVERYTHING you want to save off your Windows!

---

### Post by NightwishFan on 2011-02-10
Keep an Ubuntu Live CD handy in case any thing goes wrong. I doubt it will.

---

### Post by dragon1111 on 2011-02-10
ok i'll enter that in the terminal...what exactly is gonna happen after that coz i'm an absolute noob when it  comes to ubuntu and i dont wanna mess anything up coz then i wouldnt know how to bring it back to normal...also,how do i delete my NTFS partition and then resize  ubuntu

---

### Post by theozzlives on 2011-02-10
> **dragon1111 said:**
> ok i'll enter that in the terminal...what exactly is gonna happen after that coz i'm an absolute noob when it  comes to ubuntu and i dont wanna mess anything up coz then i wouldnt know how to bring it back to normal...also,how do i delete my NTFS partition and then resize  ubuntu

you go to system > administration > gparted. Enter your password and it show you a map of your drive.

edit: Oh wait! my bad! you gotta use gparted off the live CD. You can't resize a mounted volume. The rest is correct.

---

### Post by dragon1111 on 2011-02-10
i've attached the screenshot image...this is how it looks

---

### Post by Linyx on 2011-02-10
@[dragon1111]("http://ubuntuforums.org/member.php?u=1203921"):-

__It is better if you use 1-thread for a single Purpose > [http://ubuntuforums.org/showthread.php?p=10445655#post10445655](http://ubuntuforums.org/showthread.php?p=10445655#post10445655)

---

