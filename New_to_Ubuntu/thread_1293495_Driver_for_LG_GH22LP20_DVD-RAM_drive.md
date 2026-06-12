---
title: "Driver for LG GH22LP20 DVD-RAM drive"
date: 2009-10-17
forum: New to Ubuntu
---

### Post by windyrij on 2009-10-17
Hello:
Ubuntu 8.04, Kernel Linux 2.6.24-24 generic, GNOME 2.22.3, 503 MB memory, AMD Duron 850. EPOX ATX motherboard EP-8KTA3L

I replaced one of the 2 optical drives on the Secondary IDE with a LG GH22LP20, as master (master selected on drive). The ribbon cable is 40 conductor, until I can get an 80 conductor.

Under Windows 2000 on the same system, the drive reads CDs and DVDs ok. Under Ubuntu, no luck - the drive cannot be mounted.

Device Manager returns the following info:
DVD-RAM GH22LP20
Vendor HL-DT-ST
Device File /dev/scd0
Firmware Version 1.03

A search on Google returns Windows drivers, but no Linux/Ubuntu drivers.

Can anyone help?


Many thanks,   windyrij

---

### Post by nhasian on 2009-10-17
are you sure you have one device set to master and the other set to slave?  both devices are on the same ribbon?  Can both devices be detected by the bios during bootup?

If all is good, can you boot from an Ubuntu 9.10 LiveCD?

Another even better test would be if you could put the Ubuntu 9.10 live on a usb thumbdrive with unetbootin.  then the cd drive would be free for testing.

---

### Post by Big_Croc7 on 2009-10-17
[deleted]

---

### Post by windyrij on 2009-10-18
Many thanks, nhasian, for responding:

> **nhasian said:**
> are you sure you have one device set to master and the other set to slave?  both devices are on the same ribbon?  Can both devices be detected by the bios during bootup?

If all is good, can you boot from an Ubuntu 9.10 LiveCD?

Another even better test would be if you could put the Ubuntu 9.10 live on a usb thumbdrive with unetbootin.  then the cd drive would be free for testing.

1. Yes, the system has 2 drives,CD-RW and DVD-RW oith of which were working, the DVD drive failed after putting in a second cd in top of one already in there (by mistake!). Both on the same ribbon (secondary IDE). The new drive was set to master, like the one it replaced.

2, Yes, I can. Only dowloaded and burnt a 9.04 Live CD today. I booted from the Slave CD-RW drive. I can now read the new drive CDs and DVDs. This cannot be done with a 8.04 Live CD. Interestingly, booting from a Damn Small Linux CD, again in the slave drive, also allows me to access this new drive.

3. Due to the Award BIOS in the system, it won't boot from USB, as I found when I made a DSL USB boot drive, which worked in a friend's system.

Looks like 9.04 has the driver. However, I went for 8.04, since it has LTS, and suspect I may have issues with some apps if I migrate. I'll probaly install 9.04 in a second partition, and check it out.

Many thanks, again

windyrij

---

### Post by nhasian on 2009-10-19
No need to muck around with 9.04 anymore.  Go ahead and throw Karmic Koala 9.10 on there instead.

---

### Post by dude123dude on 2012-09-30
This thread is mega ancient, but I feel the need to answer and close it. :popcorn:


I have precisely LG GH22LP20, its an IDE burner. And I experience the same thing with MediBuntu.

[SIZE=3]**Most important foremost: What should you do. **[/SIZE]

**You should throw it in the trashbin** and get good drive. I have another machine with Pioneer drive, that works flawlessly.

You can also connect to another machine with good burner via NFS or SMB and get the files.

You could also try to (re)burn your media with ISO(if you get along) or older UDF using drive that can read it. I suspect the original reason behind this, is that the drive does not support more advanced more recent (we speak about 2005 and up..) UDF filesystems. Precisely prior to 2.0.

[SIZE=3]**The reason:**[/SIZE] The reason is that LG drive somehow refuses not read **BURNED DVD** (+/- R, RW; TDK, Verbatim, Maxell) media. You can clearly see it in GNOME Disk Utility, that discs don't get recognized.

This is not driver problem.
This is not linux problem.
This is not mechanical/physical problem.
This is not problem with firmware.
This is solely internal drive problem.

You will have **no** problems with **factory burned** DVD, DVD-Video, CD, CDAudio or **home-burned CD**. I will continue on experimenting, like burning media with LG GH22LP20 and checking it with qPXTool, comparing the quality and results with my Pioneer(and older media from Plextor PX-712). Will report later if I get more positive results.

**[SIZE=3]What did I try:[/SIZE]**
I did not try LG in windows, because I have no need for the later. The same media however is recognized with Pioneer under Medibuntu and LMDE.

GNOME Disc Utility is also quite awesome tool, I was able to find out that the drive has old firmware and searched for the newer one. The 2.00 version is provided, however LG is stupid enough to provide windows-only all-in-one executable. Thats right, you can't update the drive from Freedos, Dos, Linux, Mac or anything else. Only from Windows. There is a project named Flasher to automatically extract firmware from executable and patch the drive under Linux/Mac, but it was not updated since 2010, and this LG drive is not supported.

So I went on, got windows mini-livecd, thrown firmware there and patched the drive with 2.0. Ofc I removed the mini-livecd after that because that was "compile dependency". When I have no freedom, it is not my problem.

So, the effect was simply .. absent. Same behaviour.

I have also disassembled the drive, cleaned the lens (idea is that much tinier DVD frequency laser is much more susceptible to dust on the lens). No effect. Also, normal movie dvds, protected or not, **are recognised** by the drive under Linux. Burned DVD+/-R/RW not.

So here we go. I hope this historical post will save some many headaches[SIZE=3] **and remind dear LG engineers how stupid they are due to supporting only windows firmware update paths**[/SIZE]. They get **no** money from me from now on. Same as logitech craptoids and gigabyte (although gigabyte is still "acceptable").

---

### Post by oldos2er on 2012-09-30
Please don't bump old threads. From the Code of Conduct:

If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

