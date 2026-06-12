---
title: "Stuck in installer menu --Base system won't install"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by jchastain77 on 2009-01-14
Hi I am new to linux and have been trying to install anythat will work but none have.  I finally got Ubuntu to start to install but mid way through it started saying that the base system was not installing , then it came up with an error saying something about theit not be an active kernal or something like that so now I am stuck in the install menu.

I have a Acer TravelMate 2480-2874
I repartioned the hard drive to just one partion.
Intel Celeron M processor410
1.46 GHz
Mobil Intel 940 GML Express Chipset
2 gigs memory

1.  Can I undo the half install and still have a bootable computer.

or

2. Can anybody help me firgue out whats going on with the install.

Thank you

---

### Post by mapes12 on 2009-01-14
> **jchastain77 said:**
> Hi I am new to linux and have been trying to install anythat will work but none have.  I finally got Ubuntu to start to install but mid way through it started saying that the base system was not installing , then it came up with an error saying something about theit not be an active kernal or something like that so now I am stuck in the install menu.

I have a Acer TravelMate 2480-2874
I repartioned the hard drive to just one partion.
Intel Celeron M processor410
1.46 GHz
Mobil Intel 940 GML Express Chipset
2 gigs memory

1.  Can I undo the half install and still have a bootable computer.

or

2. Can anybody help me firgue out whats going on with the install.

Thank you

Your system looks more than capable of running Ubu.

Can you get the Live CD to run by booting from the CD drive? That will determine that your machine can run Ubu.

I would recommend looking at the partitioning again. Your HDD will need wiping clean for a fresh Ubu install. The installation CD will do this for you as the default option is "Guided - Use entire disk".

---

### Post by jchastain77 on 2009-01-14
I have tried both the normal and alt iso images. Is that different than the live cd, is that like the DSL live cd.  And I did choose the Guided- entire disk option.

Update
Error message says-
No installable kernal was found in the defined APT sources

no idea

---

### Post by jchastain77 on 2009-01-16
I have totally wiped my harddrive, and tried install Ubuntu again but the screen freezes and the little pointer just sits there and twirls around.

---

### Post by louieb on 2009-01-16
Sounds like a bad burn.  All it takes is a few twisted bits to give weird results. 
Did you run the check media for defects option? Did the CD check out?
[HowToMD5SUM - Community Ubuntu Documentation]("https://help.ubuntu.com/community/HowToMD5SUM") 
[BurningIsoHowto - Community Ubuntu Documentation]("https://help.ubuntu.com/community/BurningIsoHowto") 

Once your sure you have a good CD and your still having problems. Get back with any error messages. There are other tweaks you can try.

---

### Post by jchastain77 on 2009-01-17
I verified both copies I have, I tried both the desktp and alt iso's.  I am going to try and install the desktop one again.  Thanks

I tried installing again and got these errors which I have included pics of. Thanks

---

### Post by jchastain77 on 2009-01-17
So I tried installing again and it got passed that part now it says there is an error with the select and install software process.

---

### Post by louieb on 2009-01-18
Your not having the usual install problem. Most install problems come from just getting the CD to boot. Those are usually fixed by using a [cheat code at boot]("https://help.ubuntu.com/community/BootOptions"). 

 But your getting into the middle of the install process.  Thats almost always a sign of a bad burn. But don't think that your problem since you verified the CD. Now I wonder about the CD player itself. It may have a bad spot somewhere.  

Try doing a net install using the [mini iso]("https://help.ubuntu.com/community/Installation/MinimalCD"). The iso is only a 9-10 MB download and gets what is needed from the Internet

Or try installing from a USB Stick.
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[http://www.ubuntugeek.com/how-to-install-ubuntu-linux-from-usb-stick.html](http://www.ubuntugeek.com/how-to-install-ubuntu-linux-from-usb-stick.html)

---

### Post by theozzlives on 2009-01-18
Are you using a CD-R or CD-RW???

---

### Post by stalkingwolf on 2009-01-18
Check and clean your CD/DVD Rom.  I have had this problem and have usually
been able to cure it by cleaning the hardware or using another ROM. ( I have an external CD-ROM that usually works.)

---

