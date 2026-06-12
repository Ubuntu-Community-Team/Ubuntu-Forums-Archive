---
title: "no such device. NEED SERIOUS HELP!"
date: 2010-12-04
forum: New to Ubuntu
---

### Post by Jesus's Homie on 2010-12-04
I was Duel booting Windows XP and Ubuntu 10.10. I had Ubuntu 10.10 on a 250GB external HDD and I used the whole 250GB to do it (no partitions) and XP was on the internal 40GB SATA and GRUB2 was the manager. I decided I didn't want Ubuntu anymore so I formatted the 250GB HDD and now when I start my computer I get error:no such device:892ec58c-fb85-4213-9601-e6c07cdb436b. grub rescue>. I cant boot windows because when I formatted the HDD i think it deleted grub and the windows XP boot loader and now I cant boot xp or ubuntu or access the cd rom drive to run the LiveCD or the XP recovery to fix it. Is there anyone out there that knows anything about what is going on and how I can fix this or at the very least does anyone know how to access the bios settings directly from grub rescue>??

---

### Post by asmoore82 on 2010-12-04
Do you get this error if you attempt to boot without the external drive connected?

If so, you need to run `fixmbr` or the Vista equivalent **from a windows boot disc**.

---

### Post by Jesus's Homie on 2010-12-04
Yea with and without.

---

### Post by ikt on 2010-12-04
> **Jesus's Homie said:**
> Yea with and without.

2 ways afaik, reinstall ubuntu on the external drive and run "grub-update" in terminal, or run the xp boot cd, go into recovery console, and type fix mbr or the equivalent as posted above.

---

### Post by Jesus's Homie on 2010-12-04
I got the same error when trying both of those. I cant access ANYTHING my PC is bricked it seems. Nothing happens when I put a cd in the drive and nothing happened when I reinstalled Ubuntu on the ext hdd. I cant even get into my bios anymore.

---

### Post by ikt on 2010-12-04
> **Jesus's Homie said:**
> I got the same error when trying both of those. I cant access ANYTHING my PC is bricked it seems. Nothing happens when I put a cd in the drive and nothing happened when I reinstalled Ubuntu on the ext hdd. I cant even get into my bios anymore.

If you are unable to boot off of a cd, then you need to make sure all your hardware is correctly installed, there might be a loose cable etc.

If you can't get into your bios, try resetting your bios by taking out the battery for a minute.

---

### Post by Jesus's Homie on 2010-12-04
Everything was working perfectly untill I formatted my ext hdd and now I get that error msg and I cant get boot windowsXP and when I try to fix it with the xp installation cd the drive lights up but nothing happens. I also tried reinstalling ubuntu on the ext hdd and that didnt work either. my bios is trying to boot from internal HDD first (from the sounds that my pc is making at start up). I am UNABLE to access my bios setting to change this due to the fact that when the pc comes on it goes straight to the grub error msg.

---

### Post by Jesus's Homie on 2010-12-04
edit - Im on a desktop will jumping the motherboard do the same as taking out the battery as far as resetting the bios goes?

---

### Post by Jesus's Homie on 2010-12-04
I fixed the problem. I had to take the case off of my desktop and unplug the internal hdd to get the bios settings to come up. then change the boot order to onboard cdrom. then repair with fixmbr.
thanks everyone for your help.

---

