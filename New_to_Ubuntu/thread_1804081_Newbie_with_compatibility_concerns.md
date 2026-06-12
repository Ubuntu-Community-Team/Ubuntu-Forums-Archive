---
title: "Newbie with compatibility concerns"
date: 2011-07-14
forum: New to Ubuntu
---

### Post by imhotep531 on 2011-07-14
I'm putting together a system to run Ubuntu Server and I'm coming from a Windows background so a few things aren't clear to me.  In Windows I'm used to popping CD's in the drive and installing drivers for things like RAID controllers and motherboards.  How does this work in Ubuntu Server which is all command line unless I install the GUI?  I'd rather not install the GUI on a server.

Also, do I need to worry about which CPUs, motherboards, video chipsets, etc are compatible with Ubuntu, or does it "Just work" ?

---

### Post by Mark Phelps on 2011-07-14
In terms of drivers, it's a completely different system with Linux.  The drivers are compiled to run in kernel space, so they are installed automatically when Ubuntu gets installed based on the hardware that gets detected.  You CAN download additional drivers, but it tends to be a lot of work because you usually have to compile them from source. It's not the MS Windows method of stick in a CD and run an app.

As to compatibility, the best way to find out is to boot from a LiveCD of the Ubuntu version you wish to run and see how well it detects the hardware and installs the proper drivers.  And yeah, I know you want to run the server version, but the desktop CD will give you a feel for hardware detection accuracy.

---

### Post by Bucky Ball on 2011-07-14
Unless you are very familiar with the terminal and code (or intend to be) installing a lightweight desktop environment like xfce will make life a lot easier when you're setting up your server. You can uninstall the DE whenever you feel like it, of course. ;)

---

### Post by imhotep531 on 2011-07-14
> **Mark Phelps said:**
> As to compatibility, the best way to find out is to boot from a LiveCD of the Ubuntu version you wish to run and see how well it detects the hardware and installs the proper drivers.  And yeah, I know you want to run the server version, but the desktop CD will give you a feel for hardware detection accuracy.

Thanks.  I was planning to install the latest version of Ubuntu Server which is 11.04.  So would I run a LiveCD of it or of the latest desktop version of Ubuntu?  Sorry for the dumb questions.

---

### Post by 3rdalbum on 2011-07-14
> **imhotep531 said:**
> Thanks.  I was planning to install the latest version of Ubuntu Server which is 11.04.  So would I run a LiveCD of it or of the latest desktop version of Ubuntu?  Sorry for the dumb questions.

Run a live CD of the desktop version. There's no live CD of the server edition.

---

### Post by Bucky Ball on 2011-07-14
LTS (long-term support) releases recommended for servers/production machines. 10.04 LTS would be my choice (supported until April 2015). Probably Ubuntu 10.04 LTS Server using xfce4 desktop environment, but that is me. ;)

---

### Post by imhotep531 on 2011-07-14
Thanks for the help guys.  I'll take your collective advice and get started.  I ordered some components from Newegg with positive feedback from Ubuntu users.  I feel pretty good about the mobo/CPU/RAID controller I'll be using.

---

### Post by Bucky Ball on 2011-07-14
Just fyi:

[http://www.ubuntugeek.com/the-ubuntu-release-cycle.html](http://www.ubuntugeek.com/the-ubuntu-release-cycle.html)

Good luck with it and post a new thread with further issues. ;)

---

### Post by imhotep531 on 2011-07-19
I've got all my new hardware put together and I'm ready to boot a live CD and confirm everything is recognized.  I'd like to use 64-bit Ubuntu 10.04 LTS but the site recommends 32-bit instead.  Should I go with 32-bit and why?

Here's the hardware if it matters:

Intel Celeron E3400 Wolfdale 2.6GHz 1MB L2 Cache LGA 775 65W Dual-Core
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819116348](http://www.newegg.com/Product/Product.aspx?Item=N82E16819116348)

Foxconn G41MXE-V LGA 775 Intel G41 Micro ATX Intel Motherboard
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813186202](http://www.newegg.com/Product/Product.aspx?Item=N82E16813186202)

RAID controller card
[http://www.newegg.com/Product/Product.aspx?Item=N82E16815124027](http://www.newegg.com/Product/Product.aspx?Item=N82E16815124027)

4GB RAM
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820231253](http://www.newegg.com/Product/Product.aspx?Item=N82E16820231253)

Thanks again.

---

### Post by Roasted on 2011-07-19
Ubuntu only recommends 32 bit because that's what a LOT of users still have. A lot of users do not have 64 bit compatible processors. It's not that Ubuntu thinks 32 bit is better or anything, but 32 bit is a bit more well rounded.

I mean, think about it like this. 32 bit can run on a 64 bit processor. 32 bit can run on a 32 bit processor. However, you NEED 64 bit processor to run 64 bit Ubuntu. That said, 32 bit is the winner for being the most compatible to EVERYBODY's hardware.

Personally, I always run 64 bit unless I'm working with very *very* old hardware. I don't think you'll have an issue with 64 bit on your hardware.

Also, the users that posted above about the drivers are correct, in that they are packaged within the kernel itself. It makes things much easier for the end user, however there are some oddballs out there, such as video drivers that often aren't packaged automatically and must be installed after the installation completes. Don't worry about that, though, as most times the hardware driver manager comes to you saying there is a driver available for your Nvidia graphics card, etc. In my six years of running Linux, graphics drivers (and the occasional Broadcom wireless card driver) are the only drivers I've had to get, and they came to me with ease of installation. Not all drivers are like that, but most of the necessities are.

That said, I noticed you spoke about RAID. I personally use software RAID built into Linux via "mdadm". There are no drivers needed for that since it is software based. Now if you have a hardware RAID controller in your system, Ubuntu should already see the drive array accordingly. Example, if you have a RAID 1 mirror with two 500gb drives, Ubuntu should only see 1 500gb disk space and install accordingly, just as you want it.

Welcome to the Ubuntu forums. If you approach the Linux world with an open mind and have the patience to learn, you're going to be amazed with what you find here. It's really a unique and solid platform. Good luck!

---

### Post by imhotep531 on 2011-07-19
Roasted, thanks for the feedback I really appreciate it.  Building on the RAID topic, I'm all ears if you have any advice on the following.

My main goal for this server box is a home NAS.  I was looking into FreeNAS for awhile, trying to figure out if I could run it as a VM using VirtualBox and Ubuntu, until someone said "hey, you can do all of that, or you could just run Ubuntu Server and SMB and basically have a NAS like any other network share".  Sounds good to me.  So I will indeed have RAID 1 with two 500GB drives as the main volume for my NAS.  I plan to install the OS on a separate 80GB drive.

I used to have these same two drives as RAID 1 using Silicon Image software, but it was a little finicky and I always wished I could run hardware RAID instead.  That way, like you said, the OS sees a single volume and hardware does the rest.  So that's what I'm hoping to do this time around.  But that's not to say I have anything against mdadm.  Everything I have read says its solid and easy to configure.  I'm just really interested in getting hardware RAID up and running for once.

Thanks again.

---

### Post by imhotep531 on 2011-07-19
After reading my reply again I realized something might not be clear.  I have abandoned the idea of using FreeNAS and am working towards sharing out the raided volume via SMB, just in case that was muddled.

---

### Post by Bucky Ball on 2011-07-19
64bit. Go for it. Boot from the LiveCD and see how you go. You can check most problems you might have that way before installing. Research some fixes if you need to, install and fix them!

---

### Post by Roasted on 2011-07-19
> **imhotep531 said:**
> After reading my reply again I realized something might not be clear.  I have abandoned the idea of using FreeNAS and am working towards sharing out the raided volume via SMB, just in case that was muddled.

I too was in your shoes, and I dumped FreeNAS in favor of just using Ubuntu for several reasons.

[LIST]
FreeNAS's attracting point is the ZFS file system. ZFS requires a ton of RAM to work properly. Meanwhile, an Ubuntu file server with software raid can run on a lot less RAM.
[/LIST][LIST]
FreeNAS seems to be in an identity crisis, with two variants of it out (0.7.2 and 8.0) with a mixture of tension, between community development of 0.7.2 and IXSystems development of 8.0. Just sounds a little "ehh" to me.
[/LIST][LIST]
Oracle bought Sun, who created ZFS. Oracle is closing the source, and thereby two forks will exist. Open ZFS and closed ZFS. Way to be a dumb ***, Oracle.
[/LIST][LIST]
I ran into a bug where I could not back up more than 575 files to a CIFS/Samba share on FreeNAS. It was a common bug that was being worked on, but it was the last thing I wanted to deal with when I knew CIFS/Samba worked perfectly on a Linux based file server.
[/LIST]

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

I used this link. You can install software RAID on the fly during the installation, but only if you use the Alternate CD. You can also install software RAID on a regular instance of Ubuntu, but not until the installation is complete. I've done it both ways. If you're not afraid of terminal, then it won't be hard to set it up manually. Like, no joke I think it was 4 or 5 commands I used total, which you can see at the bottom of that link. If I recall, I just installed mdadm, added sdb1 and sdc1 to the array, at some point I selected the type of raid I wanted (in my case, raid 1 mirror) and then using the cat /proc/mdstat command I could see the status of the array in terms of how built it was. The first time it takes a while to build the array and get it going. Afterwards, it works like a champ. It does appear as if most of those commands are maintaining an existing array, though. I think I ran a command like this to start it:

sudo mdadm --create /dev/md0 --level=1 -metadata=1.0 --raid-devices=2 /dev/sda1 /dev/sdb1

level=1 being raid1, if I recall. --raid-devices=2 meaning two disks, and /dev/sda1 and /dev/sdb1 are my two disks in question. That creates /dev/md0 which is your array to the two disks you're using. I also used the mdadm man page quite a lot for learning the switches in these commands, which you can find in terminal by running man mdadm.

I've also heard Ubuntu's Disk Utility can handle software RAID, but I'm not entirely sure about that.

---

### Post by imhotep531 on 2011-07-19
Yeah ZFS never sat well with me, especially now that FreeNAS seems to be abandoned in favor of OpenNAS which you can't get yet....?  I did however enjoy the claims that ZFS is capable of holding more data than Earth can physically support.  Something about boiling the oceans and vaporizing all viable matter and converting all of it into stable media....and still there wouldn't be enough storage space to max out a ZFS volume.  That's neat, but all you'd have a is a planet-sized NAS with lots of bugs.

I'll report back after I play with the live CD and then attempt to fire up hardware-based RAID on an installation of Ubuntu Server.

---

### Post by imhotep531 on 2011-07-19
Ok I've hit my first problem.  I went ahead and started a separate thread:

[http://ubuntuforums.org/showthread.php?p=11065596#post11065596](http://ubuntuforums.org/showthread.php?p=11065596#post11065596)

---

