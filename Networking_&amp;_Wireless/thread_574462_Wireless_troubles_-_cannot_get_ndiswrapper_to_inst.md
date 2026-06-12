---
title: "Wireless troubles - cannot get ndiswrapper to install"
date: 2007-10-12
forum: Networking &amp; Wireless
---

### Post by JamesDP on 2007-10-12
I really didn't want to start a new post, so I searched these forums and others, read a lot of threads to try and find some answers, and after 6+ hours (and 4 hours to install), I'm at my wits end.

I just bought a new machine (for the purpose of building a MythTV box) and I'm using a TrendNet TEW-424UB USB Wireless adapter. I'm using 7.04 (32-bit). I've attempted to follow the install directions for ndiswrapper, but I'm getting all sorts of error messages that I can't decipher or find any answers to, so I hope someone can help. Since I don't have any internet connection on that machine, I don't have anyway of copying and pasting all the codes and stuff here, but my troubles come at the "make" step during the install. Everything is find up to that point. I can't seem to find anything on the ndiswrapper sourceforge site that helps, so if anyone can help me out or point me in the right direction, it would be much appreciated.

Thanks!

---

### Post by kevdog on 2007-10-12
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

[SIZE=2]**This guide assumes we are downloading and installing ndiswrapper version 1.48**[/SIZE].  As ndiswrapper is developed and new versions put forth, version 1.48 may not be available in the future.  In this case it may be best to visit the ndiswrapper website and manually download the .tar.gz version for the most recent version - [http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482).  Use the remainder of this guide as a reference, paying close note to the actual version number that you have downloaded.  Directories in this guide will be referenced for version 1.48.  Directories may have to be reference by a different number (i.e 1.49) if using a more recent version. 

***The following section will work if you have an internet connection
*** If you do not have an internet connection, on a different computer you will need to download the ndiswrapper source file from: 
[http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.48.tar.gz](http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.48.tar.gz)
Please place this file on an alternative transfer medium (USB Flash drive / or CD-ROM), transfer it to the Ubuntu machine, and place the file in the ~/ndiswrapper directory.  Skip the instructions listed directly below and go to the next set of instructions for extracting ndiswrapper.
****Note: Those wanting to use the SVN version of ndiswrapper please skip to the appropriate section below

```
cd ~
mkdir ndiswrapper
wget http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.48.tar.gz -O ~/ndiswrapper/ndiswrapper-1.48.tar.gz 
cd ndiswrapper

```

Extract ndiswrapper
```
tar -zxvf ndiswrapper-1.48.tar.gz
cd ndiswrapper-1.48

```


*** SVN version of ndiswrapper - An alternative installation method for those with existing ethernet connection 
For those wanting to live on the edge and use the most recent beta release of ndiswrapper, this package can be download from the svn repository. 
Install the subversion package
```
 sudo aptitude install subversion 
```
Download the ndiswrapper svn package
```

cd ~
mkdir ndiswrapper
cd ndiswrapper
mkdir ndiswrapper-svn
svn co co https://ndiswrapper.svn.sourceforge.net/svnroot/ndiswrapper/trunk/ndiswrapper ndiswrapper-svn
cd ndiswrapper-svn

```
***

The remainder of the steps are applicable to all ndiswrapper installation methods
Compile and Install ndiswrapper
```

make distclean
make
sudo make install
```

Verify installation with
```
ndiswrapper -v
```

The output should be something similar to the following (svn version may differ slightly):
```

utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.48
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

### Post by JamesDP on 2007-10-12
1. I don't have a USB flash drive.

2. When I got to "sudo aptitude update" it returned a whole host of errors along the lines of "Could not resolve 'security.ubuntu.com'".

---

### Post by kevdog on 2007-10-12
1. Use a CD instead -- just a medium to transfer the files

2. Forget about the errors -- you are getting them most likely because you are not connected to the internet.

---

### Post by JamesDP on 2007-10-12
"make distclean" works.
"make" still brings up a whole bunch of errors.
"sudo make install" brings up the same batch of errors.
"ndiswrapper -v" says "ndiswrapper is not installed. You can install it by typing: sudo apt-get install ndiswrapper-common"

---

### Post by kevdog on 2007-10-12
Are you sure you typed #4 at the beginning of the guide correctly??  Its `uname -r` with backticks

---

### Post by JamesDP on 2007-10-13
I'm not sure I did the backticks. The terminal window doesn't go back that far.

Is the "uname" my username or literally "uname"?

---

### Post by kevdog on 2007-10-13
Just take that command line from #4, copy and paste it into your terminal (without #4)

---

### Post by JamesDP on 2007-10-13
Okay. Followed everything to the letter and got a wireless connection. Connected to the network here at the house and I'm in, but I have 0% signal strength. Any ideas?

---

### Post by kevdog on 2007-10-13
Post the following

iwlist scan
lshw -C network
ndiswrapper -l
modinfo ndiswrapper
route -n

---

### Post by JamesDP on 2007-10-13
```
iwlist scan
lo	Interface doesn't support scanning.

