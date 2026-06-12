---
title: "What to Partition As"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by bob202 on 2009-01-03
I'm trying to install the latest version of ubuntu onto my PC, but I have vista, so I don't want to format my PC's hard drive. I have an external hard drive which my bios recognises as a boot option but the linux partitioner installer doesn't recognise it. It does show  up on the boot from the live CD though... Would creating an unformatted partition in the EHD allow me to install linux on it?

---

### Post by Paqman on 2009-01-03
> **bob202 said:**
> I don't want to format my PC's hard drive.

Have you tried Wubi? It's an install option which allows you to install Ubuntu onto a virtual hard drive located on your existing Windows NTFS partition. No formatting or partitioning involved.

If you already have the LiveCD just put it in while you're in Windows and click the option to "install from within Windows". Couldn't be simpler, really.

---

### Post by bob202 on 2009-01-03
Thanks, but I would like a seperate linux partition, but I don't want it on my internal one, and when I go into to the installer, I don't get the option to install it to the hard drive

---

### Post by cotcot on 2009-01-03
Sure you do not want to touch you internal drive ? 
Using the vista partitioner to reduce a vista partition should be safe. Have you seen [[COLOR="Red"]this[/COLOR]]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm") ?

---

### Post by Paqman on 2009-01-03
> **bob202 said:**
> Thanks, but I would like a seperate linux partition, but I don't want it on my internal one, and when I go into to the installer, I don't get the option to install it to the hard drive

Alright. What about if you go into the manual partitioner? Does it show up in there?

---

### Post by Papa-san on 2009-01-03
You don't have to format your hard-drive to install Ubuntu. What size is the hard-drive?

Yes, What you are looking for will 'show up' there.

You definitely want to separate off some of your hard-drive from _inside of Windows_. If you just format a piece of your drive (What gparted does), Windows isn't going to know what to do with itself next time you boot into it, and you'll be re-installing Windows anyways.

AFTER you have gone into Windows Disk management and have delegated some space for Ubuntu, then you will use either 'Use the largest bit of empty space' (automated) OR do it manually. (I recommend manual)
Then you are going to give Ubuntu an amount that is double the size of available memory for a swap partition. Next, depending on the size of your drive, you will make a root ( / ) partition no less than 4 or 5 gigs.(ext3) and the remaining allocated space should be for a home partition ( /home ).

---

### Post by bob202 on 2009-01-03
Hmm, I went into the standalone installer and it worked perfectly, for some reason when I went into a live CD session the installer didn't list my hard drive. Is this a bug that needs reporting?

---

### Post by abhinavk on 2009-01-03
Read myself made guide to install Ubuntu with Vista (installed first) with having Vista Boot Manager and Vista in Master Boot Record and Vista as default OS
[http://ubuntuforums.org/showthread.php?p=6480975#post6480975]("http://ubuntuforums.org/showthread.php?p=6480975#post6480975")

---

### Post by bob202 on 2009-01-03
well i just fixed Vista Mbr after grub installed on both. thanks for the link just it up and all

---

