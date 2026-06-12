---
title: "Ximeta Net Disk"
date: 2005-05-02
forum: Networking &amp; Wireless
---

### Post by rickwood on 2005-05-02
Does anyone know how to get a Ximeta NetDisk working with Ubuntu?  I see that they have beta drivers on their website for SuSE and Redhat/Fedora.  This driver must be downloaded and compiled.  However, I can't seem to get it to compile under Ubuntu.  Here's what I get:


root@Dad:/usr/src/ndas-0.0.3 # make
make -C /lib/modules/2.6.10-5-686/build \
        SUBDIRS=/usr/src/ndas-0.0.3 \
        KBUILD_VERBOSE=1 \
        ndas_root=/usr/src/ndas-0.0.3 \
        modules
make: *** /lib/modules/2.6.10-5-686/build: No such file or directory.  Stop.
make: *** [/usr/src/ndas-0.0.3/ndas_sal.ko] Error 2


Has anyone made this work yet?  Or, more importantly, has anyone made a deb file of this driver that will work with Ubuntu?

---

### Post by nathanhill on 2005-06-03
I've been wondering the same thing...

I've found a few links showing people trying to build .DEB install (the instructions for building that come with the driver seem to explain RPM building only) in relation to this driver, but I'm too much of a noob to make sense of the info presented.

Here's a link:
[http://lists.debian.org/debian-user/2005/03/msg03958.html](http://lists.debian.org/debian-user/2005/03/msg03958.html)

If you or anyone else figures this out, I'd be very greatful - as I can not use my NetDisk  with Linux right now...

-Nathan

---

### Post by nathanhill on 2005-09-01
Looks like Ximeta has updated their linux driver. (See here: [http://code.ximeta.com/cgi-bin/trac.cgi](http://code.ximeta.com/cgi-bin/trac.cgi))  Now they offer a 'Tarball'.
The only instructions they provide are still the ones for creating RPM's.
Ximeta welcomes any info on how to get the binaries to install on other distribution, unfortunately doing this is a bit beyond my knowledge.

If anyone could can shed some light on how to create a deb install I would be greatly appreciative!

-Nathan

---

### Post by nathanhill on 2005-09-05
Bump...

I could really use a hand...  
I don't know how to build a deb from binaries.

This is the only thing stopping me from using Ubuntu as my daily machine (have a ton of shared files on the Ximeta disk I need to access).

Anyone know where to find instructions (that a noob like me would understand) for doing this?

Any help GREATLY appreciated...

-Nathan Hill

---

### Post by msolano23 on 2005-10-27
I was able to install the software as follows:

1)  Installed alien and rpm from synaptic
2)  Downloaded the fedora core 4 rpm for ximeta netdisk
3)  Executed the .bin containing the rpm to extract it
4)  cd'd into the directory containing the rpm package
5)  Used alien to convert to a deb package as follows:  

     alien --to-deb ndas-0.9.7-2.6.12_1.1369_FC4.46.i586.rpm 

6)  This created the following deb package:  ndas_0.9.7-3.6_i386.deb
7)  Installed this package as follows: 

      dpkg --install ndas_0.9.7-3.6_i386.deb

Getting it to work is a problem I'm still having.  Whenever I try to execute any of the ndasadmin commands, I get:

Failed to open /dev/ndas
Check NDAS device file exists, driver module is loaded and started by administration tool

If anyone knows what I'm doing wrong, please let me know.  Thanks :)

---

### Post by kcarson97404 on 2006-06-05
That's the exact same error I'm getting. I've reported this as a bug, but have yet to hear back from Ximeta. Let's hope we get this figured out soon.

---

### Post by lles on 2006-06-20
[QUOTE=msolano23]I was able to install the software as follows:

1)  Installed alien and rpm from synaptic
2)  Downloaded the fedora core 4 rpm for ximeta netdisk
3)  Executed the .bin containing the rpm to extract it
4)  cd'd into the directory containing the rpm package
5)  Used alien to convert to a deb package as follows:  

     alien --to-deb ndas-0.9.7-2.6.12_1.1369_FC4.46.i586.rpm 

6)  This created the following deb package:  ndas_0.9.7-3.6_i386.deb
7)  Installed this package as follows: 

      dpkg --install ndas_0.9.7-3.6_i386.deb

Getting it to work is a problem I'm still having.  Whenever I try to execute any of the ndasadmin commands, I get:

Failed to open /dev/ndas
Check NDAS device file exists, driver module is loaded and started by administration tool

If anyone knows what I'm doing wrong, please let me know.  Thanks :)[/QUOTE]

Simple, you only installed ndas-admin. You need the kernel module too!

