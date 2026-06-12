---
title: "lspci shows wireless card, driver installed, but wireless won't work"
date: 2007-10-09
forum: Networking &amp; Wireless
---

### Post by margiwarg on 2007-10-09
I am trying to install a wireless networking card (Trendnet TEW-423PI) in ubuntu, and have been using this link [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

When I type in ```
ndiswrapper -l
``` i get back > net8185 : driver installed device (10EC:8185) present (alternate driver:r818x) 

So the driver seems to be working. I can get to the end of section 3.5 in the instructions, but when i then go SYSTEM | ADMINISTRATION | NETWORK it shows my wired connection, but no wireless  connection, and iwconfig reports back 'no wireless extensions'

when i type in ```
lspci
``` it seems to recognize the wireless card, and says > 04:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (ref 20)

Right now I have dual boot with XP and Feisty, and the same wireless card works fine in XP. I don't have a wired connection so I've been unable to get internet in ubuntu.

any help would be appreciated,

thanks

---

### Post by kevdog on 2007-10-09
Can you post the following

lshw -C network
iwlist scan

You can either try to use ndiswrapper along with win 98 driver for this card, or use the native r818x driver with a slight twist to get it to work.  Im open to either suggestion.

---

### Post by margiwarg on 2007-10-09
Here's a copy of the output. Right now I have the  winXP driver iinstalled... do I need to uninstall that, and if so, how? (sorry, I am new to ubuntu and have no idea what i'm doing). Thanks so much!

margaret@margaret:~$ lshw -C network 
WARNING: you should run this program as super-user. 
  *-network UNCLAIMED      
       description: Ethernet controller 
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 8 
       bus info: pci@04:08.0 
       version: 20 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list 
       configuration: latency=32 maxlatency=64 mingnt=32 
       resources: ioport:9c00-9cff iomemory:fdbff000-fdbff3ff irq:5 


margaret@margaret:~$ iwlist scan 
lo        Interface doesn't support scanning. 
 
eth0      Interface doesn't support scanning.

---

### Post by margiwarg on 2007-10-09
ok, so I figured out how to uninstall the winXP driver (using sudo ndiswrapper -e <drivername>), but when i install the win98 driver and check it with ndiswrapper -l, it comes back with 

net8185 : driver installed
     device (10EC:8185) present (alternate driver: r818x)
win : invalid driver!


so I'm guessing that the win98 driver is invalid and I am somehow going to have to use the r818x one? what type of 'twist' do i have to do to get the native driver to work?

---

### Post by kevdog on 2007-10-09
Try this first

sudo rmmod r818x

