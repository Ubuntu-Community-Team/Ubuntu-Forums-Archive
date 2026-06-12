---
title: "Ubuntu 7.04 doesn't recognize  Ethernet card"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by slobodan on 2007-10-19
Yesterday I installed Ubuntu 7.04 Dekstop i386 on a dual -boot machine with XP . 
I can't connect to Internet through my ethernet card. Going to Network panel Ubuntu recognizes my modem but not my Ethernet card. I have a cd with drivers  and tried to compile it as per the instruction but :
slobodan@deus:~$ cd /home/slobodan/sc92031
slobodan@deus:~/sc92031$ make install
Makefile:37: *** Linux kernel source not configured - missing config.h.  Stop.

The card is from some chinese manufacturer  without a name in a package, just PCI2.0 10/100Mbps. This is from the c source file:
#define DRV_NAME      "Rsltek 8139"
#define DRV_VERSION   "1.0.0"

#define SILAN_DRIVER_NAME  DRV_NAME"Rsltek 8139D PCI Fast Ethernet driver  v"DRV_VERSION

While going through forum tried some shell commands, ( I don't know what they mean exactly)
slobodan@deus:~$ sudo lshw -C network
Password:
  *-network UNCLAIMED     
       description: Ethernet controller
       product: RTL8139D [Realtek] PCI 10/100BaseTX ethernet adaptor
       vendor: Hangzhou Silan Microelectronics Co., Ltd.
       physical id: 9
       bus info: pci@00:09.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=32 maxlatency=40 mingnt=20
       resources: iomemory:dfffff00-dfffffff ioport:ec00-ecff irq:10
slobodan@deus:~$ lspci -nn
00:00.0 Host bridge [0600]: VIA Technologies, Inc. VT8753 [P4X266 AGP] [1106:3128] (rev 01)
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP] [1106:b091]
**00:09.0 Ethernet controller [0200]: Hangzhou Silan Microelectronics Co., Ltd. RTL8139D [Realtek] PCI 10/100BaseTX ethernet adaptor [1904:8139] (rev 01)**
00:10.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.3 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 82)
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8235 ISA Bridge [1106:3177]
00:11.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06)
00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller [1106:3059] (rev 50)
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV17 [GeForce4 MX 440] [10de:0171] (rev a3)
slobodan@deus:~$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:994 errors:0 dropped:0 overruns:0 frame:0
          TX packets:994 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:78516 (76.6 KiB)  TX bytes:78516 (76.6 KiB)

slobodan@deus:~$ uname -a
Linux deus 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux

thanks in advance

Slobodan

---

### Post by noob12 on 2007-10-19
First check if the 8139too driver will claim it if explicitly loaded.

Plug into an active ethernet port and type:
```

sudo modprobe 8139too

sudo lshw -C network

```
See whether the UNCLAIMED goes away.

If that works (the UNCLAIMED goes away), you just need to add a line with just **8139too** to the **/etc/modules** file.  You do not need to build.

If it does not work, you will probably have to build the driver you got.

In order to do that you need to run the following commands before running make.

First insert the Feisty CDROM.  Then type
```

sudo apt-cdrom add

sudo apt-get install build-essential

```

Then try your build.

---

### Post by slobodan on 2007-10-19
Still no luck with the card. It remained unclaimed so I fallowed the advice and tried to rebuild. Theresult is the same  missing config.h  Uploaded folder with cd rom linux druvers if it means something .
Here's the interaction with terminal

slobodan@deus:~$ sudo modprobe 8139too
Password:
slobodan@deus:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: RTL8139D [Realtek] PCI 10/100BaseTX ethernet adaptor
       vendor: Hangzhou Silan Microelectronics Co., Ltd.
       physical id: 9
       bus info: pci@00:09.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=32 maxlatency=40 mingnt=20
       resources: iomemory:dfffff00-dfffffff ioport:ec00-ecff irq:10
slobodan@deus:~$ sudo apt-cdrom add
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
Copying package lists...gpgv: Signature made Sun 15 Apr 2007 03:52:01 PM CEST using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Reading Package Indexes... Done
Writing new source list
Source list entries for this disc are:
deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
Unmounting CD-ROM...Repeat this process for the rest of the CDs in your set.
slobodan@deus:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev
Suggested packages:
  debian-keyring gcc-4.1-doc lib64stdc++6 glibc-doc manpages-dev
  libstdc++6-4.1-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev
  linux-libc-dev
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/8050kB of archives.
After unpacking 33.7MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Selecting previously deselected package linux-libc-dev.
(Reading database ... 88002 files and directories currently installed.)
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.20-15.27_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.5-0ubuntu14_i386.deb) ...
Selecting previously deselected package libstdc++6-4.1-dev.
Unpacking libstdc++6-4.1-dev (from .../libstdc++6-4.1-dev_4.1.2-0ubuntu4_i386.deb) ...
Selecting previously deselected package g++-4.1.
Unpacking g++-4.1 (from .../g++-4.1_4.1.2-0ubuntu4_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4.1.2-1ubuntu1_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.13.24ubuntu6_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.3_i386.deb) ...
Setting up linux-libc-dev (2.6.20-15.27) ...
Setting up libc6-dev (2.5-0ubuntu14) ...
Setting up dpkg-dev (1.13.24ubuntu6) ...
Setting up libstdc++6-4.1-dev (4.1.2-0ubuntu4) ...
Setting up g++-4.1 (4.1.2-0ubuntu4) ...
Setting up g++ (4.1.2-1ubuntu1) ...

