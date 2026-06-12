---
title: "HOWTO build/install updated e1000 driver when you have no net"
date: 2007-09-15
forum: Networking &amp; Wireless
---

### Post by noob12 on 2007-09-15
[SIZE="5"]
HOWTO build/install updated e1000 driver when you have no net [/SIZE]

History of significant edits:
[LIST]
[*]9/15/2007: Original version
[*]9/15/2007: Added note that binary attachments only work for 32-bit generic kernel. 
[*]9/16/2007: Build procedure tested by yang.  Found issue with Intel make install target installing man page.  Replaced make install by direct install command.
[*]9/16/2007: Add e1000 to /etc/modules to load on boot.
[*]9/16/2007: Added list of device ids affected.
[/LIST]


Several new motherboards have Intel chipsets that aren't covered by the e1000 driver that is shipped in Ubuntu 7.04 (e1000 driver version 7.3.15-k2-NAPI).  

This includes some of the Intel 82562 and 82566 cards.  This includes some 100mbps devices that are unsupported by e100 and are supported by the e1000 driver.  Following is the list of device IDs affected.  This HOWTO applies to you if you see that your ethernet controller has any one of these device ids when you run the command **lspci -nn**
```

8086:10A5
8086:10BD
8086:10C0
8086:10C2
8086:10C3
8086:294C

```

If you have one of these devices and find that the e1000 driver in Feisty is not claiming your device, you will need to build and install the latest driver from Intel.  The latest e1000 driver from Intel (e1000 version 7.6.5) does support these devices.

This HOWTO provides a procedure to build and install this driver, particularly for the case that you have no other network access from the Ubuntu host.  It also provides pre-built versions of the modules and an installation script for them.  

You can use the pre-built versions if you are running the 32-bit 2.6.20-15 or 2.6.20-16 kernels.  You can tell your kernel version by typing **uname -r**.    Although the pre-built binaries work with only the 32-bit kernels, the build procedure will work for both 32 and 64-bit kernels on Intel.

This build procedure is based on the 2.6.20-15-generic kernel running on the i386 (x86 and x86_64) architectures and provides instructions for dealing with the upgrade to 2.6.20-16-generic for i386 as well as well.  You may be able to generalize from this to other kernel and architecture variants by replacing the version and architecture-specific strings and links in this text.

I'm hoping that Gutsy will ship with an updated e1000, but I haven't been able to determine whether this is the case yet.

[SIZE="4"]**Using the pre-built attached modules**[/SIZE]

I've attached pre-built modules for the 2.6.20-15-generic and 2.6.20-16-generic kernels and the i386 architecture.  [COLOR="Red"]**These only work on 32 bit kernels**.[/COLOR]  *Since you don't know me from the next noob (noob13 :) ) and the forum isn't really a secure distribution channel, you might still want to build for yourself.*  If you are building your own, skip this step and go to the section **Install Build Preliminaries**.


The attachments are two files **e1000-7.6.5-i386-bin-1a.tar.bz2** (which contains the 2.6.20-15-generic build) and **e1000-7.6.5-i386-bin-1b.tar.bz2** (which contains the 2.6.20-16-generic build).  

Put each one in your /tmp directory and install as follows.  
```

# Unpack the file in tmp
cd /tmp
bunzip2 e1000-7.6.5-i386-bin-1a.tar.bz2
tar xf e1000-7.6.5-i386-bin-1a.tar
cd e1000-7.6.5-i386-bin-1a

# This does a dry run and will tell you what it will do.
./install.sh -n

# This runs it as root and will do the installations.
sudo ./install.sh

# Load the new driver and restart networking
modprobe e1000
sudo /etc/init.d/networking restart

```

This command will add e1000 explicitly in your **/etc/modules** file in order to get the updated e1000 driver to load at boot.  You only need to run this for the first installation.  If you install the 2.6.20-16 version later, then you should omit this in the second installation.
```

echo "e1000" | sudo tee -a /etc/modules

```

That's it.  You are done for the 2.6.20-15-generic kernel.

Install the second file **e1000-7.6.5-i386-bin-1b.tar.bz2** in the same way after you have installed the 2.6.20-16 upgrade (which you will get automatically soon after your network is running).


