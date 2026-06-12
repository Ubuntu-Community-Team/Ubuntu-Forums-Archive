---
title: "Help! Drivers stopped working after update"
date: 2016-01-28
forum: Networking &amp; Wireless
---

### Post by Ncio on 2016-01-28
i`m a Ubuntu newbie ( installed it today), I had version 14.04,but after the OS asked for an upgrade,several I ran into a login loop,but managed to fix it. But after the upgrade, drivers like wifi,ethernet and GPU stopped working... anybody can help me?

---

### Post by Hadaka on 2016-01-28
Hi,please open a terminal ctrl/alt/t then copy and paste..
```
lspci -n | awk '/0200|0280/{print$3}'
```
post the output please
thanks.

---

### Post by Ncio on 2016-01-29
I'm using Ubuntu on another pc so I'll take photos

---

### Post by Ncio on 2016-01-29
Got no output at all! It jumped to a new line,but this time, it didnt had my username:myusername:~$ thing

---

### Post by Ncio on 2016-01-29
Okay,so only after 3 tries I got it right :

---

### Post by Hadaka on 2016-01-29
Hi, since you have no internet access and your ubuntu install is new,
I would suggest reloading and this time not do the upgrade- upgrade
means upgrading from 14.04 to 15.X I have no idea which one was offered.
Also it is most likely to fail if you attept to load with a wireless connection.
Try re installing 14.04 using a wired connection.
*Your screen capture shows you are on 14.04 are you adding to the confusion
by saying upgrade when you mean update?...there is a difference.
thanks.

---

### Post by Ncio on 2016-01-30
Hi! Thanks a lot for helping me! But it happens that when the drivers were gone,I ran into a login loop and my ubuntu kinda rolled back to 14.04( don't ask me how tho) and also,my USB drivers are gone! The only thing that it accepts is my phone (Moto E2 ) and I've downloaded a IMG file of the ubuntu 14.04 but it is in XZ format, how do I extract it in my Ubuntu ( uncopressed file is to big to store in my phone). PS: Sorry for bad english!

---

### Post by Hadaka on 2016-01-30
Hi, if you have burned your Ubuntu 14.04 correctly to a dvd then you need to
boot from your cd rom drive to load it. In bios of the computer you wish to load
14.04 on change the boot drive order to have cd rom dive first.
good luck

---

### Post by Ncio on 2016-02-01
Ok so now I ran into kinda of a problem,I dont have any CD slots, I'm using a Intel Netbook;BUT I managed to find and download the files of my wireless driver,unfortunately I dont know how to install it,I got it into my Netbook,and it's Ucode files (i don't know how to install them)

---

### Post by Hadaka on 2016-02-01
Hi,please boot your computer and hold down the "shift" key while booting.
this shoud put you into the recovery mode. choose boot to an eariler version
of 14.04. If that is not possible, then use the dvd or usb or whatever you used
to originally load ubuntu 14.04 and try to load that. You have no access right now to
run diagnostics so you dont even know if you need those ucodes or not.
report back your findings please
thanks.

---