eth0	Interface doesn't support scanning.

wlan0	Scan completed:
	Cell 01 - Address: 00:14:6C:7C:FE:A0
		  ESSID:"OPN-1"
		  Protocol:IEEE 802.11g
		  Mode:Managed
		  Frequency:2.437 GHz (Channel 6)
		  Quality:18/100  Signal level:-84 dBm  Noise level: -96dBm
		  Encryption key:on
		  Bit rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
			    12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
			    48 Mb/s; 54Mb/s
		  Extra:bcn_int=100
		  Extra:atim=0
		  IE: WPA Version 1
		      Group Cipher : TKIP
		      Pairwise Ciphers (1) : TKIP
		      Authentication Suites (1) : PSK

```
```
lshw -C network
WARNING:  you should run this program as super-user
  *-network
       description: Ethernet interface
       product: RTL8111/81688 PCI Express Gigabit Ethernet controller
       vendor: RealTek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@04:00.0
       logical name: eth0
       version: 01
       serial: 00:e0:4d:39:fb:80
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=0 multicast=yes
       resources: ioport:ac00-acff iomemory:fddff000-fddfffff irq: 19
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:d1:3c:d8:0c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes drover=ndiswrapper+net8187b driverversion=1.48+Realtek Semiconductor Corp. multicast=yes wireless=IEEE 802.11g

```
```
ndiswrapper -l
net8187b : driver installed
        device (OBDA:8189) present

```
```
modinfo ndiswrapper
filename:        /lib/modules/2.6.20-15-generic/misc/ndiswrapper.ko
license:         GPL
version:         1.48
description:     NDIS wrapper driver
author:          ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:      3C6A9B2C518323EF6FE1A9D
depends:         usbcore
vermagic:        2.6.20-15-generic SMP mod_unload 586
parm:            if_name:Network interface name or template (default wlan%d) (charp)
parm:            proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:            proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:            debug: debug level (int)
parm:            hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:            utils_version:Compatible version of utils (read only: 1.9) (charp)