[SIZE="4"]
**Install Build Preliminaries**[/SIZE]

**With no network access**

If you have no network access on your Ubuntu host, you will need the Ubuntu 7.04 installation CD-ROM, a FAT-32-formatted USB jump drive to transfer files to your Ubuntu host (or a shared FAT filesystem with a dual-boot host), and some other machine where you can download files and can put them on the shared .

Starting on your Ubuntu host, install the build-essential meta-package from your installation CD-ROM by inserting the CD-ROM and typing:
```

sudo apt-cdrom add

sudo apt-get install build-essential

```

On your separate host with network access, you need to download the driver source and the linux-headers packages corresponding to your kernel version and put them on your flash drive (or shared partition).  

The e1000-7.6.5 driver source can be downloaded from Intel here: 
[http://downloadcenter.intel.com/confirm.aspx?httpDown=http://downloadmirror.intel.com/9180/eng/e1000-7.6.5.tar.gz&agr=N&ProductID=983&DwnldId=9180&strOSs=All&OSFullName=All%20Operating%20Systems&lang=eng](http://downloadcenter.intel.com/confirm.aspx?httpDown=http://downloadmirror.intel.com/9180/eng/e1000-7.6.5.tar.gz&agr=N&ProductID=983&DwnldId=9180&strOSs=All&OSFullName=All%20Operating%20Systems&lang=eng)

As a result of this download you should get a file **e1000-7.6.5.tar.gz**.  Copy it to your jump drive.

Check your kernel version by typing **uname -r**.  The most common for Feisty users in this situation will be 2.6.20-15-generic.  If you have a different version, substitute your actual version string in the link below.  

These links download the linux header packages for the 2.6.20-15-generic kernel for the i386 architecture.

linux-headers-2.6.20-15-generic for i386:
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fl%2Flinux-source-2.6.20%2Flinux-headers-2.6.20-15-generic_2.6.20-15.27_i386.deb&md5sum=510cbf1efb528a0322690009cdb9d233&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fl%2Flinux-source-2.6.20%2Flinux-headers-2.6.20-15-generic_2.6.20-15.27_i386.deb&md5sum=510cbf1efb528a0322690009cdb9d233&arch=i386&type=main) 

linux-headers-2.6.20-15 for i386:
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fl%2Flinux-source-2.6.20%2Flinux-headers-2.6.20-15_2.6.20-15.27_i386.deb&md5sum=dbe032628ed1d485fa3d642e8da8437a&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fl%2Flinux-source-2.6.20%2Flinux-headers-2.6.20-15_2.6.20-15.27_i386.deb&md5sum=dbe032628ed1d485fa3d642e8da8437a&arch=i386&type=main)

As a result of these you will get two package files: **linux-headers-2.6.20-15-generic_2.6.20-15.27_i386.deb** and **linux-headers-2.6.20-15_2.6.20-15.27_i386.deb**

Copy those to your jump drive or shared partition as well.  

Take your jump-drive to your Ubuntu host and copy the three files to the **/tmp** directory on the hard drive.

Open a Terminal window and run these commands to install the two deb packages.
```

cd /tmp
dpkg --install linux-headers-2.6.20-15-generic_2.6.20-15.27_i386.deb
dpkg --install linux-headers-2.6.20-15_2.6.20-15.27_i386.deb

```

Now jump to **Building the Driver**.

**With existing network access on one interface**

If you have existing network access using a different interface on your Ubuntu host, (e.g your wireless or s separate working ethernet card), you can download the required packages as follows:
```

sudo apt-get install build-essential linux-headers-`uname -r`

```

Use the same link as in the previous section to download the e1000-7.6.5 driver source.
Put the file e1000-7.6.5.tar.gz file in /tmp and proceed to the next section.

[SIZE="4"]**Building the Driver**[/SIZE]

Here are the steps to building the driver.
```

# Get to the tmp dir
cd /tmp

# Unpack the file
tar xvfz e1000-7.6.5.tar.gz

# Go to the source directory that's been unpacked
cd e1000-7.6.5/src

# This places a backup copy of the original driver in your home directory
sudo cp /lib/modules/2.6.20-15-generic/kernel/drivers/net/e1000/e1000.ko ~/e1000-2.6.20-15-generic.orig.ko

# Build
make 

# If you got no errors, proceed to install
sudo install -D -m 644 e1000.ko /lib/modules/2.6.20-15-generic/kernel/drivers/net/e1000/e1000.ko

# Try this to see if it claims your ethernet device.
sudo modprobe e1000

```

