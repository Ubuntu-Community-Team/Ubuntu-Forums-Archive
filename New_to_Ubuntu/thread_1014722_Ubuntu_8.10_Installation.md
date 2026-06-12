---
title: "Ubuntu 8.10 Installation"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by Shippou on 2008-12-18
Hello folks...

I am trying to install Ubuntu 8.10 today via a Live CD. But then, it won't boot to the live cd. I have already tested the ISO on Virtualbox and it works fine. But then, when I boot from the CD itself, it does load but after maybe 30 seconds it defaults into a black screen with the familiar initramfs and a description of ash, whatever that is.

This really sucks. But then, Ubuntu does not suck.

Please help.

And yeah, the same goes for Linux Mint Felicia.

---

### Post by kestrel1 on 2008-12-18
Instead of running the live CD can you just go for a straight install from the CD. You should have the option in the initial menu.

---

### Post by nhasian on 2008-12-18
have you tried installing ubuntu 8.10 using the Alternate CD?  

Also I like your Avatar of Shippou from Inu Yasha :KS

---

### Post by Shippou on 2008-12-18
> **kestrel1 said:**
> Instead of running the live CD can you just go for a straight install from the CD. You should have the option in the initial menu.

I tried this already but then it still defaults to the initramfs, whatever that is.

> **nhasian said:**
> have you tried installing ubuntu 8.10 using the Alternate CD?  

Also I like your Avatar of Shippou from Inu Yasha :KS

What do you mean by the Akternative CD? Sorry I don't understand.

Also the avatar is only a screenshot. :)

Thanks for all the help.

P.S. I am dual-booting with Windows.

---

### Post by nhasian on 2008-12-18
download the alternate CD ISO and burn it to disc.  then use this text based installer instead of the regular liveCD:

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

---

### Post by kestrel1 on 2008-12-18
If you have Windows installed already have you tried the wubi install from within Windows? That may work for you.

---

### Post by rybaxs on 2008-12-18
install the desktop one..

---

### Post by _noob_ on 2008-12-18
I tried the Wubi. I didn't care for it too much. The Firefox and other elements of it were kinda WAY glitchy. But that is just me. Lol. Just my opinion of course. :)

---

### Post by kestrel1 on 2008-12-18
Not tried a wubi install myself, so don't know about any glitches but it may be worth it.
BTW what hardware are you using? Graphics card etc.

---

### Post by Shippou on 2009-01-27
Hello again...

I still cannot reformat my Linux partition. I have tried your suggestions, but it still gives me the initramfs screen.

Sorry if I have only replied today.

---

### Post by kestrel1 on 2009-01-28
How is your Windows drive formatted?
if it is FAT32, it could be that causing the problem.
To see if your drive is FAT32, go to My Computer & select your hard drive & in the left pane you should see 'File System'. If this says FAT32, you will need to convert it to NTFS
To do that look [HERE]("http://www.aumha.org/win5/a/ntfscvt.php")

---

### Post by Shippou on 2009-01-28
> **kestrel1 said:**
> How is your Windows drive formatted?
if it is FAT32, it could be that causing the problem.
To see if your drive is FAT32, go to My Computer & select your hard drive & in the left pane you should see 'File System'. If this says FAT32, you will need to convert it to NTFS
To do that look [HERE]("http://www.aumha.org/win5/a/ntfscvt.php")

My Windows partition is in NTFS format.

---

### Post by theozzlives on 2009-01-28
Try re-burning the CD at the lowest speed possible.

---

### Post by kestrel1 on 2009-01-28
OK, that blows that theory out of the water then :)
I will hae to think about it a bit more then.
What hardware are you using?
CPU 
RAM
Graphics

---

### Post by Shippou on 2009-01-31
> **kestrel1 said:**
> OK, that blows that theory out of the water then :)
I will hae to think about it a bit more then.
What hardware are you using?
CPU 
RAM
Graphics

Sorry for the late reply.

CPU: Athlon64
RAM: 2.5GB ddr2 (I think)
No external graphics card

---

### Post by kestrel1 on 2009-01-31
What graphics chip is onboard & how much ram is dedicated to it?

---

