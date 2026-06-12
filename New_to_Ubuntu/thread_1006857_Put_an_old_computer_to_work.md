---
title: "Put an old computer to work"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by WillT87 on 2008-12-09
I have an old computer and i wanted to put it to work as a file\printer server. what is the best type of linux to put on it

Specs intel celeron 800mhz 192mb ram 80gb hdd

Sorry if this is the wrong section

---

### Post by gettinoriginal on 2008-12-09
Here is a discussion you might find interesting    Good Luck :p

[http://www.linux.com/forums/topic/1549](http://www.linux.com/forums/topic/1549)

---

### Post by ibutho on 2008-12-09
Any distro will do as long as you don't try to run a heavy GUI like GNOME or KDE because performance will not be very good due to the amount of ram you have. Just pick a distro you are comfortable using. I put Ubuntu Server edition on an old PIII with 128MB ram. I use it mainly as a print and dhcp server and it works really well.

---

### Post by fluxlizard on 2008-12-09
pcfluxboxos
 or
sam linux

both will work great with those specs and you can run anything on it with them- open office, gimp, firefox and they will run quite comfortably.

---

### Post by WillT87 on 2008-12-09
Are there guide/programs to set this up?
In windows it was a 3 or 4 click process

---

### Post by stalkier on 2008-12-09
> **WillT87 said:**
> Are there guide/programs to set this up?
In windows it was a 3 or 4 click process

You will just download a distro and burn the app to a disc. Boot the PC with the disc in and then just format the hard disk and install like you would a Windows install. Very easy.

---

### Post by WillT87 on 2008-12-09
Ive installed ubuntu before but how would i set up a file/printer server

---

### Post by stalkier on 2008-12-09
> **WillT87 said:**
> Ive installed ubuntu before but how would i set up a file/printer server

Ah sorry for the misunderstanding. I cannot help with that as I have never done it before.

---

### Post by WillT87 on 2008-12-09
would this work?

[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/cups.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/cups.html)

are there any differences from server and desktop version of ubuntu

---

### Post by theozzlives on 2008-12-09
> **WillT87 said:**
> I have an old computer and i wanted to put it to work as a file\printer server. what is the best type of linux to put on it

Specs intel celeron 800mhz 192mb ram 80gb hdd

Sorry if this is the wrong section

I have a PII 333 MHz, 256 MB RAM, 35 GB HD I use as a print server and sharing my scanners over the network and it's running Ubuntu, with GNOME.

---

### Post by ibutho on 2008-12-09
> **WillT87 said:**
> would this work?

[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/cups.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/cups.html)

are there any differences from server and desktop version of ubuntu
That should work, for setting up the print server. For setting up the file server, take a look at the articles [here]("https://help.ubuntu.com/8.10/serverguide/C/index.html"). You probably need to look at the articles relating to SAMBA.

---

### Post by rev0lv3r on 2008-12-09
Personally

If I were you I would google for "freenas"
Download the iso
Burn it to a disc
Put it into the computer
Boot from it and setup RAID 1 and call it a day

Turn on the FTP services, and maybe samba services
That way you can access your files through ftp or through samba (windows file sharing)
I am not sure re: print servers
I bet it is easy to do (but that might be difficult only because of finding drivers)

I have a cheap Gateway (yes, I know, it's a Gateway) 950mhz computer.
I bought a cheap SATA raid card that'll do RAID 1. I bought 2 500gb harddrives for 60$ each and now all my photos and files are secure.

They say that 1 drive can fail, and I'll still have 100% of my information
Raid 1 is also called "mirroring"

---

### Post by WillT87 on 2008-12-09
I only have 192mb of ram and i got an error saying I should have atleast 256mb and It may crash

I continued anyways. will ubuntu still run normally

---

### Post by theozzlives on 2008-12-09
> **WillT87 said:**
> I only have 192mb of ram and i got an error saying I should have atleast 256mb and It may crash

I continued anyways. will ubuntu still run normally

If the install crashes, use the alternate CD.

---

### Post by WillT87 on 2008-12-09
> **rev0lv3r said:**
> Personally

If I were you I would google for "freenas"
Download the iso
Burn it to a disc
Put it into the computer
Boot from it and setup RAID 1 and call it a day

Turn on the FTP services, and maybe samba services
That way you can access your files through ftp or through samba (windows file sharing)
I am not sure re: print servers
I bet it is easy to do (but that might be difficult only because of finding drivers)

I have a cheap Gateway (yes, I know, it's a Gateway) 950mhz computer.
I bought a cheap SATA raid card that'll do RAID 1. I bought 2 500gb harddrives for 60$ each and now all my photos and files are secure.

They say that 1 drive can fail, and I'll still have 100% of my information
Raid 1 is also called "mirroring"


This computer doesn't even have SATA its so old
It doesn't really matter but whats the difference from raid 0 1 and 5

---

### Post by ibutho on 2008-12-09
> **WillT87 said:**
> I only have 192mb of ram and i got an error saying I should have atleast 256mb and It may crash

I continued anyways. will ubuntu still run normally
The server cd installs in text mode, so does not require as much ram as the live cd. I've installed it on a system with 128MB of ram and the installation worked fine for me.

---

### Post by rev0lv3r on 2008-12-09
You can do it on IDE
I just wanted SATA since it was relatively cheap

RAID 0 = striping
This is fast, but dangerous. If a drive dies, you lose ALL your data
Raid 1 = mirroring
This is semi-fast but safe. If a drive dies, the other drive is a 100% exact copy. Replace the failed drive and the array will be rebuilt
Raid 5 = Striping with parity
This means 1/nth of your drives are dedicated to parity so you can lose 1 drive and still recover that data
However, these days since drives are so big, the statistical mean time between failures of similar batched drives are so close to each other that the probability of two similar drives failing within the time of recovery is supposed to be near 1.

ZFS is supposed to be the next-big thing.

---

### Post by WillT87 on 2008-12-09
found my problem... 
[http://www.ubuntu.com/products/WhatIsUbuntu/serveredition](http://www.ubuntu.com/products/WhatIsUbuntu/serveredition)
if you click Download ubuntu server edition at the very bottom it takes you to the desktop download

i am going to download the server iso  and call it tonight ill be back after school tomorrow

---

### Post by WillT87 on 2008-12-10
When I was prompted to select which server type I wanted I installed a mail server instead of a print server how can I fix this.

---

### Post by rev0lv3r on 2008-12-10
There is not much difference between server edition and desktop edition
The main difference is that the GUI is not installed by default on the server edition
Just FYI

BTW: I think you try looking for "tasksel"
[https://help.ubuntu.com/community/Tasksel](https://help.ubuntu.com/community/Tasksel)

---

### Post by ayoung on 2008-12-10
> **WillT87 said:**
> Ive installed ubuntu before but how would i set up a file/printer server

The two programs (aside from core Ubuntu server functionality) you're after are cups and nfs: [http://ubuntuforums.org/showthread.php?t=310450](http://ubuntuforums.org/showthread.php?t=310450) and [http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

---

### Post by WillT87 on 2008-12-10
Im trying to set up my static ip how do I save in GNU nano 2.0.7

---