[SIZE="1"]
[INDENT]Note for the experienced:  The Makefile does have an install target and it works to install the driver but fails with an ugly error when trying to install the man page. As a result, we've opted to avoid using the install target and instead to run the underlying install command directly.[/INDENT][/SIZE]


Now run **ifconfig -a** to see if you have the new device.

If it is there, then running
```
sudo /etc/init.d/networking/restart
``` 
should get you up on the net in normal circumstances.

In order to have the driver loaded on subsequent boots,  run this
```

echo "e1000" | sudo tee -a /etc/modules

```


**Building for 2.6.20-16-generic while running 2.6.20-15**

When you pull the latest Feisty updates, among the upgrades you'll get
is the 2.6.20-16 kernel upgrade.

When you upgrade your kernel to 2.6.20-16 you will lose your own upgraded e1000 driver; you will revert to the older Ubuntu-shipped e1000 driver.  You will lose the network.

After you upgrade you can still boot back to the 2.6.20-15 kernel by selecting it in the grub menu at boot.  You will need to do that.  This gets you back to where you have a working network to run this procedure.  By doing the following cross-build, you can upgrade the 2.6.20-16 kernel while running the 2.6.20-15 kernel.

While running under 2.6.20-15 do the following
```

sudo aptitude install linux-headers-2.6.20-16-generic

cd /tmp/e1000-7.6.5/src

# The sudo here is just in case you ran the make as sudo earlier.
# You will need to be root to clean out the old artifacts in that case.
sudo make clean

make BUILD_KERNEL=2.6.20-16-generic

```

If you get no errors, you can proceed.

[COLOR="Red"]IF YOU HAVE NOT YET UPGRADED TO 2.6.20-16, THEN WAIT UNTIL YOU DO SO BEFORE RUNNING THE FOLLOWING COMMANDS.[/COLOR]

You can do this while booted to either 2.6.20-15 or 2.6.20-16, but you should already have installed the 2.6.20-16-generic kernel.
```

cd /tmp/e1000-7.6.5/src

# This places a backup copy of the original driver in your home directory
sudo cp /lib/modules/2.6.20-16-generic/kernel/drivers/net/e1000/e1000.ko ~/e1000-2.6.20-16-generic.orig.ko

sudo install -D -m 644 e1000.ko /lib/modules/2.6.20-16-generic/kernel/drivers/net/e1000/e1000.ko

```

If all has gone well, you should be able to reboot into kernel 2.6.20-16 and have networking.

---

### Post by yang on 2007-09-15
A couple of preliminary results from working through the first part (using prebuilt binaries):

1.

Apparently I already have an e1000.ko present, which gets backed up. Trying to modprobe that original .ko doesn't give me any errors, and shows up in lsmod. (I don't know what to do next to enable and check for Ethernet functionality.) Running /etc/init.d/networking restart gives me a bunch of errors, and I have no network connectivity at the end. Is all this expected?

2.

I have 2.6.20-15, so I used 1a. install.sh claims to support 64-bit, but I get this when trying to sudo modprobe e1000:

```

FATAL: Error inserting e1000 (/lib/.../e1000.ko): Invalid module format

```

---

### Post by noob12 on 2007-09-15
OK.  My fault.  Thanks for testing.

That means the ko needs to be rebuilt for 64 bit, so you are probably going to want to use the instructions to build on your own box.

