---
title: "Home server questions"
date: 2010-01-23
forum: New to Ubuntu
---

### Post by Rayve on 2010-01-23
I was planning on making a small home server, just a place to keep media files, mainly, and make them available to the other computers in my house (an Ubuntu machine and an iMac) as well as room for basic backups.  This is the build I was thinking of:

Rosewill FB-01 Black ATX Mid-Tower Computer Case
Western Digital 1TB RE3 7200RPM HDD (x2 for a Raid1 setup)
Thermaltake TR2 600W ATX 12V PSU
OCZ Reaper 2x2GB (4GB total) DDR2 1066 desktop memory
ASUS P5KPL-AM EPU LGA 775 Intel G31 Micro ATX Motherboard
Intel Celeron E3200 Wolfdale 2.4GHz LGA 775 65W Dual-Core Processor

I know that installing a server software-wise is different, in that there is no graphic display only command line, but the insides of the computer are still the same, right?  Do I need to get a server processor just for a home network?

Anything I'm forgetting/should know about?  :)  I have an old keyboard and monitor I can switch to use for the server, and then I believe I can ssh in from another computer once everything is set up, so I'm not worried about ordering those parts specifically for the server machine.

Does anyone have any good reading links?  Most of the server stuff I've read so far has been for Apache/MySQL/etc, but I just want a simple home network server. 

Thanks!
[]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819116265")

---

### Post by theozzlives on 2010-01-23
> **Rayve said:**
> I was planning on making a small home server, just a place to keep media files, mainly, and make them available to the other computers in my house (an Ubuntu machine and an iMac) as well as room for basic backups.  This is the build I was thinking of:

Rosewill FB-01 Black ATX Mid-Tower Computer Case
Western Digital 1TB RE3 7200RPM HDD (x2 for a Raid1 setup)
Thermaltake TR2 600W ATX 12V PSU
OCZ Reaper 2x2GB (4GB total) DDR2 1066 desktop memory
ASUS P5KPL-AM EPU LGA 775 Intel G31 Micro ATX Motherboard
Intel Celeron E3200 Wolfdale 2.4GHz LGA 775 65W Dual-Core Processor

I know that installing a server software-wise is different, in that there is no graphic display only command line, but the insides of the computer are still the same, right?  Do I need to get a server processor just for a home network?

Anything I'm forgetting/should know about?  :)  I have an old keyboard and monitor I can switch to use for the server, and then I believe I can ssh in from another computer once everything is set up, so I'm not worried about ordering those parts specifically for the server machine.

Does anyone have any good reading links?  Most of the server stuff I've read so far has been for Apache/MySQL/etc, but I just want a simple home network server. 

Thanks!
[]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819116265")

You don't need a server, just setup a peer-to-peer network and create a folder (or folders) to share. You'll need Samba to share with Windows.

---

### Post by Rayve on 2010-01-23
theozzlives,

Thanks!  How do I go about setting up a p2p network?  Just with an Ubuntu and an iMac.

---

### Post by acho on 2010-01-23
Try this.......

