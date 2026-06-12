---
title: "Wireless install without internet connection."
date: 2007-09-19
forum: Networking &amp; Wireless
---

### Post by Anaphylaxis on 2007-09-19
Hi Y'all

I have a problem following the wireless tutorials, they all tell me to install something using apt-get and downloading from the net, but I have no wired connection. 

Right now I am typing from my Win XP comp. I have a D-Link dwl G510 wireless card Rev C using the **rt61** ralink drivers in windows. 

Could anybody give me directions **which packages** I have to download to get my wireless card working, and **how I install them** from a burnt CD or an external drive? 

Problem is that I can't find .deb files for all the components I need to have installed for ndiswrapper to work, and I don't know how to install the tar.gz/tar.bz2 files, I don't even think the tools needed are installed by default. 

This goes for other solutions not using ndiswrapper as well.

If anybody could tell me what to do, or show me a link to a site where a similar offline install is explained, I would be grateful.

---

### Post by kevdog on 2007-09-19
You need to compile the drivers from source -- tar.gz is just a zip format which contains the source files.

You definitely will need a computer with an internet connection to download these source files and then bring them to ubuntu with usb stick.

You will also need ubuntu installation cd.

Lets get started with the basics
1. Boot into ubuntu and then stick installation cd into drive
2. At command line type: sudo apt-cdrom add
3. sudo aptitude update
4. sudo aptitude install build-essential linux-headers-`uname -r`

Those are backticks and not quotes on command #4

Ok, now lets get the source files for rt61.  They are located here:
[http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz)

Download those onto USB stick and then transfer onto Ubuntu machine.
Just to make life difficult I want the above file in the following directory:

~/serialmonkey.

You might have to drag and drop into this folder along with creating the folder.

Ok go into this directory on command line
cd ~/serialmonkey
tar zxvf rt61-cvs-daily.tar.gz
cd rt61-cvs-daily

Ok all the sources are before you.
Type the following at the command line to compile and install the drivers:
make
sudo make install

Ok there are only a couple of more steps. Make sure the USB device is not plugged in at this point:

sudo modprobe -r rt73usb
sudo modprobe -r rt2570
sudo modprobe -r rt2500usb
sudo modprobe -r rt2x00lib

Blacklist these modules, so that they aren't loaded on startup.

gksu gedit /etc/modprobe.d/blacklist (if you are using Ubuntu)
kdesu kate /etc/modprobe.d/blacklist (if you are using Kubuntu)

Add the following lines to the text file:

# Blacklist rt73usb, as it is a non-functional beta module which conflicts with the working rt73 module.
blacklist rt73usb
# Blacklist rt2570, as it causes conflicts with rt73
blacklist rt2570
# Other modules that break rt73
blacklist rt2500usb
blacklist rt2x00lib

Now lets load the rt61 module into the kernel
sudo modprobe -v rt61

Id reboot at this time with the USB device on board.  It might not work completely at this point.  If it doesnt work, can you post the following:

lshw -C network

Thanks

---

### Post by Anaphylaxis on 2007-09-19
Thanks a lot. So I have to use programs included on the install CD which aren't installed. I will try that right away. 

Only thing is I have the pci card, not the dwl-g122 usb stick. Don't know if that means anything.

---

### Post by kevdog on 2007-09-19
The rt61 drivers are only for pci based devices, not usb.  Not everything is installed from the installation cd, so the need to ask the cd to install additional programs (kind of like windows).

You will need a usb stick to transfer files from a computer with an internet connection.

As long as you are sure the wireless card needs the rt61 drivers these steps will work.  I am trusting you that you are telling me the correct information since I havent verified anything you have told me.  Im just recommnending the next series of steps based on what you have reported.

---

### Post by Anaphylaxis on 2007-09-19
Kevdog, thx for helping me out. 

I can't get past the "make" and "make install", however.

The untarred folders are named differently than what u typed. And I don't know where to type in "make"

In the first folder when I type make, I get:

> make*** no targets specified and no makefiles found. Stop

---

### Post by Lord Illidan on 2007-09-19
What are they named, then?

---

### Post by Anaphylaxis on 2007-09-19
The whole process looked like this. I made the "serialmonkey" folder on my usb drive:

> me@xubuntu:/$ cd /media/"WD PASSPORT"/linux/serialmonkey/
me@xubuntu:/media/WD PASSPORT/linux/serialmonkey$ ls
rt61-cvs-daily.tar.gz

me@xubuntu:/media/WD PASSPORT/linux/serialmonkey$ tar -zxvf rt61-cvs-daily.tar.gz
rt61-cvs-2007091911/Module/ReleaseNote
… lotsa untarring
rt61-cvs-2007091911/Module/sanity.c

me@xubuntu:/media/WD PASSPORT/linux/serialmonkey$ cd rt61-cvs-2007091911
me@xubuntu:/media/WD PASSPORT/linux/serialmonkey/rt61-cvs-2007091911$ ls
CHANGELOG  CVS  FAQ  LICENSE  Module  THANKS  WPA_Supplicant
me@xubuntu:/media/WD PASSPORT/linux/serialmonkey/rt61-cvs-2007091911$ make
make: *** No targets specified and no makefile found.  Stop.

me@xubuntu:/media/WD PASSPORT/linux/serialmonkey/rt61-cvs-2007091911$ cd CVS

me@xubuntu:/media/WD PASSPORT/linux/serialmonkey/rt61-cvs-2007091911/CVS$ ls
Entries  Entries.Log  Repository  Root

me@xubuntu:/media/WD PASSPORT/linux/serialmonkey/rt61-cvs-2007091911/CVS$ make
make: *** No targets specified and no makefile found.  Stop.

me@xubuntu:/media/WD PASSPORT/linux/serialmonkey/rt61-cvs-2007091911/CVS$ cd ..
me@xubuntu:/media/WD PASSPORT/linux/serialmonkey/rt61-cvs-2007091911$ cd Module
me@xubuntu:/media/WD PASSPORT/linux/serialmonkey/rt61-cvs-2007091911/Module$ ls
assoc.c           mlme.c         rt2x00debug.h  rtmp_wep.c
auth.c            mlme.h         rt_config.h    sanity.c
auth_rsp.c        oid.h          rtmp_data.c    STA_iwpriv_ATE_usage.txt
connect.c         README         rtmp_def.h     sync.c
CVS               ReleaseNote    rtmp.h         TESTING
eeprom.c          rt2561.bin     rtmp_info.c    wpa.c
iwpriv_usage.txt  rt2561s.bin    rtmp_init.c    wpa.h
Makefile          rt2661.bin     rtmp_main.c
md5.c             rt2661.h       rtmp_tkip.c
md5.h             rt2x00debug.c  rtmp_type.h