Setting up build-essential (11.3) ...
slobodan@deus:~$ cd /home/slobodan/sc92031
slobodan@deus:~/sc92031$ make install
Makefile:37: *** Linux kernel source not configured - missing config.h.  Stop.
slobodan@deus:~/sc92031$ sudo make install
Makefile:37: *** Linux kernel source not configured - missing config.h.  Stop.
slobodan@deus:~/sc92031$

---

### Post by chili555 on 2007-10-19
This may be helpful: [http://ubuntuforums.org/showthread.php?t=478063](http://ubuntuforums.org/showthread.php?t=478063)

---

### Post by slobodan on 2007-10-19
I've downloaded sc92031-2.6.tar.gz and fallowed the post procedure :
4) Compile the driver source files and it will generate sc92031.ko
	   $ make

	5) copy it to /lib/modules/YOUR_KERNEL_VERSION/kernel/drivers/net/
       # make install

	4) # cd /lib/modules/YOUR_KERNEL_VERSION/kernel/drivers/net/
	   and check if you are able to install the module like
	   # insmod sc92031.ko	  	

**Above is Ok. I've build  sc92031.ko and copy it   **
    6) Check configuration file (/etc/modules.conf or /etc/conf.modules,it 
       depend on your Linux distribution) for loading kernel modules. Make sure
       there is the following content in the configuration file, where # is 
       interface number :
        alias eth# sc92031 

**  I can not find /etc/modules.conf nor /etc/conf.modules  . Such files doesn't exist**


Slobodan

---

### Post by noob12 on 2007-10-19
Add a line with just **sc92031** to the file **/etc/modules**.

I don't think you need the alias for eth0 but if you do, you can create a new file called **sc92031-alias** (any filename that isn't there already will work) in **/etc/modprobe.d** and put the alias line in it, for example:
```

alias eth0 sc92031

```

---

### Post by slobodan on 2007-10-19
Add a line with just sc92031 to the file /etc/modules.

**Tried ain't help**

I don't think you need the alias for eth0 but if you do, you can create a new file called sc92031-alias (any filename that isn't there already will work) in /etc/modprobe.d and put the alias line in it, for example:
Code:

alias eth0 sc92031

**Added and rebooted , still no luck.**

This is starting to sound like old Russian tale:
A : My health is deteriorating.
B: Stop smoking.
A: Tried, ain't help.
B: Start exercising .
A: Tried, ain't help.
B: Go to hospital.
A: Tried, ain't help.
B: Than prey to god.
A: Tried, ain't help.


Well at least I'm making a quick  progress with my shell skill :)

---

### Post by noob12 on 2007-10-19
It sounds like you may not have installed the module properly.

If you did install it properly then **modinfo sc92031** should find it and list information about it and **sudo modprobe sc92031** should manually load it. 

Where did you put the sc92031.ko file that you built?

---

### Post by slobodan on 2007-10-20
It's in a /lib/modules/YOUR_KERNEL_VERSION/kernel/drivers/net/
my Kernel is 2.6.20-15-generic  . I checked manually it's there.

---

### Post by noob12 on 2007-10-20
You did replace the string YOUR_KERNEL_VERSION with your actual kernel version right?

The module should be in the following location.  Check that this listing shows it and does not
report "No such file or directory".
```

ls -l /lib/modules/2.6.20-15-generic/kernel/drivers/net/sc92031.ko

```

If that works, verify that
```

modinfo sc92031

```
shows you information about that module and does not report "modinfo: could not find module sc92031".

If these don't find the module, make sure it is in the location above:  **/lib/modules/2.6.20-15-generic/kernel/drivers/net/sc92031.ko**

---

### Post by slobodan on 2007-10-20
>You did replace the string YOUR_KERNEL_VERSION with your actual kernel version right?

Yes I did, and I sow the file there. I'm unable to check anything else as  I downloaded 7.10, burn it and boot it as live cd and it recognized the Ethernet card automatically . So I deleted 7.04 and installed 7.10, now I'm using it to write it's text. :)

Thank you for your patience and advice.

All the best

Slobodan

---