```
```
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 eth0
```

---

### Post by ayenack on 2007-10-13
Not sure if you know this but the TRENDnet TEW-424UB should work out of the box on Ubuntu 7.04.  Have a look at this.

[https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-424UB_(ndiswrapper)](https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-424UB_(ndiswrapper)))

---

### Post by JamesDP on 2007-10-13
> **ayenack said:**
> Not sure if you know this but the TRENDnet TEW-424UB should work out of the box on Ubuntu 7.04.  Have a look at this.

[https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-424UB_(ndiswrapper)](https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-424UB_(ndiswrapper)))

I appreciate the suggestion, but apparently TrendNet switched the TEW-424UB from the SiS chip to a RealTek chip, so I'm not sure those directions would have helped. They may have, but it's kinda moot because I have it working. My problem at this point is that even though the system recognizes it and has connected to our home network, I have 0% signal strength, so I can't do anything--no internet, email, etc.

---

### Post by JamesDP on 2007-10-13
Okay, very weird. I moved the adapter from the back of the computer (because the box and the LCD TV I'm using for a monitor are between the adapter and the router) to a port on the front and now I have 60-70% signal strength, but still no internet connection. Is there a setting I'm missing somewhere?

---

### Post by ayenack on 2007-10-13
Didn't know that. Don't know enough about ndiswrraper to offer any more help. Sorry. Can I ask what RealTek chipset it uses?

---

### Post by kevdog on 2007-10-13
Turn off the WPA encryption on the router for one -- that would be a start.

Also check dmesg | more and see if you see any errors regarding your wireless card after a reboot.

The signal quality (if its accurate) is only 18/100 which sometimes causes errors too.

You can also not run wired and wireless at the same time (if you are doing so).

To disable wired and get wireless working.
sudo ifconfig eth0 down
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up

---

### Post by JamesDP on 2007-10-14
The only error messages I saw come up in dmesg came up at the very end:
```
[   56.320000] ADDRCONF (NETDEV_UP): eth0: link is not ready
[   56.320000] ADDRCONF (NETDEV_UP): wlan0: link is not ready
[   85.572000] ADDRCONF (NETDEV_CHANGE): wlan0: link is not ready
[   86.292000] wlan0: duplicate address detected!
[  101.792000] ADDRCONF (NETDEV_UP): wlan0: link is not ready
```
Is turning off the WPA a requirement? And if so, why? I didn't have to do that with any of our Windows machines or my Mac laptop and I'm not entirely comfortable with unsecuring our whole network.

---

### Post by kevdog on 2007-10-14
Can you post your /etc/iftab file

Turning of WPA is just for testing purposes to get this whole thing up and running.  Once its running then we can go back to WPA.  WPA is sometimes a pain in the butt to get going.

---

### Post by JamesDP on 2007-10-14
/etc/iftab
```
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:e0:4d:39:fb:80 arp1
```
As to turning off WPA, that's a no-go, but we have a second DSL line at the house here, so I'm gonna have to hook up an old router to it.

---

### Post by kevdog on 2007-10-14
Some of the messages you are providing are very strange.  Let me know when you get an unencrypted wireless connection going.  Can you post:

```
lsmod | egrep '(ndis | 818)'
```

---

### Post by JamesDP on 2007-10-14
Kevdog, I appreciate your help, but this just isn't going to work for me. I've been spending every waking moment for the last three days trying to get this to work and I don't want to have to go through setting up a DSL modem that may or may not work with Ubuntu and then a router that may or may not work with Ubuntu and then hope that it all works with the USB Wireless Adapter that doesn't seem to want to work with Ubuntu.

I was really excited about trying about Ubuntu - I last used Linux over 7 years ago (RedHat) and while I found it interesting, I didn't find any benefit at the time to make it worth switching - and was completely set to having a Linux-only machine because frankly I'm sick of Windows and only use it on my other machine because that's for my business - but it works. Setting up wireless with it took an hour and I thought *that* was a pain, but three days of not being able to get the wireless working has sucked all the fun out of computing for me. I'm not one of those that's going to go, "Oh Ubuntu sucks" or "Linux sucks" - even though they don't make it easy. But it's that way because of Microsoft and manufacturers who have to cowtow to them in order to make any money. But if I don't have an internet connection on this machine, then it's just a really fast, really pretty doorstop.

Again, thanks for your help, but it looks like I'm gonna have to suck it up and put XP on this box. Maybe I'll set it up to dual-boot and leave a partition for Ubuntu.

---

### Post by kevdog on 2007-10-14
Check back if you ever change your mind..Good luck

---

### Post by richardfenderson on 2007-10-14
Looks like this is a good time to hijack the thread.

> **kevdog said:**
> 
*** If you do not have an internet connection, on a different computer you will need to download the ndiswrapper source file from: 
[http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.48.tar.gz](http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.48.tar.gz)
Please place this file on an alternative transfer medium (USB Flash drive / or CD-ROM), transfer it to the Ubuntu machine, and place the file in the ~/ndiswrapper directory.

I have the file on a USB, and I can transfer it anywhere useful on the Linux machine, but how do I place it in the ~/ndiswrapper directory?

Edit: Oh yeah, I'm using Ubuntu 6.06.1, if that matters for anything.

---

### Post by kevdog on 2007-10-14
mkdir ~/ndiswrapper
cp ndiswrapper-1.48.tar.gz ~/ndiswrapper

---

### Post by richardfenderson on 2007-10-20
> **kevdog said:**
> 
The remainder of the steps are applicable to all ndiswrapper installation methods
Compile and Install ndiswrapper
```

make distclean
make
sudo make install
```

I get this:```
bash: mk: command not found
```

... for all three steps.

It looked like everything worked until then.

---

### Post by kevdog on 2007-10-20
did you install the build-essential package??

---

### Post by wieman01 on 2007-10-20
Question to you guys... why make it so complicated and install from source? The packages come with the CD. Just pop it in the drive and install it using Synaptic (or follow Kevdog's instructions given earlier). There is no need to install from source.

---

### Post by richardfenderson on 2007-10-21
> **kevdog said:**
> did you install the build-essential package??

I think so.

In any case, I ended up re-installing the whole system (after a failed attempt to install 7.10), so I've started from scratch.  I've gotten to this:

> **kevdog said:**
> 
The output should be something similar to the following (svn version may differ slightly):
```

utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.48
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

I got roughly the output described in the first box, so that worked.  I also followed the next few steps (up to "cd driver") and they seemed to work.  At least, there weren't any error messages.  However, the .sys and .inf stuff is beyond me.

I have the driver file (Utility_Driver_TEW-421PC_423PI_b1_2.00.zip) saved to the Home folder, but I'm not sure what to do with it.

---

### Post by kevdog on 2007-10-21
You need to unzip this and then probably go into the winxp subfolder and look for the sys and inf file for your particular driver.  Just to save you some time, if you have a win computer available Id probably do it this way.  If not you then try unzip to unzip the file.

---

### Post by guppygould on 2007-10-28
This guide is really quite nice. I can follow it all through and understand all the commands that are being used, the problem is that I get an 'unable to mount the cd' message after typing in 'sudo apt-cdrom add'. 

It's probably somehting really simple that I'm doing wrong though.

Any ideas?

Cheers,

-Leo

---

