---
title: "Cannot see where installation occured"
date: 2010-07-05
forum: New to Ubuntu
---

### Post by pierrefv on 2010-07-05
Hi All
My name is Pierre Viljoen from Durban S.A. and I am a TOTAL newbie!
I am encountering difficulties in the installation of my "10.4 net-book" installation.
I am currently using a "Dell D630 Latitude" with "Windows 7" as my OS.
I downloaded the 10.4net-book installation and burnt it to a DVD.I then proceeded to install it onto my system as an alternative OS as I wanted to try it out before committing to it as my main OS.
After rebooting as required, I could not find where the installation took place, when I insert the disc it asks me if I want to install one of the three options ! I have already done so, have I not? 
Please could someone tell me that it is a typical "id10t" error and how to remedy it, not something major which is going to take tons of time and application to rectify.
Many Thanks

---

### Post by SmokeyThePanda on 2010-07-05
I've never messed with a netbook, but you should be able to find it in your boot menu..When you open up the boot menu, it should give you the option to boot in using Ubuntu or Windows 7.

---

### Post by pierrefv on 2010-07-05
Hi Smokie,
Unfortunately it is not showing any options on booting up, it only asks for my normal Windows Password and then proceeds to Win 7. 
Thanks 
Pierre

---

### Post by SmokeyThePanda on 2010-07-05
I forget exactly how it works...:s I never actually dual booted. I tried it but accidentally deleted my XP partition. Soooo..I forget how to get to the boot menu. I think it's F2 or something, then select hard disk and it gives you your boot options..

---

### Post by yetiman64 on 2010-07-05
If it still boots directly to Win 7 on the HDD, don't worry about your BIOS boot menu (F2 etc), as the hard drive is being booted and Ubuntu isn't likely installed yet. Sounds very much as though you've actually booted the cd to the live cd desktop by selecting the "try without installing" option (probably by accident- hence you may have thought the live cd desktop was the install). 

**Question:** Did you actually get a desktop (and an installer link) or did you go directly to the install program on booting the cd?

To test which is the case run the live cd again (try without installing) and open gparted (not sure how the menus are set up on the netbook version - have a look for "gparted" or "partition editor"). Look at /dev/sda and look for the Ubuntu partitions if any. If unsure, post back screenshots of the gparted interface here. I am assuming you have only 1 hard drive (/dev/sda).

Note, if you've successfully installed Ubuntu and Win 7 on the same machine, then the grub2 boot menu will automatically show during the boot sequence (will time out to the default OS - usually Ubuntu being grub), _hence my thinking that Ubuntu isn't actually installed yet._

Also, although I dual boot on my desktop machine I'm not familiar with the netbook installer and there may be a few differences between it and the desktop installer.

---

### Post by QLee on 2010-07-05
pierrefv,

If you actually havent installed yet, you may want to consider installing the standard version rather than the netbook edition. The netbook edition was crafted with a simple interface to be useful for netbooks with their generally low-end graphics and small screens. You might find you prefer the user experience of the standard edition on your laptop.

---

