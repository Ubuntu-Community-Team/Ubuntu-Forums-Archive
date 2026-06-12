---
title: "Ubuntu compatible external HDD"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by taminrob on 2009-02-17
Need a good external HDD. It will only be used for my Ubuntu system but in looking at several (really like the Western Digital "MY Book World Edition - 1TB) they only list Windows and Mac compatibility (not surprised by this in the slightest) and I would like to make sure that it installs with minimal fuss or tweaking...any suggestions?

---

### Post by Cypher on 2009-02-18
When the manufacturers list Windows and Mac compatibility, it's usually for some extra software that's included in a product. In the case of the WD My Book, once you plug it into a Windows or Mac machine it will install some software that will give you an icon in the taskbar to give you basic information about the My Book. Plus, you can use that application to control the LEDs and other things on the My Book.

All of these extras are going to be missing in Linux, but that doesn't mean that the drive won't work in Linux. Virtually all the external HDDs out there use either USB or Firewire as the interconnect to the PC. So as long as your computer has one or both of these interfaces (you definitely have USB) then you can use the HDD.

---

### Post by superprash2003 on 2009-02-18
since its only for linux you could use the EXT filesystem

---

### Post by crho85 on 2009-02-18
I just want to chime in here. I have a WD Mybook and linux (intrepid) says it cannot mount. I check the details it lists an error with an improper windows shut down. 

Any clues or ideas?

---

### Post by superprash2003 on 2009-02-19
connect it to a windows machine and use the safely remove hardware option and then plug it back into ubuntu

---

### Post by egalvan on 2009-02-19
> **taminrob said:**
> Need a good external HDD. It will only be used for my Ubuntu system (really like Western Digital "MY Book World Edition - 1TB) only Windows and Mac compatibility () I would like to **make sure that it installs with minimal fuss or tweaking**...any suggestions?

It can. But  most Microsoft-type drives have a space in the name...
this can cause headaches to Linux.

I would buy it from someone who has an iron-clad no-excuse full refund policy.
If it does not work, just return it, state "it did not work".
DON'T mention Linux.

I purchased an external enclosure, and a separate drive.

Used  dban to make sure it was empty.

Used Partionmagic LiveCD to partition and format to ext3.

I named my drive:

750g-data1

the "750g" refers to the marketing size.
the "data1" refers to the contents, ( "1" in case i ever get another 750g drive).

Maybe someone can chime in here on how to set the **"reserved blocks"** option for ext3 data drives.

---

### Post by RaZoR1394 on 2009-02-20
I can't mount my WD My book 1TB with eSATA but it works with Firewire 400 and USB 2.0. The eSATA port works with my Revoltec enclosure.

I backed up the files on the drive and then I removed the partition and formatted to ext3.

How do I make eSATA work?

---

### Post by CryNGRoad on 2009-07-12
I just bought a Western Digital My Book Home Edition 1TB (USB 2.0, Firewire 400, eSATA).

On Ubuntu 9.04 using Firewire, it worked out of the box with one small problem. When the computer goes into suspend mode, the drive powers down and on resume, it powers back up, but then the computer hangs with a black screen. Not using suspend isn't that big of a deal, though.

Now I just need to determine the best file system to use for reliably storing photos and videos.

---

