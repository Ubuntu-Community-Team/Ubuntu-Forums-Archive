---
title: "Ubuntu won't work with IDE"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by Gp. on 2009-04-03
Hi,
In my system all my devices except one are Sata 2 connections.

One of my DVD readers is an IDE. I've had to disable it because when I tried to install Ubuntu it wouldn't work if it wasn't disabled and now that Ubuntu is installed, if I re-enable it it won't boot.

The errors I get are seen here:

[http://ubuntuforums.org/showthread.php?t=1052987](http://ubuntuforums.org/showthread.php?t=1052987)

Any light on getting this drive to work with Ubuntu?

---

### Post by gn2 on 2009-04-03
Does it have the jumper set correctly and have you tried changing it?

---

### Post by presence1960 on 2009-04-03
> **gn2 said:**
> Does it have the jumper set correctly and have you tried changing it?

I agree that the problem **_most likely_**lies with something like the jumper, possibly your cable or something to do with your drive. I have an IDE HDD, SATA HDD and an IDE DVD-RAM drive on my machine. My daughter has an IDE HDD and an IDE DVD-RW drive on her machine. They all work fine. I wish I had more info to give you.

---

### Post by Gp. on 2009-04-03
The jumper settings are fine, and windows doesn't have a problem with it.

---

### Post by gn2 on 2009-04-03
By "fine" do you mean that it's on cable select, or is it properly set for master or slave?

Tried changing it?

---

### Post by Malalo on 2009-04-03
I had a similar problem which I resolved by flash my mobo the latest BIOS update. At first, Cable Select was "iffy", but after the BIOS flash all went well.

---

### Post by Gp. on 2009-04-03
It's set to master and it's at the end of the cable.

---

### Post by anewguy on 2009-04-03
Do you any other drives on that channel?  I ask because I had a similar problem when I tried to install on an old computer (not saying yours is old, just that the one I was trying was;) ).  It turned out to be a combination of 2 things:

- couldn't be on cable select (you appear not to be using this anyway)

- couldn't be master and try to boot from it. I had to make it the slave and add my CD-Rom drive to that channel as master, and then boot from the CD-Rom drive.

I don't know why - just happened that way.  I suspect it was something in the BIOS for the motherboard, but the motherboard was old and no new updates for the BIOS for several years.

Are you trying to boot the install disk from that drive? Does your BIOS have the option to boot from DVD or does it just say CD-Rom?  I don't know if that makes any difference or not either.  My "good" PC - only 6 months old now - only has a DVD-RW dual-layer in it, and it boots fine from the DVD drive - that's why I'm only guessing that perhaps it is a BIOS issue.

Best of luck!
Dave :)

---

### Post by Gp. on 2009-04-11
The problem is not the drive, it's my motherboard.

Issue for a few people with the EP45-DQ6 motherboard. :(

---