- [http://code.ximeta.com/cgi-bin/trac.cgi/wiki/FedoraCore4](http://code.ximeta.com/cgi-bin/trac.cgi/wiki/FedoraCore4)

/lles

---

### Post by Brandel Valico on 2006-10-24
I had my Net Disk working in Dapper. By Following the instructions found here.

[http://http://code.ximeta.com/cgi-bin/tracX.cgi/wiki/Ubuntu]("http://code.ximeta.com/cgi-bin/tracX.cgi/wiki/Ubuntu")

It claims to work with 6.10 also. But I have yet to try it.

The big problem seems to be that Net Disk only runs with a .686 system and Ubuntu puts out a .386 system Kernel. So it's very important that you download and run the .686 kernel before you even bother installing the Admin program and drivers.

---

### Post by Dr.Calimero on 2006-10-28
> **Brandel Valico said:**
> I had my Net Disk working in Dapper. By Following the instructions found here.

[http://http://code.ximeta.com/cgi-bin/tracX.cgi/wiki/Ubuntu]("http://code.ximeta.com/cgi-bin/tracX.cgi/wiki/Ubuntu")

It claims to work with 6.10 also. But I have yet to try it.

The big problem seems to be that Net Disk only runs with a .686 system and Ubuntu puts out a .386 system Kernel. So it's very important that you download and run the .686 kernel before you even bother installing the Admin program and drivers.

how does one make sure they have the right kernel installed?
thanks
Dr C

---

### Post by Brandel Valico on 2006-11-07
[B]Ubuntu's default kernel is for 80386. but we only provide 686 kernel. so please upgrade your kernel
Kernel ¶

Make sure that you have installed and running i686 kernel
[I]
apt-get install linux-image-2.6.15-26-686[/I]

Then reboot[/B]

The Above will get you the current 686 version they are offering that they claim is compatable.

But I have yet to again try it in anything besides Dapper and Breezy.

---

### Post by simonjudge on 2007-06-22
Anyone any positive experience of getting this (NDAS beta driver) working in feisty?  The HowTo linked above seems a bit scary.... will it work?

I assume it will allow me to access any NDAS device with an NDAS ID?  E.g also a Freecom MediaPlayer?

Cheers,

Simon

---

### Post by pototo on 2007-06-25
I'm using a FREECOM net disk with the Ximeta NDAS drivers, and it works fine. The only issue I've had is I can't write if there's any windows PC using the net disk. When the windows computers are off I can ead/write the disk.

I'm using feisty fawn, and installed the drivers downloading the tarball, make, sudo make install, and then registering the netdisk. I've had no problems during the installation.

---

### Post by claypole on 2007-07-03
I have managed to successfully install the kernel and ndasadmin tool on Ubuntu Studio 7.04 using [http://code.ximeta.com/trac-ndas/wiki/HowToBuildDEB](http://code.ximeta.com/trac-ndas/wiki/HowToBuildDEB).  I had to reboot after installing the kernel module before the ndasadmin install would work.

I haven't actually tested it yet (I have an MVIX-760HD) but I will report back.

---

### Post by StGermain on 2007-12-01
I was able to install the drivers and I can access my disk over USB but I have no idea how to mount it over the network?

---

### Post by diskace on 2007-12-21
> **StGermain said:**
> I was able to install the drivers and I can access my disk over USB but I have no idea how to mount it over the network?

You need to follow theses steps:

[http://code.ximeta.com/trac-ndas/wiki/HowToBuildDEB](http://code.ximeta.com/trac-ndas/wiki/HowToBuildDEB)

Once installed use ndasadmin command in shell to register your netdisk.

Step3) you must format the drive in order to be able to read it in your OS.

I use the command:

0p2 is my ext3 partition

ndas-00526367-0 main drive
ndas-00526367-0p1 extfs3
ndas-00526367-0p2 ntfs

root@fixit-laptop:/dev# mount -t ext3 /dev/ndas-00526367-0p2 /media/netdisk

Good luck !

---

### Post by frederic.tardif on 2008-04-01
Fast question,

I just bought a new netdisk 500GB of Ximeta. I need to backup my windows machine on it before installing linux.

This thread seems to pretty well explain how to mount it in ubuntu, but I was wondering if my File system should be formated as FAT32 prior to backup my stuff or ubuntu is gonna be able to read-write a NTFS drive.

Thanks

---

### Post by r76 on 2008-04-02
My opinion, go with NTFS, I've been doing so for over 6 months and not a single problem.

As regards the Ximeta system - I gave up 5 months ago, bought a couple ofpowered USB cables (5m each, you can chain up to 5 together, plus the original cable) and never looked back. Life is sweet, blissful uncomplicated no-network setup.  Oh and did I mention it's about a gazillion times faster than NAS? Mmmm... progress.

---

### Post by mozz on 2008-04-12
Ximeta dropped Linux support, the module won't compile on 2.6.24 ([http://code.ximeta.com/trac-ndas/ticket/749](http://code.ximeta.com/trac-ndas/ticket/749))

---

### Post by ahillerin on 2008-04-21
That s OK now: see my post:

[http://ubuntuforums.org/showthread.php?p=4757643#post4757643](http://ubuntuforums.org/showthread.php?p=4757643#post4757643)

AH

---

