---
title: "How to install Ubuntu without installing Windows"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by Godblessme on 2010-07-22
Hi, this is the first time ever I come to this forum. I have installed Ubuntu inside my Windows XP, now I like to know how to install Ubuntu only onto my hard drive without installing XP. I now have wubi.exe and  ubuntu-10.04-desktop-i386.iso in my USB key. Please explain in plain English, because I know nothing about Linus. Thanks.:p

---

### Post by mbzn on 2010-07-22
Hi and welcome to the forum

1. Ensure your BIOS is configured to boot from CD first.
2. insert the Ubuntu CD and boot.
3. Select 'start or install Ubuntu'
4. Double click the icon on the desktop 'install Ubuntu'
5. At partitioning, select use entire disk.
6. now your done..

Any further Questions, you already found the right forum, just ask

---

### Post by Naderovski on 2010-07-22
I don't quite get you. Do you want to keep Windows or not?

---

### Post by nothingspecial on 2010-07-22
Do you intend to wipe windows entirely?

First, make a backup of any data you don`t want to loose to some sort of removeable media, then remove it.

If so install usb-creator from the ubuntu software center. Copy the iso from the usb stick to the computer.

Tell the usb creator to use the iso that you copied. The reason for copying it is that usb-creator will wipe everything from the usb stick.

Then reboot and select boot from usb in your bios, you will have to press escape or one of the F buttons, it should tell you.

Then during the install, at the partitioning section, choose "use entire disk"

[SIZE=4][COLOR=Red]This will completely remove windows and any data you have on your computer[/COLOR][/SIZE]

---

### Post by Godblessme on 2010-07-22
Thanks mbzn, I have wubi.exe and ubuntu-10.04-desktop-i386.iso in my USB key, and I do not know how to make my computer to boot from USB.

---

### Post by Godblessme on 2010-07-22
Thanks for your advice nothingspecial, I will try as you said.

---

### Post by Wim Sturkenboom on 2010-07-22
I have no experience with 10.04 install, but in general:

Burn the ISO to a cd using Nero or Roxio (under Windows). Make sure to burn as ISO / image.
Check afterwards, you should have multiple files on the CD (not just the iso).

Leave the CD in and reboot your PC. Make sure it will boot from CD before HD (check the BIOS if it does not).

You will probably see a menu with some options (in random order):
1) one used to be (or still is) to check CD for defects; run that first.
2) another one that allows you to install Ubuntu; run that after the previous one (if it was succesful).
3) try without installing; you can use that and install from there (instead of using 2)

As I said, no experience with 10.04. Some points however:
1)
I suggest that you create 3 partitions; one for root (/) of about 20-30GB, one for swap (my personal rule: for a desktop 2x size of memory with a max of 1 GB, for a laptop 2x size of memory to allow for hybernate) and the rest for /home
Ubuntu used to allocate only 3 GB for itself (and might still do so), which is not really enough if you want to install some other apps.
2)
When using method 3 for the install, be carefull as installation might take some extra time due to automatic updates if a network is present; you might want to pull the network cable out before you start the install; I had this problem when installing 9.04 on a netbook and did not know what was going on.

Good luck

---