me@xubuntu:/media/WD PASSPORT/linux/serialmonkey/rt61-cvs-2007091911/Module$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
make[1]: *** No rule to make target `PASSPORT/linux/serialmonkey/rt61-cvs-2007091911/Module'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
rt61.ko failed to build!
make: *** [module] Error 1


---

### Post by kevdog on 2007-09-19
Ok you were right,  you need to go into the Module directory, sorry for not mentioning that.

Let me try it in a minute. I did this process about 3 months ago without any problem

---

### Post by Lord Illidan on 2007-09-19
To the original poster : Remember that you can get a solution much faster if you give more information, instead of "It doesn't work".  There are no limits on post length, so go ahead..and goodluck!

---

### Post by kevdog on 2007-09-19
Im looking at the info you provided again, and I think the problem is because you have a space in the directory name -- WD Passport.  Can you rename this directory to something else without a space in the name???  If you look at the error you are getting this seems to be the cause of the problem.

Lets say you cant rename it, you could possibly use a symbolic link --- maybe this would work also.

---

### Post by Anaphylaxis on 2007-09-19
Could very well be the reason- cuz I copied the serialmonkey folder over to my Desktop and typed "make" in the copied modules folder. 

It works!! :KS

I don't know how to rename the "WD PASSPORT" because it is my external drive, and it was automatically known as WD PASSPORT. 

The fact that copying the files to my Desktop worked could mean that you are right. No idea how you came to think of that. U must be one smart dude.

I am gonna make a quick summary of how I got this working and change title to [solved]. 

Perhaps there should even be a howto for this topic.

Thanx a lot!!!

---

### Post by kevdog on 2007-09-19
Thats it?!!  It worked without having to do anything else???  Im surprised about that.  

Can you do me a favor and with the working connection post the following:

cat /etc/network/interfaces
cat /etc/iftab
lshw -C network
modinfo rt61

That would at least make me feel better.

---

### Post by Anaphylaxis on 2007-09-19
> **kevdog said:**
> Thats it?!!  It worked without having to do anything else???  Im surprised about that.  

Can you do me a favor and with the working connection post the following:

cat /etc/network/interfaces
cat /etc/iftab
lshw -C network
modinfo rt61

That would at least make me feel better.

Here you go:

> me@xubuntu:/$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface wlan0 inet dhcp
wireless-essid Foxhound Network
wireless-key notgonnapostethat!



iface wmaster0 inet static
address 192.168.0.11
netmask 255.255.255.0
wireless-essid Foxhound Network
wireless-key notgonnapostethat!



auto wmaster0

auto wlan0
me@xubuntu:/$ 

> me@xubuntu:/$ cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:20:ed:b2:6b:0b arp 1
wlan0 mac 00:17:9a:75:1c:5c arp 1
me@xubuntu:/$ 

> lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: RaLink
       vendor: RaLink
       physical id: 9
       bus info: pci@00:09.0
       logical name: wlan0
       version: 00
       serial: 00:17:9a:75:1c:5c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt61 ip=192.168.0.135 multicast=yes wireless=RT61 Wireless
       resources: iomemory:dfff0000-dfff7fff irq:201
  *-network:1 DISABLED
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 10
       bus info: pci@00:10.0
       logical name: eth0
       version: 10
       serial: 00:20:ed:b2:6b:0b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too multicast=yes
       resources: ioport:d800-d8ff iomemory:dffefe00-dffefeff irq:201


>  modinfo rt61
filename:       /lib/modules/2.6.17-10-generic/extra/rt61.ko
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
description:    Ralink RT61 802.11abg WLAN Driver 1.1.0 CVS 2007091911
license:        GPL
vermagic:       2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1
depends:        
alias:          pci:v00001814d00000301sv*sd*bc*sc*i*
alias:          pci:v00001814d00000302sv*sd*bc*sc*i*
alias:          pci:v00001814d00000401sv*sd*bc*sc*i*
srcversion:     E065C4921787EBFAD21C5EA
parm:           ifname:Network device name (default wlan%d) (charp)
parm:           debug:Debug mask: n selects filter, 0 for none (int)
me@xubuntu:/$

---

### Post by kevdog on 2007-09-19
You dont need the wmaster stuff in your /etc/network/interfaces do you??

And I thought your interfaces file would have needed to look something like the following:

auto wlan0
iface wlan0 inet dhcp
        pre-up ifconfig wlan0 up
	pre-up iwconfig wlan0 essid YOUR_ESSID
	pre-up iwconfig wlan0 key WEP_KEY_OR_"OFF"_IF_YOU_HAVE_NONE


Thats what I would have thought!!!

---

### Post by Anaphylaxis on 2007-09-19
I have no idea what you are talking about, I am 100% n00b!! Hehe. 

I tried to install build-essential and ndiswrapper by using .deb packages earlier + made an attempt at compilation. Perhaps there is some junk lying around after that.

Anyway, the computer seems to freeze on no notice now and then. It started when I wanted to download the newest skype from their homepage. Is this connected to the modifications we just went through, or do you think it has something to do with the auto-detection done by the skype homepage?

I am on a lowmem system, so perhaps I will play around with a minimum install and do this whole thing again to learn it properly.

---

### Post by kevdog on 2007-09-19
Use this in your /etc/network/interfaces file (modify appropriately):

auto wlan0
iface wlan0 inet dhcp
pre-up ifconfig wlan0 up
pre-up iwconfig wlan0 essid YOUR_ESSID
pre-up iwconfig wlan0 key WEP_KEY_OR_"OFF"_IF_YOU_HAVE_NONE

and get rid of all the junk with wmaster0

---

