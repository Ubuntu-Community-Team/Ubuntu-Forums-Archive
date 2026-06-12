---
title: "[SOLVED] Odd issue with recognizing device"
date: 2007-10-06
forum: Networking &amp; Wireless
---

### Post by soluphobe on 2007-10-06
Hi, All,

I'm having a strange issue with setting up my wireless connection.  I'm using a wusb54gsc and the latest version of ndiswrapper (1.49, I think), but I've gotten a weird error.  The driver shows up as installed, and the device is recognized when plugged in, but when I run iwconfig I get:

lo
No wireless extensions

Eth0
No wireless extensions

What's up with this?

EDIT:  For clarity, I'm running Ubuntu 7.04 with a relatively clean system (I've only messed around with it to get this to work) on a dual-booting Dell Inspiron 1000.

---

### Post by soluphobe on 2007-10-12
*bump*  
Help, anyone?  Am I doing something incredibly stupid?  Or is this a real issue?

---

### Post by tkon1567 on 2007-10-12
I can't even get the driver loaded can you help me with a quick rundown...
I've downloaded the latest ndiswrapper on a separate desktop from here am I suppose to alter the file or burn it right to a disk.  Then after this when I load the file onto my 6.06 lts dapper how do I go about installing or whatever action I need to take?

---

### Post by soluphobe on 2007-10-12
First off:  My internet still doesn't work, so I may have messed up with these instructions (I mainly used [this HowTo](http://ubuntuforums.org/showthread.php?t=225206) for instructions).

Here's what I did:

Get the driver off the Linksys CD.  (There's a big folder called Drivers, just get the .inf file out of it.)  put it on your desktop.  Now get the latest version of ndiswrapper.  The version on the CD doesn't work.  sourceforge.net has it.  I'm not sure (other tutorials have it).  Now browse to your desktop in the command line, then to the folder you nave ndiswrapper in.

From the Ubuntu CD, make sure you have (in Synaptic) a package called 'universal' (or something) installed from the CD.  If not, install it.  The thread I linked to might provide more explicit instructions, but from what I can tell there are a few packages the Ubuntu CD that aren't installed and really should be (only 3/4, I just installed them all).

***restart***

Now browse to your desktop in the command line, then to the folder you nave ndiswrapper in.
Type:

[I]sudo make uninstall
make
sudo make install[/I]

That should install ndiswrapper on your system.  

***restart***

Now comes the tricky bit.  Browse to where you stored the .inf file from the Drivers folder on your Linksys CD.  Type:

*sudo ndiswrapper -i wusb54gsc.inf  *//if you use a different device, then alter wusb54gsc accordingly

IGNORE ERRORS SUCH AS_ 'Cannot find disksourcefile.  Continuing anyway'_  This is caused by a lack of .sys files, which you fix later.

Now, find the files **usb8023.sys** and **rndismp.sys**.  I got these from a windows partition in System32 or Windows, whatever.  Search for them if you must, but they are in a folder called Drivers.  Copy these into your linux partition, then from there into the folder **/etc/ndiswrapper/wusb54gsc/** (you need to be logged in as root to do this).

***restart***

Now type:

*ndiswrapper -l*

This should give you something like:

*wusb54gsc (Driver installed)*

If it says

*wusb54gsc (Invalid Driver)*

you need the .sys files copied.

I hope that helps.  Please tell me if you find something I missed.

---

### Post by kevdog on 2007-10-12
copy the .sys and .inf files onto the hard disk. and then type the commands you used directly here.

Here are my ndiswrapper instructions:
Here are my ndiswrapper instructions.  
To complete **without a working internet** connection you will need:
1. The ubuntu installation cd
2. USB flash drive
3. Another computer with an internet connection to transfer just a few files
4. WinXP drivers for your wireless card (unless you have a RTL chipset in which case you will need the Win98 drivers)
	****Note that if you are doing an installation on Ubuntu 64 bit, that you will need the appropriate WinXP 64 bit driver for your wireless card


This guide is now getting rather long.  It is organized into the following sections
1. Installation of ndiswrapper and windows drivers from source files (what most people want)
2. Ensuring that your wireless interface is on wlan0 and not some other interace (eth1,ath1,etc)
3. Modification of /etc/network/interfaces file (for those wanting to use NetworkManager)
4. Common Tips Problems, Suggestions (This section is continually growing, check here first if you have a problem)

**[SIZE="4"]Download, Compiling, Installing and Configuring Ndiswrapper from Source Files[/SIZE]**

If you already have an internet connection (ie a working wired ethernet connection),
please skip to step #4. Without any internet connection, please begin at step #1.

All commands typed at command prompt:

```

   1. After booting into Ubuntu, put the Ubuntu installation CD in drive and wait for it to "spin up"
   2. sudo apt-cdrom add
   3. sudo aptitude update
   4. sudo aptitude install build-essential linux-headers-`uname -r`
```


OK next we want to download the ndiswrapper source files (Reference URL = _[http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)_)

We are grabbing ndiswrapper-1.49rc3.tar.gz

***The following section will work if you have an internet connection
*** If you do not have an internet connection, on a different computer you will need to download the ndiswrapper source file from: 
[http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.48rc1.tar.gz](http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.48rc1.tar.gz)
Please place this file on a flash drive (USB Flash drive), transfer it to the Ubuntu machine, and then place it in the ~/ndiswrapper directory.  Continue with the next following set of instructions
```
cd ~
mkdir ndiswrapper
wget http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.49rc3.tar.gz -O ~/ndiswrapper/ndiswrapper-1.49rc3.tar.gz 
cd ndiswrapper

```

Extract, compile, and install ndiswrapper
```
tar -zxvf ndiswrapper-1.49rc3.tar.gz
cd ndiswrapper-1.49rc3
make distclean
make
sudo make install
```

Verify installation with
```
ndiswrapper -v
```

The output should be something like the following:
```

utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.49rc3
vermagic:       2.6.20-16-generic SMP mod_unload 586

```

Next create and place your Window's wireless driver into ~/driver:
```
cd ~
mkdir driver
cd driver
```

Ensuring the ***.sys and ***.inf file for the Window's driver are in the~/driver directory:
```
sudo ndiswrapper -i *****.inf
```

Verify installation with:
```
ndiswrapper -l
```
Make sure no errors are reported and you get something like:
> 
bcmwl5: driver installed
device (14E4:4320) present


Ok, to insert the ndiswrapper module into the linux kernel:
```
sudo depmod -a
```

Ensure you dont get any errors when running this command.  Then:
```
sudo modprobe ndiswrapper
```

To verify there wasnt any errors:
```
dmesg
```
and look for something like:
> ndiswrapper version *version* loaded

Next lets make an alias for wlan0 associated with ndiswrapper
```
sudo ndiswrapper -m
```

And ensure that the ndiswrapper module is loaded at boot:
```
echo "ndiswrapper" | sudo tee -a /etc/modules
```

I recommend rebooting at this time.
```
sudo shutdown -r now
```

Additional modifications may be needed to your /etc/network/interfaces and /etc/iftab files (see below).
In addition, please turn off any (WEP/WPA/MAC filtering) that may be present in the router.  This is to confirm that the basic ndiswrapper setup can connect to an unencrypted network.  Instructions how to configure for WEP/WPA encryption are included in another separate guide. 

Ndiswrapper by default assumes your card to be assigned to the interface wlan0 -- this may or may not be the case.
If after rebooting, and you issue the following command:
```
ifconfig
```
And you do not see an interface named wlan0, then continue.
Below are some strategies that I have used to ensure that your wireless device is assigned to the wlan0 interface.

**Verification/Modification of /etc/iftab file**

The /etc/iftab file acts to permanently asssociate a given MAC Address with an interface name.  Additions in this file are only necessary if you need to lock down the interface name with a MAC Address.  First discover what interface name is currently associated to your network card MAC Address:
```
lshw -C network
```

Example output:
```

  *-network               
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@06:00.0
       **logical name: wlan0**
       version: 03
       **serial: 00:12:17:35:17:10 **
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+lsbcmnds driverversion=1.48rc1+Cisco-Linksys ,LLC.,02/1 ip=192.168.1.101 latency=64 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:3c000000-3c001fff irq:11

```

In the example above my card's MAC Address - 00:12:17:35:17:10 - is currently assigned to wlan0 (logical name line).  If your card is assigned to a different logical name (such as eth1, ath0, ra0), then modifications will be needed to your /etc/iftab file.  

To modify your /etc/iftab file:
```
gksu gedit /etc/iftab
```

You will need to ensure your interface name is associated with wlan0 rather than a different interface name. There are two ways to accomplish this: 
#1) Let the computer do it automatically at boot, 
#2) Manually make the association  

In case #1 manually comment all the associations listed in your /etc/iftab file -- allow the computer to assign them internally at boot.  **This solution is probably the most viable for most users.**  An example of how to accomplish this:  

```

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

#eth1 mac 00:12:17:35:17:10 arp 1

```

Because the association of eth1 with the MAC Address was commented, the computer will internally and automatically make the assocation of an interface name with the MAC address.  This process of associating wlan0 with the networking device's MAC Address should work about 99% of the time.  If for some reasom it does not, proceed to step #2.

In case #2 - Manually make the association you need to ensure there is only one MAC address associated with one interface name.

```

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

#eth1 mac 00:12:17:35:17:10 arp 1
wlan0 mac 00:12:17:35:17:10 arp 1

```

In this example the old interface associated of eth1 was commented, and the new association of wlan0 to the card MAC address was made manually.

If modification of the /etc/iftab file was performed, a reboot is recommended at this time.
```
sudo shutdown -r now
```

**Modification of /etc/network/interfaces file**

First step is to comment out all the unnecessary interface names with the file.  In order to discover what interface names are currently needed:

```
lshw -C network
```
With all the devices listed, note their logical names.  An example:

```

  *-network               
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@06:00.0
       **logical name: wlan0**
       version: 03
       serial: 00:12:17:35:17:10
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+lsbcmnds driverversion=1.48rc1+Cisco-Linksys ,LLC.,02/1 ip=192.168.1.101 latency=64 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:3c000000-3c001fff irq:11

```

Only the names mentioned with this command need to be listed in the /etc/network/interfaces file (along with the loopback address).

First backup your current interface file configuration in case something goes wrong:
```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak

To modify your /etc/network/interfaces file:
[CODE]gksu gedit /etc/network/interfaces
```


A basic interface file, might include the following (assuming a wired ethernet device is present - eth0, and the wireless device installed with ndiswrapper - wlan0) -- Note in this example I commented out the old eth1 interface -- I could have also removed these lines to have the same effect.

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

```

Further modications may be needed to this file, depending if you need to run your card in roaming mode (convenient with laptops that often connect to different routers of networks), configure your card with static IP address, desire to set WEP/WPA authentication parameters manually, etc.  Again there are many possibilites at this point, far too many to list the different permutations, however this gives you a basic starting point.


**[SIZE="4"]Common Tips Problems, Suggestions[/SIZE]**

Suggestions:
1. The command **[SIZE="3"]lshw -C network[/SIZE]** always tells you what driver you are using. Here is an example:
```

  *-network               
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@06:00.0
       logical name: wlan0
       version: 03
       serial: 00:12:17:35:17:10
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes **[SIZE="3"]driver=ndiswrapper+lsbcmnds driverversion=1.48rc1+Cisco-Linksys ,LLC.,02/1[/SIZE]** ip=192.168.1.102 latency=64 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:3c000000-3c001fff irq:11


```

If you are having a problem after the installation, ensure that you have the correct version of ndiswrapper installed, and that you are not using another driver.

2. Discovering your chipset -- You can always find the chipset of your pci wireless device with the following command (***Note this will not work for wireless USB dongles):

```
lspci -nn | grep Network
```

3. **Broadcom chipset users** -- Be sure to blacklist the bcm43xx driver in the /etc/modprobe.d/blacklist file

For broadcom chipset users, in most cases you will need to blacklist the native bcm43xx drivers since they take precedence over ndiswrapper.  If after installing ndiswrapper, and things are not working, and you check lshw -C network and you find the following:
```

  *-network               
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@06:00.0
       logical name: wlan0
       version: 03
       serial: 00:12:17:35:17:10
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes **[SIZE="3"]bcm43xx[/SIZE]** ip=192.168.1.102 latency=64 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:3c000000-3c001fff irq:11


```

You need to do ONE of the following to solve this problem:
a. At command line type:
```
echo "blacklist bcm43xx" | sudo tee -a /etc/modprobe.d/blacklist
```

b. Manually edit the /etc/modprobe.d/blacklist file: (```
gksu gedit /etc/modprobe.d/blacklist
```), and add the following:
```
blacklist bcm43xx
```

4. INVALID DRIVER - Ive installed ndiswrapper but when I try to install the Windows driver Im getting a line that states:

```

root@dhcppc1 ndiswrapper-1.47]# /usr/sbin/ndiswrapper -i bcmwl5.inf
driver bcmwl5 is already installed
root@dhcppc1 ndiswrapper-1.47]# /usr/sbin/ndiswrapper -l
bcmwl5 : invalid driver!
driver : invalid driver!

```

This error usually means that there are duplicate or more than one driver installed with ndiswrapper.  The easiest way to resolve this message is to do the following:

```
sudo rm -R /etc/ndiswrapper *
```

You will then have to reinstall your windows driver via.
```
sudo ndiswrapper **********.inf  <-----Substitue the appropriate name of your inf file here.
```

5. I tried install ndiswrapper from repository before I found this guide.  How do I uninstall it??

**[SIZE="4"]Ndiswrapper Uninstall Instructions[/SIZE]**

These are instructions for manual un-installation of ndiswrapper.  I would suggest if you installed ndiswrapper from repository with use of Synaptic, apt-get(aptitude), or some other means (Aptitude), you use the same means to uninstall the ndiswrapper program.  Sometimes however un-installation via these means are unsuccessful and the following steps are necessary.  These steps are also necessary if you have ever installed ndiswrapper from source sometime in the past.

Dont worry if some of these commands don't do anything or seem not to work -- some may be repetitive.

```

sudo aptitude purge ndiswrapper
sudo rm /etc/modprobe.d/ndiswrapper
sudo sh -c "sed '/^ndiswrapper$/d' /etc/modules > /etc/modules.temp.rm; mv /etc/modules.temp.rm /etc/modules"
sudo rmmod ndiswrapper
sudo /lib/modules/`uname -r`/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko
sudo rm -rf /etc/ndiswrapper
sudo rm /usr/sbin/ndiswrapper
sudo rm /sbin/loadndisdriver
sudo rm /lib/modules/`uname -r`/misc/ndiswrapper.ko

```

---

### Post by soluphobe on 2007-10-13
Wow!  Thanks so much.  I'll try that out (I think the issue might be that ndiswrapper isn't loading at boot).  I'll post if it works (got to go now).  Thanks again!

---

### Post by soluphobe on 2007-10-14
Alright.  I tried all the instructions up to when I type:
```
lshw -C network
```
I get:
```
*-network
                  description:  **Ethernet interface**
                  product:  SiS900 PCI Fast Ethernet
                  vendor: Silicon Integrated Systems [SiS]
                  physical id: 4
                  bus info: pci@00L04.0
                  logical name: **eth0**
                  version: 91
                  width: 32 bits
                  clock: 33MHz
                  capabilities: bus_master cap_list ethernet physical
                  configuration:  broadcast=yes driver=**sis900** driverversion=v1.08.10 Apr. 2 2006 latency=173 maxlatency=11 mingnt=52 multicast=yes
                  resources: ioport:1800-18ff iomemory:e4003000-e4003fff irq:22
```

My wireless adapter doesn't show up!  So I just typed ```
lshw | less
``` and I found:
```
*-usb:1 UNCLAIMED
                   description: Communication device
                   product: Compact Wireless-G USB Network Adapter with SpeedBooster
                   vendor: Broadcom
                   physical id: 3
                   bus info: usb@3:3
                   version: 0.06
                   serial: 8057
                   capabilities: usb-2.00
                   configuration: speed=480.0MB/s
```

Also, I ran lspci and I got a ton of results, most connected to this SiS thing (I think they made my motherboard).  

Now, I don't have a PCI card (I have a slot for one, however).  I also blacklisted the sis900 driver, and this still comes up.  Should I go ahead and transfer my network settings to wlan0?  Or do I need to go through something special to get rid of my phantom PCI card?

EDIT:  One other thing.  Sometimes (it seems intermittently), I get a network device called eth0:avahi.  I don't know where this comes from or if it is important, but it seems to show up related to ndiswrapper.    When I try to configure it, I get a message that says it does not exist.  Does anyone know what it is?

EDIT2:  In my /etc/network/interfaces file, I have:

```
auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto ath0
iface ath0 inet dhcp

auto **wlan0**
**iface wlan0 inet dhcp**
``` (I've never edited the file).  I've already run ```
sudo depmod
sudo modprobe ndiswrapper
ndiswrapper -m
``` but it doesn't make anything work.

---

### Post by soluphobe on 2007-10-16
*bump*

Okay, I think I've got the problem narrowed down to the fact that my wireless device never shows up as a wireless interface.  I think some other driver must be hijacking it at boot/plugin and not giving ndiswrapper a chance, despite the fact that I've told ndiswrapper repeatedly to use its installed driver for the device.  Is there a command to view what driver a device is using?  I can't find it.

---

### Post by soluphobe on 2007-10-21
YAY!  Wireless works!  I eventually got it working by following a hybrid of the [ndiswrapper wiki]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/") and the instructions kevdog posted.

First, my system was getting trashed (~3 months of terminal fiddling by a noob = bad news) so I reinstalled Ubuntu 7.04.  I then installed everything off the CD that ndiswrapper needed.  After that, I got the driver correctly installed, .sys files and all.

NDiswrapper v1.48, wusb54gsc driver, all fine.  

I have two custom files in /etc/udev/rules.d , 99-custom.rules and 50-udev.rules .  For the contents of these rules, see the ndiswrapper wiki section on Linksys WUSB54GSC.

Originally, 50-udev.rules had no BUS=="usb" clause in it, and I came up with two or three 'Bad CDC descriptors' errors in systemlog.  I added the clause and then I got only one, in addition to something called a rndis_host as an interface driver.

I then ran

```
sudo depmod -a
sudo modprobe ndiswrapper
```

This loaded a WORKING version of the wusb54gsc driver into my kernel.  I rebooted.

Wlan0 was gone.  So I reran depmod -a/modprobe ndiswrapper, and wlan0 reappeared.  Then, to make the change permanent, I ran

```
sudo ndiswrapper -m
```

which made it permanent.   The important issue seems to be not to run any depmod/modprobe stuff (and certainly not ndiswrapper -m) until your driver is installed properly.

At this point, it all worked.  Thanks!

---

