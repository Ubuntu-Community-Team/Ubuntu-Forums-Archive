---
title: "Linksys USB adapter will not find my wifi!"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by ReMO451 on 2008-12-14
Hi guys,
First off, I want to say that from my experience with Ubuntu, I absolutely love it. However, I am having problems getting my wireless network adapter to work with Ubuntu 8.10.

I purchased a Linksys Rangeplus wirless network USB adapter a couple weeks ago after moving my computer to a different room. Windows XP recognizes the adapter and it works fine in XP, but when I try to use the internet on Ubuntu, the network manager does not even show any connections. My Linksys router is currently unprotected (I live in the middle of the woods with no neighbors so there isn't any need for me to block people from using wifi). If someone could point me in the direction of an easy to follow beginners guide to solving this, it would be most appreciated. 

If you guys need any more information to solve the issue, please let me know. Also, I put this in the beginner's section because, well, I don't know what I'm doing (haha). Feel free to move it if needed.

Thanks!
Ryan ):P

---

### Post by northern lights on 2008-12-14
Can you please post the outputs of ```
sudo lshw -C network
``` and ```
lsusb
```
Thank you.

---

### Post by ReMO451 on 2008-12-14
ryan@ubuntu:~$ sudo lshw -c network
[sudo] password for ryan: 
  *-network               
       description: Ethernet interface
       product: 82801G (ICH7 Family) LAN Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:03:08.0
       logical name: eth0
       version: 01
       serial: 00:12:3f:9d:29:1f
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: da:d7:81:e1:e3:d5
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

ryan@ubuntu:~$ lsusb
Bus 005 Device 006: ID 0457:0151 Silicon Integrated Systems Corp. Super Flash 1GB / GXT  64MB Flash Drive
Bus 005 Device 005: ID 1737:0070 Linksys 
Bus 005 Device 003: ID 0bc2:3000 Seagate RSS LLC 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c041 Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


Hope that helps. It took a little longer than I thought because I got distracted. My bad!

---

### Post by ieee488 on 2008-12-14
I'm guessing you have a WUSB100.