[https://help.ubuntu.com/community/P2PHowTo]("https://help.ubuntu.com/community/P2PHowTo")

:KS

---

### Post by mick222 on 2010-01-23
> **acho said:**
> Try this.......

[https://help.ubuntu.com/community/P2PHowTo]("https://help.ubuntu.com/community/P2PHowTo")

:KS

Thats for filsharing he wanted to know how to share files between his own computers. You could look here might help [https://help.ubuntu.com/community/HowToZeroconf](https://help.ubuntu.com/community/HowToZeroconf)
or look at samba but i dont know if that works on mac and it can be quite complicated.Someone more knowledgable will probably reply.

---

### Post by acho on 2010-01-23
> **mick222 said:**
> Thats for filsharing he wanted to know how to share files between his own computers. You could look here might help [https://help.ubuntu.com/community/HowToZeroconf](https://help.ubuntu.com/community/HowToZeroconf)
or look at samba but i dont know if that works on mac and it can be quite complicated.Someone more knowledgable will probably reply.

yups, u'r right... :D  I think there is a link going to Bonjour for mac networking....

[http://developer.apple.com/networking/bonjour/index.html]("http://developer.apple.com/networking/bonjour/index.html")

---

### Post by Rayve on 2010-01-25
Thank you, all!  :)  I'll do some more research on setting up the p2p network here at home!

Related to that: my Ubuntu machine, which will be connected to the Internet and the home network, is going to be using two 10,000 RPM HDDs in a RAID0 for gaming.  Can I throw a 2TB HDD into that machine and make it the shareable one (if I understand sharing files are what the p2p network is all about), or will that disturb the RAID?

---

### Post by Paqman on 2010-01-25
> **Rayve said:**
> 
Related to that: my Ubuntu machine, which will be connected to the Internet and the home network, is going to be using two 10,000 RPM HDDs in a RAID0 for gaming.

First of all: Ubuntu for gaming? Really?
Secondly: if you want high disk performance for gaming, you might want to look at an SSD instead of RAID0. It'd be faster, simpler, _much_ more reliable and might even be cheaper than two 10,000RPM disks...

---

### Post by CharlesA on 2010-01-25
You can add another hard drive without it interfereing with any current RAID set up.

Why are you going to use two 10K drives in RAID 0 for gaming?

---

### Post by Rayve on 2010-01-25
I read a book about building a gaming computer... should I not use the RAID setup?

---

### Post by Paqman on 2010-01-25
> **CharlesA said:**
> Why are you going to use two 10K drives in RAID 0 for gaming?

High throughput = lower loading times.

The trouble with RAID0 is that it doubles your chance of a hard drive failure causing data loss. Never put anything precious on that kind of array.

---

### Post by Rayve on 2010-01-25
Would the best bet be to stick with one 10K HDD then?  Will I still see a significant increase in loading speed?

---

### Post by Paqman on 2010-01-26
> **Rayve said:**
> Would the best bet be to stick with one 10K HDD then?  Will I still see a significant increase in loading speed?

Single 10,000RPM = Faster than 7,200RPM
10,000RPM RAID0 = Faster than single 10,000RPM
Single Indilinx or Intel SSD = Faster than 10K RAID0

But in terms of reliability the RAID array is _twice_ as likely to fail. That's because either drive failing will take down the whole array. 

As for price, here in the UK Velociraptor 150GB 10K drives seem to go for about £115, so you're looking at £230 for your RAID0. You could get a 120GB Indilinx SSD for £202, or one of the awesome Intel drives for £320.

Go for a single 10K drive if you want lots of storage, since big SSDs are eye-wateringly expensive. If you want performance forget RAID0 HDDs and go for an SSD.

---

### Post by J V on 2010-01-26
SSD is much faster, if you are willing to pay for hardware for "teh ultimot gamez" you should stick it all in a new computer, stick windows on it, and use a kvm, ubuntu is good, but its far from all games compatible...

---

### Post by CharlesA on 2010-01-26
> **Paqman said:**
> High throughput = lower loading times.

That's true, but I suppose it's a trade-off of price vs speed.

It would definitely be better just to run off an SSD. Even if they are more expensive.

---

### Post by Rayve on 2010-01-26
I do have a Windows machine that I'm upgrading a bit, but it's going to be for offline gaming.

I've decided I'll still buy the two 10K 300GB drives I was planning on, but instead of RAID'ing them, I'll put one in the Linux machine (the one I'm building) and one in the Windows... if I start wishing I had more speed (unlikely, honestly, because the comp I'm building is a massive upgrade from what I have now) I'll consider an SSD at that time.

Thanks, everyone!

Edited to bring this back on Home Server topic: do I need to format my file-sharing drive a certain way so it can be read by both Mac and Linux?  Or, because the Mac will be accessing files over the network and not physically reading the drive, does it not matter?

---

### Post by Paqman on 2010-01-26
> **Rayve said:**
> do I need to format my file-sharing drive a certain way so it can be read by both Mac and Linux?

Nope, the filesystem of the actual storage device doesn't matter at all, since the files will be accessed through a network protocol. Probably the most universally compatible protocol is SMB/CIFS. It's native to Windows, and on Ubuntu you just need to install smbfs to mount SMB/CIFS shares. I'm not gripped up on OSX, but I can't imagine it'd be too hard.

---

### Post by jd65pl on 2010-01-26
I'd check this out if you want to use your system to back up your mac using time machine. Its also good for using afp to share files with your mac as a supplement to smb for windows

[http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/)

---