sudo rm -rf /etc/ndiswrapper/*
Make sure the /etc/ndiswrapper directory is completely empty -- no subdirectories or files

Try installing the win98 driver again.  If it doesnt work, then go for the xp driver.

---

### Post by margiwarg on 2007-10-09
'sudo rmmod r818x' returns:

ERROR: Module r818x does not exist in /proc/modules

the /etc/ndiswrapper is completely empty

The win98 driver no longer shows up as invalid, but it still doesn't work. I've tried re-installing the win98, winXP, and then the win2000 drivers, and none of them seem to work. After installing a driver I go through

sudo depmod -a
sudo modprobe ndiswrapper

am I missing some critical step?

---

### Post by kevdog on 2007-10-09
Ok

Lets back up a step
You can load all the driver (win98, xp, 2000) into ndiswrapper, and then you load the ndiswrapper kernel module into the kernel (with modprobe)

After loading the kernel module, verify it is now associated with your wireless card:
lshw -C network

If you see a driver= statement in the above output you are in business.  

Then you need to bring up your interface and connect using the command line, Network Manager, WICD, etc.

Here is a guide that tells you how to connect via command line (good for initial setup but not good for everyday use -- it will tell us however if something is wrong with your setup):

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by chipfay73 on 2007-10-09
I am having the exact same problem (with same output) on my gateway mx3414 rtl8185 wireless chip.

After following the preceding posts I get  

>lshw -C network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@06:09.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64 maxlatency=64 mingnt=32
       resources: ioport:6000-60ff iomemory:b3400000-b34001ff irq:11

Nothing about a driver yet.  Also anytime I have tried to use ndiswrapper it causes my computer
to stall on boot up (probably because of bad settings, which makes it really hard to test anything)

---

### Post by kevdog on 2007-10-09
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

### Post by margiwarg on 2007-10-10
Thanks very much for your help kevdog. My wireless is up and running! 

I think my problem was that I had the 64bit version of ubuntu installed, and I was trying to install the 32 bit drivers. When I went to install the 64 bit driver, something happened, and when I went to reboot my machine it stalled and I'd get  'Kernel panic' ... so since it's a brand new computer with nothing on it I just decided to reinstall ubuntu, and to install the i386 version instead. From the download page I thought you had to install the 64 bit version on an AMD64 machine, until I started reading around the forums. I'm a total newbie (obviously) and I'm not planning on running any high end numerical simulations etc. any time in the near (or distant) future, so I figured I'd take the path of least resistance...

I really appreciate your help. After re-installing ubuntu I followed your instructions and everything is working great!

---

### Post by chipfay73 on 2007-10-16
I am glad to see it works on the 32bit ubuntu.  I am trying to get it to work on the  64bit ubuntu, because I do high end computing, I don't want to change my system.  It is not working yet, any hints?

---

### Post by aggieml on 2007-11-11
I'm having a similar problem with my rtl8185 wireless card.  Let me start off by saying that I've gotten it working easily and quickly in pclinuxos 2007 and the latest Zenwalk, but I cannot get ndiswrapper to work with this chipset in Debian or Mepis.  I blacklisted r818x, then installed ndiswrapper from source without a problem.  Then I installed the win98 driver using ndiswrapper and it says "driver installed, driver present".  Everything looks perfect, right?  If I do iwconfig, wlan0 is there.  But that's as far as I can go... I cannot connect to anything.  If I open network manager, it says "no wireless networks available" and if I manually type in my network info it attempts to connect but never does and does not give me an error message.  If I try to do it manually with iwconfig wlan0 essid myessid mode managed key xxxxxxxxxxxxxxxxxxxxxxxxx and then dhclient wlan0, it spits out a few lines of listening and then says "no dhcp leases offered - sleeping".  And if I try iwlist wlan0 scan, it says "scan complete.  no networks" but I know for a fact that there's plenty of networks around me, even completely unsecured ones.  Even if I try iwconfig wlan0 key off essid any and then dhclient wlan0, it will not associate with any access points.

Any ideas?  Could it be a coincidence that I can't get it to work on debian-based systems but I can on pclinux and zenwalk?  

One last note:  I installed ndisgtk just to see if that would spit out any errors.  At this point I had already installed my win98 drivers with ndiswrapper via konsole and it said driver was installed and hardware was present.  But when I open ndisgtk there is nothing listed under "installed windows drivers".  If I then try to reinstall the driver using ndisgtk, it says "driver DRIVER already installed"  WTF???

Thanks.

---

### Post by Paradoxfox93 on 2007-11-16
ndiswrapper -v returns:

module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
filename:       /lib/modules/2.6.20-15-generic/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.38
vermagic:       2.6.20-15-generic SMP mod_unload 

You may need to upgrade driver and/or utils to latest versions available at
[http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)

I'm so green. wth does that mean?   It seems me the differences indicate something significant.

---

### Post by Paradoxfox93 on 2007-11-16
Err...I should note that I'm doing this process because my problems seem similar.  Device list shows my card, which is a Realtek 8185.  I have eth1 connection and have followed the steps to there.  Moreover I'm not sure how to put the WinXP dirver in the directory.  Or where the directory ~/* is that we are using through the terminal.

Oh and here is my PC:

[http://www.newegg.com/Product/Product.asp?Item=N82E16834101093](http://www.newegg.com/Product/Product.asp?Item=N82E16834101093)

And that I have followed the instructions thus far up to:

ndiswrapper -v

---

### Post by Paradoxfox93 on 2007-11-16
I found this:

[http://www.opendrivers.com/driver/234627/realtek-rtl8185l-wireless-driver-26.1010-linux-kernel-2.6.x-free-download.html](http://www.opendrivers.com/driver/234627/realtek-rtl8185l-wireless-driver-26.1010-linux-kernel-2.6.x-free-download.html)

It is a linux driver for the realtek 8185 will this work just as well? On 64 bit?  How do I go about putting it on? Oh...my head hurts!  LOL!

---

### Post by Paradoxfox93 on 2007-11-19
TYVM Kevdog!!!!!!!!! I have wireless sucess on a MT3422 Gateway in 32-bit Feisty!!!!!  You rock!!  I will be attempting this with 64 bit now that I know which driver to use. However before I go there I'll be working on getting my sound running first. Again, thanks, I was already looking at wireless USB prices and compatability...

---

### Post by coolbrook on 2007-11-27
I picked up this same card today and I just want to say thanks Kevdog for the suggestion to use the Win 98 driver.  XP's didn't get me anywhere but 98's works like a charm on Gutsy.

:cool:

---