[http://ubuntuforums.org/showthread.php?t=907809](http://ubuntuforums.org/showthread.php?t=907809)

[http://www.linuxforums.org/forum/wireless-internet/118831-wusb100-help-please.html](http://www.linuxforums.org/forum/wireless-internet/118831-wusb100-help-please.html)

---

### Post by ReMO451 on 2008-12-14
Thank you. I will try this out tomorrow and see if it would solve the problem.

---

### Post by ReMO451 on 2008-12-15
Hi again,

It seems that I do not have ndiswrapper installed, and I have no idea on how to get installed. Without this, the two other threads that ieee has showed me are useless (I think). Is there any way to install it manually i.e. download it from XP then put it on my desktop in Ubuntu? 

I also tried to pop in the CD that came with my adapter to no avail. Ubuntu would not recognize any of the .exe, .dll, etc files on it, which may be obvious to you guys but not to me because I am a noob haha. Whenever I would click on them to run or run in terminal, the progress bar in archive manager would hang then tell an error. 

Help would be appreciated! Thank you so far.

EDIT: okay, I got the ndiswrapper from SourceForge, and downloaded it onto my flash drive to put into Ubuntu, so I'm going to try using either one of those guides now with ndiswrapper. Wish me luck.

---

### Post by northern lights on 2008-12-15
Just seen this thread again and already am on the way to hit the hay (mainland Europe, class early morning).

Too tired to do in-depth thinking on your problem and the added info. However as for getting ndiswrapper of your XP or from another machine, check [http://getdeb.net]("http://getdeb.net").

---

### Post by ReMO451 on 2008-12-15
I have downloaded ndiswrapper, put it onto Ubuntu, unpacked it, and now I can't figure out how to install it. The install guide is very complex and confusing, especially for someone not used to linux. I kept receiving error messages saying that x doesn't exist or y cannot be found. I wish that you could just click on the thing and make it work haha.

Also I tried every one of those rt drivers but I don't know how to install them. The guide said to put them in the /lib/firmwire folder, but when I tried to do that it told me I didn't have the permissions, and I don't know how to log in as root (nor do I want to unless I absolutely have to, because I don't want to screw anything up too badly.)

---

### Post by linuxford on 2008-12-16
Here's what I did and it worked for me...
--------------------------------------------------------------
Steps:

   1. Open the terminal
   2. type this
      ```
sudo apt-get install build-essential
```
   3. copy and paste OR type this (each is a separate line in the terminal)
      ```
wget [http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2](http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2)
      tar xjf b43-fwcutter-011.tar.bz2
      cd b43-fwcutter-011
      make
      cd ..
```
   4. then
      ```
export FIRMWARE_INSTALL_DIR="/lib/firmware"
      wget [http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2)
      tar xjf broadcom-wl-4.80.53.0.tar.bz2
      cd broadcom-wl-4.80.53.0/kmod
      sudo ../../b43-fwcutter-011/b43-fwcutter -w "/lib/firmware" wl_apsta.o
```
   5. Now reboot Ubuntu and you should be good to go.

Note that you FIRMWARE_INSTALL_DIR might change with the distro.
-------------------------------------------------------------------
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/219775](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/219775)

---

### Post by ReMO451 on 2008-12-16
Ok thanks for the proposed solution - I will attempt this in a bit and see if it works!

---

### Post by linuxford on 2008-12-17
my bad ... I was thinking your hardware was broadcom for some reason .. the person ieee488 was thinking you have the WUSB100, like this? check out these links, are these like yours?

[http://www.amazon.com/Linksys-Range-Wireless-Compact-Adapter/dp/B0010OXEGW/ref=sr_1_6?ie=UTF8&s=pc&qid=1229498573&sr=1-6](http://www.amazon.com/Linksys-Range-Wireless-Compact-Adapter/dp/B0010OXEGW/ref=sr_1_6?ie=UTF8&s=pc&qid=1229498573&sr=1-6)

[http://review.zdnet.com/product/adaptersnics/linksys-rangeplus-wireless-network-usb-adapter-wusb100-network-adapter/32824793](http://review.zdnet.com/product/adaptersnics/linksys-rangeplus-wireless-network-usb-adapter-wusb100-network-adapter/32824793)

---

### Post by linuxford on 2008-12-17
Linux is still up and coming, but usually if you buying older stuff (1-2 years old in technology release) there is a driver out there. I switched my desktop and laptop to Ubuntu Linux because there wireless support is pretty good, but is still maturing some. Also, Linux is powerful, and there are tons of things and tons of free software out there that would cost hundreds of dollars each.

Anyway, here is a few things I was looking at last nite and trying to educate myself, and thought it may be of a little interest to you if you don't know it. These are generalities and I am not expert, I'm learning only.

The Linux system we are using with the Ubuntu distribution has an Operating System with a Kernel at its core. This kernel is basically the software brain of the system. For each piece of hardware in your system, you need an interface that is between your Kernel and the piece of the hardware, called a device driver. These device drivers are now not typically part of the Kernel, but instead are implemented in little "modules." So these commands like modprobe, lsmod, etc. are for these modules.

Now, software programmers committed to the cause, write device drivers for all kinds of hardware and lots of time, you don't have to do anything, your hardware is detected, and the modules loaded, etc... But some of these pieces of hardware don't have linux drivers or they are not open-source (no one can see the code). So instead you take a windows driver of some sort, and you use a special program called ndiswrapper. The concept is that you wrap this windows driver with a cool program, that will talk to the windows driver, translate it to linux speak, and then receive/send message to the kernel.

Now, since "a module is simply a single object file containing all the code for the driver"[SIZE="1"]1[/SIZE] and they either have a .o or .ko suffix, we may need to try and see if we can get one for your Linksys USB adapter, and then maybe we can use

insmod whatever.ko

to load it?

1. "Running Linux," Oreilly publication, page 622.

---

### Post by mrbiggbrain on 2008-12-17
doesn't apt-get require a network connection though? it gets things from repositorys on the internet, so id assume so.

Also, wlecome to linux, and the ubuntu world! i hope you learn quickly, and have a fire to solve problems, and build your knowlege everyday

---

### Post by linuxford on 2008-12-18
> **mrbiggbrain said:**
> doesn't apt-get require a network connection though? it gets things from repositorys on the internet, so id assume so.

Also, wlecome to linux, and the ubuntu world! i hope you learn quickly, and have a fire to solve problems, and build your knowlege everyday

Cool .. thanks .. good point, yes, you need networking for apt-get. Although technically if you download all the stuff you needed and burned it on CD, you could add the CD as a repository and get it off that. But with all the dependencies, sometimes it could be tough, depending on what you are downloading.

Get a ethernet cable, looks like telephone cable but bigger (as you probably already are aware of), and you should have a plug on your laptop, and then plug it directly to your laptop. Your onboard networking should be working okay. 

I was looking at "ieee488"s link again, and it said that the WUSB100 uses rt2870 drivers. So, I found a link that looks like what you need hopefully. You might have a good shot at it. Here's the link:
[http://onlyubuntu.blogspot.com/2008/10/howto-get-rt2870-wifi-80211abgn-chipset.html](http://onlyubuntu.blogspot.com/2008/10/howto-get-rt2870-wifi-80211abgn-chipset.html)

---

### Post by ReMO451 on 2008-12-22
Ok, sorry for the long reply. I was without a computer for a few days.

First I tried the sudo lshw -C network command, and this is what came up.

```
ryan@ubuntu:~$ sudo lshw -C network
[sudo] password for ryan: 
  *-network               
       description: Ethernet interface
       product: 82801G (ICH7 Family) LAN Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:03:08.0
       logical name: eth0
       version: 01
       serial: 00:12:3f:9d:29:1f
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 82:20:78:9f:46:02
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


```

It says that the network is disabled, and according to the offical documentation on 8.10, it means that the device is not on. I know for a fact that it is on and I couldn't find any thing that would say that it was turned off through Windows. 

Next, I tried Linuxford's solution, and it came up with error messages again.

```
ryan@ubuntu:~$ wget http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2
--2008-12-22 11:16:40--  http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2
Resolving bu3sch.de... failed: Name or service not known.
wget: unable to resolve host address `bu3sch.de'
ryan@ubuntu:~$ tar xjf b43-fwcutter-011.tar.bz2
tar: b43-fwcutter-011.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
ryan@ubuntu:~$ cd b43-fwcutter-011
bash: cd: b43-fwcutter-011: No such file or directory


``` 

I'm wondering if that would make any sense to you guys (being a newbie, it doesn't to me haha).

BTW, I am running Ubuntu 8.10 through WUBI from my H drive (the entire drive is formated NTFS but the section with ubuntu in it is not.) My USB network adapter is WUSB100 from Linksys, and my router is a WRT54G, no wireless protection (i.e. no WEP, WPA, etc). SSID is "linksys" w/o the quotes. If you need any other information, please let me know.

Thanks,
Ryan

edit: I did not see Linuxford's post that told me to use the command "insmod whatever.ko". I will try that later. What would go in the "whatever" field?

---

### Post by linuxford on 2008-12-23
> **linuxford said:**
>  I was looking at "ieee488"s link again, and it said that the WUSB100 uses rt2870 drivers. So, I found a link that looks like what you need hopefully. You might have a good shot at it. Here's the link:
[http://onlyubuntu.blogspot.com/2008/10/howto-get-rt2870-wifi-80211abgn-chipset.html](http://onlyubuntu.blogspot.com/2008/10/howto-get-rt2870-wifi-80211abgn-chipset.html)

iee488 thinks you probably have the WUSB100 model. This piece of hardware needs a device driver, which should be the "rt2870" drivers. Linux will use this driver so the software can communicate to the piece of hardware (WUSB100 device). 

But before we can even deal with the driver, the first step is to make sure you have a certain software program (package) installed called "build essential." After programmers create programs or device drivers, they need to be compiled or turned into a language the computer understands, the build-essential will do this conversion.

The easiest way to get this, is to be connected to the internet to get this. So check your laptop, and see if you have a network plug to plug into it. That way we can get a "wired" connection for now. So the plug looks kind of like a telephone jack, but bigger. Try pluggin laptop into and make sure you are on the internet, then open up a terminal windows and at the command prompt type

```
sudo apt-get install build-essential
```

---

### Post by newbee70 on 2008-12-23
Linuxford;

have you gone into\:

system / administration / hardware drivers: and made sure your driver is enabled?

and then you left clicked on your network Icon "upper left toolbar".
to make sure your wireless unit is setup?

and that you have right clicked on the network Icon and made sure networking is enabled?

**Welcome to the forums**

---

### Post by ReMO451 on 2008-12-26
see, the problem is I have no way of putting my computer (not a laptop) in a wired connection without unplugging everything, lugging it halfway across the house to where my router is, and then setting it back up again. This may sound odd but is there any way to download build essential from Windows XP, transferring it to Ubuntu, then installing it there?

---

### Post by northern lights on 2008-12-26
> **ReMO451 said:**
> see, the problem is I have no way of putting my computer (not a laptop) in a wired connection without unplugging everything, lugging it halfway across the house to where my router is, and then setting it back up again. This may sound odd but is there any way to download build essential from Windows XP, transferring it to Ubuntu, then installing it there?
*[build-essential]("http://packages.debian.org/sid/build-essential")* is a meta-package containing several compilers and the like, such as gcc (GNU C Compiler), g++ (GNU C++ Compiler) and make.

While I don't think you will find a .deb with all of them in it, you can download its elements separately. The above link provides a .deb, but that's merely 7.0 KB and contains only info on what else apt-get or aptitude is supposed to download.

Theoretically you can download everything it contains as .debs, but sorting out dependencies is going to be a pain in the butt (you'd be going back to the stoneage before package management tools). Probably a bigger pain than transferring the comp to the router.

However, if you know exactly what it is you need (just gcc, for instance), you might want to give it a try.

---

### Post by ReMO451 on 2008-12-26
Alright, good point. I will try to move the computer near the router within the next few days after I clean up all the junk from Christmas time (BTW, I hope you all had a merry Christmas/happy holiday). I will post my results within the next few days.

---

### Post by smarterdeal on 2009-01-07
Worldofcables deals in USB Cables, DVI Cables, Firewire Cables, Monitor Cables, Adapters, Connectors, Audio Video Cables, Gaming Accessories, PDA & Phone Accessories, PC Cables, iPOD Accessories & more

[http://www.worldofcables.com/store/default.asp](http://www.worldofcables.com/store/default.asp)

---

### Post by ugm6hr on 2009-01-11
Hope you have this solved by now.

If not - can I point you to some help:

[https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.24/+bug/185193](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.24/+bug/185193)
[https://launchpad.net/~henrik-hw0/+archive](https://launchpad.net/~henrik-hw0/+archive)
[http://ubuntuforums.org/showpost.php?p=4808839&postcount=6](http://ubuntuforums.org/showpost.php?p=4808839&postcount=6)
[http://ppa.launchpad.net/henrik-kabelkaos/ubuntu/pool/main/r/rt28xx-linux-sta/](http://ppa.launchpad.net/henrik-kabelkaos/ubuntu/pool/main/r/rt28xx-linux-sta/)

It appears that if you use Intrepid (or Hardy), there should be no need for ndiswrapper.  If you decide you want to use ndiswrapper (which apparently works), you can download it from the repository rather than compiling it (3 files to transfer by USB stick from your connected XP system).

My suggestion (assuming you use Intrepid 32- or 64-bit):
Grab the driver: [http://ppa.launchpad.net/henrik-kabelkaos/ubuntu/pool/main/r/rt28xx-linux-sta/rt2870-linux-sta-dkms_20080925-0ubuntu2_all.deb](http://ppa.launchpad.net/henrik-kabelkaos/ubuntu/pool/main/r/rt28xx-linux-sta/rt2870-linux-sta-dkms_20080925-0ubuntu2_all.deb)

> Depends: build-essential, dkms, linux-headers-
Install build-essential and dkms:
[http://packages.ubuntu.com/intrepid/build-essential](http://packages.ubuntu.com/intrepid/build-essential)
[http://packages.ubuntu.com/intrepid/dkms](http://packages.ubuntu.com/intrepid/dkms)
This may be time-consuming, and the necessary packages may be on the Install CD.  Unfortunately, these will probably not install, since they have multiple dependencies (which are detailed on the pages), so if you haven't already got those you will need to download them.
Use the search option here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
I suspect the packages you will need are:
build-essential dpkg-dev g++ g++-4.2 libc6-dev libstdc++6-4.2-dev libtimedate-perl linux-libc-dev patch
You may also need a new linux-headers package.

Put all these files in a single directory (e.g. in /home/username/debs, and install them all:
```
sudo dpkg -i ~/debs/*.deb
```

If it complains about dependencies, just search and install those files too.

---