I will revise the bundles and the HOWTO posting.  Can you try the build (if you haven't already started down that path).

It's expected that you have one present and that we backed it up.  It is the older version.  You can restore that.  It will load, but it won't claim the device.

---

### Post by yang on 2007-09-15
I now have a working Internet connection in -16-generic! The build process seemed to have gone smoothly, except for this last snippet from the output of the final sudo make install:

```

...
install -D -m 644 e1000.7.gz /usr/share/man/man7/e1000.7.gz
man -c -P'cat > /dev/null' e1000 || true
man:
cannot write to /var/cache/man/cat7/e1000.7.gz in catman mode
e1000.

```

While I may be able to live without the man page for e1000, I don't know if there was anything else important that should have followed that, but got aborted due to the exception.

Also, how do I have Ubuntu auto-load this module for me so that I don't have to enter "sudo modprobe e1000" every time I boot?

In any case, thanks a ton for your guidance. Now I'm off to try some fixes for my GMA 950 issues. :)

---

### Post by noob12 on 2007-09-15
I actually expected that it would autoload on boot, but if that isn't happening, you should add a line that says just **e1000** to **/etc/modules**.

This will do that:
```

echo "e1000" | sudo tee -a /etc/modules

```

---

### Post by yang on 2007-09-15
Maybe that's something that should've happened after the man page business.

---

### Post by noob12 on 2007-09-15
No the Intel Makefile isn't going to do  that for you even if it succeeded with the man page.

I may have to add instructions to create a new initrd image.  I'll keep you posted if I learn anything.  Thanks for testing this, I'll add the additional info in a little while based on your feedback and then I can let the public try it.  Thanks for testing it out.

[COLOR="DarkGreen"]UPDATE: This thread is now tested and ready to go.  At least two users have reported success so far using it.[/COLOR]

---

### Post by Joe325 on 2007-09-19
I have a P35T-A ECS mobo which uses the Intel Pro100/1000 NIC.(82566).
I have run Ubuntu 704 disc and noticed I had no network connection. (Modem was there for some reason)
To get my NIC detected and working, I d/loaded the Intel Driver for linux e1000-7.6.5.tar.gz from another machine and saved it to my desktop. Extracted the file there also.
Then I cd'd into <driver name>/src/ & ran ' sudo make install'
The last line of that install gave me " can not write to var/cache........in catman mode e1000.
I logged in as root and changed the permissions of the folder listed above and ran another time, this time without any errors.
I then went back into the terminal and ran: rmmod e1000 & then sudo modprobe e1000...

A little balloon popped up in the top right corner advising me that I was now connected to the wired network......Woohoo. Im back online with Ubuntu.:lolflag:

---

### Post by noob12 on 2007-09-19
> Then I cd'd into <driver name>/src/ & ran ' sudo make install'

Great!  While the **make install** target does work, my instructions avoid it in order to avoid the confusion that most users will face when seeing the man page installation error.  Also, note that you will need to rebuild for the 2-6-20-16 kernel as soon as you upgrade (as described in the instructions).

---

### Post by asafche on 2007-09-26
hay everyone,

i'm a green noob, and i had so far very hard time in config my 82566dc, espcialy cause i aien't familier with linux and/or ubuntu.

i have an intell proccesor, and i've installed ubuntu 7.04 feisty successfuly...
the kernel ver. is 2.6.20-15-generic.

i've followed this HWOTO step by step, but i got stuck when iafter the command:

sudo install -D -m 644... and so on...

i've got nothing back.

then i tryed to check with:

sudo modprobe e1ooo 

 - also nothing


i really don't know what to do...
i hope for some help soon...

thanks...

---

### Post by asafche on 2007-09-26
some other thing:
i managed to see the "wired connection" in the network setting now, but...
1. i can't hook to the net.
2. the command:

"**sudo /etc/init.d/networking restart**"

had this result:

[B]"RTNETLINK answers: No such process...
there are already a pid file /var/run/dhclient.eth0.pid with pid 6845
killed old client process, removed PID file

eth1:ERROR while getting interface flags: No such device...[/B]"

and so on and on...

3. i can't figure it out, need help

---

### Post by asafche on 2007-09-26
o.k. - i reinstalled the driver - did it all from the bigning and it's working! i maneged to activate the ethernet card and to log on! thank you for this guude.

---

### Post by noob12 on 2007-09-26
asafche:  Great to hear you got it working!  

One thing to add: the errors you see in restarting your networking are unrelated.  They are due to the fact that Ubuntu ships with a default **/etc/network/interfaces** file that has configurations for many interfaces that you may not actually have.  You can remove the ones that don't exist.  You can see which ones do exist by typing the command:  **ifconfig -a**.

For future travelers on this thread, please notice the time zone in my postings. When you post a question about the HOWTO in the middle of my night, you'll probably have to wait until morning  here before you get a response from me. :-)

---

### Post by kuahyeow on 2007-09-26
Hi, thanks for the instructions and the builds.
I found that installing 2.6.15 is ok, but upon update to 2.6.16 and installing the second driver, the command
```

modprobe e1000
```

does not work..

A previous poster mentions doing 

```
rmmod e1000
``` and then ```
modprobe e1000,

```
and that worked!

---

### Post by noob12 on 2007-09-27
Yep. That will work.  The instructions for the second build actually suggest that you reboot, which will work and restart everything.  On booting for the second build the old e1000 driver gets loaded because of the entry in /etc/modules.  When you reboot you get the new driver.

---

### Post by ldormon on 2007-09-27
Thanks alot for this, it all worked a treat. One small prob, should these things run at  gigabit?

Plugged into my gig switch, it brings it up 100Mb :(

Cheers
Lee

---

### Post by noob12 on 2007-09-27
Sometimes you'll experience autonegotiation problems, but generally speaking the drivers support gigabit automatically if your device is gigabit and you are connected to a gigabit switch.

[COLOR="Red"]NOTE:  Some of the devices supported by this driver are actually 10/100 cards.[/COLOR]

If lspci -nn shows one of these device ids (following Intel's cute vendor id 8086), you have a 10/100 card; so it won't go gigabit:

        104c  82562V 10/100 Network Connection
        10c0  82562V-2 10/100 Network Connection
        10c2  82562G-2 10/100 Network Connection
        10c3  82562GT-2 10/100 Network Connection
        10c4  82562GT 10/100 Network Connection
        10c5  82562G 10/100 Network Connection

There's a complete list in the pci.updates file in the top-level extracted directory of the source bundle.

If you verify you really have a gigabit card and think you have an autonegotiation problem.  You can try this command (replace interface name as appropriate):
```

sudo ethtool -s eth0 speed 1000 duplex full autoneg off

```
and if it works, you can put this in a pre-up line in the stanza for the interface in /etc/network/interfaces to adjust speed and duplex, for example:

```

auto eth0
iface eth0 inet dhcp
pre-up ethtool -s eth0 speed 1000 duplex full autoneg off

```

---

### Post by candtalan on 2007-10-02
A big thank you for this thread to 
noob12
and contributors!

---

### Post by kiuri on 2007-10-06
hello, Im here again cause I have a problem with the network again, I installed that way that you said and it worked but I updated my pc and it stopped working again, it only recognizes modem connection. I tried to reinstall and it didnt work heres the console:
I updated using this commands:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

after restarting it wasnt working again
--------------------------------------------------------------------------------------------------------------
kiuri@kiuri-desktop:~$ sudo apt-cdrom add
Password:
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter
Mounting CD-ROM...
E: Failed to mount the cdrom.
kiuri@kiuri-desktop:~$ sudo apt-cdrom add
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter
Mounting CD-ROM...
Identifying.. [b0eec9ebb2f73cb755ea5ff17b89a5e4-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes, 0 translation indexes and 1 signatures
This disc is called:
'Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)'
Copying package lists...gpgv: Signature made Sun 15 Apr 2007 07:22:01 PM IST using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Reading Package Indexes... Done
Writing new source list
Source list entries for this disc are:
deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
Unmounting CD-ROM...Repeat this process for the rest of the CDs in your set.
kiuri@kiuri-desktop:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kiuri@kiuri-desktop:~$ cd /tmp
kiuri@kiuri-desktop:/tmp$ dpkg --install linux-headers-2.6.20-15-generic_2.6.20-15.27_i386.deb
dpkg: requested operation requires superuser privilege
kiuri@kiuri-desktop:/tmp$ sudo dpkg --install linux-headers-2.6.20-15-generic_2.6.20-15.27_i386.deb
(Reading database ... 112911 files and directories currently installed.)
Preparing to replace linux-headers-2.6.20-15-generic 2.6.20-15.27 (using linux-headers-2.6.20-15-generic_2.6.20-15.27_i386.deb) ...
Unpacking replacement linux-headers-2.6.20-15-generic ...
Setting up linux-headers-2.6.20-15-generic (2.6.20-15.27) ...
kiuri@kiuri-desktop:/tmp$ cd /tmp
kiuri@kiuri-desktop:/tmp$ tar xvfz e1000-7.6.5.tar.gz
e1000-7.6.5/
e1000-7.6.5/src/
e1000-7.6.5/src/Makefile
e1000-7.6.5/src/e1000.h
e1000-7.6.5/src/e1000_80003es2lan.c
e1000-7.6.5/src/e1000_80003es2lan.h
e1000-7.6.5/src/e1000_82540.c
e1000-7.6.5/src/e1000_82541.c
e1000-7.6.5/src/e1000_82541.h
e1000-7.6.5/src/e1000_82542.c
e1000-7.6.5/src/e1000_82543.c
e1000-7.6.5/src/e1000_82543.h
e1000-7.6.5/src/e1000_82571.c
e1000-7.6.5/src/e1000_82571.h
e1000-7.6.5/src/e1000_api.c
e1000-7.6.5/src/e1000_api.h
e1000-7.6.5/src/e1000_defines.h
e1000-7.6.5/src/e1000_ethtool.c
e1000-7.6.5/src/e1000_hw.h
e1000-7.6.5/src/e1000_ich8lan.c
e1000-7.6.5/src/e1000_ich8lan.h
e1000-7.6.5/src/e1000_mac.c
e1000-7.6.5/src/e1000_mac.h
e1000-7.6.5/src/e1000_main.c
e1000-7.6.5/src/e1000_manage.c
e1000-7.6.5/src/e1000_manage.h
e1000-7.6.5/src/e1000_nvm.c
e1000-7.6.5/src/e1000_nvm.h
e1000-7.6.5/src/e1000_osdep.h
e1000-7.6.5/src/e1000_param.c
e1000-7.6.5/src/e1000_phy.c
e1000-7.6.5/src/e1000_phy.h
e1000-7.6.5/src/e1000_regs.h
e1000-7.6.5/src/kcompat.c
e1000-7.6.5/src/kcompat.h
e1000-7.6.5/src/kcompat_ethtool.c
e1000-7.6.5/COPYING
e1000-7.6.5/README
e1000-7.6.5/ldistrib.txt
e1000-7.6.5/pci.updates
e1000-7.6.5/e1000.spec
e1000-7.6.5/e1000.7
e1000-7.6.5/SUMS
kiuri@kiuri-desktop:/tmp$ cd e1000-7.6.5/src
kiuri@kiuri-desktop:/tmp/e1000-7.6.5/src$ sudo cp /lib/modules/2.6.20-15-generic/kernel/drivers/net/e1000/e1000.ko ~/e1000-2.6.20-15-generic.orig.ko
kiuri@kiuri-desktop:/tmp/e1000-7.6.5/src$ make
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/tmp/e1000-7.6.5/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
CC [M] /tmp/e1000-7.6.5/src/e1000_main.o
CC [M] /tmp/e1000-7.6.5/src/e1000_82540.o
CC [M] /tmp/e1000-7.6.5/src/e1000_82542.o
CC [M] /tmp/e1000-7.6.5/src/e1000_82571.o
CC [M] /tmp/e1000-7.6.5/src/e1000_82541.o
CC [M] /tmp/e1000-7.6.5/src/e1000_82543.o
CC [M] /tmp/e1000-7.6.5/src/e1000_ich8lan.o
CC [M] /tmp/e1000-7.6.5/src/e1000_80003es2lan.o
CC [M] /tmp/e1000-7.6.5/src/e1000_mac.o
CC [M] /tmp/e1000-7.6.5/src/e1000_nvm.o
CC [M] /tmp/e1000-7.6.5/src/e1000_phy.o
CC [M] /tmp/e1000-7.6.5/src/e1000_manage.o
CC [M] /tmp/e1000-7.6.5/src/e1000_param.o
CC [M] /tmp/e1000-7.6.5/src/e1000_ethtool.o
CC [M] /tmp/e1000-7.6.5/src/kcompat.o
CC [M] /tmp/e1000-7.6.5/src/e1000_api.o
LD [M] /tmp/e1000-7.6.5/src/e1000.o
Building modules, stage 2.
MODPOST 1 modules
CC /tmp/e1000-7.6.5/src/e1000.mod.o
LD [M] /tmp/e1000-7.6.5/src/e1000.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
kiuri@kiuri-desktop:/tmp/e1000-7.6.5/src$ sudo install -D -m 644 e1000.ko /lib/modules/2.6.20-15-generic/kernel/drivers/net/e1000/e1000.ko
kiuri@kiuri-desktop:/tmp/e1000-7.6.5/src$
kiuri@kiuri-desktop:/tmp/e1000-7.6.5/src$ sudo modprobe e1000
kiuri@kiuri-desktop:/tmp/e1000-7.6.5/src$ ifconfig -a
lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:6 errors:0 dropped:0 overruns:0 frame:0
TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:300 (300.0 b) TX bytes:300 (300.0 b)

kiuri@kiuri-desktop:/tmp/e1000-7.6.5/src$ sudo /etc/init.d/networking/restart
sudo: /etc/init.d/networking/restart: command not found
kiuri@kiuri-desktop:/tmp/e1000-7.6.5/src$ echo "e1000" | sudo tee -a /etc/modules
e1000
kiuri@kiuri-desktop:/tmp/e1000-7.6.5/src$ cd /tmp/e1000-7.6.5/src
kiuri@kiuri-desktop:/tmp/e1000-7.6.5/src$ sudo cp /lib/modules/2.6.20-16-generic/kernel/drivers/net/e1000/e1000.ko ~/e1000-2.6.20-16-generic.orig.ko
kiuri@kiuri-desktop:/tmp/e1000-7.6.5/src$
kiuri@kiuri-desktop:/tmp/e1000-7.6.5/src$ sudo install -D -m 644 e1000.ko /lib/modules/2.6.20-16-generic/kernel/drivers/net/e1000/e1000.ko
kiuri@kiuri-desktop:/tmp/e1000-7.6.5/src$
--------------------------------------------------------------------------------------------------------------

please help

---

### Post by kiuri on 2007-10-06
I restarted my pc, and loged in with vista, then I restarted again and logged in with ubuntu and my network is now working fine again... strange...
thanks anyway

---

### Post by noob12 on 2007-10-06
Remember to follow the second section in the HOWTO, which describes how to build for the 2.6.20-16 kernel (!)

In the exhilaration of getting the net working the first time people can miss that second section.

When you upgrade from 2.6.20-15 (which is on the CD-ROM) to 2.6.20-16 (which you will get on pulling updates from the net) you will not get the custom modules that you installed in the 2.6.20-15 kernel.  This means you will lose the network.

That second section tells you how to install into the 2.6.20-16 kernel taking advantage of your existing connectivity when booting 2.6.20-15.  When you finish the second section, you will have connectivity when booting either kernel.

Cheers.

---

### Post by ronaldw on 2007-10-09
noob12: it worked great, built it myself (even though I'm pretty much a linux / ubuntu noob...

Thanks a lot,

Ronald:)

---

### Post by Verner on 2007-11-14
Sorry for bumping but i've managed to install the drivers on ubuntu 6.06 server, took like 3 hours of looking around in several forums, and the e1000 is loaded (lsmod | grep e1000) but what should I do to get it to show up in ifconfig? I've tried modprobe e1000 and i don't recieve any error..

---

### Post by noob12 on 2007-11-15
Check **tail /var/log/kern.log** after your modprobe and make sure it is happy.  You should get the interface right away if things worked normally.

---

### Post by dragos.marian on 2008-01-07
Just wanted to add, make sure you also update your BIOS to whatever latest official release. That's what ultimately solved my issues (which were similar, not exactly the same). The problem was the ACPI implementation for my HP 6720s.

---

### Post by alainhenry on 2008-01-31
I have a HP 6820s laptop, with a network card 82562GT 10/100 and the lspci -nn command gives 
8086:10C4. Kernel is 2.6.22-14-generic
not sure how to check the version of e1000 in Gutsy though.
The card is not recognised by Gutsy (neither live CD nor after install).  I assume I could apply the same solution, while using the latest HP driver and correct kernel headers ?

---

### Post by rookie76 on 2008-02-01
I have the same issue.

I have a Compaq 6820s and I have 7.10 (64 bit version) installed with kernel 2.6.22-14.  I tried the process from this thread and could not located the linux-headers-2.6.22-14-generic for amd64.

Any body know what to do?

---

### Post by alainhenry on 2008-02-05
Well, I tried this process after installing Gutsy on my HP 6820s. The  header files (2.6.22-14 generic) are installed by the standard Gutsy installation process. I just had to copy the latest e1000 driver.  
The process went smoothly, no error at all, but I did not get a connection  at the end either, even after a full reboot.  The new file e1000.ko is different from the old one (bigger), so the replacement has indeed been done. I also noticed the new one was owned by root, while the old one was owned by user, but changing that did  not affect the negative result.  
I had the same problem with knoppix, and I assume all other distros would show the same problem, as it is linked to the HP driver. I plan to give the new hardy heron alpha a try and will post the result here.
Alain

Edit: I went again through the process, without achieving connection.  The mandriva 2008 live CD does get conenction either.

---

### Post by alainhenry on 2008-02-09
Just for information :-)
I just installed OpenSUSE 10.3 on my laptop, and the network card is detected and seem to work correctly. It should thus be possible to have it working with Ubuntu.

---

### Post by mmiat on 2008-02-21
does it work with debian etch ( kernel 2.6.18 )?
does anyone try it?

thanks VERY VERY much

---

### Post by mmiat on 2008-02-22
yes, it works!!! :)

# in other pc with debian etch ( kernel 2.6.18 )

apt-get install build-essential linux-headers-`uname -r`
tar xvfz e1000-7.6.15.4.tar.gz
cd e1000-7.6.15.4/src
cp /lib/modules/2.6.18-6-686/kernel/drivers/net/e1000/e1000.ko ~/e1000.orig.ko
make

# copy-paste on usb key and then copy in the notebook

install -D -m 644 e1000.ko /lib/modules/2.6.18-6-686/kernel/drivers/net/e1000/e1000.ko
modprobe e1000

# reboot, modify /etc/network/interfaces and....
ifup eth0

---

### Post by Stone123 on 2008-02-22
Can you please test this CD to try to fix intel nic.

Nice thread, just that there are 1000 threads about e100 e1000 alike.


[http://www.matinfo.ch/files/blog/cdproboot-0.2.iso]("http://www.matinfo.ch/files/blog/cdproboot-0.2.iso")


Instructions, well not realy just how it works

[http://www.matinfo.ch/blog/archive/2007/01/26/intel-nic-pxe-e05-error.html](http://www.matinfo.ch/blog/archive/2007/01/26/intel-nic-pxe-e05-error.html)

---

### Post by alainhenry on 2008-03-07
Good news, Hardy alpha 6 live CD works on my laptop HP 6820S. I did not install it, but the wired network connection worked perfectly well. 
 
> **alainhenry said:**
> Just for information :-)
I just installed OpenSUSE 10.3 on my laptop, and the network card is detected and seem to work correctly. It should thus be possible to have it working with Ubuntu.

---

### Post by thethimble on 2008-04-30
Thank you SO much noob12. You are a god amongst mere mortals.

---

### Post by vckarthic on 2008-05-15
Dear Noob12, 

Although the how-to was idiot proof, I am quickly challenging that piece. Same issue here. Fresh install of Hardy on my Compaq Presario v3000 laptop yields working wireless but not ethernet. 

I followed your instructions to the core but have only screeshots of errors to show for it. Any help you can give would be awesome since I have formatted my existing win HDD to go to ubuntu completely. 

Please let me know if you need any more information or screenshots. 

Cheers, 

Karthic

---

### Post by candtalan on 2008-05-15
> **vckarthic said:**
> Dear Noob12, 

Although the how-to was idiot proof, I am quickly challenging that piece. Same issue here. Fresh install of Hardy on my Compaq Presario v3000 laptop yields working wireless but not ethernet. 

I followed your instructions to the core but have only screeshots of errors to show for it. Any help you can give would be awesome since I have formatted my existing win HDD to go to ubuntu completely. 

Please let me know if you need any more information or screenshots. 

Cheers, 

Karthic

I am told that the drivers for e1000 are in hardy anyway, so I wonder how sure are you that this is the problem? Is something disabled maybe?

---