### Post by kevdog on 2007-10-28
Hmm, unable to mount cdrom??  Just to make sure of a few things
1. That the cdrom is actually in the driver when you type sudo apt-cdrom add
2. Verify the cd rom is actually readable (maybe on a different computer).

---

### Post by guppygould on 2007-10-28
Yeah the CD-ROM is in the drive -I've tried it both ways. and the CD can be read on my both of my computers.

Will it make a difference with my ubuntu install being through wubi on the pc which needs the ndiswrapper?

Thanks,

-Leo

---

### Post by kevdog on 2007-10-28
I dont know a lot about wubi -- do you have wired internet access at all on the computer?  Have you tried another disc.

---

### Post by guppygould on 2007-10-28
Sadly, no.

I might haul the computer downstairs next weekend and plug it in to the router but it's a bit of a pain. My friend has my other feisty CD so I'll see if he can let me try that one.

When I insert the CD ubuntu recognises it and opens it like when you open a directory in ubuntu if that's of any use?

Thanks for the help,

-Leo

---

### Post by kevdog on 2007-10-28
Ok - so the cd works.  If you close this window, and type the apt-cdrom add command you still get the error message about not mounting  -- you are typing sudo apt-cdrom add?

---

### Post by guppygould on 2007-10-28
I've tried both of those and they still give the 'failed to mount' thing! :(

---

### Post by kevdog on 2007-10-28
Ok, download the ndiswrapper source files from sourceforge.  Place the tar.gz package on a usb stick or some other medium and bring it to the ubuntu machine.  

As far as the linux headers and build essential package, you are going to have to look for the .deb packges on the internet, likely they are located in a debian repository.  I dont know why its not working for you.

---

### Post by guppygould on 2007-10-28
Yeah I've already got those. So I'll have a hunt for those .deb packages on the net. Thanks for your help.

-Leo

---

### Post by wieman01 on 2007-10-29
> **guppygould said:**
> Will it make a difference with my ubuntu install being through wubi on the pc which needs the ndiswrapper?
Actually it should make no difference at all.

This does not work for you?
> sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9

---

### Post by guppygould on 2007-10-29
Nope the problem is I can't mount the disc to begin with :(

I just tried to use my old 6.10 disc and that was no use either, so the .deb files are the only option now. I've had a look around for them but I'm not sure where the right files I'm looking for are, so could anyone help me out with that?

I'm sorry for bugging you guys with all of this but an OS without the internet is pretty annoying.

---

### Post by kevdog on 2007-10-29
Determine your kernel version

Type at command line
uname -r

Then you want the package
linux-headers-<kernel version>.deb
build-essential.deb

[http://packages.debian.org/etch/build-essential](http://packages.debian.org/etch/build-essential)
[http://packages.debian.org/search?keywords=linux-headers&searchon=names&suite=stable&section=all](http://packages.debian.org/search?keywords=linux-headers&searchon=names&suite=stable&section=all)

---

### Post by guppygould on 2007-11-02
Thanks for all the help guys! No internet yet but my card is recognized in the network manager it just can't see any networks. It's progress I guess. :)

---

### Post by kevdog on 2007-11-02
Ok can you post the following:

lshw -C network
iwlist scan

---

### Post by guppygould on 2007-11-03
lshw -C network:
> 
root@ubuntu:/home/guppygould# lshw -C network
  *-network               
       description: Ethernet interface
       product: 190 Gigabit Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@00:04.0
       logical name: eth0
       version: 00
       serial: 00:13:d4:29:ea:61
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis190 driverversion=1.2 duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: iomemory:febf3c00-febf3c7f ioport:cc00-cc7f irq:21
  *-network
       description: Wireless interface
       physical id: 1
       logical name: rausb0
       serial: 00:11:50:6b:1c:45
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


iwlist scan:
> 
guppygould@ubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Failed to read scan data : Operation not supported

rausb0    No scan results



---

### Post by kevdog on 2007-11-03
Looks like from what you posted that you dont have ndiswrapper set up correctly.  Can you post

modinfo ndiswrapper
ndiswrapper -l
lsmod | grep ndis

---

### Post by guppygould on 2007-11-03
Hmm just had a look and my ndiswrapper and it's missing some of the utils files. I've decided that the way forward is to do it the inconveniant way of taking everything downstairs and cableing it to the router. I'll know that way will work at least and it'll only take 1/2 an hour or so, which'll save both my time and yours. Next time I'm buying some other wifi card. It's surprising as a lot of people have said that it works out of the box, I guess there will always be some anomalies (would be mine wouldn't it? :P)

Thanks for the help Kevdog!

---

### Post by kevdog on 2007-11-03
Atheros cards seem to work really well in Ubuntu.  Least that is from my non-scientific poll:
[http://ubuntuforums.org/showthread.php?t=594857](http://ubuntuforums.org/showthread.php?t=594857)

I have a broadcom and atheros card, --both work -- the atheros card worked out of the box.

---

