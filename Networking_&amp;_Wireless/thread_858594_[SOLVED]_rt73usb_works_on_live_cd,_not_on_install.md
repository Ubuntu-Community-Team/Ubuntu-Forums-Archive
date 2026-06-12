---
title: "[SOLVED] rt73usb works on live cd, not on install"
date: 2008-07-13
forum: Networking &amp; Wireless
---

### Post by kkjaergaard on 2008-07-13
I have a Linksys WUSB54GC with the chipset rt73. The card works on the live CD, but it does not work on a fresh install.

I have no clue about what to do (aka. me being quite a newbie).

---

### Post by Tom--d on 2008-07-13
Install ndiswrapper and use the windows wireless driver on the cd.

It works perfect after :)

sudo apt-get install ndisgtk

this wil install ndiswrapper and all the gui of ndiswrapper.

Then go to System > Admin > Windows Wireless Drivers

Load them in. 
Then go to The network icon.

Bam. You have wireless :D!

---

### Post by kkjaergaard on 2008-07-14
> **Tom--d said:**
> Install ndiswrapper and use the windows wireless driver on the cd.

It works perfect after :)

Is this the way it works on the live cd? Anyway thanks, it works.

---

### Post by Tom--d on 2008-07-16
> **kkjaergaard said:**
> Is this the way it works on the live cd? Anyway thanks, it works.

No. 
On the live CD, it uses the r73usb module but for some reason it as not used it in the installation.

---

### Post by kkjaergaard on 2008-07-19
It seems the bug has been reported and a solution with the native Linux driver is proposed at [https://answers.launchpad.net/ubuntu/+question/5290]("https://answers.launchpad.net/ubuntu/+question/5290"). Some people will definitely prefer using the native Linux driver.

---

