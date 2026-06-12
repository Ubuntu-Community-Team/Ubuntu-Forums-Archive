---
title: "How To: Install Ndiswrapper (source, svn) - with Included Problem Solving Suggestions"
date: 2007-10-12
forum: Networking &amp; Wireless
---

### Post by kevdog on 2007-10-12
[SIZE="4"]**My own Personal Ndiswraper Guide - Troubleshooting Tips Included**[/SIZE]

Ive compiled this guide over many months after helping countless people with their installation procedure.  Included in the guide is how to install ndiswrapper (from either source or svn).  At the bottom of this guide are included many common tips and suggestions for problems that I have seen many people struggle with time and time again.  I hope you find this guide useful and insightful.  Please contact me with any additional tips that I can use (particularly troubleshooting tips) so that together we can make future installations of ndiswrapper as painless as possible.  

Please read through the guide at least once before performing any of the commands.  This will give you a better sense where everything is leading to.


To complete **without a working internet** connection you will need:
1. The ubuntu installation cd
2. USB flash drive
3. Another computer with an internet connection to transfer just a few files
4. WinXP drivers for your wireless card (unless you have a RTL chipset in which case you will need the Win98 drivers)
	****Note that if you are doing an installation on Ubuntu 64 bit, that you will need the appropriate WinXP 64 bit driver for your wireless card
            ****The Broadcom 64 bit driver can be found here: [http://www.linuxant.com/driverloader/drivers.php](http://www.linuxant.com/driverloader/drivers.php)


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

The following command is formated with backticks (`) and not single quotes (')
Type the command as it is exactly written or just cut and paste the instruction to a terminal
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


**[SIZE=3] PLEASE NOTE THAT THE /etc/iftab file IS ONLY PRESENT IN RELEASES PRE-GUTSY. WITH GUTSY AND HARDY RELEASES THE FOLLOWING SECTION IS NOT APPLICABLE[/SIZE]**
**Verification/Modification of /etc/iftab file **

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
echo "blacklist b43" | sudo tee -a /etc/modprobe.d/blacklist
echo "blacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist

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
sudo rm -R /etc/ndiswrapper/*
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

**[SIZE="4"]Miscellaneous Driver Resources for Ndiswrapper[/SIZE]**
**Broadcom Chipsets - Drivers -**[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by jeremy119 on 2007-12-05
how do i get to ~/ndiswrapper

---

### Post by kevdog on 2007-12-05
If you created the directory ndiswrapper, you just do a 

cd ~/ndiswrapper

---

### Post by jeremy119 on 2007-12-06
> **kevdog said:**
> If you created the directory ndiswrapper, you just do a 

cd ~/ndiswrapper

so how do i create the directory for ndiswrapper 
cause it doenst say

---

### Post by jeremy119 on 2007-12-06
nvm i found were i messed up thanks though

---

### Post by jeremy119 on 2007-12-06
when ever i enter in 
 
tar -zxvf ndiswrapper-1.48.tar.gz
cd ndiswrapper-1.48 

i get an error and i dont know why

---

### Post by kevdog on 2007-12-06
What's the error -- cant say people have stumbled on this step before.

---

### Post by b1ankskater on 2007-12-23
Hi i Have a toshiba a215 s4757 with ubuntu 7.10 and i cant get the wireless to work i have been trying many things but i am some what of a noob when it comes to ubuntu and the console. Ok i can get all the way to this step "Verify installation with:
Code:

ndiswrapper -l

"Then when i type this command i get this reply 
***** : invalid driver!
net5211 : invalid driver!
Please help i will continue to try and solve my problem untill i hear from some one here

---

### Post by kevdog on 2007-12-23
Do the following:

sudo rm -R /etc/modules/ndiswrapper/*

Make sure the /etc/modules/ndiswrapper directory is totally empty (no subdirectories or files).

Then just start over again wiith 
sudo ndiswrapper -i net5211.inf

---

### Post by b1ankskater on 2007-12-23
ok i tried to do what you told me and this is what i got

kyle@kyle-laptop:~$ sudo rm -R /etc/modules/ndiswrapper/*
rm: cannot remove `/etc/modules/ndiswrapper/*': Not a directory

then i tried to start again even with the cannot remove message and it gave me this

kyle@kyle-laptop:~$ sudo ndiswrapper -i net5211.inf
driver net5211 is already installed
kyle@kyle-laptop:~$ ndiswrapper -l
***** : invalid driver!
net5211 : invalid driver!

please do what you can to help me

---

### Post by kevdog on 2007-12-23
sudo rm -R /etc/ndiswrapper *

---

### Post by sharpycore on 2007-12-25
I can't thank you enough for this, I was so stuck until I read this guide. I'm now posting from Ubuntu. For anyone looking for the 64 bit broadcom drivers needed for 64 bit installs using this guide, they can be found here

[http://www.linuxant.com/driverloader/drivers.php](http://www.linuxant.com/driverloader/drivers.php)

But strangely enough not on the broadcom site... weird.
Thanks again, this community is full of absolute saints.

---

### Post by firegoggles on 2008-01-14
Could you please add more detail in the step by step.. It is unclear from the very start you said this at the start 

cd ~
mkdir ndiswrapper
wget [http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.48.tar.gz](http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.48.tar.gz) -O ~/ndiswrapper/ndiswrapper-1.48.tar.gz 
cd ndiswrapper

but what if i have the file on a fash drive how do i correctly copy it from a terminal window to what?how is the folder ndiswrapper folder created in this case.. (also what is " cd ~ "?) as you can tell I'm a noob and I'm begging you to give more detail in the step by step its just not clear to a total noob ...( i ended up with stuff on my desktop tried copying files around and they just wont copy they kept "flying" back to other folders when i tried to drag and drop I assume this is cuz you got be root but u cant log on in root so how the heck do you do this from comand line? you see how basic i need it hehe sorry but im honest..


ok in the next line you said this :
tar -zxvf ndiswrapper-1.48.tar.gz
cd ndiswrapper-1.48

yet in the instructions right before this it says mkdir ndiswrapper not ndisrapper-1.48 ? thats really confusing what are we doing with the plain ndiswrapper folder you said to create the very line before that?


next line that applies to me is the 
cd ~
mkdir driver
cd driver

umm where exactly do i open a terminal window to type this? does it matter?
to me its completely unclear where this folder is being created?

then you say this next :
Ensuring the ***.sys and ***.inf file for the Window's driver are in the~/driver directory:
UMMM what? well thats clear hehe?your gonna have to be exact on this i tried like dragging my inf. and .sys file into a folder and it wont even drag it just flys back where it came from ?how do i copy my .sys and .inf file into the proper folder?Please be as detailed as possible about this ... the total noob has no idea what your talking about.

perhaps if you can clean this much up i can try again .. and hopefully i can get through it i cant get online with my laptop at all presently but im confident if you can clean up some of these questions i can handle it.. 
I do appreciate your efforts very much and my tone is certainly humble and hope you read me as such..welp thanks in advance
Fire

---

### Post by kevdog on 2008-01-14
~ is a short hand notation for your home directory.  Pop open a terminal window and you are automatically placed in your home directory.  This in literal terms would be a directory named:

/home/<username>

Files on your Desktop are located in
/home/<username>/Desktop  or simply ~/Desktop

---

### Post by finno on 2008-01-19
Stepped through this (version 1.51) with no apparent problems, however no joy. I have wireless LED showing on card but nothing else.... I do not have any technical knowledge to interpret the following results
ndiswrapper -l
```
net8185 : driver installed
    	device (1799:701F) present

```

lspci
```
00:12.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139  C+ (rev 10)
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M
02:00.0 Ethernet controller: Belkin Unknown device 701f (rev 20)
```

lspci -n
```
00:00.0 0600: 1002:cbb2 (rev 02)
00:01.0 0604: 1002:7010
00:03.0 0703: 10b9:5457
00:04.0 0401: 10b9:5451 (rev 02)
00:06.0 0680: 10b9:7101
00:07.0 0601: 10b9:1533
00:0a.0 0607: 104c:ac8e
00:0a.2 0c00: 104c:802e
00:0a.3 0180: 104c:ac8f
00:0c.0 0c03: 1033:0035 (rev 43)
00:0c.1 0c03: 1033:0035 (rev 43)
00:0c.2 0c03: 1033:00e0 (rev 04)
00:0f.0 0101: 10b9:5229 (rev c4)
00:12.0 0200: 10ec:8139 (rev 10)
01:05.0 0300: 1002:4337
02:00.0 0200: 1799:701f (rev 20)
```

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan      IEEE 802.11g  ESSID:off/any
          Mode:Auto  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3
          RTS thr=2432 B   Fragment thr=2432 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Contents of iftab
```
# This file assigns persistent names to network interfaces.

# See iftab(5) for syntax.



eth0 mac 08:00:46:e9:49:50 arp 1

wlan mac 00:17:3f:32:f5:81
```

lshw -C network
```
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 10
       serial: 08:00:46:e9:49:50
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.1 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: ioport:9000-90ff iomemory:e000bc00-e000bdff irq:3
  *-network
       description: Wireless interface
       product: Belkin
       vendor: Belkin
       physical id: 0
       bus info: pci@02:00.0
       logical name: wlan
       version: 20
       serial: 00:17:3f:32:f5:81
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8185 driverversion=1.51+Realtek,02/01/2007,5.1097.0 latency=64 maxlatency=64 mingnt=32 multicast=yes wireless=IEEE 802.11g
       resources: ioport:1400-14ff iomemory:34000000-340003ff irq:4
```

Any assistance would be greatly appreciated !

---

### Post by kevdog on 2008-01-19
finno

You are close -- everything seems to be set up correctly.

Can you post
iwlist scan?

Is your network using any encryption -- Id suggest at least turning it off for now just not to confuse things.

---

### Post by finno on 2008-01-23
Many thanks for your very kind assistance...I do not have time to pursue this until next weekend due to work and family committments. Turning off WEP on router (Netopia) gives me green LED on card but they are still not talking to each other. I note that System/Network GUI only shows WEP and WPA options - I have it set for WEP and DHCP. 
iwlist output is as follows: 
```
Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency
              [interface] channel
              [interface] bitrate
              [interface] rate
              [interface] encryption
              [interface] keys
              [interface] power
              [interface] txpower
              [interface] retry
              [interface] ap
              [interface] accesspoints
              [interface] peers
              [interface] event
              [interface] auth
              [interface] wpakeys
              [interface] genie
              [interface] modulation

```

---

### Post by finno on 2008-01-23
Since my last post, I find that by turning off privacy and restarting the router from the browser, then (Using Gnome System/Network) to set the wlan properties to: 
Password: WPA Personal 
Configuration:Static IP Address
then completing the IP address, subnet and gateway values, I am finally on the air!!!!

I guess I am now going to have to do a whole lot of reading on WPA etc. before I trouble the forum again. After twelve months with Ubuntu, I find that the entire hardware issue can leave one feeling like a whipped dog returning to lick the hand of its master!.

---

### Post by kevdog on 2008-01-23
> I find that by turning off privacy

What is privacy?

---

### Post by finno on 2008-01-24
That is my ISP's user friendly description of encryption on their interface for router. 
Many thanks again for your help

---

### Post by Buster95 on 2008-01-25
Would appreciate some guidance on what I'm doing wrong here.

Followed the guide by cut and paste after first removing any possible existing versions. It failed.
Thought that perhaps it failed because ndiswrapper-1.48 wasn't the latest version, so I tried again with version 1.49. Still failed.

I'm pasting the part where I think it goes off the rails. The entire sequence is too long to bore you with and I don't know how to display it any other way.
.......
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/dexter/ndiswrapper-1.49/driver/ndiswrapper.mod.o
  LD [M]  /home/dexter/ndiswrapper-1.49/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make[1]: Leaving directory `/home/dexter/ndiswrapper-1.49/driver'
make -C utils
make[1]: Entering directory `/home/dexter/ndiswrapper-1.49/utils'
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
loadndisdriver.c:15:20: error: stdlib.h: No such file or directory
loadndisdriver.c:16:19: error: stdio.h: No such file or directory
loadndisdriver.c:17:19: error: errno.h: No such file or directory
loadndisdriver.c:18:20: error: string.h: No such file or directory
loadndisdriver.c:19:20: error: libgen.h: No such file or directory
loadndisdriver.c:21:22: error: sys/mman.h: No such file or directory
loadndisdriver.c:23:23: error: sys/types.h: No such file or directory
loadndisdriver.c:24:23: error: sys/ioctl.h: No such file or directory
loadndisdriver.c:25:22: error: sys/stat.h: No such file or directory
loadndisdriver.c:26:20: error: unistd.h: No such file or directory
loadndisdriver.c:27:19: error: fcntl.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:11,
                 from loadndisdriver.c:28:
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:122:61: error: limits.h: No such file or directory
loadndisdriver.c:29:19: error: ctype.h: No such file or directory
loadndisdriver.c:30:20: error: dirent.h: No such file or directory
loadndisdriver.c:31:20: error: syslog.h: No such file or directory
loadndisdriver.c:34:25: error: linux/major.h: No such file or directory
loadndisdriver.c:35:25: error: linux/ioctl.h: No such file or directory
In file included from loadndisdriver.c:37:
../driver/loader.h:24: error: expected specifier-qualifier-list before ‘size_t’
loadndisdriver.c: In function ‘load_file’:
loadndisdriver.c:67: error: ‘size_t’ undeclared (first use in this function)
loadndisdriver.c:67: error: (Each undeclared identifier is reported only once
loadndisdriver.c:67: error: for each function it appears in.)
loadndisdriver.c:67: error: expected ‘;’ before ‘size’
loadndisdriver.c:68: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:69: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:71: warning: implicit declaration of function ‘basename’
loadndisdriver.c:71: warning: initialisation makes pointer from integer without a cast
loadndisdriver.c:73: warning: implicit declaration of function ‘open’
loadndisdriver.c:73: error: ‘O_RDONLY’ undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function ‘syslog’
loadndisdriver.c:75: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:75: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function ‘strerror’
loadndisdriver.c:75: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:76: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:79: warning: implicit declaration of function ‘fstat’
loadndisdriver.c:81: warning: implicit declaration of function ‘close’
loadndisdriver.c:84: error: ‘size’ undeclared (first use in this function)
loadndisdriver.c:86: warning: implicit declaration of function ‘mmap’
loadndisdriver.c:86: error: ‘PROT_READ’ undeclared (first use in this function)
loadndisdriver.c:86: error: ‘MAP_PRIVATE’ undeclared (first use in this function)
loadndisdriver.c:86: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:87: error: ‘MAP_FAILED’ undeclared (first use in this function)
loadndisdriver.c:93: warning: implicit declaration of function ‘strncpy’
loadndisdriver.c:93: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:95: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:96: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:69: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘parse_setting_line’:
loadndisdriver.c:109: warning: implicit declaration of function ‘isspace’
loadndisdriver.c:115: warning: implicit declaration of function ‘strchr’
loadndisdriver.c:115: warning: incompatible implicit declaration of built-in function ‘strchr’
loadndisdriver.c:115: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:117: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:117: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:118: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:138: warning: implicit declaration of function ‘strlen’
loadndisdriver.c:138: warning: incompatible implicit declaration of built-in function ‘strlen’
loadndisdriver.c: In function ‘read_conf_file’:
loadndisdriver.c:150: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:151: error: ‘FILE’ undeclared (first use in this function)
loadndisdriver.c:151: error: ‘config’ undeclared (first use in this function)
loadndisdriver.c:157: warning: implicit declaration of function ‘lstat’
loadndisdriver.c:158: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:158: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:158: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:160: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:163: warning: implicit declaration of function ‘sscanf’
loadndisdriver.c:163: warning: incompatible implicit declaration of built-in function ‘sscanf’
loadndisdriver.c:178: warning: implicit declaration of function ‘fopen’
loadndisdriver.c:178: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:182: warning: implicit declaration of function ‘fgets’
loadndisdriver.c:194: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:205: warning: implicit declaration of function ‘fclose’
loadndisdriver.c:150: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘load_bin_file’:
loadndisdriver.c:217: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:217: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:219: warning: implicit declaration of function ‘tolower’
loadndisdriver.c:221: warning: implicit declaration of function ‘chdir’
loadndisdriver.c:222: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:224: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:230: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:232: warning: implicit declaration of function ‘ioctl’
loadndisdriver.c:232: warning: implicit declaration of function ‘_IOW’
loadndisdriver.c:232: error: expected expression before ‘struct’
loadndisdriver.c: In function ‘load_driver’:
loadndisdriver.c:249: error: ‘DIR’ undeclared (first use in this function)
loadndisdriver.c:249: error: ‘driver_dir’ undeclared (first use in this function)
loadndisdriver.c:251: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:255: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:255: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:257: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:259: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:261: warning: implicit declaration of function ‘opendir’
loadndisdriver.c:267: warning: implicit declaration of function ‘malloc’
loadndisdriver.c:267: warning: incompatible implicit declaration of built-in function ‘malloc’
loadndisdriver.c:271: warning: implicit declaration of function ‘memset’
loadndisdriver.c:271: warning: incompatible implicit declaration of built-in function ‘memset’
loadndisdriver.c:272: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:280: warning: implicit declaration of function ‘readdir’
loadndisdriver.c:280: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:282: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:284: error: dereferencing pointer to incomplete type
loadndisdriver.c:287: warning: implicit declaration of function ‘stat’
loadndisdriver.c:287: error: dereferencing pointer to incomplete type
loadndisdriver.c:288: warning: implicit declaration of function ‘S_ISREG’
loadndisdriver.c:289: error: dereferencing pointer to incomplete type
loadndisdriver.c:294: warning: incompatible implicit declaration of built-in function ‘strlen’
loadndisdriver.c:294: error: dereferencing pointer to incomplete type
loadndisdriver.c:296: warning: implicit declaration of function ‘strcasecmp’
loadndisdriver.c:296: error: dereferencing pointer to incomplete type
loadndisdriver.c:299: error: dereferencing pointer to incomplete type
loadndisdriver.c:302: error: dereferencing pointer to incomplete type
loadndisdriver.c:303: error: dereferencing pointer to incomplete type
loadndisdriver.c:305: error: dereferencing pointer to incomplete type
loadndisdriver.c:311: error: dereferencing pointer to incomplete type
loadndisdriver.c:312: error: dereferencing pointer to incomplete type
loadndisdriver.c:313: warning: implicit declaration of function ‘strcpy’
loadndisdriver.c:313: warning: incompatible implicit declaration of built-in function ‘strcpy’
loadndisdriver.c:314: error: dereferencing pointer to incomplete type
loadndisdriver.c:317: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:318: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:321: error: dereferencing pointer to incomplete type
loadndisdriver.c:282: warning: unused variable ‘statbuf’
loadndisdriver.c:344: error: expected expression before ‘struct’
loadndisdriver.c:346: warning: implicit declaration of function ‘closedir’
loadndisdriver.c:348: warning: implicit declaration of function ‘free’
loadndisdriver.c:355: warning: implicit declaration of function ‘munmap’
loadndisdriver.c:355: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:355: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:357: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:357: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c: In function ‘get_device’:
loadndisdriver.c:367: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:370: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:370: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:373: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:374: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:376: warning: implicit declaration of function ‘snprintf’
loadndisdriver.c:376: warning: incompatible implicit declaration of built-in function ‘snprintf’
loadndisdriver.c:407: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:367: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘load_device’:
loadndisdriver.c:419: error: ‘DIR’ undeclared (first use in this function)
loadndisdriver.c:419: error: ‘dir’ undeclared (first use in this function)
loadndisdriver.c:423: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:423: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:424: warning: incompatible implicit declaration of built-in function ‘memset’
loadndisdriver.c:426: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:427: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:429: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:434: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:435: error: dereferencing pointer to incomplete type
loadndisdriver.c:436: error: dereferencing pointer to incomplete type
loadndisdriver.c:439: error: dereferencing pointer to incomplete type
loadndisdriver.c:447: error: expected expression before ‘struct’
loadndisdriver.c: In function ‘get_ioctl_device’:
loadndisdriver.c:464: error: ‘FILE’ undeclared (first use in this function)
loadndisdriver.c:464: error: ‘proc_misc’ undeclared (first use in this function)
loadndisdriver.c:472: warning: implicit declaration of function ‘strstr’
loadndisdriver.c:472: warning: incompatible implicit declaration of built-in function ‘strstr’
loadndisdriver.c:473: warning: implicit declaration of function ‘strtol’
loadndisdriver.c:473: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:483: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:483: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:488: warning: implicit declaration of function ‘unlink’
loadndisdriver.c:489: warning: implicit declaration of function ‘mknod’
loadndisdriver.c:489: error: ‘S_IFCHR’ undeclared (first use in this function)
loadndisdriver.c:489: error: ‘MISC_MAJOR’ undeclared (first use in this function)
loadndisdriver.c:490: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:495: error: ‘O_RDONLY’ undeclared (first use in this function)
loadndisdriver.c: In function ‘main’:
loadndisdriver.c:511: warning: implicit declaration of function ‘openlog’
loadndisdriver.c:511: error: ‘LOG_PERROR’ undeclared (first use in this function)
loadndisdriver.c:511: error: ‘LOG_CONS’ undeclared (first use in this function)
loadndisdriver.c:511: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:511: error: ‘LOG_DEBUG’ undeclared (first use in this function)
loadndisdriver.c:513: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:515: warning: implicit declaration of function ‘strncmp’
loadndisdriver.c:517: warning: implicit declaration of function ‘printf’
loadndisdriver.c:517: warning: incompatible implicit declaration of built-in function ‘printf’
loadndisdriver.c:527: warning: implicit declaration of function ‘atoi’
loadndisdriver.c:542: warning: implicit declaration of function ‘atof’
loadndisdriver.c:549: warning: implicit declaration of function ‘strcmp’
loadndisdriver.c:556: warning: incompatible implicit declaration of built-in function ‘sscanf’
loadndisdriver.c:590: warning: implicit declaration of function ‘closelog’
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/dexter/ndiswrapper-1.49/utils'
make: *** [all] Error 2
dexter@dexter-laptop:~/ndiswrapper-1.49$ sudo make install
make -C driver install
make[1]: Entering directory `/home/dexter/ndiswrapper-1.49/driver'
make -C /usr/src/linux-headers-2.6.20-16-generic SUBDIRS=/home/dexter/ndiswrapper-1.49/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
echo /lib/modules/2.6.20-16-generic/misc
/lib/modules/2.6.20-16-generic/misc
mkdir -p /lib/modules/2.6.20-16-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.20-16-generic/misc
/sbin/depmod -a 2.6.20-16-generic -b /
make[1]: Leaving directory `/home/dexter/ndiswrapper-1.49/driver'
make -C utils install
make[1]: Entering directory `/home/dexter/ndiswrapper-1.49/utils'
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
loadndisdriver.c:15:20: error: stdlib.h: No such file or directory
loadndisdriver.c:16:19: error: stdio.h: No such file or directory
loadndisdriver.c:17:19: error: errno.h: No such file or directory
loadndisdriver.c:18:20: error: string.h: No such file or directory
loadndisdriver.c:19:20: error: libgen.h: No such file or directory
loadndisdriver.c:21:22: error: sys/mman.h: No such file or directory
loadndisdriver.c:23:23: error: sys/types.h: No such file or directory
loadndisdriver.c:24:23: error: sys/ioctl.h: No such file or directory
loadndisdriver.c:25:22: error: sys/stat.h: No such file or directory
loadndisdriver.c:26:20: error: unistd.h: No such file or directory
loadndisdriver.c:27:19: error: fcntl.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:11,
                 from loadndisdriver.c:28:
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:122:61: error: limits.h: No such file or directory
loadndisdriver.c:29:19: error: ctype.h: No such file or directory
loadndisdriver.c:30:20: error: dirent.h: No such file or directory
loadndisdriver.c:31:20: error: syslog.h: No such file or directory
loadndisdriver.c:34:25: error: linux/major.h: No such file or directory
loadndisdriver.c:35:25: error: linux/ioctl.h: No such file or directory
In file included from loadndisdriver.c:37:
../driver/loader.h:24: error: expected specifier-qualifier-list before ‘size_t’
loadndisdriver.c: In function ‘load_file’:
loadndisdriver.c:67: error: ‘size_t’ undeclared (first use in this function)
loadndisdriver.c:67: error: (Each undeclared identifier is reported only once
loadndisdriver.c:67: error: for each function it appears in.)
loadndisdriver.c:67: error: expected ‘;’ before ‘size’
loadndisdriver.c:68: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:69: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:71: warning: implicit declaration of function ‘basename’
loadndisdriver.c:71: warning: initialisation makes pointer from integer without a cast
loadndisdriver.c:73: warning: implicit declaration of function ‘open’
loadndisdriver.c:73: error: ‘O_RDONLY’ undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function ‘syslog’
loadndisdriver.c:75: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:75: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function ‘strerror’
loadndisdriver.c:75: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:76: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:79: warning: implicit declaration of function ‘fstat’
loadndisdriver.c:81: warning: implicit declaration of function ‘close’
loadndisdriver.c:84: error: ‘size’ undeclared (first use in this function)
loadndisdriver.c:86: warning: implicit declaration of function ‘mmap’
loadndisdriver.c:86: error: ‘PROT_READ’ undeclared (first use in this function)
loadndisdriver.c:86: error: ‘MAP_PRIVATE’ undeclared (first use in this function)
loadndisdriver.c:86: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:87: error: ‘MAP_FAILED’ undeclared (first use in this function)
loadndisdriver.c:93: warning: implicit declaration of function ‘strncpy’
loadndisdriver.c:93: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:95: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:96: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:69: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘parse_setting_line’:
loadndisdriver.c:109: warning: implicit declaration of function ‘isspace’
loadndisdriver.c:115: warning: implicit declaration of function ‘strchr’
loadndisdriver.c:115: warning: incompatible implicit declaration of built-in function ‘strchr’
loadndisdriver.c:115: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:117: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:117: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:118: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:138: warning: implicit declaration of function ‘strlen’
loadndisdriver.c:138: warning: incompatible implicit declaration of built-in function ‘strlen’
loadndisdriver.c: In function ‘read_conf_file’:
loadndisdriver.c:150: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:151: error: ‘FILE’ undeclared (first use in this function)
loadndisdriver.c:151: error: ‘config’ undeclared (first use in this function)
loadndisdriver.c:157: warning: implicit declaration of function ‘lstat’
loadndisdriver.c:158: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:158: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:158: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:160: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:163: warning: implicit declaration of function ‘sscanf’
loadndisdriver.c:163: warning: incompatible implicit declaration of built-in function ‘sscanf’
loadndisdriver.c:178: warning: implicit declaration of function ‘fopen’
loadndisdriver.c:178: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:182: warning: implicit declaration of function ‘fgets’
loadndisdriver.c:194: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:205: warning: implicit declaration of function ‘fclose’
loadndisdriver.c:150: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘load_bin_file’:
loadndisdriver.c:217: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:217: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:219: warning: implicit declaration of function ‘tolower’
loadndisdriver.c:221: warning: implicit declaration of function ‘chdir’
loadndisdriver.c:222: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:224: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:230: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:232: warning: implicit declaration of function ‘ioctl’
loadndisdriver.c:232: warning: implicit declaration of function ‘_IOW’
loadndisdriver.c:232: error: expected expression before ‘struct’
loadndisdriver.c: In function ‘load_driver’:
loadndisdriver.c:249: error: ‘DIR’ undeclared (first use in this function)
loadndisdriver.c:249: error: ‘driver_dir’ undeclared (first use in this function)
loadndisdriver.c:251: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:255: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:255: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:257: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:259: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:261: warning: implicit declaration of function ‘opendir’
loadndisdriver.c:267: warning: implicit declaration of function ‘malloc’
loadndisdriver.c:267: warning: incompatible implicit declaration of built-in function ‘malloc’
loadndisdriver.c:271: warning: implicit declaration of function ‘memset’
loadndisdriver.c:271: warning: incompatible implicit declaration of built-in function ‘memset’
loadndisdriver.c:272: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:280: warning: implicit declaration of function ‘readdir’
loadndisdriver.c:280: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:282: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:284: error: dereferencing pointer to incomplete type
loadndisdriver.c:287: warning: implicit declaration of function ‘stat’
loadndisdriver.c:287: error: dereferencing pointer to incomplete type
loadndisdriver.c:288: warning: implicit declaration of function ‘S_ISREG’
loadndisdriver.c:289: error: dereferencing pointer to incomplete type
loadndisdriver.c:294: warning: incompatible implicit declaration of built-in function ‘strlen’
loadndisdriver.c:294: error: dereferencing pointer to incomplete type
loadndisdriver.c:296: warning: implicit declaration of function ‘strcasecmp’
loadndisdriver.c:296: error: dereferencing pointer to incomplete type
loadndisdriver.c:299: error: dereferencing pointer to incomplete type
loadndisdriver.c:302: error: dereferencing pointer to incomplete type
loadndisdriver.c:303: error: dereferencing pointer to incomplete type
loadndisdriver.c:305: error: dereferencing pointer to incomplete type
loadndisdriver.c:311: error: dereferencing pointer to incomplete type
loadndisdriver.c:312: error: dereferencing pointer to incomplete type
loadndisdriver.c:313: warning: implicit declaration of function ‘strcpy’
loadndisdriver.c:313: warning: incompatible implicit declaration of built-in function ‘strcpy’
loadndisdriver.c:314: error: dereferencing pointer to incomplete type
loadndisdriver.c:317: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:318: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:321: error: dereferencing pointer to incomplete type
loadndisdriver.c:282: warning: unused variable ‘statbuf’
loadndisdriver.c:344: error: expected expression before ‘struct’
loadndisdriver.c:346: warning: implicit declaration of function ‘closedir’
loadndisdriver.c:348: warning: implicit declaration of function ‘free’
loadndisdriver.c:355: warning: implicit declaration of function ‘munmap’
loadndisdriver.c:355: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:355: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:357: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:357: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c: In function ‘get_device’:
loadndisdriver.c:367: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:370: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:370: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:373: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:374: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:376: warning: implicit declaration of function ‘snprintf’
loadndisdriver.c:376: warning: incompatible implicit declaration of built-in function ‘snprintf’
loadndisdriver.c:407: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:367: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘load_device’:
loadndisdriver.c:419: error: ‘DIR’ undeclared (first use in this function)
loadndisdriver.c:419: error: ‘dir’ undeclared (first use in this function)
loadndisdriver.c:423: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:423: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:424: warning: incompatible implicit declaration of built-in function ‘memset’
loadndisdriver.c:426: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:427: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:429: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:434: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:435: error: dereferencing pointer to incomplete type
loadndisdriver.c:436: error: dereferencing pointer to incomplete type
loadndisdriver.c:439: error: dereferencing pointer to incomplete type
loadndisdriver.c:447: error: expected expression before ‘struct’
loadndisdriver.c: In function ‘get_ioctl_device’:
loadndisdriver.c:464: error: ‘FILE’ undeclared (first use in this function)
loadndisdriver.c:464: error: ‘proc_misc’ undeclared (first use in this function)
loadndisdriver.c:472: warning: implicit declaration of function ‘strstr’
loadndisdriver.c:472: warning: incompatible implicit declaration of built-in function ‘strstr’
loadndisdriver.c:473: warning: implicit declaration of function ‘strtol’
loadndisdriver.c:473: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:483: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:483: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:488: warning: implicit declaration of function ‘unlink’
loadndisdriver.c:489: warning: implicit declaration of function ‘mknod’
loadndisdriver.c:489: error: ‘S_IFCHR’ undeclared (first use in this function)
loadndisdriver.c:489: error: ‘MISC_MAJOR’ undeclared (first use in this function)
loadndisdriver.c:490: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:495: error: ‘O_RDONLY’ undeclared (first use in this function)
loadndisdriver.c: In function ‘main’:
loadndisdriver.c:511: warning: implicit declaration of function ‘openlog’
loadndisdriver.c:511: error: ‘LOG_PERROR’ undeclared (first use in this function)
loadndisdriver.c:511: error: ‘LOG_CONS’ undeclared (first use in this function)
loadndisdriver.c:511: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:511: error: ‘LOG_DEBUG’ undeclared (first use in this function)
loadndisdriver.c:513: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:515: warning: implicit declaration of function ‘strncmp’
loadndisdriver.c:517: warning: implicit declaration of function ‘printf’
loadndisdriver.c:517: warning: incompatible implicit declaration of built-in function ‘printf’
loadndisdriver.c:527: warning: implicit declaration of function ‘atoi’
loadndisdriver.c:542: warning: implicit declaration of function ‘atof’
loadndisdriver.c:549: warning: implicit declaration of function ‘strcmp’
loadndisdriver.c:556: warning: incompatible implicit declaration of built-in function ‘sscanf’
loadndisdriver.c:590: warning: implicit declaration of function ‘closelog’
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/dexter/ndiswrapper-1.49/utils'
make: *** [install] Error 2
dexter@dexter-laptop:~/ndiswrapper-1.49$ ndiswrapper -v
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found
dexter@dexter-laptop:~/ndiswrapper-1.49$

---

### Post by m.capurso on 2008-01-25
Help needed. I have an AMD PCIMCIA wireless card working under Windows XP.
I am trying to have it working under UBUNTU 7.10  .
I followed all the steps with ndiswrapper and I have it working.
ndiswrapper -v  gives the expected results.
I am able to load the windows xp modules and writing 

ndiswrapper -l 

I  have

NETAM772: driver installed
                 device (1022:2003) present

next I write 

depmod -a

but when I write

modprobe ndiswrapper

the system hangs and I have to switch the computer off manually (after some time).
Any help ?

---

### Post by kevdog on 2008-01-25
sounds like the driver is bad, i would visit the manufacture's website and see if they have different drivers

---

### Post by kevdog on 2008-01-25
buster95

im fairly certain you didn't do this step:
4. sudo aptitude install build-essential linux-headers-`uname -r`

---

### Post by Buster95 on 2008-01-26
> **kevdog said:**
> buster95

im fairly certain you didn't do this step:
4. sudo aptitude install build-essential linux-headers-`uname -r`

Thanks kevdog,
You're probably right. I was using "cut-and-paste" to avoid transcription errors and very likely baffled myself.
Re-tried it with direct entry (and using the latest stable version) and got further. It seems I now have two drivers and am uncertain whether it is necessary to remove one and indeed, how to.
This shows the drivers.

dexter@dexter-laptop:~/driver$ ndiswrapper -l
net8187b : driver installed
        device (0BDA:8187) present (alternate driver: rtl8187)
dexter@dexter-laptop:~/driver$ 

What next?
Thanks

The first driver is the

---

### Post by kevdog on 2008-01-26
Your post got cut off.

Make sure you have the r8187 driver blacklisted in the /etc/modprobe.d/blacklist file.

Can you also post 
lshw -C network only for your networking card?  You wouldn't happen to be on a Toshiba laptop?

---

### Post by m.capurso on 2008-01-26
GREAT. I succeded in using the SITECOM WL-011 V2 with chip
Advanced Micro Devices [AMD] Am 1771 MBW [Alchemy] (rev 04)
It is a PCIMCIA IEEE802.11b card

The Solution is using the Win98/ME  driver.
I used Synaptics to install ndiswrapper 1.45 from the Ubuntu 7.10 repository

Let's test if installed OK:
admin@sassuxp:~$ ndiswrapper -v
utils version: 1.9
driver filename:       /lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.45
vermagic:       2.6.22-14-generic SMP mod_unload 586 

Next, I put  the WIN/98 files in a linux directory from the CDROM containing the drivers

cd ~
mkdir driver
cd driver

I copied all the files and then i entered in root mode

su root
root@sassuxp:/home/admin#  ndiswrapper -i /home/admin/driver/NetAm772.inf

Let's verify

root@sassuxp:/home/admin#  ndiswrapper -l
root@sassuxp:/home/admin#depmod -a
root@sassuxp:/home/admin#modprobe ndismapper

Let's see the result
dmesg

...
[ 1333.468000] ndiswrapper version 1.45 loaded (smp=yes)
[ 1333.500000] ndiswrapper: driver netam772 (Advanced Micro Devices,10/27/2003,2.0.0.4) loaded
[ 1333.500000] PCI: Enabling device 0000:03:00.0 (0000 -> 0002)
[ 1333.500000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[ 1333.500000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[ 1333.500000] ndiswrapper: using IRQ 11
[ 1333.720000] wlan0: ethernet device 00:0c:f6:0c:6c:96 using NDIS driver: netam772, version: 0x2000004, NDIS version: 0x500, vendor: 'Am1772(tm) Wireless LAN Chipset', 1022:2003.5.conf
[ 1333.808000] ndiswrapper: changing interface name from 'wlan0' to 'wlan1'
[ 1334.216000] ndiswrapper (set_encr_mode:673): setting encryption mode to 6 failed (C00000BB)
[ 1334.316000] wlan1: encryption modes supported: WEP; TKIP with WPA
[ 1334.516000] ndiswrapper (wrap_procfs_add_ndis_device:367): wlan1 already registered?
[ 1334.524000] usbcore: registered new interface driver ndiswrapper
[ 1334.616000] ADDRCONF(NETDEV_UP): wlan1: link is not ready

Let's write the configuration  for modprobe

root@sassuxp:/home/admin/driver# ndiswrapper -m
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...


Let's see if seen
root@sassuxp:/home/admin/driver# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   Tx-Power:20 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Let's put ndiswrapper in the modules
echo "ndiswrapper" | sudo tee -a /etc/modules
ndiswrapper


Let's reboot
root@sassuxp:/home/admin/driver#shutdown -r now

After reboot, Let's see if in the list of the hardware
(reboot)
root@sassuxp:/home/admin/driver#lshw
...
 *-generic
          description: Wireless interface
          product: Am 1771 MBW [Alchemy]
          vendor: Advanced Micro Devices [AMD]
          physical id: 0
          bus info: pci@0000:03:00.0
          logical name: wlan1
          version: 04
          serial: 00:0c:f6:0c:6c:96
          width: 32 bits
          clock: 33MHz
          capabilities: bus_master cap_list ethernet physical wireless
          configuration: broadcast=yes driver=ndiswrapper+netam772 driverversion=1.45+Advanced Micro Devices,10/2 latency=64 maxlatency=52 mingnt=4 module=ndiswrapper multicast=yes wireless=IEEE 802.11b

Now,it is seen in the Network Manager

---

### Post by Buster95 on 2008-01-26
> **kevdog said:**
> Your post got cut off.

Make sure you have the r8187 driver blacklisted in the /etc/modprobe.d/blacklist file.

Can you also post 
lshw -C network only for your networking card?  You wouldn't happen to be on a Toshiba laptop?

Thanks for taking the trouble to reply kevdog.
Completing my cut-off post;
The first driver is the one that shows up in "lsusb"  on this damned laptop (which uses an internal usb wireless setup). I'm not sure how to blacklist it. Here's the lsusb display, showing the 8187 driver

dexter@dexter-laptop:~$ lsusb
Bus 005 Device 003: ID 0bda:8187 Realtek Semiconductor Corp. 
Bus 005 Device 002: ID 0402:5602 ALi Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
dexter@dexter-laptop:~$ 

The laptop is a Clevo.
I already had blacklisted the Realtek rtl8187 (and the Ralink driver r8187, just in case).  lshw is only displaying the ethernet connection (see below).
In anticipation of you asking, the wireless card router on this laptop previously worked on XP. The router is also currently working, with regular successful wireless connections to a Powerbook and to another XP laptop.

dexter@dexter-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 7c
       serial: 00:90:f5:57:ba:bb
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.2 ip=192.168.0.5 latency=32 maxlatency=8 mingnt=3 multicast=yes
       resources: ioport:4800-48ff iomemory:cb400400-cb4004ff irq:18
dexter@dexter-laptop:~$ 


I'm not sure what to do next, except for the usual silent scream of frustration.

Thanks

---

### Post by kevdog on 2008-01-26
Ok, there are two possible courses of action for you -- these internal USB devices are tough, so just grin and bear with me for a while.

Lets just see what kernel modules are loaded in your system right now.  To do this 

lsmod

This command lists modules (lsmod) which are currently loaded.  You are hoping to see ndis or ndiswrapper and not anything with a 818x or 8187 or something similar.

If after going through some more struggling, we might have to totally abandon the ndiswrapper approach and go with cuervo's or realtek's drivers for the 8187 usb device.  Lets just keep working for the ndiswrapper solution for now  before we jump ship.

---

### Post by Buster95 on 2008-01-26
> **kevdog said:**
> Ok, there are two possible courses of action for you -- these internal USB devices are tough, so just grin and bear with me for a while.

Lets just see what kernel modules are loaded in your system right now.  To do this 

lsmod

This command lists modules (lsmod) which are currently loaded.  You are hoping to see ndis or ndiswrapper and not anything with a 818x or 8187 or something similar.

If after going through some more struggling, we might have to totally abandon the ndiswrapper approach and go with cuervo's or realtek's drivers for the 8187 usb device.  Lets just keep working for the ndiswrapper solution for now  before we jump ship.

Hello kevdog,
You surprised me with the speed of your reply. Burning the midnight oil?
I didn't edit this down because I didn't want to cut out anything that may assist.
Cheers

dexter@dexter-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
acpi_cpufreq           10056  2 
cpufreq_ondemand        9228  1 
cpufreq_stats           7360  0 
cpufreq_userspace       5408  0 
cpufreq_powersave       2688  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_conservative     8200  0 
dev_acpi               12292  0 
sony_acpi               6284  0 
tc1100_wmi              8068  0 
pcc_acpi               13184  0 
sbs                    15652  0 
i2c_ec                  6016  1 sbs
asus_acpi              17308  0 
ac                      6020  0 
container               5248  0 
video                  16388  0 
dock                   10268  0 
button                  8720  0 
battery                10756  0 
backlight               7040  1 asus_acpi
ipv6                  269088  16 
parport_pc             36388  0 
lp                     12452  0 
parport                36936  3 ppdev,parport_pc,lp
fuse                   46612  0 
joydev                 10816  0 
snd_hda_intel          21912  1 
snd_hda_codec         205056  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
sdhci                  18700  0 
i2c_viapro             10132  0 
mmc_core               26756  1 sdhci
af_packet              23816  2 
serio_raw               7940  0 
pcspkr                  4224  0 
psmouse                38920  0 
i2c_core               22656  2 i2c_ec,i2c_viapro
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
tsdev                   8768  0 
evdev                  11008  4 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sd_mod                 23428  3 
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
sata_via               12548  2 
via_rhine              25608  0 
mii                     6528  1 via_rhine
ehci_hcd               34188  0 
uhci_hcd               25360  0 
ata_generic             9092  0 
via82cxxx              10372  0 [permanent]
usbcore               134280  3 ehci_hcd,uhci_hcd
libata                125720  2 sata_via,ata_generic
scsi_mod              142348  3 sg,sd_mod,libata
generic                 5124  0 [permanent]
thermal                14856  0 
processor              31048  2 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability
dexter@dexter-laptop:~$

---

### Post by kevdog on 2008-01-26
Hmm, by your posted lsmod output I dont see any 818x driver or ndiswrapper kernel module loaded.  I was thinking I was going to see both of them, but none of them are loaded.  Have you tried loading the ndiswrapper module?

sudo modprobe ndiswrapper

Check dmesg to see if any error messages were presented with this command.

---

### Post by Buster95 on 2008-01-26
> **kevdog said:**
> Hmm, by your posted lsmod output I dont see any 818x driver or ndiswrapper kernel module loaded.  I was thinking I was going to see both of them, but none of them are loaded.  Have you tried loading the ndiswrapper module?

sudo modprobe ndiswrapper

Check dmesg to see if any error messages were presented with this command.

dexter@dexter-laptop:~$ sudo modprobe ndiswrapper
Password:
dexter@dexter-laptop:~$ lsmod
Module                  Size  Used by
ndiswrapper           194608  0 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
acpi_cpufreq           10056  2 
cpufreq_ondemand        9228  1 
cpufreq_stats           7360  0 
cpufreq_userspace       5408  0 
cpufreq_powersave       2688  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_conservative     8200  0 
dev_acpi               12292  0 
sony_acpi               6284  0 
tc1100_wmi              8068  0 
pcc_acpi               13184  0 
sbs                    15652  0 
i2c_ec                  6016  1 sbs
asus_acpi              17308  0 
ac                      6020  0 
container               5248  0 
video                  16388  0 
dock                   10268  0 
button                  8720  0 
battery                10756  0 
backlight               7040  1 asus_acpi
ipv6                  269088  16 
parport_pc             36388  0 
lp                     12452  0 
parport                36936  3 ppdev,parport_pc,lp
fuse                   46612  0 
joydev                 10816  0 
snd_hda_intel          21912  1 
snd_hda_codec         205056  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
sdhci                  18700  0 
i2c_viapro             10132  0 
mmc_core               26756  1 sdhci
af_packet              23816  2 
serio_raw               7940  0 
pcspkr                  4224  0 
psmouse                38920  0 
i2c_core               22656  2 i2c_ec,i2c_viapro
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
tsdev                   8768  0 
evdev                  11008  4 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sd_mod                 23428  3 
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
sata_via               12548  2 
via_rhine              25608  0 
mii                     6528  1 via_rhine
ehci_hcd               34188  0 
uhci_hcd               25360  0 
ata_generic             9092  0 
via82cxxx              10372  0 [permanent]
usbcore               134280  4 ndiswrapper,ehci_hcd,uhci_hcd
libata                125720  2 sata_via,ata_generic
scsi_mod              142348  3 sg,sd_mod,libata
generic                 5124  0 [permanent]
thermal                14856  0 
processor              31048  2 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability
dexter@dexter-laptop:~$ 

dsmeg is too long to bore you with. I have extracted what I think are the "meaty bits"

[   53.865225] eth0: no IPv6 routers present
[ 1719.609819] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
[ 1719.925703] usb 5-7: reset high speed USB device using ehci_hcd and address 3
[ 1720.121318] ndiswrapper: driver net8187b (Realtek Semiconductor Corp.,07/18/2007,5.1097.0718.2007) loaded
[ 1720.124116] ndiswrapper (miniport_init:275): couldn't initialize device: C0010006
[ 1720.124130] ndiswrapper (pnp_start_device:426): Windows driver couldn't initialize the device (C0000001)
[ 1720.124401] unregister_netdevice: device eth%d/c24ee000 never was registered
[ 1720.124501] ndiswrapper (miniport_halt:339): device c24ee400 is not initialized - not halting
[ 1720.124617] ndiswrapper: device eth%d removed
[ 1720.124723] ndiswrapper: probe of 5-7:1.0 failed with error -22
[ 1720.124820] usbcore: registered new interface driver ndiswrapper
dexter@dexter-laptop:~$ 

Some observations:
Ndiswrapper V 1.38 is shown. I thought I loaded V 1.51
I used W98 driver
Cheers

---

### Post by kevdog on 2008-01-26
could you try with a newer ndis version perhaps?

---

### Post by Buster95 on 2008-01-26
> **kevdog said:**
> could you try with a newer ndis version perhaps?

I have purged ndiswrapper twice (following your uninstall instructions) and re-loaded v 1.51 twice. However, when I run ndiswrapper -v, it displays v 1.38.
Cheers

---

### Post by kevdog on 2008-01-26
Uninstall ndiswrapper from the synaptic menu repository!

or 
sudo aptitude purge ndiswrapper

---

### Post by Buster95 on 2008-01-26
> **kevdog said:**
> Uninstall ndiswrapper from the synaptic menu repository!

or 
sudo aptitude purge ndiswrapper

Un-installed ndiswrapper via synaptic AND purged as above. Still can't shake it loose

dexter@dexter-laptop:~$ cd ndiswrapper
dexter@dexter-laptop:~/ndiswrapper$ cd ndiswrapper-1.51
dexter@dexter-laptop:~/ndiswrapper/ndiswrapper-1.51$ ndiswrapper -v
module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
filename:       /lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.38
vermagic:       2.6.20-16-generic SMP mod_unload 586 

You may need to upgrade driver and/or utils to latest versions available at
[http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)
dexter@dexter-laptop:~/ndiswrapper/ndiswrapper-1.51$

---

### Post by kevdog on 2008-01-26
Unistall completely within the ndiswrapper source directory with:

sudo updatedb
locate ndiswrapper

remove all the files listed

locate loadndiswrapper

remove all the files listed


You need to remove with the 

sudo rm .....

Then 
sudo make clean

and then recompile

---

### Post by Buster95 on 2008-01-26
> **kevdog said:**
> Unistall completely within the ndiswrapper source directory with:

sudo updatedb
locate ndiswrapper

remove all the files listed

locate loadndiswrapper

remove all the files listed


You need to remove with the 

sudo rm .....

Then 
sudo make clean

and then recompile

The only references to v 1.38 are as follows:
dexter@dexter-laptop:~/ndiswrapper$ locate ndiswrapper
/var/cache/apt/archives/ndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb
/var/cache/apt/archives/ndiswrapper-source_1.38-1ubuntu1_all.deb

The 50 or so other files seemed to be referring to v 1.51 only
Should I remove these two archive files or anything with ndiswrapper attached to it?
Cheers
/ho

---

### Post by kevdog on 2008-01-27
remove everything.

---

### Post by Buster95 on 2008-01-27
> **kevdog said:**
> remove everything.

Removed everything and reloaded the latest ndiswrapper.  Command "ndiswrapper -v" now shows:
dexter@dexter-laptop:~/ndiswrapper/ndiswrapper-1.51$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.51
vermagic:       2.6.20-16-generic SMP mod_unload 586 

So far so good

Reloaded the W98 driver and checked it:
dexter@dexter-laptop:~/driver$ sudo ndiswrapper -i net8187b.inf
installing net8187b ...
dexter@dexter-laptop:~/driver$ ndiswrapper -l
net8187b : driver installed
        device (0BDA:8187) present (alternate driver: rtl8187)

I'm now back to the 2 driver scenario I had before. The first is the one that shows up in the "lsusb" command; presumably the second is the "ndiswrapped" driver.

What next?

Thanks

I have already blacklisted rtl8187 and r8187

---

### Post by kevdog on 2008-01-27
Ok, the two steps with ndiswrapper are basically

#1 - loading the windows driver inside ndiswrapper and then verifying the wrap (that is what you presented above (ndiswrapper -i and ndiswrapper -v))

#2- Inserting the ndiswrapper kernel module inside the kernel and verifying the insertion (you do this with modprobe and check with dmesg)

So proceed to load the kernel module:
sudo modprobe ndiswrapper

Then check with 
dmesg

---

### Post by Buster95 on 2008-01-27
> **kevdog said:**
> Ok, the two steps with ndiswrapper are basically

#1 - loading the windows driver inside ndiswrapper and then verifying the wrap (that is what you presented above (ndiswrapper -i and ndiswrapper -v))

#2- Inserting the ndiswrapper kernel module inside the kernel and verifying the insertion (you do this with modprobe and check with dmesg)

So proceed to load the kernel module:
sudo modprobe ndiswrapper

Then check with 
dmesg

The highlighted extract from "dmesg" doesn't look promising.

[  200.860041] ndiswrapper version 1.51 loaded (smp=yes, preempt=no)
[  201.192172] usb 5-7: reset high speed USB device using ehci_hcd and address 3
[  201.374253] ndiswrapper: driver net8187b (Realtek Semiconductor Corp.,07/18/2007,5.1097.0718.2007) loaded
[COLOR="Red"][  201.377312] ndiswrapper (mp_init:216): couldn't initialize device: C0010006[/COLOR]
[  201.377325] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
[  201.377407] ndiswrapper (mp_halt:259): device d125ac00 is not initialized - not halting
[  201.377423] ndiswrapper: device eth%d removed
[  201.377528] ndiswrapper: probe of 5-7:1.0 failed with error -22
[  201.377587] usbcore: registered new interface driver ndiswrapper
dexter@dexter-laptop:~/ndiswrapper$

---

### Post by kevdog on 2008-01-27
Try with the xp driver.  Just give that a chance.  I doubt it will work, but would like to be thorough before we skip to another method.

---

### Post by Buster95 on 2008-01-28
> **kevdog said:**
> Try with the xp driver.  Just give that a chance.  I doubt it will work, but would like to be thorough before we skip to another method.

Thanks kevdog,
What's the method for removing the ndiswrapped W98 driver?
Cheers

---

### Post by kevdog on 2008-01-28
Again, just remember the basic premise of ndiswrapper and you will be golden.

#1. Unload the ndiswrapper kernel module
#2. Unload the windows driver inside ndiswrapper

Do the reverse for installation.

So to accomplish these goals:
#1 sudo modprobe -r ndiswrapper 
#2. sudo ndiswrapper -r NAME_OF_INF_FILE without the .inf extension   
                         or
       sudo rm -R /etc/ndiswrapper/*

I personally think option b on #2 is the easiest!

For the reverse its:
sudo ndiswrapper -i NAME.inf
sudo modprobe ndiswrapper

I left out the verification steps for the installation, but I think you get the idea!

---

### Post by Buster95 on 2008-01-29
> **kevdog said:**
> Again, just remember the basic premise of ndiswrapper and you will be golden.

#1. Unload the ndiswrapper kernel module
#2. Unload the windows driver inside ndiswrapper

Do the reverse for installation.

So to accomplish these goals:
#1 sudo modprobe -r ndiswrapper 
#2. sudo ndiswrapper -r NAME_OF_INF_FILE without the .inf extension   
                         or
       sudo rm -R /etc/ndiswrapper/*

I personally think option b on #2 is the easiest!

For the reverse its:
sudo ndiswrapper -i NAME.inf
sudo modprobe ndiswrapper

I left out the verification steps for the installation, but I think you get the idea!

1 Unloaded the ndiswrapper kernel module
2 Unloaded the W98 driver
3 Confirmed that ndiswrapper was still there.

[COLOR="Blue"]dexter@dexter-laptop:~/driver$ sudo ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.51
vermagic:       2.6.20-16-generic SMP mod_unload 586 
dexter@dexter-laptop:~/driver$[/COLOR] 

4 Loaded the WXP driver into ndiswrapper
5 Confirmed the driver. As before, 2 drivers show up,

[COLOR="Blue"]dexter@dexter-laptop:~/driver$ ndiswrapper -l
net8187b : driver installed
        device (0BDA:8187) present (alternate driver: rtl8187)
dexter@dexter-laptop:~/driver$ [/COLOR]

6 Review "dmesg" for errors. Same bad news as before.

[COLOR="Blue"][ 1043.513785] ndiswrapper version 1.51 loaded (smp=yes, preempt=no)
[ 1043.771148] usb 5-7: reset high speed USB device using ehci_hcd and address 3
[ 1043.907984] ndiswrapper: driver net8187b (Realtek Semiconductor Corp.,07/18/2007,5.1097.0718.2007) loaded[/COLOR]
[[COLOR="Red"] 1043.915307] ndiswrapper (mp_init:216): couldn't initialize device: C0010006
[ 1043.915331] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
[ 1043.915854] ndiswrapper (mp_halt:259): device cf4b9400 is not initialized - not halting
[ 1043.916087] ndiswrapper: device eth%d removed
[ 1043.916253] ndiswrapper: probe of 5-7:1.0 failed with error -22[/COLOR]
[[COLOR="Blue"] 1043.916447] usbcore: registered new interface driver ndiswrapper
dexter@dexter-laptop:~/driver$ [/COLOR]

Any suggestions?

---

### Post by kevdog on 2008-01-30
Wow, that is bad news -- I think obviously we haven't found the correct driver for your card yet.  This is more a manufacture problem since they never distributed linux drivers for your card than linux.  Remind me just real quick -- this is an internal USB device using the realtk8187 chipset correct??

One other idea, 

Remove ndiswrapper for right now.  Do you have a 8187 driver (native) contained somewhere on your system?  Do a
sudo updatedb
locate 8187

If nothing works, try
locate 818x

---

### Post by Buster95 on 2008-01-30
> **kevdog said:**
> Wow, that is bad news -- I think obviously we haven't found the correct driver for your card yet.  This is more a manufacture problem since they never distributed linux drivers for your card than linux.  Remind me just real quick -- this is an internal USB device using the realtk8187 chipset correct??

One other idea, 

Remove ndiswrapper for right now.  Do you have a 8187 driver (native) contained somewhere on your system?  Do a
sudo updatedb
locate 8187

If nothing works, try
locate 818x

Hello kevdog,
yes, this laptop uses an internal USB wireless device, using the Realtek rtl8187 chipset. It has previously worked OK with Windows XP and Ubuntu 6.10 with a dual boot arrangement.

I removed the dual boot and the W-XP when I upgraded to 7.04. When the wireless connection didn't work on 7.04, I tried 7.10 (first by downloaded upgrade and then by Canonical disk), but that also broke the ethernet, so I reverted to 7.04 for this laptop, just to keep the ethernet working.

I have the 8187B drivers for W-Vista, W-XP, W2000, W-Me and W-98 which I downloaded from a site that I was directed to by the Wireless Installation Documentation. These are shown below.

[COLOR="Blue"]dexter@dexter-laptop:~$ sudo updatedb 
Password: 
dexter@dexter-laptop:~$ locate 8187 
/home/dexter/driver/rtl8187B.sys 
/home/dexter/driver/net8187b.inf 
/home/dexter/driver/net8187b.cat 
/home/dexter/driver/RTL8187B 
/home/dexter/driver/RTL8187B/Win2000 
/home/dexter/driver/RTL8187B/Win2000/rtl8187B.sys 
/home/dexter/driver/RTL8187B/Win2000/net8187b.inf 
/home/dexter/driver/RTL8187B/Win2000/net8187b.cat 
/home/dexter/driver/RTL8187B/Win98 
/home/dexter/driver/RTL8187B/Win98/rtl8187B.sys 
/home/dexter/driver/RTL8187B/Win98/net8187b.inf 
/home/dexter/driver/RTL8187B/X64 
/home/dexter/driver/RTL8187B/X64/rtl8187B.sys 
/home/dexter/driver/RTL8187B/X64/net8187b.inf 
/home/dexter/driver/RTL8187B/X64/net8187b.cat 
/home/dexter/driver/RTL8187B/WinME 
/home/dexter/driver/RTL8187B/WinME/rtl8187B.sys 
/home/dexter/driver/RTL8187B/WinME/net8187b.inf 
/home/dexter/driver/RTL8187B/VistaX86 
/home/dexter/driver/RTL8187B/VistaX86/rtl8187B.sys 
/home/dexter/driver/RTL8187B/VistaX86/net8187b.inf 
/home/dexter/driver/RTL8187B/VistaX86/net8187b.cat 
/home/dexter/driver/RTL8187B/WinXP 
/home/dexter/driver/RTL8187B/WinXP/rtl8187B.sys 
/home/dexter/driver/RTL8187B/WinXP/net8187b.inf 
/home/dexter/driver/RTL8187B/WinXP/net8187b.cat 
/home/dexter/driver/RTL8187B/VistaX64 
/home/dexter/driver/RTL8187B/VistaX64/rtl8187B.sys 
/home/dexter/driver/RTL8187B/VistaX64/net8187b.inf 
/home/dexter/driver/RTL8187B/VistaX64/net8187b.cat 
/lib/modules/2.6.20-15-generic/kernel/ubuntu/wireless/rtl8187 
/lib/modules/2.6.20-15-generic/kernel/ubuntu/wireless/rtl8187/rtl8187.ko 
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rtl8187 
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rtl8187/rtl8187.ko 
/usr/src/linux-headers-2.6.20-16-generic/include/config/rtl8187.h 
/usr/src/linux-headers-2.6.20-15-generic/include/config/rtl8187.h 
/usr/src/linux-headers-2.6.20-15/ubuntu/wireless/rtl8187 
/usr/src/linux-headers-2.6.20-15/ubuntu/wireless/rtl8187/Makefile 
/usr/src/linux-headers-2.6.20-15/ubuntu/wireless/rtl8187/Kconfig 
/usr/src/linux-headers-2.6.20-16/ubuntu/wireless/rtl8187 
/usr/src/linux-headers-2.6.20-16/ubuntu/wireless/rtl8187/Makefile 
/usr/src/linux-headers-2.6.20-16/ubuntu/wireless/rtl8187/Kconfig 
/etc/ndiswrapper/net8187b 
/etc/ndiswrapper/net8187b/net8187b.inf 
/etc/ndiswrapper/net8187b/0BDA:8187.F.conf 
/etc/ndiswrapper/net8187b/rtl8187b.sys 
/etc/ndiswrapper/net8187b/0BDA:8189.F.conf 
dexter@dexter-laptop:~$[/COLOR]

I am now removing ndiswrapper from the system.
I'll have another look at the Realtek website to see if they can offer an alternate Linux driver. I think I abandoned this approach a while ago, but it's worth having another go.

Any suggestions?

---

### Post by phidia on 2008-01-30
Hey kevdog excellant guide!! 
I am having some problems trying to get my MAC address to to be permanently saved so that I don't have to enter this:  
sudo ifconfig wlan0 hw ether 00:1E:4C:4D:DC:F2
sudo ifconfig wlan0 up

with every boot.

I am using 64bit 7.10 with the atheros ar5007eg chipset.
I installed an older version of ndiswrapper per instructions by afterstep13 at [this]("http://ubuntuforums.org/showthread.php?p=4238142#post4238142") thread. 
Here's my network parameters: lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth22
       version: a2
       serial: 00:00:6c:11:f8:99
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.60 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network
       description: Wireless interface
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:1e:4c:4d:dc:f2
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.44+,06/21/2007,5.3.0.56 ip=192.168.1.3 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g


I thought this thread had the answer when you said that /etc/iftab was where the MAC address is saved, but I don't have a iftab file and doing locate iftab seems to show that  iftab has been replaced some how by udev??
If anyone can shed any light on this I would very much appreciate it.

Edit: Ok i found where that 'lives" now-which is /etc/udev/rules.d/70-persistent-net.rules
Looking there i found the entry for my card below


# PCI device 0x168c:0x001c (ndiswrapper)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:1e:4c:4d:dc:f2", ATTRS{type}=="1", NAME="wlan0"

# PCI device 0x10de:0x054c (forcedeth)

But, the interface/network doesn't come up unless I enter those commands I listed  previously. Why is that?

---

### Post by kevdog on 2008-01-31
Ive seen a lot of threads about changing MAC addresses but unfortunately I havent been able tofigure out what works consistently.  I saw a thread about a month ago with udev, MAC address changer, but I can't seem to find the link.

---

### Post by emcus on 2008-01-31
I followed the instructions and I still get the old driver when I enter "lshw -C Network":

configuration: broadcast=yes **driver=acx_pc**i latency=32 module=acx multicast=yes wireless=IEEE 802.11b+/g+

It appears as my wg311v2 driver is installed according to this, right?

marcus@marcus-ubuntu:~$ ndiswrapper -l
wg311v2 : driver installed
        device (104C:9066) present (alternate driver: acx)

Where did I go wrong?

---

### Post by kevdog on 2008-01-31
You didnt do two things,

First you did not unload the acx_pci driver.  You can do this by doing the following:
sudo modprobe -r acx_pci

Then load the ndiswrapper module
sudo modprobe ndiswrapper

To prevent the acx_pci module from loading at boot, please add the acx_pci driver to the /etc/modprobe.d/blacklist file.

---

### Post by emcus on 2008-02-02
Thanks! That did the trick with the driver. It still didn't solve my original problem though. I still get "No DHCPOFFERS" when I run "DHCLIENT WLAN0". I don't get it, because the network icon tells me I'm connected to my wireless network with perfect signal strength. What could be wrong?

---

### Post by chew5011 on 2008-02-02
Morning man......
I need some help here....
can you please guide me ???

this is what i get when i key in "lshw -C network" command
it its "network UNCLAIMED" instead of "network".
How do i CLAIM that UNCLAIMED network???
i do follow every step of your guide...
but somehow i can't get the desired result as yours...

```
[root@localhost ~]# lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0

```

can you please guide me through this???

---

### Post by kevdog on 2008-02-02
emcus

can you post iwlist scan and ifconfig

chew5011
Although I dont see why this guide would not work with intel chipsets, Ive never tried it with any intel chipset.  I would search the forums to see what other people have been using for their driver for the ipw3945 chipset.

---

### Post by chew5011 on 2008-02-02
output of iwlist wlan0 scan
```
iwlist wlan0 scan
wlan0     Interface doesn't support scanning.


Message from syslogd@localhost at Feb  3 19:03:57 ...
 kernel: general protection fault: 0000 [1] SMP 

```

```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1C:23:A3:F0:2E  
          inet6 addr: fe80::21c:23ff:fea3:f02e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2978 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4942638 (4.7 MiB)  TX bytes:327035 (319.3 KiB)
          Interrupt:17 

eth0:0    Link encap:Ethernet  HWaddr 00:1C:23:A3:F0:2E  
          inet addr:192.168.1.125  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9294 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9294 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2836460 (2.7 MiB)  TX bytes:2836460 (2.7 MiB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:192.168.250.1  Bcast:192.168.250.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:192.168.137.1  Bcast:192.168.137.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```
Actually i did search in some forums about my problem.....
i did it for a very long time but still can't get over it...
so i post  my problem here.....

besides, i will be losing my wireless connection until the following following tuesday cause i am back to my hometown now to celebrate chinese new year.....
sorry if i caused inconvinent.....
can you help me make the wireless connection claimed first???

THank you ya

---

### Post by Buster95 on 2008-02-04
> **Buster95 said:**
> Hello kevdog,
yes, this laptop uses an internal USB wireless device, using the Realtek rtl8187 chipset. It has previously worked OK with Windows XP and Ubuntu 6.10 with a dual boot arrangement.

I removed the dual boot and the W-XP when I upgraded to 7.04. When the wireless connection didn't work on 7.04, I tried 7.10 (first by downloaded upgrade and then by Canonical disk), but that also broke the ethernet, so I reverted to 7.04 for this laptop, just to keep the ethernet working.

I have the 8187B drivers for W-Vista, W-XP, W2000, W-Me and W-98 which I downloaded from a site that I was directed to by the Wireless Installation Documentation. These are shown below.

[COLOR="Blue"]dexter@dexter-laptop:~$ sudo updatedb 
Password: 
dexter@dexter-laptop:~$ locate 8187 
/home/dexter/driver/rtl8187B.sys 
/home/dexter/driver/net8187b.inf 
/home/dexter/driver/net8187b.cat 
/home/dexter/driver/RTL8187B 
/home/dexter/driver/RTL8187B/Win2000 
/home/dexter/driver/RTL8187B/Win2000/rtl8187B.sys 
/home/dexter/driver/RTL8187B/Win2000/net8187b.inf 
/home/dexter/driver/RTL8187B/Win2000/net8187b.cat 
/home/dexter/driver/RTL8187B/Win98 
/home/dexter/driver/RTL8187B/Win98/rtl8187B.sys 
/home/dexter/driver/RTL8187B/Win98/net8187b.inf 
/home/dexter/driver/RTL8187B/X64 
/home/dexter/driver/RTL8187B/X64/rtl8187B.sys 
/home/dexter/driver/RTL8187B/X64/net8187b.inf 
/home/dexter/driver/RTL8187B/X64/net8187b.cat 
/home/dexter/driver/RTL8187B/WinME 
/home/dexter/driver/RTL8187B/WinME/rtl8187B.sys 
/home/dexter/driver/RTL8187B/WinME/net8187b.inf 
/home/dexter/driver/RTL8187B/VistaX86 
/home/dexter/driver/RTL8187B/VistaX86/rtl8187B.sys 
/home/dexter/driver/RTL8187B/VistaX86/net8187b.inf 
/home/dexter/driver/RTL8187B/VistaX86/net8187b.cat 
/home/dexter/driver/RTL8187B/WinXP 
/home/dexter/driver/RTL8187B/WinXP/rtl8187B.sys 
/home/dexter/driver/RTL8187B/WinXP/net8187b.inf 
/home/dexter/driver/RTL8187B/WinXP/net8187b.cat 
/home/dexter/driver/RTL8187B/VistaX64 
/home/dexter/driver/RTL8187B/VistaX64/rtl8187B.sys 
/home/dexter/driver/RTL8187B/VistaX64/net8187b.inf 
/home/dexter/driver/RTL8187B/VistaX64/net8187b.cat 
/lib/modules/2.6.20-15-generic/kernel/ubuntu/wireless/rtl8187 
/lib/modules/2.6.20-15-generic/kernel/ubuntu/wireless/rtl8187/rtl8187.ko 
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rtl8187 
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rtl8187/rtl8187.ko 
/usr/src/linux-headers-2.6.20-16-generic/include/config/rtl8187.h 
/usr/src/linux-headers-2.6.20-15-generic/include/config/rtl8187.h 
/usr/src/linux-headers-2.6.20-15/ubuntu/wireless/rtl8187 
/usr/src/linux-headers-2.6.20-15/ubuntu/wireless/rtl8187/Makefile 
/usr/src/linux-headers-2.6.20-15/ubuntu/wireless/rtl8187/Kconfig 
/usr/src/linux-headers-2.6.20-16/ubuntu/wireless/rtl8187 
/usr/src/linux-headers-2.6.20-16/ubuntu/wireless/rtl8187/Makefile 
/usr/src/linux-headers-2.6.20-16/ubuntu/wireless/rtl8187/Kconfig 
/etc/ndiswrapper/net8187b 
/etc/ndiswrapper/net8187b/net8187b.inf 
/etc/ndiswrapper/net8187b/0BDA:8187.F.conf 
/etc/ndiswrapper/net8187b/rtl8187b.sys 
/etc/ndiswrapper/net8187b/0BDA:8189.F.conf 
dexter@dexter-laptop:~$[/COLOR]

I am now removing ndiswrapper from the system.
I'll have another look at the Realtek website to see if they can offer an alternate Linux driver. I think I abandoned this approach a while ago, but it's worth having another go.

Any suggestions?

kevdog,
I had just about given up on ever getting this damned rtl8187 usb wireless to work on my laptop, but there's been a curious development.

This morning, Download Manager offered what appeared to be a routine kernel update. I downloaded it and did the recommended restart.
After restart, I noticed that it was displaying a 5 bar read of my wireless router (for the first time EVER).
With barely concealed excitement, I tried to connect to Google but, no cigar -  it couldn't connect.

Using a different computer, I accessed the router and disabled all wireless security and tried again. BINGO, it hauled up Google. I then tried to access other sites but couldn't complete a connection. I then tried Google again but couldn't connect.
I restarted the laptop, got the bars again and tried to connect manually. I got a message that I was required to create a default keyring (whatever that is), which I did.

Still no connection.

Thought I'd look a little closer. On a terminal, the command "lshw -C network still did not describe an associated driver for wlan0. And yet, the 5 bar icon is still there. When I hover the mouse over the icon, it says "wireless network connection to NETGEAR 80%"
I thought that without an associated driver, nothing would happen.

Can you help me understand what;s going on here?

---

### Post by kevdog on 2008-02-04
lshw -C network only lists pci devices and not usb, so no surprise here.  You can try lsusb -v but its definitely not as informative.

If you want to see signal strength on the command line try
iwlist scan

ifconfig will tell you if you are connected as wlan0 or another name (they are all just placeholders anyway).
  
lsmod should list the driver that is being used.  lsmod lists all the loaded kernel modules, so somewhere in the output should be listed your wireless driver kernel module.

Again you might want to try updating to Hardy's developing kernel.  Instructions are in a post in the tutorials and tips section.

---

### Post by emcus on 2008-02-05
> **kevdog said:**
> emcus

can you post iwlist scan and ifconfig

chew5011
Although I dont see why this guide would not work with intel chipsets, Ive never tried it with any intel chipset.  I would search the forums to see what other people have been using for their driver for the ipw3945 chipset.

I have posted the iwlist scan and ifconfig in [this post]("http://ubuntuforums.org/showthread.php?p=4204846#post4204846"). Thankful for replies!

---

### Post by chew5011 on 2008-02-05
Morning kevdog,
do you have any idea on why my wlan0 remained unclaimed (not listed in ifconfig and iwconfig) although i installed my driver and ndiswrapper? 
it is visible in "lshw -C network"....
:wink::-P:mrgreen:

---

### Post by kevdog on 2008-02-05
remove and reload the kernel module 

sudo modprobe -r ndiswrapper 
sudo modprobe ndiswrapper

Then check dmesg, it will probably give you an error and hint as to what the problem is.

---

### Post by Buster95 on 2008-02-05
> **kevdog said:**
> lshw -C network only lists pci devices and not usb, so no surprise here.  You can try lsusb -v but its definitely not as informative.

If you want to see signal strength on the command line try
iwlist scan

ifconfig will tell you if you are connected as wlan0 or another name (they are all just placeholders anyway).
  
lsmod should list the driver that is being used.  lsmod lists all the loaded kernel modules, so somewhere in the output should be listed your wireless driver kernel module.

Again you might want to try updating to Hardy's developing kernel.  Instructions are in a post in the tutorials and tips section.

Thanks kevdog,
I'll have a look at the Hardy kernel, but am not hopeful. Had to downgrade from Gutsy to Feisty just to get the ethernet to work on this laptop. I haven't had wireless working on it since 6.10.

Cheers

---

### Post by skuz on 2008-02-06
The business! Thanks kevdog.

Your how to and some assistance blacklisting the acx driver...[http://ubuntuguide.org/wiki/Ubuntu:Edgy/Hardware#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29](http://ubuntuguide.org/wiki/Ubuntu:Edgy/Hardware#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29) got my TNET1130 driver installed.

---

### Post by slats on 2008-02-06
everytime i get to the step where i have to make
right before make install i get this
```
slats@Slat-Machine:~/Desktop/ndiswrapper-1.48$ make
make -C driver
make[1]: Entering directory `/home/slats/Desktop/ndiswrapper-1.48/driver'
make -C /usr/src/linux-headers-2.6.22-14-generic SUBDIRS=/home/slats/Desktop/ndiswrapper-1.48/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  LD      /home/slats/Desktop/ndiswrapper-1.48/driver/built-in.o
  CC [M]  /home/slats/Desktop/ndiswrapper-1.48/driver/crt.o
  CC [M]  /home/slats/Desktop/ndiswrapper-1.48/driver/hal.o
  CC [M]  /home/slats/Desktop/ndiswrapper-1.48/driver/iw_ndis.o
  CC [M]  /home/slats/Desktop/ndiswrapper-1.48/driver/loader.o
  CC [M]  /home/slats/Desktop/ndiswrapper-1.48/driver/ndis.o
  CC [M]  /home/slats/Desktop/ndiswrapper-1.48/driver/ntoskernel.o
  CC [M]  /home/slats/Desktop/ndiswrapper-1.48/driver/ntoskernel_io.o
  CC [M]  /home/slats/Desktop/ndiswrapper-1.48/driver/pe_linker.o
  CC [M]  /home/slats/Desktop/ndiswrapper-1.48/driver/pnp.o
  CC [M]  /home/slats/Desktop/ndiswrapper-1.48/driver/proc.o
  CC [M]  /home/slats/Desktop/ndiswrapper-1.48/driver/rtl.o
  CC [M]  /home/slats/Desktop/ndiswrapper-1.48/driver/wrapmem.o
  CC [M]  /home/slats/Desktop/ndiswrapper-1.48/driver/wrapndis.o
  CC [M]  /home/slats/Desktop/ndiswrapper-1.48/driver/wrapper.o
  CC [M]  /home/slats/Desktop/ndiswrapper-1.48/driver/usb.o
  CC [M]  /home/slats/Desktop/ndiswrapper-1.48/driver/divdi3.o
  LD [M]  /home/slats/Desktop/ndiswrapper-1.48/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/slats/Desktop/ndiswrapper-1.48/driver/ndiswrapper.mod.o
  LD [M]  /home/slats/Desktop/ndiswrapper-1.48/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: Leaving directory `/home/slats/Desktop/ndiswrapper-1.48/driver'
make -C utils
make[1]: Entering directory `/home/slats/Desktop/ndiswrapper-1.48/utils'
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
loadndisdriver.c:15:20: error: stdlib.h: No such file or directory
loadndisdriver.c:16:19: error: stdio.h: No such file or directory
loadndisdriver.c:17:19: error: errno.h: No such file or directory
loadndisdriver.c:18:20: error: string.h: No such file or directory
loadndisdriver.c:19:20: error: libgen.h: No such file or directory
loadndisdriver.c:21:22: error: sys/mman.h: No such file or directory
loadndisdriver.c:23:23: error: sys/types.h: No such file or directory
loadndisdriver.c:24:23: error: sys/ioctl.h: No such file or directory
loadndisdriver.c:25:22: error: sys/stat.h: No such file or directory
loadndisdriver.c:26:20: error: unistd.h: No such file or directory
loadndisdriver.c:27:19: error: fcntl.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.3/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.3/include/limits.h:11,
                 from loadndisdriver.c:28:
/usr/lib/gcc/i486-linux-gnu/4.1.3/include/limits.h:122:61: error: limits.h: No such file or directory
loadndisdriver.c:29:19: error: ctype.h: No such file or directory
loadndisdriver.c:30:20: error: dirent.h: No such file or directory
loadndisdriver.c:31:20: error: syslog.h: No such file or directory
loadndisdriver.c:34:25: error: linux/major.h: No such file or directory
loadndisdriver.c:35:25: error: linux/ioctl.h: No such file or directory
In file included from loadndisdriver.c:37:
../driver/loader.h:24: error: expected specifier-qualifier-list before ‘size_t’
loadndisdriver.c: In function ‘load_file’:
loadndisdriver.c:67: error: ‘size_t’ undeclared (first use in this function)
loadndisdriver.c:67: error: (Each undeclared identifier is reported only once
loadndisdriver.c:67: error: for each function it appears in.)
loadndisdriver.c:67: error: expected ‘;’ before ‘size’
loadndisdriver.c:68: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:69: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:71: warning: implicit declaration of function ‘basename’
loadndisdriver.c:71: warning: initialization makes pointer from integer without a cast
loadndisdriver.c:73: warning: implicit declaration of function ‘open’
loadndisdriver.c:73: error: ‘O_RDONLY’ undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function ‘syslog’
loadndisdriver.c:75: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:75: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function ‘strerror’
loadndisdriver.c:75: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:76: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:79: warning: implicit declaration of function ‘fstat’
loadndisdriver.c:81: warning: implicit declaration of function ‘close’
loadndisdriver.c:84: error: ‘size’ undeclared (first use in this function)
loadndisdriver.c:86: warning: implicit declaration of function ‘mmap’
loadndisdriver.c:86: error: ‘PROT_READ’ undeclared (first use in this function)
loadndisdriver.c:86: error: ‘MAP_PRIVATE’ undeclared (first use in this function)
loadndisdriver.c:86: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:87: error: ‘MAP_FAILED’ undeclared (first use in this function)
loadndisdriver.c:93: warning: implicit declaration of function ‘strncpy’
loadndisdriver.c:93: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:95: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:96: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:69: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘parse_setting_line’:
loadndisdriver.c:109: warning: implicit declaration of function ‘isspace’
loadndisdriver.c:115: warning: implicit declaration of function ‘strchr’
loadndisdriver.c:115: warning: incompatible implicit declaration of built-in function ‘strchr’
loadndisdriver.c:115: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:117: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:117: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:118: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:138: warning: implicit declaration of function ‘strlen’
loadndisdriver.c:138: warning: incompatible implicit declaration of built-in function ‘strlen’
loadndisdriver.c: In function ‘read_conf_file’:
loadndisdriver.c:150: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:151: error: ‘FILE’ undeclared (first use in this function)
loadndisdriver.c:151: error: ‘config’ undeclared (first use in this function)
loadndisdriver.c:157: warning: implicit declaration of function ‘lstat’
loadndisdriver.c:158: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:158: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:158: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:160: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:163: warning: implicit declaration of function ‘sscanf’
loadndisdriver.c:163: warning: incompatible implicit declaration of built-in function ‘sscanf’
loadndisdriver.c:178: warning: implicit declaration of function ‘fopen’
loadndisdriver.c:178: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:182: warning: implicit declaration of function ‘fgets’
loadndisdriver.c:194: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:205: warning: implicit declaration of function ‘fclose’
loadndisdriver.c:150: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘load_bin_file’:
loadndisdriver.c:217: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:217: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:219: warning: implicit declaration of function ‘tolower’
loadndisdriver.c:221: warning: implicit declaration of function ‘chdir’
loadndisdriver.c:222: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:224: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:230: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:232: warning: implicit declaration of function ‘ioctl’
loadndisdriver.c:232: warning: implicit declaration of function ‘_IOW’
loadndisdriver.c:232: error: expected expression before ‘struct’
loadndisdriver.c: In function ‘load_driver’:
loadndisdriver.c:249: error: ‘DIR’ undeclared (first use in this function)
loadndisdriver.c:249: error: ‘driver_dir’ undeclared (first use in this function)
loadndisdriver.c:251: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:255: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:255: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:257: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:259: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:261: warning: implicit declaration of function ‘opendir’
loadndisdriver.c:267: warning: implicit declaration of function ‘malloc’
loadndisdriver.c:267: warning: incompatible implicit declaration of built-in function ‘malloc’
loadndisdriver.c:271: warning: implicit declaration of function ‘memset’
loadndisdriver.c:271: warning: incompatible implicit declaration of built-in function ‘memset’
loadndisdriver.c:272: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:280: warning: implicit declaration of function ‘readdir’
loadndisdriver.c:280: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:282: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:284: error: dereferencing pointer to incomplete type
loadndisdriver.c:287: warning: implicit declaration of function ‘stat’
loadndisdriver.c:287: error: dereferencing pointer to incomplete type
loadndisdriver.c:288: warning: implicit declaration of function ‘S_ISREG’
loadndisdriver.c:289: error: dereferencing pointer to incomplete type
loadndisdriver.c:294: warning: incompatible implicit declaration of built-in function ‘strlen’
loadndisdriver.c:294: error: dereferencing pointer to incomplete type
loadndisdriver.c:296: warning: implicit declaration of function ‘strcasecmp’
loadndisdriver.c:296: error: dereferencing pointer to incomplete type
loadndisdriver.c:299: error: dereferencing pointer to incomplete type
loadndisdriver.c:302: error: dereferencing pointer to incomplete type
loadndisdriver.c:303: error: dereferencing pointer to incomplete type
loadndisdriver.c:305: error: dereferencing pointer to incomplete type
loadndisdriver.c:311: error: dereferencing pointer to incomplete type
loadndisdriver.c:312: error: dereferencing pointer to incomplete type
loadndisdriver.c:313: warning: implicit declaration of function ‘strcpy’
loadndisdriver.c:313: warning: incompatible implicit declaration of built-in function ‘strcpy’
loadndisdriver.c:314: error: dereferencing pointer to incomplete type
loadndisdriver.c:317: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:318: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:321: error: dereferencing pointer to incomplete type
loadndisdriver.c:282: warning: unused variable ‘statbuf’
loadndisdriver.c:344: error: expected expression before ‘struct’
loadndisdriver.c:346: warning: implicit declaration of function ‘closedir’
loadndisdriver.c:348: warning: implicit declaration of function ‘free’
loadndisdriver.c:355: warning: implicit declaration of function ‘munmap’
loadndisdriver.c:355: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:355: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:357: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:357: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c: In function ‘get_device’:
loadndisdriver.c:367: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:370: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:370: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:373: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:374: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:376: warning: implicit declaration of function ‘snprintf’
loadndisdriver.c:376: warning: incompatible implicit declaration of built-in function ‘snprintf’
loadndisdriver.c:407: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:367: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘load_device’:
loadndisdriver.c:419: error: ‘DIR’ undeclared (first use in this function)
loadndisdriver.c:419: error: ‘dir’ undeclared (first use in this function)
loadndisdriver.c:423: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:423: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:424: warning: incompatible implicit declaration of built-in function ‘memset’
loadndisdriver.c:426: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:427: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:429: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:434: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:435: error: dereferencing pointer to incomplete type
loadndisdriver.c:436: error: dereferencing pointer to incomplete type
loadndisdriver.c:439: error: dereferencing pointer to incomplete type
loadndisdriver.c:447: error: expected expression before ‘struct’
loadndisdriver.c: In function ‘get_ioctl_device’:
loadndisdriver.c:464: error: ‘FILE’ undeclared (first use in this function)
loadndisdriver.c:464: error: ‘proc_misc’ undeclared (first use in this function)
loadndisdriver.c:472: warning: implicit declaration of function ‘strstr’
loadndisdriver.c:472: warning: incompatible implicit declaration of built-in function ‘strstr’
loadndisdriver.c:473: warning: implicit declaration of function ‘strtol’
loadndisdriver.c:473: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:483: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:483: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:488: warning: implicit declaration of function ‘unlink’
loadndisdriver.c:489: warning: implicit declaration of function ‘mknod’
loadndisdriver.c:489: error: ‘S_IFCHR’ undeclared (first use in this function)
loadndisdriver.c:489: error: ‘MISC_MAJOR’ undeclared (first use in this function)
loadndisdriver.c:490: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:495: error: ‘O_RDONLY’ undeclared (first use in this function)
loadndisdriver.c: In function ‘main’:
loadndisdriver.c:511: warning: implicit declaration of function ‘openlog’
loadndisdriver.c:511: error: ‘LOG_PERROR’ undeclared (first use in this function)
loadndisdriver.c:511: error: ‘LOG_CONS’ undeclared (first use in this function)
loadndisdriver.c:511: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:511: error: ‘LOG_DEBUG’ undeclared (first use in this function)
loadndisdriver.c:513: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:515: warning: implicit declaration of function ‘strncmp’
loadndisdriver.c:517: warning: implicit declaration of function ‘printf’
loadndisdriver.c:517: warning: incompatible implicit declaration of built-in function ‘printf’
loadndisdriver.c:527: warning: implicit declaration of function ‘atoi’
loadndisdriver.c:542: warning: implicit declaration of function ‘atof’
loadndisdriver.c:549: warning: implicit declaration of function ‘strcmp’
loadndisdriver.c:556: warning: incompatible implicit declaration of built-in function ‘sscanf’
loadndisdriver.c:590: warning: implicit declaration of function ‘closelog’
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/slats/Desktop/ndiswrapper-1.48/utils'
make: *** [all] Error 2
slats@Slat-Machine:~/Desktop/ndiswrapper-1.48$ 


```

---

### Post by kevdog on 2008-02-06
Is the linux hearders for your kernel and build-essential package installed?

---

### Post by frozenjake on 2008-02-07
So here I am, joining the crowd of n00bs who are still getting their feet wet. My pc loads the Wireless manager and ndiswrapper at startup, and it says device found, driver installed and all that when i '-l' and lsusb, but when I ifconfig, it doesn't show the wlan0 adapter and it's not listed in the networking options!

Where did I go wrong? I had it working before.....:confused:
Thanks in advance!

Oh, and I used the Debian install available through wget.

---

### Post by kevdog on 2008-02-07
Did you load the kernel module with the modprobe statement?  After this process did you check dmesg for any potential errors?

---

### Post by quodlibetor on 2008-02-07
Hey thanks for the guide, could you help me fix a problem it left me with? The internet doesn't work. I had things working before, but I was running into problems with wpa supplicant, so i was recommended to follow your guide and install ndiswrapper from source.

So now network-manager doesn't report any wireless networks. 

Some info included below. The only thing that my noob eyes can see as obviously weird is the second wlan0:ava section, and the ridiculous iwlist result:

Ubuntu 7.10
Linksys WMP300n

**Output from ifconfig, while plugged into a wired ethernet:**
```
eth0      Link encap:Ethernet  HWaddr 00:18:F3:61:9E:00  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:f3ff:fe61:9e00/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23398 errors:3 dropped:0 overruns:0 frame:2
          TX packets:20912 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:23457004 (22.3 MB)  TX bytes:4378609 (4.1 MB)
          Base address:0xff00 Memory:fdfc0000-fdfe0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:18:F8:2B:82:4C  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Memory:fdef8000-fdefc000 

wlan0:ava     Link encap:Ethernet  HWaddr 00:18:F8:2B:82:4C  
              inet addr:169.254.6.14  Bcast:169.254.255.255  Mask:255.255.0.0
              UP BROADCAST MULTICAST  MTU:1500  Metric:1
              Interrupt:17 Memory:fdef8000-fdefc000 
```

**Output from dmesg|grep ndiswrapper:**
```
[  112.965287] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  113.017557] ndiswrapper (link_pe_images:576): fixing KI_USER_SHARED_DATA address in the driver
[  113.019285] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[  113.040031] ndiswrapper: using IRQ 17
[  113.287042] usbcore: registered new interface driver ndiswrapper
[ 5225.826233] ndiswrapper: device wlan0 removed
[ 5225.826374] usbcore: deregistering interface driver ndiswrapper
[ 5232.715618] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[ 5232.724991] ndiswrapper (link_pe_images:576): fixing KI_USER_SHARED_DATA address in the driver
[ 5232.727154] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[ 5233.194931] ndiswrapper: using IRQ 17
[ 5236.500713] usbcore: registered new interface driver ndiswrapper
```

**Output of iwlist:**
```
Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation 
```
Thanks again for the guide, and for any help you might be able to give me.

---

### Post by frozenjake on 2008-02-07
*bows head in awe* thanks for the tutorial....:guitar:all is well in the land of oz now....
Thanks guys!

---

### Post by kevdog on 2008-02-08
Any potential steps you took to solve your problem that you would like to share with everyone else?

---

### Post by chew5011 on 2008-02-08
> **kevdog said:**
> remove and reload the kernel module 

sudo modprobe -r ndiswrapper 
sudo modprobe ndiswrapper

Then check dmesg, it will probably give you an error and hint as to what the problem is.

Thanks man.....
i get something that told me that module "ndiswrapper" is not found by this step....
then i reinstalled my ndiswrapper....
now the network is claimed....

but....
i still cannot get the desired output as you stated
this is the output of lshw -C network 
[B]
lshw -C network [/B]
```
 *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 02
       serial: 00:1c:bf:1c:f2:10
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netw4x64 driverversion=1.52+Intel,08/08/2007,11.1.1.22 latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g

```

is it any Command that i can enable the device????
Hohohoho.....
Thanks man.....

---

### Post by kevdog on 2008-02-08
Try this

sudo ifconfig wlan0 up

---

### Post by fissionmailed on 2008-02-09
Ok, I have installed ndiswrapper and all.  And I eve ngot it working, but then it quit working after I did some updates and added some software.   I'm not sure it this is a wpa-problem or a conf problem. *smacks forhead*  I got it to work following your instructions in the other thread that's stickied.

This is where I get the problem it seems.

> root@fission:/home/wfsaibot/Desktop/misclinuxfolders/alsa-wireless-files/wireless/ndiswrapper-1.51# wpa_supplicant -w -Dwext -iwlan0 -c/etc/wpa_supplicant_home.conf -dd
Initializing interface 'wlan0' conf '/etc/wpa_supplicant_home.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant_home.conf' -> '/etc/wpa_supplicant_home.conf'
Reading configuration file '/etc/wpa_supplicant_home.conf'
ap_scan=1
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=7):
     77 6f 6f 64 73 77 6c                              woodswl         
scan_ssid=0 (0x0)
proto: 0x1
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=10): [REMOVED]
pairwise: 0x8
group: 0x8
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='woodswl'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=22 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:1b:9e:85:6a:38
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
Setting scan request: 0 sec 100000 usec
Using existing control interface directory.
ctrl_iface bind(PF_UNIX) failed: Address already in use
ctrl_iface exists and seems to be in use - cannot override it
Delete '/var/run/wpa_supplicant/wlan0' manually if it is not used anymore
Failed to initialize control interface '/var/run/wpa_supplicant'.
You may have another wpa_supplicant process already running or the file was
left by an unclean termination of wpa_supplicant in which case you will need
to manually remove this file before starting wpa_supplicant again.

Failed to add interface wlan0
State: DISCONNECTED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_wext_set_wpa
wpa_driver_wext_set_drop_unencrypted
wpa_driver_wext_set_countermeasures
No keys have been configured - skip key clearing
Cancelling scan request
Cancelling authentication timeout
WEXT: Operstate: linkmode=0, operstate=6


I got it to work a couple of times earlier but like I said, it quit working,  after I got a 32 bit browser with plug ins, a VM with windows, my sound working and the video all sorted out.  I tried reinstalling ndiswrapper, I tried about three different drivers and nothing will work now.  If I haven't mentioned it, it's an atheros ar5007eg.

---

### Post by kevdog on 2008-02-10
Have you looked at a few of the other threads addressing this chipset: atheros ar5007eg??  This seems to be a very problematic atheros version.

---

### Post by fissionmailed on 2008-02-10
> **kevdog said:**
> Have you looked at a few of the other threads addressing this chipset: atheros ar5007eg??  This seems to be a very problematic atheros version.

Very much so, I've mostly likely looked about a good dozen of them.  I just hope madwifi comes out with a new version with a corrected HAL before I end up throwing the laptop out of the window. >_<

It there anything in there that hints to a problem?  Oh is there something else that I should post?

---

### Post by fissionmailed on 2008-02-11
Got it to work without a hitch.  After a month.... >_<

ifconfig wlan0 hw ether 00:1b:9e:85:6a:38

is the magic key, er mac. :lolflag:


[http://ndiswrapper.sourceforge.net/joomla/index.php?option=com_fireboard&Itemid=34&func=view&id=906&catid=2#906](http://ndiswrapper.sourceforge.net/joomla/index.php?option=com_fireboard&Itemid=34&func=view&id=906&catid=2#906)

That got me started on it.   Well, I did what he posted and it didn't work, but it I do it in the command line before the wpa and all it works fine.  
ifconfig wlan0 hw ether etc

I tried the script and all but it didn't work. :\

Oh well, I can use my wireless, I'm a happy camper. :D

---

### Post by beerjen on 2008-02-13
I followed the instructions but no succes.

Im using kubuntu 7.10 and gave a belkin wireless G desktop card.
I can see teh card in the network configuration but I can't make a connection with a wireless network. 

These are my output files:
```
internet@internet-desktop:~$ ndiswrapper -l
net8185 : driver installed
        device (1799:700F) present
```

```

lspci
03:09.0 Ethernet controller: Belkin Unknown device 700f (rev 20)
```

```
lspci -n
03:09.0 0200: 1799:700f (rev 20)
```

```
internet@internet-desktop:~$ iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Auto  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:-2147483648 dBm   Sensitivity=0/3
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0g
```

```
lshw -C network

  *-network
       description: Wireless interface
       product: Belkin
       vendor: Belkin
       physical id: 9
       bus info: pci@0000:03:09.0
       logical name: wlan0
       version: 20
       serial: 00:17:3f:31:5a:79
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8185 driverversion=1.52+Realtek,02/01/2007,5.1097.0 latency=64 link=no maxlatency=64 mingnt=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
internet@internet-de
```

```
iwlist
internet@internet-desktop:~$ iwlist
Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency
              [interface] channel
              [interface] bitrate
              [interface] rate
              [interface] encryption
              [interface] keys
              [interface] power
              [interface] txpower
              [interface] retry
              [interface] ap
              [interface] accesspoints
              [interface] peers
              [interface] event
              [interface] auth
              [interface] wpakeys
              [interface] genie
              [interface] modulation
```

Can someone help me? I'm getting frustrated about this

Thanks,
Bert

---

### Post by kevdog on 2008-02-14
Can you post iwlist scan?

---

### Post by beerjen on 2008-02-14
I get nothing from that scan. absolutely nothing.

I don't understand.

---

### Post by kevdog on 2008-02-15
Definitely confused about this.  The only way you should get nothing is if there are no wireless networks in the area.  Have you check dmesg for any errors?

---

### Post by beerjen on 2008-02-15
there were no errors in dmesg.. .

But I gave up. My boss wanted internet so I went for windows. (online after 2 minutes)
On other forums there were other people with the same wireless belkin card and they had the same problems. 
Next time I will check linux compatibility before I buy hardware. 

Damn, 

Thanks anyway for the help

Bert

---

### Post by alanjackson on 2008-02-15
I'm having the identical set of problems with the same card.

Belkin Wireless Desktop, F5D7000v7000, 1799:700f rev 20

I tried loading the driver from the CD (BLKWGDv7.inf) with ndiswrapper. It said everything was fine. But the wlan0 device never actually shows up anywhere. Has anyone actually gotten this particular card to work?

---

### Post by kevdog on 2008-02-15
Does the device show up with lspci?

---

### Post by alanjackson on 2008-02-15
Belkin unknown device 700f (rev 20)

---

### Post by kevdog on 2008-02-15
Hmm, thats a bad sign.  Wonder if any thing has changed with the Hardy kernel.  It might be a device truly incompatible with linux -- although that is kind of hard to believe.

---

### Post by beerjen on 2008-02-16
I spent two days trying to get it to work. No luck. 
And I read other posts from a lot of different people that had the same problem.
 I think we bought the one not supported card!

---

### Post by chew5011 on 2008-02-16
Hello man....
i am facing a problem again.....
i ran these commands

```

ifconfig wlan0 up
iwconfig wlan0 essid "abc"

```

but my essid is not changed.
this is the output of 
**]iwconfig wlan0**
```
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

and this is the output of 
**ifup wlan0**
```
/sbin/ifup: configuration for wlan0 not found.

```

this is the output of 
**iwlist wlan0 scan**
```
          Cell 04 - Address: 00:18:F8:F9:91:1C
                    ESSID:"abc"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:84/100  Signal level:-42 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

```


this is a line that i found suspicious in my 
**dmesg**
```
ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

Thank you in advance man......

---

### Post by kevdog on 2008-02-16
After you boot into ubuntu and check dmesg, do you get the error message about the link not being ready?

---

### Post by odzx on 2008-02-16
hi   everyone
hi kevdog. thanx for the great howto
i'm having problems with a level one card (chipset: realtek 8185). the card is recognized but can not connect. 
the driver that is being used is r8180. after reading different forum post about this chipset i decided to try and load the windows driver with ndiswrapper. i followed this how to and installed the realtek rtl8185 driver, witch seemed to install fine and i actually got my wireless card connected to the network. 
the problem started after i rebooted the machine. the card seems to be recognized but no driver is loaded.
>  lshw -C network
 *-network:0 UNCLAIMED
       description: Ethernet controller
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:01:01.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64 maxlatency=64 mingnt=32
  *-network:1
       description: Ethernet interface
       product: RTL-8110SC/8169SC Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:01:05.0
       logical name: eth0
       version: 10
       serial: 00:1a:4d:fc:fd:69
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 ip=192.168.0.3 latency=64 maxlatency=64 mingnt=32 module=r8169 multicast=yes
i have blacklisted r8180 and r818x but it does show up as the alternative driver
> ndiswrapper -l
net8185 : driver installed
        device (10EC:8185) present (alternate driver: r818x)
i tried the same with ubuntu an pclos installations and got the same results.
in pclos i actually get a gui window saying : "
       configuration: latency=64 maxlatency=64 mingnt=32
  *-network:1
       description: Ethernet interface
       product: RTL-8110SC/8169SC Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:01:05.0
       logical name: eth0
       version: 10
       serial: 00:1a:4d:fc:fd:69
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 ip=192.168.0.3 latency=64 maxlatency=64 mingnt=32 module=r8169 multicast=yes[/QUOTE]
i have blacklisted r8180 and r818x but it does show up as the alternative driver
> ndiswrapper -l
net8185 : driver installed
        device (10EC:8185) present (alternate driver: r818x)
i tried the same with ubuntu an pclos installations and got the same results.
in pclos i actually get a gui window saying : "
       configuration: latency=64 maxlatency=64 mingnt=32
  *-network:1
       description: Ethernet interface
       product: RTL-8110SC/8169SC Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:01:05.0
       logical name: eth0
       version: 10
       serial: 00:1a:4d:fc:fd:69
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 ip=192.168.0.3 latency=64 maxlatency=64 mingnt=32 module=r8169 multicast=yes[/QUOTE]
i have blacklisted r8180 and r818x but it does show up as the alternative driver
> ndiswrapper -l
net8185 : driver installed
        device (10EC:8185) present (alternate driver: r818x)
i tried the same with ubuntu an pclos installations and got the same results.
in pclos i actually get a gui window saying : "
       configuration: latency=64 maxlatency=64 mingnt=32
  *-network:1
       description: Ethernet interface
       product: RTL-8110SC/8169SC Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:01:05.0
       logical name: eth0
       version: 10
       serial: 00:1a:4d:fc:fd:69
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 ip=192.168.0.3 latency=64 maxlatency=64 mingnt=32 module=r8169 multicast=yes[/QUOTE]
i have blacklisted r8180 and r818x but it does show up as the alternative driver
> ndiswrapper -l
net8185 : driver installed
        device (10EC:8185) present (alternate driver: r818x)
i tried the same with ubuntu an pclos installations and got the same results.
in pclos i actually get a gui window saying : "
       configuration: latency=64 maxlatency=64 mingnt=32
  *-network:1
       description: Ethernet interface
       product: RTL-8110SC/8169SC Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:01:05.0
       logical name: eth0
       version: 10
       serial: 00:1a:4d:fc:fd:69
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 ip=192.168.0.3 latency=64 maxlatency=64 mingnt=32 module=r8169 multicast=yes[/QUOTE]
i have blacklisted r8180 and r818x but it does show up as the alternative driver
> ndiswrapper -l
net8185 : driver installed
        device (10EC:8185) present (alternate driver: r818x)
i tried the same with ubuntu an pclos installations and got the same results.
in pclos i actually get a gui window saying : "unable to find network interface for selected device (using 8180 driver)" when i try enable the wireless network.
what am i missing here?

---

### Post by alanjackson on 2008-02-16
> **kevdog said:**
> Hmm, thats a bad sign.  Wonder if any thing has changed with the Hardy kernel.  It might be a device truly incompatible with linux -- although that is kind of hard to believe.

Be just my luck to buy the only incompatible card. I'm running a fresh, clean, updated install of Gutsy.

I tried downloading the Linux driver from Realtek that looked like it might be the right one, but it just hangs when I try to bring it up.

---

### Post by chew5011 on 2008-02-16
> **kevdog said:**
> After you boot into ubuntu and check dmesg, do you get the error message about the link not being ready?

do you mean i check the dmesg once i reboot my fedora???

---

### Post by kevdog on 2008-02-16
I know nothing about fedora -- sorry!

---

### Post by alanjackson on 2008-02-16
Well, I'm just about ready to throw in the towel. Anyone want to suggest a cheap, easily installed, wireless card?

For future reference, here is all my info... note that dmesg seems to show an error

Running a clean install of Gutsy Gibbon with all the updates

Wireless card is a Belkin Wireless G Desktop Card
F5D7000v7000  1799:700f rev 20

I tried loading the XP driver from the CD,
BLKWGDv7.inf
using ndiswrapper version 1.45
$ ndiswrapper -v
utils version: 1.9
driver filename:       /lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.45
vermagic:       2.6.22-14-generic SMP mod_unload 586 

```

~$ ndiswrapper -l
blkwgdv7 : driver installed
        device (1799:700F) present

```

```

$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```

```

$ sudo lshw -C network
  *-network:0             
       description: Ethernet controller
       product: Belkin
       vendor: Belkin
       physical id: b
       bus info: pci@0000:01:0b.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=ndiswrapper latency=64 maxlatency=64 mingnt=32
  *-network:1
       description: Ethernet interface
       product: SMC2-1211TX
       vendor: Accton Technology Corporation
       physical id: d
       bus info: pci@0000:01:0d.0
       logical name: eth0
       version: 10
       serial: 00:10:b5:8a:fb:36
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.17 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s

```

```

$  ifconfig
eth0      Link encap:Ethernet  HWaddr 00:10:B5:8A:FB:36  
          inet addr:192.168.0.17  Bcast:192.168.0.31  Mask:255.255.255.224
          inet6 addr: fe80::210:b5ff:fe8a:fb36/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1880 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1582 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:297543 (290.5 KB)  TX bytes:217441 (212.3 KB)
          Interrupt:9 Base address:0xc400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

```

$  sudo lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82810 GMCH (Graphics Memory Controller Hub) [8086:7120] (rev 03)
00:01.0 VGA compatible controller [0300]: Intel Corporation 82810 (CGC) Chipset Graphics Controller [8086:7121] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801AA PCI Bridge [8086:2418] (rev 02)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801AA ISA Bridge (LPC) [8086:2410] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801AA IDE Controller [8086:2411] (rev 02)
00:1f.2 USB Controller [0c03]: Intel Corporation 82801AA USB Controller [8086:2412] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801AA SMBus Controller [8086:2413] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801AA AC'97 Audio Controller [8086:2415] (rev 02)
01:0b.0 Ethernet controller [0200]: Belkin Unknown device [1799:700f] (rev 20)
01:0d.0 Ethernet controller [0200]: Accton Technology Corporation SMC2-1211TX [1113:1211] (rev 10)

```

```

$ dmesg
...
[   51.706259] ndiswrapper version 1.45 loaded (smp=yes)
[   51.830826] ndiswrapper: driver blkwgdv7 (Belkin,10/19/2006,5.87.19.106) loaded
[   51.831741] PCI: Enabling device 0000:01:0b.0 (0114 -> 0117)
[   51.831776] PCI: setting IRQ 3 as level-triggered
[   51.831784] PCI: Assigned IRQ 3 for device 0000:01:0b.0
[   51.836524] BUG: unable to handle kernel NULL pointer dereference at virtual address 00000000
[   51.836557]  printing eip:
[   51.836562] d0b78239
[   51.836566] *pde = 00000000
[   51.836580] Oops: 0002 [#1]
[   51.836584] SMP 
[   51.836594] Modules linked in: ndiswrapper lp snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_mpu401 snd_mpu401_
uart snd_seq_dummy parport_pc pcspkr analog snd_seq_oss snd_seq_midi gameport parport snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq
_device i2c_i810 i2c_algo_bit psmouse serio_raw intel_agp agpgart i2c_core snd soundcore snd_page_alloc intel_rng iTCO_wdt iTCO_vendor_support
 shpchp pci_hotplug evdev ext3 jbd mbcache sg sr_mod cdrom sd_mod floppy ata_generic 8139too mii uhci_hcd usbcore ata_piix libata scsi_mod fus
e apparmor commoncap
[   51.836704] CPU:    0
[   51.836707] EIP:    0060:[<d0b78239>]    Tainted: P       VLI
[   51.836711] EFLAGS: 00010202   (2.6.22-14-generic #1)
[   51.836727] EIP is at 0xd0b78239
[   51.836734] eax: 00000000   ebx: 00000000   ecx: 0000003d   edx: d0ba2e52
[   51.836744] esi: d0c4981a   edi: d0bb003d   ebp: c9d15b00   esp: c9d15af4
[   51.836753] ds: 007b   es: 007b   fs: 00d8  gs: 0033  ss: 0068
[   51.836764] Process modprobe (pid: 3458, ti=c9d14000 task=ce6f6a60 task.ti=c9d14000)
[   51.836771] Stack: d0c4981a d0bbe000 d0ba9271 c9d15b68 d0b7860f d0c4981a d0ba7980 0000003d 
[   51.836791]        00000000 00000000 c9cd3200 c0105223 c9d15b84 d0bbe000 cf97b2f0 c9cd3200 
[   51.836809]        00000000 000000c7 00000003 c0000001 d0b499ff d0b49420 d0bbeaac c9d15b84 
[   51.836827] Call Trace:
[   51.836847]  [<c0105223>] common_interrupt+0x23/0x30
[   51.836886]  [<d0b499ff>] NdisInitializeEvent+0x1f/0x30 [ndiswrapper]
[   51.837037]  [<d0b49420>] NdisAllocateSpinLock+0x10/0x20 [ndiswrapper]
[   51.837101]  [<d0b57fd4>] mp_init+0xa4/0x180 [ndiswrapper]
[   51.837156]  [<d0b58729>] NdisDispatchPnp+0xd9/0xdb0 [ndiswrapper]
[   51.837197]  [<c01f9752>] __next_cpu+0x12/0x20
[   51.837243]  [<c010320a>] __switch_to+0xaa/0x1d0
[   51.837262]  [<c02f2335>] schedule+0x515/0x890
[   51.837290]  [<d0b51a9b>] IoAllocateIrp+0x5b/0x80 [ndiswrapper]
[   51.837338]  [<d0b521e5>] IoBuildAsynchronousFsdRequest+0x35/0x170 [ndiswrapper]
[   51.837386]  [<d0b516e5>] IofCallDriver+0x55/0xc0 [ndiswrapper]
[   51.837433]  [<d0b5697b>] IoSendIrpTopDev+0xbb/0x120 [ndiswrapper]
[   51.837487]  [<d0b56cd0>] pnp_start_device+0x50/0xb0 [ndiswrapper]
[   51.837542]  [<d0b56f13>] wrap_pnp_start_device+0x1e3/0x290 [ndiswrapper]
[   51.837598]  [<d0b57005>] wrap_pnp_start_pci_device+0x45/0x50 [ndiswrapper]
[   51.837643]  [<c01c405f>] sysfs_make_dirent+0x2f/0x50
[   51.837662]  [<c01c50b4>] sysfs_create_link+0xf4/0x140
[   51.837680]  [<c02099e3>] pci_match_device+0x13/0xc0
[   51.837719]  [<c0209b06>] pci_device_probe+0x56/0x80
[   51.837734]  [<c02611ae>] driver_probe_device+0x8e/0x190
[   51.837757]  [<c026141e>] __driver_attach+0x9e/0xa0
[   51.837770]  [<c026059b>] bus_for_each_dev+0x3b/0x60
[   51.837809]  [<c0261026>] driver_attach+0x16/0x20
[   51.837819]  [<c0261380>] __driver_attach+0x0/0xa0
[   51.837828]  [<c026096a>] bus_add_driver+0x8a/0x1b0
[   51.837847]  [<c0209cb3>] __pci_register_driver+0x53/0xa0
[   51.837862]  [<d0b46dc7>] loader_init+0x107/0x230 [ndiswrapper]
[   51.837901]  [<d0b5366f>] wrap_procfs_init+0x3f/0xb0 [ndiswrapper]
[   51.837942]  [<d08c90b5>] wrapper_init+0xb5/0xc2 [ndiswrapper]
[   51.837976]  [<c014a7f1>] sys_init_module+0x151/0x1a00
[   51.837992]  [<c01fb43f>] prio_tree_insert+0x1f/0x250
[   51.838063]  [<c01041d2>] sysenter_past_esp+0x6b/0xa9
[   51.838090]  =======================
[   51.838095] Code: 04 00 cc cc cc cc cc cc 8b ff 55 8b ec 56 8b 75 08 57 66 8b 7d 10 0f b7 cf 33 c0 85 c9 7e 15 53 8b 55 0c 8b 52 04 8a 14 4
2 8b 1e <88> 14 18 40 3b c1 7c ed 5b 66 89 7e 04 5f 33 c0 5e 5d c2 0c 00 
[   51.838173] EIP: [<d0b78239>] 0xd0b78239 SS:ESP 0068:c9d15af4


```

---

### Post by kevdog on 2008-02-16
Did you do a sudo modprobe ndiswrapper?

Check lsmod to see if the ndiswrapper module is loaded!

---

### Post by alanjackson on 2008-02-16
> **kevdog said:**
> Did you do a sudo modprobe ndiswrapper?

Check lsmod to see if the ndiswrapper module is loaded!

$ lsmod | grep ndis
ndiswrapper           185434  1 
usbcore               138632  3 ndiswrapper,uhci_hcd

$ sudo modprobe -l | grep ndis
/lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko

---

### Post by kevdog on 2008-02-17
Rereading your output from dmesg above a lot of those errors really dont sound good.  Id say the there is definitely a driver problem going on.  Unless you can find another driver, I say you are out of luck.  Remind me the chipset of the card again

---

### Post by alanjackson on 2008-02-17
> **kevdog said:**
> Rereading your output from dmesg above a lot of those errors really dont sound good.  Id say the there is definitely a driver problem going on.  Unless you can find another driver, I say you are out of luck.  Remind me the chipset of the card again

On the chip on the card it reads RTL8185L

---

### Post by kevdog on 2008-02-17
Alan

Did you ever try with another method other than ndiswrapper?

---

### Post by alanjackson on 2008-02-17
> **kevdog said:**
> Alan

Did you ever try with another method other than ndiswrapper?

I tried what I *thought* might be a Linux driver, but that just got hung.

---

### Post by kevdog on 2008-02-17
Did you try downloading and compiling the source drivers from the Realtek website?? or possibly the r818x drivers contained in the kernel??  Im not sure if any method will work since this message is troubling to me:

```
01:0b.0 Ethernet controller [0200]: Belkin Unknown device [1799:700f] (rev 20)

```

---

### Post by alanjackson on 2008-02-17
> **kevdog said:**
> Did you try downloading and compiling the source drivers from the Realtek website?? or possibly the r818x drivers contained in the kernel??  Im not sure if any method will work since this message is troubling to me:

```
01:0b.0 Ethernet controller [0200]: Belkin Unknown device [1799:700f] (rev 20)

```

$ cd rtl8185_linux_26.1027.0823.2007/
$ ls
ieee80211    makedrv  release_note  rtl8185.tar.gz  wlan0dhcp  wlan0up
ifcfg-wlan0  readme   rtl8185       stack.tar.gz    wlan0down  wpa_supplicant-0.4.9.tar.gz

$ sudo ./wlan0up 
wlan0: ERROR while getting interface flags: No such device

$ sudo ./wlan0up 
insmod: error inserting 'ieee80211_crypt-rtl.ko': -1 File exists
insmod: error inserting 'ieee80211_crypt_wep-rtl.ko': -1 File exists
insmod: error inserting 'ieee80211_crypt_tkip-rtl.ko': -1 File exists
insmod: error inserting 'ieee80211_crypt_ccmp-rtl.ko': -1 File exists
insmod: error inserting 'ieee80211-rtl.ko': -1 File exists
insmod: error inserting 'r8180.ko': -1 File exists
wlan0: ERROR while getting interface flags: No such device

---

### Post by kevdog on 2008-02-17
Can you post me the source of the files you downloaded so I can take a look at them - mostly the readme file.  I dont have a realtek card so I'm kind of flying blind a little bit here!

---

### Post by alanjackson on 2008-02-17
> **kevdog said:**
> Can you post me the source of the files you downloaded so I can take a look at them - mostly the readme file.  I dont have a realtek card so I'm kind of flying blind a little bit here!

Readme file
```

RTL8185 Linux Driver v1027.0823.2007 for linux kernel 2.6

  - Support Client mode for either infrastructure or adhoc mode
  - Support WEP and WPAPSK/WPA2PSK connection

===============================================================================================
< Component >
The driver is composed of several parts:
    (1)source code
        rtl8185.tar.gz
        stack.tar.gz

    (2)Script ot build the modules
        makedrv

    (3)Script to load/unload modules
        wlan0up
        wlan0down

    (4)Script and configuration for DHCP
        wlan0dhcp
        ifcfg-wlan0

    (5)Supplicant source code
        wpa_supplicant-0.4.9.tar.gz

    (6)Example of supplicant configuration file
        wpa1.conf




< Installation >
Running the scripts can finish all operations of building up modules from source code and start the nic:

        (1)Build up the driver from the source code
                ./makedrv

        (2)Load the driver module to kernel and start up nic
                ./wlan0up
           (if "insmod: error inserting 'r8180.ko': -File exists." met,
                ./wlan0rmv
                ./wlan0down
                ./wlan0up
            should be OK.
           )
        (3)Refer to < Set wireless lan MIBs > to set Wireless LAN specific parameters.





< Set wireless lan MIBs >
This driver uses Wireless Extension as an interface allowing you to set
Wireless LAN specific parameters.

Current driver supports "iwlist" to show the device status of nic

        iwlist wlan0 [parameters]
where

        parameter explaination          [parameters]
        -----------------------         -------------
        Show available chan and freq    freq / channel
        Show and Scan BSS and IBSS      scan[ning]
        Show supported bit-rate         rate / bit[rate]
        Show Power Management mode      power

For example:

        iwlist wlan0 channel
        iwlist wlan0 scan
        iwlist wlan0 rate
        iwlist wlan0 power


Driver also supports "iwconfig", manipulate driver private ioctls, to set MIBs.

        iwconfig wlan0 [parameters] [val]
where

        parameter explaination      [parameters]                [val] constraints
        -----------------------     -------------               ------------------
        Connect to AP by address    ap                          [essid]
        Set the essid, join (I)BSS  essid                       [mac_addr]
        Set operation mode          mode                        {Managed|Ad-hoc}
        Set keys and security mode  key / enc[ryption]          {N|open|restricted|off}


For example:

        iwconfig wlan0 ap XX:XX:XX:XX:XX:XX
        iwconfig wlan0 essid "ap_name"
        iwconfig wlan0 mode Ad-hoc
        iwconfig wlan0 mode essid "name" mode Ad-hoc
        iwconfig wlan0 key 0123456789 [2] open
        iwconfig wlan0 key off
        iwconfig wlan0 key restricted [3] 0123456789

< Getting IP address >
After start up the nic, the network needs to obtain an IP address before transmit/receive data.
This can be done by setting the static IP via "ifconfig wlan0 IP_ADDRESS" command, or using DHCP.

If using DHCP, setting steps is as below:

        (1)connect to an AP via "iwconfig" settings
                iwconfig wlan0 essid [name]     or
                iwconfig wlan0 ap XX:XX:XX:XX:XX:XX

        (2)run the script which run the dhclient
                ./wlan0dhcp
           or
                dhcpcd wlan0
                (Some network admins require that you use the
                hostname and domainname provided by the DHCP server.
                In that case, use
                dhcpcd -HD wlan0)



< WPAPSK >
WPA_SUPPLICANT help the network to communicate under the protection of WPAPSK mechanism

        (1)Unpack source code of WPA supplicant:
                tar -zxvf wpa_supplicant-0.4.9.tar.gz
                cd wpa_supplicant-0.4.9

        (2)Create .config file:
                cp defconfig .config

        (3)Edit .config file, uncomment the following line:
                #CONFIG_DRIVER_IPW=y.

        (4)Build WPA supplicant:
                make

        If make error for lack of <include/md5.h>, install the openssl lib:
         1. Install the openssl lib from corresponding installation disc:
            Fedora Core 2/3/4/5/6/7(openssl-0.9.71x-xx),
            Mandrake10.2/Mandriva10.2(openssl-0.9.7x-xmdk),
            Debian 3.1(libssl-dev), Suse 9.3/10.0/10.1(openssl_devl),
            Gentoo(dev-libs/openssl), etc.
         2. Download the openssl open source package from www.openssl.org, build and install it.

        (5)Edit wpa_supplicant.conf to set up SSID and its passphrase.
        For example, the following setting in "wpa1.conf" means SSID to join is "BufAG54_Ch6"
        and its passphrase is "87654321".

                network={
                        ssid="BufAG54_Ch6"
                        proto=WPA
                        key_mgmt=WPA-PSK
                        pairwise=CCMP TKIP
                        group=CCMP TKIP WEP104 WEP40
                        psk="87654321"
                        priority=2
                }
        Note: 1. proto=WPA for WPA, proto=RSN for WPA2.
              2. If you want to connect an AP which works under WPA2 mixed mode, you'd better
                 use Realtek customed wpa_supplicant package.


        (6)Execute WPA supplicant (Assume 8185 and related modules had been loaded):
                ./wpa_supplicant -D ipw -c wpa1.conf -i wlan0 &


```

and another readme - this one is not too encouraging!

```

rtl8180-sa2400 Linux kernel driver
Released under the terms of GNU General Public Licence (GPL)
Copyright(c) Andrea Merello - 2004,2005

Portions of this driver are based on Intel Pro Wireless 2100 driver.
Thanks to the original author !! Most notabily the ieee802.11 stack
is imported from this project, altought I've modified it

------------------------------------------------------------------------------

This is an attempt to write somethig that can make my rtl8180-based wlan card
work under Linux (using only opensource stuff). It's in early development
stage so don't expect too much from it (also use it at your own risk!)
This should be considered just a fragment of code.. using it on your(any)
system is at your own risk! Please note that I never supported the idea to
use it in any way, so i cannot be considered responsible in any way for
anything deriving by it usage.

Anyway for now we have monitor mode and managed mode
basically working! This isn't necessary stable, but seems to work..
Also since v 0.16 we have an initial and incomplete support for ad-hoc
mode. *Please* see README.adhoc for further details

An official driver from Realtek exist for this NIC but
- It's mainly closed source stuff
- It doesn't work on 2.6 kernels (and on some 2.4)
- It hasn't any support for monitor mode

I have it working with ndiswrapper, but since I don't like to use windows'
closed source drv I decided to try to write this driver.

*!!Please note that only cards with a PHILIPS sa2400 or MAXIM or GCT RF chip are supported.!!*

Support for such a radio chip is also still experimental.
There are some variant of the card with rtl8180 and philips sa2400 RF:
antenna diversity, firdac etc..
Altought all configurations should be supported, some are not tested and might
fail. If you decide to test this drv on a digital-phy card, please let me know
the results.

This driver is still under development and very far from perfect. It should work on x86,
and someone reported success on PPC, while on amd64 I have some success and some failure
report. Other archs are untested.. I think there is still work to do about this.

If you decide to try it anyway (at your own risk!) and you want report me success/insuccess
I will apreciate it very much.

To compile the driver simply run make.

Note that the Makefile should work on kenrel 2.6 and 2.4.
Anyway the old Makefile for 2.6 kernel is still included as Makefile26.

FOUR modules will be compiled: the ieee802.11 stack (3 modules) and the driver
itself. You need to insmod ALL of them!


```

---

### Post by kevdog on 2008-02-17
Doesnt look encouraging!!! Did you try to compile the driver first with:

        (1)Build up the driver from the source code
                ./makedrv

---

### Post by alanjackson on 2008-02-18
> **kevdog said:**
> Doesnt look encouraging!!! Did you try to compile the driver first with:

        (1)Build up the driver from the source code
                ./makedrv

Yep. I just followed the instructions in the README

---

### Post by kevdog on 2008-02-18
Without the card in front of me its really hard to troubleshoot -- How about the built in r818x drivers?  Do they work?

---

### Post by alanjackson on 2008-02-18
> **kevdog said:**
> Without the card in front of me its really hard to troubleshoot -- How about the built in r818x drivers?  Do they work?

$ sudo modprobe r8187
FATAL: Module r8187 not found.
$ sudo modprobe r818x
FATAL: Module r818x not found.

---

### Post by kevdog on 2008-02-19
sudo updatedb
sudo locate r818*

---

### Post by alanjackson on 2008-02-19
> **kevdog said:**
> sudo updatedb
sudo locate r818*

Looks like progress....

$  sudo updatedb
$  sudo locate r818*
/lib/modules/2.6.22-14-generic/ubuntu/wireless/rtl8180/rtl8180/r8180.ko

$ sudo modprobe r8180

$ demsg
no errors.
[157191.210278] Linux kernel driver for RTL8180 / RTL8185 based WLAN cards
[157191.210294] Copyright (c) 2004-2005, Andrea Merello
[157191.210300] rtl8180: Initializing module
[157191.210306] rtl8180: Wireless extensions version 22
[157191.210312] rtl8180: Initializing proc filesystem

```

$ sudo lshw -C network
  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: Belkin
       vendor: Belkin
       physical id: b
       bus info: pci@0000:01:0b.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=64 mingnt=32
  *-network:1
       description: Ethernet interface
       product: SMC2-1211TX
       vendor: Accton Technology Corporation
       physical id: d
       bus info: pci@0000:01:0d.0
       logical name: eth0
       version: 10
       serial: 00:10:b5:8a:fb:36
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.17 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s

```

```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:10:B5:8A:FB:36  
          inet addr:192.168.0.17  Bcast:192.168.0.31  Mask:255.255.255.224
          inet6 addr: fe80::210:b5ff:fe8a:fb36/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20366 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2465 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2822252 (2.6 MB)  TX bytes:380109 (371.2 KB)
          Interrupt:9 Base address:0xc400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


```

---

### Post by kevdog on 2008-02-19
Your wireless device has me stumped!!  Have to say I've lost the faith.

---

### Post by alanjackson on 2008-02-20
> **kevdog said:**
> Your wireless device has me stumped!!  Have to say I've lost the faith.

Can you recommend a card?

---

### Post by kevdog on 2008-02-20
Depends what chipset you are looking for.  An atheros chipset that is supported by the madwifi drivers are the easiest to get going.  Ive also heard good things about an Asus rt2500 card in terms of support.  The problem with most devices is that the model of chipset is not advertised either on the box or on new egg.  I currently have a cisco card that someone gave to me - by luck it had an atheros chipset.  I have a few linksys cards, all broadcom chipsets, that work well with ndiswrapper, however a lot of people dont like ndiswrapper.  If you want to do any aircracking, wep decryption, use your computer as an access point, you cant use ndiswrapper.

---

### Post by Incite on 2008-02-24
configuration: broadcast=yes driver=forcedeth driverversion=0.60 ip=192.168.2.87 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       **logical name: eth1**
       version: 02
       serial: 00:00:00:1a:73:b2
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=0 module=bcm43xx multicast=yes wireless=IEEE 802.11b/g

What went wrong?
Shouldnt it say WAN

---

### Post by kevdog on 2008-02-24
Did you blacklist the bcm43xx driver -- this driver is included in the kernel by default.  You need to blacklist this driver and use ndiswrapper instead.

---

### Post by Incite on 2008-02-25
Im not sure if i blaklisted it 

What are the commands to do that?
 or
 How can i check?

---

### Post by Incite on 2008-02-25
bump.

---

### Post by Incite on 2008-02-25
bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR

help please. I did this twice and i am having issues

---

### Post by kevdog on 2008-02-25
To blacklist

echo "blacklist bcm43xx" | sudo tee -a /etc/modprobe.d/blacklist

---

### Post by Incite on 2008-02-26
*-network               
       description: Ethernet interface
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth23
       version: a2
       serial: 00:00:6c:48:4e:a8
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.60 ip=192.168.2.102 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network DISABLED
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 02
       serial: 00:00:00:1a:73:b2
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=0 module=bcm43xx multicast=yes wireless=IEEE 802.11b/g

Im trying to figure this out but its not cooperating?

---

### Post by Grimhound on 2008-02-26
So the Vista driver won't work?

---

### Post by Incite on 2008-02-26
:~/driver$ ndiswrapper -l
***** : invalid driver!

HELP

---

### Post by kevdog on 2008-02-26
Please post the following:

sudo ls -la /etc/ndiswrapper

---

### Post by Incite on 2008-02-26
> **kevdog said:**
> Please post the following:

sudo ls -la /etc/ndiswrapper

total 20
drwxr-xr-x   3 root root  4096 2008-02-24 20:31 .
drwxr-xr-x 121 root root 12288 2008-02-26 20:23 ..
drwxr-xr-x   2 root root  4096 2008-02-24 20:31 *****

---

### Post by kevdog on 2008-02-26
So it seems like you have a file named *

Can you do the following
sudo rm -R /etc/ndiswrapper/*

And then see if this file is no longer listed?

---

### Post by mrobinson_sr on 2008-02-26
I am using the guide, and have just installed Kubuntu 7.10 to try and get my wireless adapter to work.  In the instructions I am instructed to place the ndiswrapper file in the ndiswrapper folder.  The folder does not appear in my list of folders.  I have the file on a usb drive.  I am assuming the ndiswrapper folder should be in the root directory.  When I created the ndiswrapper folder it created in my home directory.  I tried to move it to the root but was not permitted.  I am assuming that is a permissions issue.  So I went back to log on as root, however during the install I was not asked for a password for root.  does the program install a standard password for root??  And, am I correct in assuming the ndiswrapper directory needs to be in the root to work correctly?

Thank you.

---

### Post by kevdog on 2008-02-27
The ndiswrapper folder can be anywhere.  You need to have sudo privileges however so you need to know the root password.

---

### Post by mrobinson_sr on 2008-02-27
Shouldn't the install have asked me for a Root password?  It did ask for me to set up my personal username and password but not the password for root?

I was able to use the sudo command using the password I used for my personal usercode, but when I log off and log back on using root as the username there is no password that works?

---

### Post by kevdog on 2008-02-27
There is no root user perse like other linux systems.  At the command line, you can change user to root (or simply assign yourselves permanent root privileges) with the sudo su command.  

Yes during setup, the username you establish with the password, is the root password.  I believe you can change this later if you need too.  

This is kind of wandering off the topic of ndiswrapper installation.  Again if you follow the instructions as written, using sudo commands as appropriate, this procedure should work.  Its been time tested by many users.

---

### Post by Incite on 2008-02-27
sudo rm -R /etc/ndiswrapper/*
rm: cannot remove `/etc/ndiswrapper/*': No such file or directory

N

---

### Post by mrobinson_sr on 2008-02-27
KevDog:

I made my way through the Ndiswrapper with which I thought was rather uneventful.  I followed all the instructions and as far as I could see there were no errors.  However, after turning off the WEP on the Westel 327w DSL router/modem I am still not able to connect.  I am supplying the information below as I have seen others do.  by the way the wireless device is a Linksys WUSB54G Ver 4.  I used the V4 driver.

michael@michael-desktop:~$ **ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:C0:49:B4:1C:DB
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:9 Base address:0xb000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:592 errors:0 dropped:0 overruns:0 frame:0
          TX packets:592 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:43104 (42.0 KB)  TX bytes:43104 (42.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:12:17:75:90:77
          inet6 addr: fe80::212:17ff:fe75:9077/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2193 errors:0 dropped:0 overruns:0 frame:0
          TX packets:124 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:185317 (180.9 KB)  TX bytes:34187 (33.3 KB)

wlan0:ava Link encap:Ethernet  HWaddr 00:12:17:75:90:77
          inet addr:169.254.6.51  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-12-17-75-90-77-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

                                           


michael@michael-desktop:~$** lspci**
00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 02)
00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 04)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 04)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 04)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 04)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS
02:07.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)
02:0a.0 Communication controller: Conexant HCF 56k Data/Fax Modem (rev 08)
02:0b.0 Ethernet controller: Accton Technology Corporation EN-1216 Ethernet Adapter (rev 11)
                      


michael@michael-desktop:~$** lshw -c network**
Hardware Lister (lshw) - B.02.10
usage: lshw [-format] [-options ...]
       lshw -version

        -version        print program version (B.02.10)

format can be
        -html           output hardware tree as HTML
        -xml            output hardware tree as XML
        -short          output hardware paths
        -businfo        output bus information

options can be
        -class CLASS    only show a certain class of hardware
        -C CLASS        same as '-class CLASS'
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
        -quiet          don't display status


 michael@michael-desktop:~$ **iwlist**
Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency
              [interface] channel
              [interface] bitrate
              [interface] rate
              [interface] encryption
              [interface] keys
              [interface] power
              [interface] txpower
              [interface] retry
              [interface] ap
              [interface] accesspoints
              [interface] peers
              [interface] event
              [interface] auth
              [interface] wpakeys
              [interface] genie
              [interface] modulation

   michael@michael-desktop:~$ **iwlist scan**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results


michael@michael-desktop:~$** iwlist wlan0 scan**
wlan0     No scan results


Any assistance would be greatly appreciated.

Thank you.

---

### Post by kevdog on 2008-02-27
Can you post lsmod?

---

### Post by mrobinson_sr on 2008-02-28
Thank you.  Below is the lsmod display.


michael@michael-desktop:~$ ismod
bash: ismod: command not found
michael@michael-desktop:~$ lsmod
Module                  Size  Used by
isofs                  36412  0
udf                    87204  0
nls_iso8859_1           5120  0
nls_cp437               6784  0
vfat                   14080  0
fat                    54300  1 vfat
ipv6                  273892  8
rfcomm                 42136  2
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
r128                   41088  2
drm                    83348  3 r128
ppdev                  10244  0
speedstep_lib           6404  0
cpufreq_conservative     8072  0
cpufreq_ondemand        9612  0
cpufreq_stats           7232  0
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       2688  0
cpufreq_userspace       5280  0
button                  8976  0
ac                      6148  0
sbs                    19592  0
dock                   10656  0
video                  18060  0
container               5504  0
battery                11012  0
ndiswrapper           185240  0
lp                     12580  0
af_packet              24840  4
snd_ens1371            27680  1
gameport               16776  1 snd_ens1371
snd_ac97_codec        100644  1 snd_ens1371
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
arc4                    2944  2
snd_seq_dummy           4740  0
ecb                     4608  2
blkcipher               7556  1 ecb
snd_seq_oss            33152  0
rc80211_simple          6912  1
snd_seq_midi            9600  0
rt2500usb              22016  0
rt2x00usb              12032  1 rt2500usb
rt2x00lib              19584  2 rt2500usb,rt2x00usb
xpad                    9988  0
rfkill                  8208  1 rt2x00lib
mac80211              171016  3 rc80211_simple,rt2x00usb,rt2x00lib
snd_rawmidi            25728  2 snd_ens1371,snd_seq_midi
cfg80211                7304  1 mac80211
usb_storage            73024  0
ide_core              116804  1 usb_storage
usbhid                 29536  0
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
hid                    28928  1 usbhid
libusual               18448  1 usb_storage
input_polldev           5896  1 rt2x00lib
crc_itu_t               3072  1 rt2x00lib
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  12 snd_ens1371,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             37412  1
parport                37448  3 ppdev,lp,parport_pc
soundcore               8800  1 snd
pcspkr                  4224  0
serio_raw               8068  0
psmouse                39952  0
snd_page_alloc         11400  1 snd_pcm
intel_agp              25620  1
agpgart                35016  2 drm,intel_agp
iTCO_wdt               11940  0
iTCO_vendor_support     4868  1 iTCO_wdt
shpchp                 34580  0
pci_hotplug            32704  1 shpchp
evdev                  11136  4
ext3                  133896  1
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0
sr_mod                 17828  0
cdrom                  37536  1 sr_mod
sd_mod                 30336  3
ata_generic             8452  0
floppy                 60004  0
tulip                  53792  0
uhci_hcd               26640  0
usbcore               138632  9 ndiswrapper,rt2500usb,rt2x00usb,xpad,usb_storage,usbhid,libusual,uhci_hcd
ata_piix               17540  2
libata                125168  2 ata_generic,ata_piix
scsi_mod              147084  5 usb_storage,sg,sr_mod,sd_mod,libata
thermal                14344  0
processor              32072  1 thermal
fan                     5764  0
fuse                   47124  1
apparmor               40728  0
commoncap               8320  1 apparmor

---

### Post by kevdog on 2008-02-28
Here are the drivers associated with your usb device:
usbcore 138632 9 ndiswrapper,rt2500usb,rt2x00usb,xpad,usb_storage,u sbhid,libusual,uhci_hcd

Yes the ndiswrapper driver is loaded, but I think the rt2500usb or rt2x00usb device is taking precedent.  Why dont you try blacklisting these drivers:

echo "blacklist rt2500usb" | sudo tee -a /etc/modprobe.d/blacklist

echo "blacklist rt2x00usb" | sudo tee -a /etc/modprobe.d/blacklist

And then rebooting and see what you get.  Again your not specifically telling me all the information to help you. #1-you are using usb device, so lspci (list pci devices) is not going to help since your device is not going through the PCI bus, rather the USB controller directly connected to the southbridge on the motherboard.  lsusb (list usb device) would be more applicable in your situation.  #2 - You didn't do any research telling me the chipset of your device -- I believe it to be a rt2500 chipset.  ndiswrapper might work for you, however so would the linux serial monkey drivers.  Again providing as much information as possible would really help others beyond the proverbial "Things aren't working" and let me just post a bunch on info that Ive seen others list on other posts.  I understand linux is a pain to get going in terms of wireless, however with each command just try to understand what it does on the surface level.  This will greatly accelerate your learning curve, since it will give you some insight in to how linux is set up.  You will be able to transfer these skills to other things later to troubleshoot other problems with a reasonable degree of confidence.

---

### Post by mrobinson_sr on 2008-02-28
You sir are a wizard of the Linux world.  I changed to the first blacklist command (not sure what it does, but) and rebooted, then up the internet came through my WUSB54G Linisys.

Thank you for your patience and expertis:).

---

### Post by erginemr on 2008-02-28
To thank someone -> You can click on the blue ribbon/badge on the bottom right part of the post(s), whose author(s), you believe, has helped you fix your problem.

---

### Post by Incite on 2008-02-28
> **kevdog said:**
> So it seems like you have a file named *

Can you do the following
sudo rm -R /etc/ndiswrapper/*

And then see if this file is no longer listed?

rm: cannot remove `/etc/ndiswrapper/*': No such file or directory

---

### Post by kevdog on 2008-02-29
Do a search how to remove a file named *.  Ive seen this problem before, I cant remember the solution.

---

### Post by Incite on 2008-03-02
> **kevdog said:**
> Do a search how to remove a file named *.  Ive seen this problem before, I cant remember the solution.

1).Where would i search?

2).logical name: eth35

?????

3).When i click the internet icon and then click manuel config it no longer gives me the wireless option. I dont know why.

---

### Post by kevdog on 2008-03-02
Search the forums or google.

---

### Post by kevdog on 2008-03-02
Can you again post the results of the following command:

ls -la /etc/ndiswrapper


Try the following:
rm "*"

---

### Post by Incite on 2008-03-02
/etc/ndiswrapper:
total 16
drwxr-xr-x   2 root root  4096 2008-02-27 15:17 .
drwxr-xr-x 125 root root 12288 2008-03-02 09:57 ..


ndiswrapper:
total 216
drwxr-xr-x  4    4096 2008-03-02 10:02 .
drwxr-xr-x 49    4096 2008-03-02 10:19 ..
drwxr-xr-x  4    4096 2008-02-02 21:45 ndiswrapper-1.52
-rw-r--r--  1  198456 2008-02-02 21:45 ndiswrapper-1.52.tar.gz
drwxr-xr-x  5   4096 2008-02-25 19:10 ndiswrapper-svn

---

### Post by kevdog on 2008-03-02
Ok, great, you dont have the * file anymore.  Do you need to recompile or insert the driver?

---

### Post by Incite on 2008-03-02
i have no idea.

Can you tell me why the wireless option does not appear in my network options?

I still have the logical name eth35 i dont know why.

---

### Post by kevdog on 2008-03-02
I cant tell you why eth35 appears, but did you follow the steps to compile and insert the ndiswrapper kernel module?

---

### Post by Incite on 2008-03-03
yes i downloaded ndiswrapper-1.52.tar.gz and in all of the coding i pasted into the terminal i changed 1.48 to 1.52

I did this several times I deleted the ndiswrapper and put it back on and 
im at wits end.The wireless option still does not appear in the network options.

is there a way i can start from scratch?

---

### Post by kevdog on 2008-03-03
Yes there is, on the first page there are uninstallation instructions at the bottom!

---

### Post by Maxwell85 on 2008-03-05
Hello, I am new to Ubuntu, and to its command line interface, I have an understanding of using Sudo, etc, however when I go by the steps you've shown here, I get to the step where you type sudo make install, at this point it begins to run down the commands, then all of them become warnings and errors and finally it closes without finishing..  I have the required wireless drivers on the hard drive waiting to use Ndiswrapper, however Ive become so frustrated with this that I'm resorting to ask for help, nothing on the forums Ive found  have helped at all.  For clarification, the Ndiswrapper folder is in my profiles folder 

EX: home\joseph\ndiswrapper-1.52  

Drivers are in:

home\joseph\Drivers

Please tell me its something simple!

---

### Post by kevdog on 2008-03-05
What are the errors?

---

### Post by Maxwell85 on 2008-03-05
The errors I believe to be the source are that the drivers for the ndiswrapper are not being found, Ill post the exact code when I get home from class tonight.

---

### Post by Maxwell85 on 2008-03-05
Heres the errors, lots of em..

loadndisdriver.c:15:20: error: stdlib.h: No such file or directory 
loadndisdriver.c:16:19: error: stdio.h: No such file or directory 
loadndisdriver.c:17:19: error: errno.h: No such file or directory 
loadndisdriver.c:18:20: error: string.h: No such file or directory 
loadndisdriver.c:19:20: error: libgen.h: No such file or directory 
loadndisdriver.c:21:22: error: sys/mman.h: No such file or directory 
loadndisdriver.c:23:23: error: sys/types.h: No such file or directory 
loadndisdriver.c:24:23: error: sys/ioctl.h: No such file or directory 
loadndisdriver.c:25:22: error: sys/stat.h: No such file or directory 
loadndisdriver.c:26:20: error: unistd.h: No such file or directory 
loadndisdriver.c:27:19: error: fcntl.h: No such file or directory 
In file included from /usr/lib/gcc/x86_64-linux-gnu/4.1.3/include/syslimits.h:7, 
                 from /usr/lib/gcc/x86_64-linux-gnu/4.1.3/include/limits.h:11, 
                 from loadndisdriver.c:28: 
/usr/lib/gcc/x86_64-linux-gnu/4.1.3/include/limits.h:122:61: error: limits.h: No such file or directory 
loadndisdriver.c:29:19: error: ctype.h: No such file or directory 
loadndisdriver.c:30:20: error: dirent.h: No such file or directory 
loadndisdriver.c:31:20: error: syslog.h: No such file or directory 
loadndisdriver.c:34:25: error: linux/major.h: No such file or directory 
loadndisdriver.c:35:25: error: linux/ioctl.h: No such file or directory 
In file included from loadndisdriver.c:37: 
../driver/loader.h:24: error: expected specifier-qualifier-list before ‘size_t’ 
loadndisdriver.c: In function ‘load_file’: 
loadndisdriver.c:67: error: ‘size_t’ undeclared (first use in this function) 
loadndisdriver.c:67: error: (Each undeclared identifier is reported only once 
loadndisdriver.c:67: error: for each function it appears in.) 
loadndisdriver.c:67: error: expected ‘;’ before ‘size’ 
loadndisdriver.c:68: error: ‘NULL’ undeclared (first use in this function) 
loadndisdriver.c:69: error: storage size of ‘statbuf’ isn’t known 
loadndisdriver.c:71: warning: implicit declaration of function ‘basename’ 
loadndisdriver.c:71: warning: initialization makes pointer from integer without a cast 
loadndisdriver.c:73: warning: implicit declaration of function ‘open’ 
loadndisdriver.c:73: error: ‘O_RDONLY’ undeclared (first use in this function) 
loadndisdriver.c:75: warning: implicit declaration of function ‘syslog’ 
loadndisdriver.c:75: error: ‘LOG_KERN’ undeclared (first use in this function) 
loadndisdriver.c:75: error: ‘LOG_INFO’ undeclared (first use in this function) 
loadndisdriver.c:75: warning: implicit declaration of function ‘strerror’ 
loadndisdriver.c:75: error: ‘errno’ undeclared (first use in this function) 
loadndisdriver.c:76: error: ‘EINVAL’ undeclared (first use in this function) 
loadndisdriver.c:79: warning: implicit declaration of function ‘fstat’ 
loadndisdriver.c:81: warning: implicit declaration of function ‘close’ 
loadndisdriver.c:84: error: ‘size’ undeclared (first use in this function) 
loadndisdriver.c:86: warning: implicit declaration of function ‘mmap’ 
loadndisdriver.c:86: error: ‘PROT_READ’ undeclared (first use in this function) 
loadndisdriver.c:86: error: ‘MAP_PRIVATE’ undeclared (first use in this function) 
loadndisdriver.c:86: warning: assignment makes pointer from integer without a cast 
loadndisdriver.c:87: error: ‘MAP_FAILED’ undeclared (first use in this function) 
loadndisdriver.c:93: warning: implicit declaration of function ‘strncpy’ 
loadndisdriver.c:93: warning: incompatible implicit declaration of built-in function ‘strncpy’ 
loadndisdriver.c:95: error: ‘struct load_driver_file’ has no member named ‘size’ 
loadndisdriver.c:96: error: ‘struct load_driver_file’ has no member named ‘data’ 
loadndisdriver.c:69: warning: unused variable ‘statbuf’ 
loadndisdriver.c: In function ‘parse_setting_line’: 
loadndisdriver.c:109: warning: implicit declaration of function ‘isspace’ 
loadndisdriver.c:115: warning: implicit declaration of function ‘strchr’ 
loadndisdriver.c:115: warning: incompatible implicit declaration of built-in function ‘strchr’ 
loadndisdriver.c:115: error: ‘NULL’ undeclared (first use in this function) 
loadndisdriver.c:117: error: ‘LOG_KERN’ undeclared (first use in this function) 
loadndisdriver.c:117: error: ‘LOG_INFO’ undeclared (first use in this function) 
loadndisdriver.c:118: error: ‘EINVAL’ undeclared (first use in this function) 
loadndisdriver.c:138: warning: implicit declaration of function ‘strlen’ 
loadndisdriver.c:138: warning: incompatible implicit declaration of built-in function ‘strlen’ 
loadndisdriver.c: In function ‘read_conf_file’: 
loadndisdriver.c:150: error: storage size of ‘statbuf’ isn’t known 
loadndisdriver.c:151: error: ‘FILE’ undeclared (first use in this function) 
loadndisdriver.c:151: error: ‘config’ undeclared (first use in this function) 
loadndisdriver.c:157: warning: implicit declaration of function ‘lstat’ 
loadndisdriver.c:158: error: ‘LOG_KERN’ undeclared (first use in this function) 
loadndisdriver.c:158: error: ‘LOG_INFO’ undeclared (first use in this function) 
loadndisdriver.c:158: error: ‘errno’ undeclared (first use in this function) 
loadndisdriver.c:160: error: ‘EINVAL’ undeclared (first use in this function) 
loadndisdriver.c:163: warning: implicit declaration of function ‘sscanf’ 
loadndisdriver.c:163: warning: incompatible implicit declaration of built-in function ‘sscanf’ 
loadndisdriver.c:178: warning: implicit declaration of function ‘fopen’ 
loadndisdriver.c:178: error: ‘NULL’ undeclared (first use in this function) 
loadndisdriver.c:182: warning: implicit declaration of function ‘fgets’ 
loadndisdriver.c:194: warning: incompatible implicit declaration of built-in function ‘strncpy’ 
loadndisdriver.c:205: warning: implicit declaration of function ‘fclose’ 
loadndisdriver.c:150: warning: unused variable ‘statbuf’ 
loadndisdriver.c: In function ‘load_bin_file’: 
loadndisdriver.c:217: error: ‘LOG_KERN’ undeclared (first use in this function) 
loadndisdriver.c:217: error: ‘LOG_INFO’ undeclared (first use in this function) 
loadndisdriver.c:219: warning: implicit declaration of function ‘tolower’ 
loadndisdriver.c:221: warning: implicit declaration of function ‘chdir’ 
loadndisdriver.c:222: error: ‘errno’ undeclared (first use in this function) 
loadndisdriver.c:224: error: ‘EINVAL’ undeclared (first use in this function) 
loadndisdriver.c:230: warning: incompatible implicit declaration of built-in function ‘strncpy’ 
loadndisdriver.c:232: warning: implicit declaration of function ‘ioctl’ 
loadndisdriver.c:232: warning: implicit declaration of function ‘_IOW’ 
loadndisdriver.c:232: error: expected expression before ‘struct’ 
loadndisdriver.c: In function ‘load_driver’: 
loadndisdriver.c:249: error: ‘DIR’ undeclared (first use in this function) 
loadndisdriver.c:249: error: ‘driver_dir’ undeclared (first use in this function) 
loadndisdriver.c:251: error: ‘NULL’ undeclared (first use in this function) 
loadndisdriver.c:255: error: ‘LOG_KERN’ undeclared (first use in this function) 
loadndisdriver.c:255: error: ‘LOG_INFO’ undeclared (first use in this function) 
loadndisdriver.c:257: error: ‘errno’ undeclared (first use in this function) 
loadndisdriver.c:259: error: ‘EINVAL’ undeclared (first use in this function) 
loadndisdriver.c:261: warning: implicit declaration of function ‘opendir’ 
loadndisdriver.c:267: warning: implicit declaration of function ‘malloc’ 
loadndisdriver.c:267: warning: incompatible implicit declaration of built-in function ‘malloc’ 
loadndisdriver.c:271: warning: implicit declaration of function ‘memset’ 
loadndisdriver.c:271: warning: incompatible implicit declaration of built-in function ‘memset’ 
loadndisdriver.c:272: warning: incompatible implicit declaration of built-in function ‘strncpy’ 
loadndisdriver.c:280: warning: implicit declaration of function ‘readdir’ 
loadndisdriver.c:280: warning: assignment makes pointer from integer without a cast 
loadndisdriver.c:282: error: storage size of ‘statbuf’ isn’t known 
loadndisdriver.c:284: error: dereferencing pointer to incomplete type 
loadndisdriver.c:287: warning: implicit declaration of function ‘stat’ 
loadndisdriver.c:287: error: dereferencing pointer to incomplete type 
loadndisdriver.c:288: warning: implicit declaration of function ‘S_ISREG’ 
loadndisdriver.c:289: error: dereferencing pointer to incomplete type 
loadndisdriver.c:294: warning: incompatible implicit declaration of built-in function ‘strlen’ 
loadndisdriver.c:294: error: dereferencing pointer to incomplete type 
loadndisdriver.c:296: warning: implicit declaration of function ‘strcasecmp’ 
loadndisdriver.c:296: error: dereferencing pointer to incomplete type 
loadndisdriver.c:299: error: dereferencing pointer to incomplete type 
loadndisdriver.c:302: error: dereferencing pointer to incomplete type 
loadndisdriver.c:303: error: dereferencing pointer to incomplete type 
loadndisdriver.c:305: error: dereferencing pointer to incomplete type 
loadndisdriver.c:311: error: dereferencing pointer to incomplete type 
loadndisdriver.c:312: error: dereferencing pointer to incomplete type 
loadndisdriver.c:313: warning: implicit declaration of function ‘strcpy’ 
loadndisdriver.c:313: warning: incompatible implicit declaration of built-in function ‘strcpy’ 
loadndisdriver.c:314: error: dereferencing pointer to incomplete type 
loadndisdriver.c:317: error: ‘struct load_driver_file’ has no member named ‘size’ 
loadndisdriver.c:318: error: ‘struct load_driver_file’ has no member named ‘data’ 
loadndisdriver.c:321: error: dereferencing pointer to incomplete type 
loadndisdriver.c:282: warning: unused variable ‘statbuf’ 
loadndisdriver.c:344: error: expected expression before ‘struct’ 
loadndisdriver.c:346: warning: implicit declaration of function ‘closedir’ 
loadndisdriver.c:348: warning: implicit declaration of function ‘free’ 
loadndisdriver.c:355: warning: implicit declaration of function ‘munmap’ 
loadndisdriver.c:355: error: ‘struct load_driver_file’ has no member named ‘data’ 
loadndisdriver.c:355: error: ‘struct load_driver_file’ has no member named ‘size’ 
loadndisdriver.c:357: error: ‘struct load_driver_file’ has no member named ‘data’ 
loadndisdriver.c:357: error: ‘struct load_driver_file’ has no member named ‘size’ 
loadndisdriver.c: In function ‘get_device’: 
loadndisdriver.c:367: error: storage size of ‘statbuf’ isn’t known 
loadndisdriver.c:370: error: ‘LOG_KERN’ undeclared (first use in this function) 
loadndisdriver.c:370: error: ‘LOG_INFO’ undeclared (first use in this function) 
loadndisdriver.c:373: error: ‘errno’ undeclared (first use in this function) 
loadndisdriver.c:374: error: ‘EINVAL’ undeclared (first use in this function) 
loadndisdriver.c:376: warning: implicit declaration of function ‘snprintf’ 
loadndisdriver.c:376: warning: incompatible implicit declaration of built-in function ‘snprintf’ 
loadndisdriver.c:407: warning: incompatible implicit declaration of built-in function ‘strncpy’ 
loadndisdriver.c:367: warning: unused variable ‘statbuf’ 
loadndisdriver.c: In function ‘load_device’: 
loadndisdriver.c:419: error: ‘DIR’ undeclared (first use in this function) 
loadndisdriver.c:419: error: ‘dir’ undeclared (first use in this function) 
loadndisdriver.c:423: error: ‘LOG_KERN’ undeclared (first use in this function) 
loadndisdriver.c:423: error: ‘LOG_INFO’ undeclared (first use in this function) 
loadndisdriver.c:424: warning: incompatible implicit declaration of built-in function ‘memset’ 
loadndisdriver.c:426: error: ‘errno’ undeclared (first use in this function) 
loadndisdriver.c:427: error: ‘EINVAL’ undeclared (first use in this function) 
loadndisdriver.c:429: error: ‘NULL’ undeclared (first use in this function) 
loadndisdriver.c:434: warning: assignment makes pointer from integer without a cast 
loadndisdriver.c:435: error: dereferencing pointer to incomplete type 
loadndisdriver.c:436: error: dereferencing pointer to incomplete type 
loadndisdriver.c:439: error: dereferencing pointer to incomplete type 
loadndisdriver.c:447: error: expected expression before ‘struct’ 
loadndisdriver.c: In function ‘get_ioctl_device’: 
loadndisdriver.c:464: error: ‘FILE’ undeclared (first use in this function) 
loadndisdriver.c:464: error: ‘proc_misc’ undeclared (first use in this function) 
loadndisdriver.c:472: warning: implicit declaration of function ‘strstr’ 
loadndisdriver.c:472: warning: incompatible implicit declaration of built-in function ‘strstr’ 
loadndisdriver.c:473: warning: implicit declaration of function ‘strtol’ 
loadndisdriver.c:473: error: ‘NULL’ undeclared (first use in this function) 
loadndisdriver.c:483: error: ‘LOG_KERN’ undeclared (first use in this function) 
loadndisdriver.c:483: error: ‘LOG_INFO’ undeclared (first use in this function) 
loadndisdriver.c:488: warning: implicit declaration of function ‘unlink’ 
loadndisdriver.c:489: warning: implicit declaration of function ‘mknod’ 
loadndisdriver.c:489: error: ‘S_IFCHR’ undeclared (first use in this function) 
loadndisdriver.c:489: error: ‘MISC_MAJOR’ undeclared (first use in this function) 
loadndisdriver.c:490: error: ‘errno’ undeclared (first use in this function) 
loadndisdriver.c:495: error: ‘O_RDONLY’ undeclared (first use in this function) 
loadndisdriver.c: In function ‘main’: 
loadndisdriver.c:511: warning: implicit declaration of function ‘openlog’ 
loadndisdriver.c:511: error: ‘LOG_PERROR’ undeclared (first use in this function) 
loadndisdriver.c:511: error: ‘LOG_CONS’ undeclared (first use in this function) 
loadndisdriver.c:511: error: ‘LOG_KERN’ undeclared (first use in this function) 
loadndisdriver.c:511: error: ‘LOG_DEBUG’ undeclared (first use in this function) 
loadndisdriver.c:513: error: ‘LOG_INFO’ undeclared (first use in this function) 
loadndisdriver.c:515: warning: implicit declaration of function ‘strncmp’ 
loadndisdriver.c:517: warning: implicit declaration of function ‘printf’ 
loadndisdriver.c:517: warning: incompatible implicit declaration of built-in function ‘printf’ 
loadndisdriver.c:527: warning: implicit declaration of function ‘atoi’ 
loadndisdriver.c:542: warning: implicit declaration of function ‘atof’ 
loadndisdriver.c:549: warning: implicit declaration of function ‘strcmp’ 
loadndisdriver.c:556: warning: incompatible implicit declaration of built-in function ‘sscanf’ 
loadndisdriver.c:590: warning: implicit declaration of function ‘closelog’ 
make[1]: *** [loadndisdriver] Error 1 
make[1]: Leaving directory `/home/joseph/ndiswrapper-1.52/utils' 
make: *** [all] Error 2

---

### Post by kevdog on 2008-03-05
You have to install the linux header files.

sudo aptitude install linux-headers-`uname -r`

---

### Post by Maxwell85 on 2008-03-05
The headers installed correctly, though the command   /make still has all the error messages.

---

### Post by kevdog on 2008-03-06
You have installed build essential package??

I might try either installing from svn, or trying a different ndiswrapper version.  Something is definitely strange here.

---

### Post by Maxwell85 on 2008-03-07
I reinstalled the build essential package, this allowed me to install Ndiswrapper!  So that part is taken care of now.  I used Ndiswrapper to install the driver and got error messages having to do with the driver being 32 bit, while the kernal is 64 bit on my Pc.  So, I uninstalled the 32 bit driver, and found a 64 bit (its for vista, that may be noteworthy) Wusb300n driver.  The driver is installed, however I cannot set up the internet still.  Ill post more info once I get back on Ubuntu and wrestle with it some more :).  Thank you for your help thus far!  I really appreciate it!!

---

### Post by kevdog on 2008-03-07
Im not 100% certain, however I dont think Vista drivers will work -- you will need the 64 bit winxp driver.

---

### Post by Maxwell85 on 2008-03-07
Ok, I will look for it.

---

### Post by Maxwell85 on 2008-03-07
Unfortunately, it seems linksys does not have a driver for this, if I cant get 
Vistas, or the normal one to work I'm effed :(

---

### Post by kevdog on 2008-03-07
I would probably concur on that one.  That chipset you have is relatively new -- that is the problem.

---

### Post by Maxwell85 on 2008-03-08
Yes, when is the next release of Ubuntu? lol

---

### Post by kevdog on 2008-03-08
The next release is in April -- Hardy Heron -- and it includes for broadcom cards the newer b43 driver rather than the bcm43xx driver.  Bad news for you however is that your new chipset isnt even on the horizon with the b43 driver.  Maybe someday, but it will definitely not be fixed with the standard next release unless a third party releases a patch.

---

### Post by nocturnalsixer on 2008-03-10
Im sorry to bother you with this same old subject that keep coming up.  i keep getting these messages  after doing everything and ndiswrapper install was fine it even verified then i get this message after typing in   "ndiswrapper -l"   thanks for taking time to read this first part.



[    0.000000] ACPI: SSDT 6FF64CF6, 0206 (r1 PTLTD  POWERNOW  6040000  LTP        1)
[    0.000000] ACPI: MCFG 6FF64EFC, 003C (r1 Nvidia NVDAACPI  6040000 NVDA        0)
[    0.000000] ACPI: HPET 6FF64F38, 0038 (r1 PTLTD  HPETTBL   6040000  LTP        1)
[    0.000000] ACPI: APIC 6FF64F70, 0068 (r1 PTLTD       APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT 6FF64FD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000006ff50000
[    0.000000] Entering add_active_range(0, 0, 158) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 458576) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000006ff50000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      158
[    0.000000]     0:      256 ->   458576
[    0.000000] On node 0 totalpages: 458478
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1127 pages reserved
[    0.000000]   DMA zone: 2815 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 6213 pages used for memmap
[    0.000000]   DMA32 zone: 448267 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009e000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000d2000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d2000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34696 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 451082
[    0.000000] Kernel command line: root=UUID=7ece2352-c89a-4fe9-a5a8-0725bcc60ee8 ro quiet splashall_generic_ide
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] Marking TSC unstable due to TSCs unsynchronized
[   16.514267] time.c: Detected 1900.251 MHz processor.
[   16.517967] Console: colour VGA+ 80x25
[   16.517984] Checking aperture...
[   16.517988] CPU 0: aperture @ 360000000 size 32 MB
[   16.517990] Aperture too small (32 MB)
[   16.524159] No AGP bridge found
[   16.540130] Memory: 1796964k/1834304k available (2274k kernel code, 36948k reserved, 1185k data, 296k init)
[   16.540179] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   16.617471] Calibrating delay using timer specific routine.. 3804.27 BogoMIPS (lpj=7608549)
[   16.617503] Security Framework v1.0.0 initialized
[   16.617509] SELinux:  Disabled at boot.
[   16.617676] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   16.618799] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   16.619345] Mount-cache hash table entries: 256
[   16.619475] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   16.619477] CPU: L2 Cache: 512K (64 bytes/line)
[   16.619481] CPU 0/0 -> Node 0
[   16.619483] CPU: Physical Processor ID: 0
[   16.619484] CPU: Processor Core ID: 0
[   16.619502] SMP alternatives: switching to UP code
[   16.619747] Early unpacking initramfs... done
[   16.925841] ACPI: Core revision 20070126
[   16.925903] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   17.491606] Using local APIC timer interrupts.
[   17.544148] result 12501656
[   17.544150] Detected 12.501 MHz APIC timer.
[   17.548016] SMP alternatives: switching to SMP code
[   17.548134] Booting processor 1/2 APIC 0x1
[   17.558579] Initializing CPU#1
[   17.636170] Calibrating delay using timer specific routine.. 3800.60 BogoMIPS (lpj=7601211)
[   17.636177] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   17.636179] CPU: L2 Cache: 512K (64 bytes/line)
[   17.636182] CPU 1/1 -> Node 0
[   17.636184] CPU: Physical Processor ID: 0
[   17.636185] CPU: Processor Core ID: 1
[   17.636289] AMD Turion(tm) 64 X2 Mobile Technology TL-58 stepping 01
[   17.639811] Brought up 2 CPUs
[   18.454179] migration_cost=179
[   18.454008] NET: Registered protocol family 16
[   18.454096] ACPI: bus type pci registered
[   18.454101] PCI: Using configuration type 1
[   18.455154] ACPI: EC: Look up EC in DSDT
[   18.455593] ACPI: EC: GPE=0x10, ports=0x66, 0x62
[   18.457987] ACPI: Interpreter enabled
[   18.457989] ACPI: (supports S0 S3 S4 S5)
[   18.458005] ACPI: Using IOAPIC for interrupt routing
[   18.524655] ACPI: EC: GPE=0x10, ports=0x66, 0x62
[   18.524705] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   18.524713] PCI: Probing PCI hardware (bus 00)
[   18.525540] PCI: Transparent bridge - 0000:00:08.0
[   18.525726] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   18.525809] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[   18.525828] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[   18.525856] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[   18.556707] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 11) *10
[   18.556915] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 *11)
[   18.557117] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 11) *0, disabled.
[   18.557319] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 11) *0, disabled.
[   18.557527] ACPI: PCI Interrupt Link [LK1E] (IRQs 16) *0, disabled.
[   18.557729] ACPI: PCI Interrupt Link [LK2E] (IRQs 17) *0, disabled.
[   18.557932] ACPI: PCI Interrupt Link [LK3E] (IRQs 18) *0, disabled.
[   18.558134] ACPI: PCI Interrupt Link [LK4E] (IRQs 19) *10
[   18.558336] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *10
[   18.558539] ACPI: PCI Interrupt Link [LUS0] (IRQs 20 21 22 23) *11
[   18.558743] ACPI: PCI Interrupt Link [LUS2] (IRQs 20 21 22 23) *7
[   18.558951] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *11
[   18.559154] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *10
[   18.559357] ACPI: PCI Interrupt Link [LGPU] (IRQs 17) *10
[   18.559559] ACPI: PCI Interrupt Link [LPID] (IRQs 20 21 22 23) *0, disabled.
[   18.559762] ACPI: PCI Interrupt Link [LSI0] (IRQs 20 21 22 23) *5
[   18.559971] ACPI: PCI Interrupt Link [Z00N] (IRQs 20 21 22 23) *10
[   18.560179] ACPI: PCI Interrupt Link [Z00O] (IRQs 20 21 22 23) *11
[   18.560383] ACPI: PCI Interrupt Link [LPMU] (IRQs 18) *11
[   18.560484] Linux Plug and Play Support v0.97 (c) Adam Belay
[   18.560498] pnp: PnP ACPI init
[   18.560509] ACPI: bus type pnp registered
[   18.591549] pnp: PnP ACPI: found 13 devices
[   18.591552] ACPI: ACPI bus type pnp unregistered
[   18.591610] PCI: Using ACPI for IRQ routing
[   18.591613] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   18.591707] NET: Registered protocol family 8
[   18.591710] NET: Registered protocol family 20
[   18.591781] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[   18.591786] hpet0: 3 32-bit timers, 25000000 Hz
[   18.592851] pnp: 00:07: iomem range 0xe0000000-0xefffffff could not be reserved
[   18.592857] pnp: 00:0a: ioport range 0x1000-0x107f has been reserved
[   18.592860] pnp: 00:0a: ioport range 0x1080-0x10ff has been reserved
[   18.592863] pnp: 00:0a: ioport range 0x1400-0x147f has been reserved
[   18.592866] pnp: 00:0a: ioport range 0x1480-0x14ff has been reserved
[   18.592869] pnp: 00:0a: ioport range 0x1800-0x187f has been reserved
[   18.592871] pnp: 00:0a: ioport range 0x1880-0x18ff has been reserved
[   18.592877] pnp: 00:0c: iomem range 0xffc00000-0xffffffff could not be reserved
[   18.592881] pnp: 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[   18.592885] pnp: 00:0c: iomem range 0xfee00000-0xfeefffff could not be reserved
[   18.592888] pnp: 00:0c: iomem range 0xfed00000-0xfed00fff has been reserved
[   18.593181] PCI: Bridge: 0000:00:08.0
[   18.593183]   IO window: disabled.
[   18.593187]   MEM window: f2300000-f23fffff
[   18.593190]   PREFETCH window: disabled.
[   18.593193] PCI: Bridge: 0000:00:0c.0
[   18.593195]   IO window: 4000-4fff
[   18.593198]   MEM window: f2000000-f21fffff
[   18.593201]   PREFETCH window: f2800000-f29fffff
[   18.593204] PCI: Bridge: 0000:00:0d.0
[   18.593205]   IO window: disabled.
[   18.593208]   MEM window: f2200000-f22fffff
[   18.593210]   PREFETCH window: disabled.
[   18.593220] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   18.593228] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   18.593234] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   18.593300] NET: Registered protocol family 2
[   18.594609] Time: hpet clocksource has been installed.
[   18.643484] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   18.644283] TCP established hash table entries: 262144 (order: 10, 6291456 bytes)
[   18.647383] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   18.647950] TCP: Hash tables configured (established 262144 bind 65536)
[   18.647954] TCP reno registered
[   18.664087] checking if image is initramfs... it is
[   19.261241] Freeing initrd memory: 7164k freed
[   19.265187] Simple Boot Flag at 0x36 set to 0x1
[   19.265778] audit: initializing netlink socket (disabled)
[   19.265789] audit(1205101341.180:1): initialized
[   19.267977] VFS: Disk quotas dquot_6.5.1
[   19.268032] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   19.268122] io scheduler noop registered
[   19.268124] io scheduler anticipatory registered
[   19.268126] io scheduler deadline registered
[   19.268222] io scheduler cfq registered (default)
[   19.269549] Boot video device is 0000:00:12.0
[   19.269723] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   19.269745] assign_interrupt_mode Found MSI capability
[   19.269748] Allocate Port Service[0000:00:0c.0:pcie00]
[   19.269815] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   19.269835] assign_interrupt_mode Found MSI capability
[   19.269838] Allocate Port Service[0000:00:0d.0:pcie00]
[   19.296719] Real Time Clock Driver v1.12ac
[   19.296936] hpet_resources: 0xfed00000 is busy
[   19.296960] Linux agpgart interface v0.102 (c) Dave Jones
[   19.296962] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   19.298120] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   19.298252] input: Macintosh mouse button emulation as /class/input/input0
[   19.298331] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   19.334048] serio: i8042 KBD port at 0x60,0x64 irq 1
[   19.334054] serio: i8042 AUX port at 0x60,0x64 irq 12
[   19.334216] mice: PS/2 mouse device common for all mice
[   19.334344] TCP cubic registered
[   19.336714] NET: Registered protocol family 1
[   19.336933] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   19.336945] Freeing unused kernel memory: 296k freed
[   19.362843] input: AT Translated Set 2 keyboard as /class/input/input1
[   19.423595] SCSI subsystem initialized
[   19.429229] libata version 2.21 loaded.
[   19.430595] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   19.430726] scsi0 : ata_generic
[   19.430802] scsi1 : ata_generic
[   19.430883] ata1: PATA max UDMA/100 cmd 0x00000000000101f0 ctl 0x00000000000103f6 bmdma 0x00000000000130c0 irq 14
[   19.430887] ata2: PATA max UDMA/100 cmd 0x0000000000010170 ctl 0x0000000000010376 bmdma 0x00000000000130c8 irq 15
[   19.749654] ata1.00: ATAPI: HL-DT-ST DVDRAM GSA-T20N, WP03, max UDMA/33
[   19.749660] ata1.00: configured for UDMA/33
[   19.910793] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T20N  WP03 PQ: 0 ANSI: 5
[   19.911288] ACPI: PCI Interrupt Link [LSI0] enabled at IRQ 23
[   19.911298] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LSI0] -> GSI 23 (level, low) -> IRQ 23
[   19.911332] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   19.911381] scsi2 : ata_generic
[   19.911458] scsi3 : ata_generic
[   19.911571] ata3: PATA max UDMA/100 cmd 0x00000000000130f0 ctl 0x00000000000130e6 bmdma 0x00000000000130d0 irq 23
[   19.911576] ata4: PATA max UDMA/100 cmd 0x00000000000130e8 ctl 0x00000000000130e2 bmdma 0x00000000000130d8 irq 23
[   20.073173] ata3.00: ATA-7: TOSHIBA MK1637GSX, DL050J, max UDMA/100
[   20.073176] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   20.073180] ata3.00: configured for PIO
[   20.230537] scsi 2:0:0:0: Direct-Access     ATA      TOSHIBA MK1637GS DL05 PQ: 0 ANSI: 5
[   21.342726] AppArmor: AppArmor initialized<5>audit(1205101343.260:2):  type=1505 info="AppArmor initialized" pid=1295
[   21.350273] fuse init (API version 7.8)
[   21.355761] Failure registering capabilities with primary security module.
[   21.388683] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   21.388689] ACPI: Processor [CPU0] (supports 8 throttling states)
[   21.388714] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   21.388725] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   21.420340] ACPI Exception (thermal-0400): AE_NOT_FOUND, Invalid active threshold [0] [20070126]
[   21.433247] ACPI: Thermal Zone [THRM] (53 C)
[   21.944472] usbcore: registered new interface driver usbfs
[   21.944501] usbcore: registered new interface driver hub
[   21.944526] usbcore: registered new device driver usb
[   21.946036] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[   21.946048] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [LUS2] -> GSI 22 (level, low) -> IRQ 22
[   21.946229] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   21.946237] ehci_hcd 0000:00:02.1: EHCI Host Controller
[   21.946405] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[   21.946440] ehci_hcd 0000:00:02.1: debug port 1
[   21.946444] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[   21.946457] ehci_hcd 0000:00:02.1: irq 22, io mem 0xf2689000
[   21.946465] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   21.946572] usb usb1: configuration #1 chosen from 1 choice
[   21.946599] hub 1-0:1.0: USB hub found
[   21.946606] hub 1-0:1.0: 5 ports detected
[   21.972389] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   21.975605] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[   21.991965] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   21.991975] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   22.052638] ACPI: PCI Interrupt Link [Z00O] enabled at IRQ 21
[   22.052652] ACPI: PCI Interrupt 0000:00:04.1[B] -> Link [Z00O] -> GSI 21 (level, low) -> IRQ 21
[   22.052835] PCI: Setting latency timer of device 0000:00:04.1 to 64
[   22.052851] ehci_hcd 0000:00:04.1: EHCI Host Controller
[   22.052907] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2
[   22.052942] ehci_hcd 0000:00:04.1: debug port 1
[   22.052947] PCI: cache line size of 64 is not supported by device 0000:00:04.1
[   22.052959] ehci_hcd 0000:00:04.1: irq 21, io mem 0xf2689400
[   22.052967] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   22.053062] usb usb2: configuration #1 chosen from 1 choice
[   22.053089] hub 2-0:1.0: USB hub found
[   22.053096] hub 2-0:1.0: 5 ports detected
[   22.159485] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 20
[   22.159499] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LUS0] -> GSI 20 (level, low) -> IRQ 20
[   22.159689] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   22.159697] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   22.159753] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3
[   22.159777] ohci_hcd 0000:00:02.0: irq 20, io mem 0xf2686000
[   22.182045] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   22.182051] Uniform CD-ROM driver Revision: 3.20
[   22.182095] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   22.187176] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   22.187358] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[   22.214389] usb usb3: configuration #1 chosen from 1 choice
[   22.214425] hub 3-0:1.0: USB hub found
[   22.214435] hub 3-0:1.0: 5 ports detected
[   22.289585] usb 1-3: new high speed USB device using ehci_hcd and address 2
[   22.316581] ACPI: PCI Interrupt Link [Z00N] enabled at IRQ 23
[   22.316587] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [Z00N] -> GSI 23 (level, low) -> IRQ 23
[   22.316770] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   22.316778] ohci_hcd 0000:00:04.0: OHCI Host Controller
[   22.316839] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 4
[   22.316859] ohci_hcd 0000:00:04.0: irq 23, io mem 0xf2687000
[   22.374101] usb usb4: configuration #1 chosen from 1 choice
[   22.374128] hub 4-0:1.0: USB hub found
[   22.374137] hub 4-0:1.0: 5 ports detected
[   22.477111] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 22
[   22.477117] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LMAC] -> GSI 22 (level, low) -> IRQ 22
[   22.477124] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   22.477134] forcedeth: using HIGHDMA
[   22.483938] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   22.483952] sd 2:0:0:0: [sda] Write Protect is off
[   22.483955] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   22.483970] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.484029] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   22.484038] sd 2:0:0:0: [sda] Write Protect is off
[   22.484041] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   22.484054] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.484059]  sda: sda1 sda2 < sda5 sda6 >
[   22.535973] sd 2:0:0:0: [sda] Attached SCSI disk
[   22.716402] usb 1-3: configuration #1 chosen from 1 choice
[   22.854182] Attempting manual resume
[   22.854186] swsusp: Resume From Partition 8:5
[   22.854188] PM: Checking swsusp image.
[   22.854835] PM: Resume from disk failed.
[   22.995550] eth0: forcedeth.c: subsystem: 01025:0126 bound to 0000:00:0a.0
[   22.996127] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 11
[   22.996139] ACPI: PCI Interrupt 0000:01:04.0[A] -> Link [LNK1] -> GSI 11 (level, low) -> IRQ 11
[   23.048282] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[11]  MMIO=[f2300000-f23007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   24.320802] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f79ba4029a0]
[   37.276169] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   37.309589] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   37.376922] ath_hal: module license 'Proprietary' taints kernel.
[   37.377765] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   37.476882] input: PC Speaker as /class/input/input2
[   37.841753] wlan: 0.8.4.2 (0.9.3.2)
[   38.064541] input: PS/2 Mouse as /class/input/input3
[   38.095373] input: AlpsPS/2 ALPS GlidePoint as /class/input/input4
[   39.489340] ACPI: PCI Interrupt Link [LGPU] enabled at IRQ 17
[   39.489355] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LGPU] -> GSI 17 (level, low) -> IRQ 17
[   39.489362] PCI: Setting latency timer of device 0000:00:12.0 to 64
[   39.489562] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  169.12  Thu Feb 14 17:51:09 PST 2008
[   39.509043] Linux video capture interface: v2.00
[   39.651964] ath_pci: 0.9.4.5 (0.9.3.2)
[   39.652972] ACPI: PCI Interrupt Link [LK4E] enabled at IRQ 19
[   39.652984] ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [LK4E] -> GSI 19 (level, low) -> IRQ 19
[   39.652994] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   39.680517] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
[   39.680534] ACPI: PCI interrupt for device 0000:05:00.0 disabled
[   39.698410] sdhci: Secure Digital Host Controller Interface driver
[   39.698415] sdhci: Copyright(c) Pierre Ossman
[   39.698488] sdhci: SDHCI controller found at 0000:01:04.1 [1180:0822] (rev 22)
[   39.698855] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 11
[   39.698859] ACPI: PCI Interrupt 0000:01:04.1[B] -> Link [LNK2] -> GSI 11 (level, low) -> IRQ 11
[   39.699171] mmc0: SDHCI at 0xf2300800 irq 11 DMA
[   39.880445] uvcvideo: Found UVC 1.00 device Acer Crystal Eye webcam  (5986:0102)
[   40.047218] usbcore: registered new interface driver uvcvideo
[   40.047223] USB Video Class driver (v0.1.0)
[   40.106973] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   40.106980] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [LAZA] -> GSI 21 (level, low) -> IRQ 21
[   40.107202] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   41.233619] lp: driver loaded but no devices found
[   41.381330] ndiswrapper version 1.45 loaded (smp=yes)
[   41.523235] ndiswrapper (link_pe_images:577): fixing KI_USER_SHARED_DATA address in the driver
[   41.524927] ndiswrapper: driver net5211 (,06/21/2007,5.3.0.56) loaded
[   41.525171] PCI: Enabling device 0000:05:00.0 (0000 -> 0002)
[   41.525181] ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [LK4E] -> GSI 19 (level, low) -> IRQ 19
[   41.525225] ndiswrapper (ZwClose:2247): closing handle 0x0 not implemented
[   41.525360] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   41.526173] ndiswrapper (NdisWriteErrorLogEntry:192): log: C0001389, count: 4, return_address: ffffffff88c0064e
[   41.526179] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0x67877400
[   41.526182] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0x28
[   41.526185] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0xb05000
[   41.526187] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0xb05000
[   41.526263] ndiswrapper (mp_init:263): couldn't initialize device: C000009A
[   41.526270] ndiswrapper (pnp_start_device:440): Windows driver couldn't initialize the device (C0000001)
[   41.526283] ndiswrapper (mp_halt:305): device ffff81006cfee780 is not initialized - not halting
[   41.526293] ndiswrapper: device eth%d removed
[   41.526305] ACPI: PCI interrupt for device 0000:05:00.0 disabled
[   41.526316] ndiswrapper: probe of 0000:05:00.0 failed with error -22
[   41.526370] usbcore: registered new interface driver ndiswrapper
[   41.585617] Adding 4883720k swap on /dev/sda5.  Priority:-1 extents:1 across:4883720k
[   43.642785] ACPI: AC Adapter [ACAD] (on-line)
[   43.841678] ACPI: Battery Slot [BAT1] (battery present)
[   43.859133] No dock devices found.
[   43.914994] input: Power Button (FF) as /class/input/input5
[   43.915297] ACPI: Power Button (FF) [PWRF]
[   43.944391] input: Lid Switch as /class/input/input6
[   43.944442] ACPI: Lid Switch [LID]
[   43.944512] input: Sleep Button (CM) as /class/input/input7
[   43.944531] ACPI: Sleep Button (CM) [SLPB]
[   43.944619] input: Power Button (CM) as /class/input/input8
[   43.944635] ACPI: Power Button (CM) [PWRB]
[   44.342644] powernow-k8: Found 2 AMD Turion(tm) 64 X2 Mobile Technology TL-58 processors (version 2.00.00)
[   44.343014] powernow-k8:    0 : fid 0xb (1900 MHz), vid 0x12
[   44.343020] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x13
[   44.343023] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x14
[   44.343025] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x1e
[   45.730723] ppdev: user-space parallel port driver
[   45.959058] audit(1205119368.981:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5082 profile="/usr/sbin/cupsd"
[   47.763860] Failure registering capabilities with primary security module.
[   48.004130] Bluetooth: Core ver 2.11
[   48.004193] NET: Registered protocol family 31
[   48.004195] Bluetooth: HCI device and connection manager initialized
[   48.004199] Bluetooth: HCI socket layer initialized
[   48.017338] Bluetooth: L2CAP ver 2.8
[   48.017344] Bluetooth: L2CAP socket layer initialized
[   48.135363] Bluetooth: RFCOMM socket layer initialized
[   48.135384] Bluetooth: RFCOMM TTY layer initialized
[   48.135387] Bluetooth: RFCOMM ver 1.8
[   51.386742] NET: Registered protocol family 17
[   71.410743] uvcvideo: Failed to query (130) UVC control 1 (unit 0) : 2 (exp. 26).
[  113.740649] NET: Registered protocol family 10
[  113.740766] lo: Disabled Privacy Extensions
[  120.423011] eth0: no IPv6 routers present
[  207.661044] eth0: link down.
[  215.407518] eth0: link up.
[  215.409460] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  227.566236] eth0: no IPv6 routers present
[ 1888.005825] psmouse.c: GlidePoint at isa0060/serio1/input0 lost sync at byte 1
[ 1888.006540] psmouse.c: GlidePoint at isa0060/serio1/input0 lost sync at byte 1
[ 1888.009961] psmouse.c: GlidePoint at isa0060/serio1/input0 - driver resynched.
[ 1888.010887] psmouse.c: GlidePoint at isa0060/serio1/input0 lost sync at byte 1
[ 1888.153874] psmouse.c: GlidePoint at isa0060/serio1/input0 - driver resynched.
[ 1888.249175] psmouse.c: GlidePoint at isa0060/serio1/input0 lost sync at byte 1
[ 1888.250402] psmouse.c: GlidePoint at isa0060/serio1/input0 lost sync at byte 1
[ 1888.253069] psmouse.c: GlidePoint at isa0060/serio1/input0 - driver resynched.
[ 1888.254436] psmouse.c: GlidePoint at isa0060/serio1/input0 lost sync at byte 1
[ 1888.334870] psmouse.c: GlidePoint at isa0060/serio1/input0 - driver resynched.
brandon@brandon-laptop:~/driver$ 


brandon@brandon-laptop:~/driver$ ifconfig
eth0      Link encap:Ethernet  HWaddr 5C:C6:56:38:1B:00  
          inet addr:192.168.0.23  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::5ec6:56ff:fe38:1b00/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6375 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5618 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7314080 (6.9 MB)  TX bytes:692365 (676.1 KB)
          Interrupt:22 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


ndon@brandon-laptop:~/driver$ lshw -c network
Hardware Lister (lshw) - B.02.10
usage: lshw [-format] [-options ...]
       lshw -version

        -version        print program version (B.02.10)

format can be
        -html           output hardware tree as HTML
        -xml            output hardware tree as XML
        -short          output hardware paths
        -businfo        output bus information

options can be
        -class CLASS    only show a certain class of hardware
        -C CLASS        same as '-class CLASS'
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
        -quiet          don't display status


then i try do depmod -a or modprobe ndiswrapper  nothing show up it just ask for another command

---

### Post by kevdog on 2008-03-10
Looks like there is a problem with the driver:
[ 41.526270] ndiswrapper (pnp_start_device:440): Windows driver couldn't initialize the device (C0000001)

Could you post
ndiswrapper -l

What kind of chipset/card do you have, and what driver are you using.  Please lists the basics first.

---

### Post by Maxwell85 on 2008-03-10
Thank you for your help!  I found the driver (finally) and the install procedure worked perfectly!  Now if I can get WINE to work properly I can switch to Ubuntu totally heh.

---

### Post by kevdog on 2008-03-10
Good luck with WINE -- I used to use it initially, but then found suitable linux replacements.  WINE is kinda slow for me -- maybe thats me though.  Alot of people like it

---

### Post by nocturnalsixer on 2008-03-12
I have a acer aspire 5520-5912 laptop 

the specification is 

Additional Specifications  
Processor Brand:  AMD  
Processor Type:  Turion 64 X2 Dual-Core  
Hard Drive Size:  160GB  
System RAM:  2048 MB  
Display Type:  15.4" TFT  
Widescreen Display:  Yes  
Max Resolution:  1280 x 800 ( WXGA )  
Processor  
Multi-Core Technology:  Dual-Core  
Processor:  AMD Turion 64 X2 mobile technology TL-58 / 1.9 GHz  
Chipset Type:  NVIDIA nForce 610M  
Cache Memory  
Type:  L2 cache  
Installed Size:  1 MB  
Storage  
Hard Drive:  160 GB  
RAM  
Installed Size:  2 GB / 4 GB (max)  
Technology:  DDR II SDRAM - 667 MHz  
Configuration Features:  2 x 1 GB  
Optical Storage  
Type:  DVD±RW (±R DL) / DVD-RAM - integrated  
Read Speed:  24x (CD) / 8x (DVD±R) / 6x (DVD±R DL)  
Write Speed:  24x (CD) / 8x (DVD±R) / 4x (DVD±R DL)  
Networking  
Data Link Protocol:  Ethernet, Fast Ethernet, Gigabit Ethernet, IEEE 802.11b, IEEE 802.11g  
Wireless LAN Supported:  Yes
Atheros AR5007EG or AR5006EG unsure  
Video  
Graphics Processor / Vendor:  NVIDIA GeForce 7000M TurboCache supporting 896MB  
Audio  
Audio Input:  Microphone   
Battery  
Technology:  6-cell lithium ion  
Installed Qty:  1  
Capacity:  4000 mAh  
Run Time (Up To):  3 hour(s)  
Notebook Camera  
Camera Type:  Integrated  
Product Dimensions  
Width:  14.4 in  
Height:  1.7 in  
Depth:  10.8 in  
Weight:  6.2 lbs  
Card Reader  
Supported Flash Memory Cards:  SD Memory Card, Memory Stick, Memory Stick PRO, MultiMediaCard, xD-Picture Card  
Miscellaneous  
Features:  Wake on LAN  
Compliant Standards:  ACPI 3.0  



I used the windows xp 64 bit driver since im on ubuntu gutsy 64 bit i tried using 32 and 64 bit drivers both

---

### Post by jedinite7 on 2008-03-16
I just wanted to start off by saying thanks to everyone who helps out these forums and puts together guides.  I followed the guide and have run into some problems.  I am trying to run Mythbuntu 7.10.  I have a D-Link DWL-G510 Rev A.  

lshw lists the product as Marvell W8300 802.11 Adapter

 Below are the only anamolies that I could see while following the guide.  When I finished and restarted my computer, it no longer fully boots.  It hangs on openssh step.  I can do an ALT-F1 to get into a console, but do not know what to do from there.  I am not too handy working with the console so if someone could walk me through diagnosing this problem I would really appreciate it. 



```
csgoodloe@fserver:~/driver$ sudo ndiswrapper -i mrv8k51.inf
installing mrv8k51 ...
couldn't find section "W8100PCI.zerocfg" -
installation may be incomplete
couldn't find section "W8100PCI.zerocfg" -
installation may be incomplete
couldn't find section "W8100PCI.zerocfg" -
installation may be incomplete
csgoodloe@fserver:~/driver$ ndiswrapper -l
mrv8k51 : driver installed
        device (11AB:1FA6) present

```

I initially installed ndiswrapper from synaptic which lists it as 1.45.  I followed the uninstall instructions, and installed version 1.52.  So I am not sure why it says 1.45 loaded.

```
[ 2006.005224] ndiswrapper version 1.45 loaded (smp=yes)
[ 2006.023264] ndiswrapper: driver mrv8k51 (D-Link,1/09/2004,2.3.0.1)
loaded
[ 2006.024434] ACPI: PCI Interrupt 0000:00:0c.0[A] -> Link [LNKA] -> GSI
11 (level, low) -> IRQ 11
[ 2006.026276] ndiswrapper: using IRQ 11
[ 2006.291009] wlan0: ethernet device 00:11:95:17:f5:60 using NDIS
driver: mrv8k51, version: 0x2030001, NDIS version: 0x501, vendor:
'Marvell 802.11 Driver', 11AB:1FA6.5.conf
[ 2006.291772] ndiswrapper (set_encr_mode:673): setting encryption mode
to 6 failed (C00000BB)
[ 2006.292196] wlan0: encryption modes supported: WEP; TKIP with WPA
[ 2006.295614] usbcore: registered new interface driver ndiswrapper
[ 2007.206347] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

---

### Post by kevdog on 2008-03-16
jedinite7

I think for a beginner you have done a wonderful job explaining the problem and diagnosing your own problem: 

csgoodloe@fserver:~/driver$ sudo ndiswrapper -i mrv8k51.inf
installing mrv8k51 ...
couldn't find section "W8100PCI.zerocfg" -
installation may be incomplete
couldn't find section "W8100PCI.zerocfg" -
installation may be incomplete
couldn't find section "W8100PCI.zerocfg" -
installation may be incomplete
csgoodloe@fserver:~/driver$ ndiswrapper -l
mrv8k51 : driver installed
        device (11AB:1FA6) present

Basically the driver you are trying to use -- there is a problem.  You dont happen to have another driver for the device?  Usually you want the winxp driver (not vista) and sometimes with other devices Ive had people try win98, me drivers.  You might have to visit the website of the usb stick maker to see if other drivers are available.

---

### Post by (((X))) on 2008-03-18
> This error usually means that there are duplicate or more than one driver installed with ndiswrapper. The easiest way to resolve this message is to do the following:


Code:
sudo rm -R /etc/ndiswrapper *

That command deleted evey single file in myuser directory
, Lucky me, I created backup this week
however
 please update this how-to and tell people what that command is doing, because rm* whatever is considered
as dangerous.

---

### Post by kevdog on 2008-03-18
How did the command 

sudo rm -R /etc/ndiswrapper/*

delete every single file in your user directory -- I'm confused??

---

### Post by (((X))) on 2008-03-19
I don't know, it just happend.
Perhaps It is my fault.

---

### Post by kevdog on 2008-03-20
Sorry about the deletion.  I hope you didn't loose anything too important :(

---

### Post by erginemr on 2008-03-20
For the new Linux users (not for kevdog of course), the code used by (((X))) was:
```
sudo rm -R /etc/ndiswrapper *
```
which naturally took away both the directory /etc/ndiswrapper and everthing inside your home folder (or whatever folder you are in, provided that you have enough permissions).

Whereas it should have been 
```
sudo rm -R /etc/ndiswrapper/*
```
as correctly pointed out in kevdog's howto, which deletes everything inside the /etc/ndiswrapper folder, but not the folder itself.

It is ironic how a single slash (/) can make a big difference...

---

### Post by kevdog on 2008-03-20
Thanks for directly pointing out the difference and sorry to anyone else whom may have gotten burned by this command.  sudo rm -rf is a powerful command but can possibly screw up a lot of things.

---

### Post by jedinite7 on 2008-03-21
Ok, so I reinstalled Mythbuntu 7.10 because I could not figure out how to change the driver in the console.  I used the Win2K driver which loaded fine.  I got to the part with dmesg and this was the result again.  I think the problem has to do with setting the encryption mode.  This may be a problem with the driver again, but I did get it to work using synaptic version of ndiswrapper and ndisgtk.  Unfortunately that only worked until I restarted and then when I tried to fix it I ran into the same problem.  So I think the driver works, it is just when I boot up ndiswrapper has this encryption isssue.  Any help is appreciated.

```
[ 2006.005224] ndiswrapper version 1.52 loaded (smp=yes)
[ 2006.023264] ndiswrapper: driver mrv8k51 (D-Link,1/09/2004,2.3.0.1)
loaded
[ 2006.024434] ACPI: PCI Interrupt 0000:00:0c.0[A] -> Link [LNKA] -> GSI
11 (level, low) -> IRQ 11
[ 2006.026276] ndiswrapper: using IRQ 11
[ 2006.291009] wlan0: ethernet device 00:11:95:17:f5:60 using NDIS
driver: mrv8k51, version: 0x2030001, NDIS version: 0x501, vendor:
'Marvell 802.11 Driver', 11AB:1FA6.5.conf
[ 2006.291772] ndiswrapper (set_encr_mode:673): setting encryption mode
to 6 failed (C00000BB)
[ 2006.292196] wlan0: encryption modes supported: WEP; TKIP with WPA
[ 2006.295614] usbcore: registered new interface driver ndiswrapper
[ 2007.206347] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

---

### Post by kevdog on 2008-03-21
I'm not sure what the error code refers to however I read someone else reset the router and everything worked -- strange I know!!

---

### Post by vstrazz on 2008-03-22
hello. First off thanks for the write-up I could imagine how long it took to write it up so nicely .
but!

when I try the first step.
```
1. After booting into Ubuntu, put the Ubuntu installation CD in drive and wait for it to "spin up"
   2. sudo apt-cdrom add
   3. sudo aptitude update

The following command is formated with backticks (`) and not single quotes (')
Type the command as it is exactly written or just cut and paste the instruction to a terminal
   4. sudo aptitude install build-essential linux-headers-`uname -r`
```

sudo apt-cdrom add seems to un-mount then I press enter it mounts and the sudo aptitude update tries to access multiple ubuntu websites, which fail because my wireless is not working lol.

something I'm doing wrong? It's a fresh gutsy install with a belkin g usb dongle. I know multiple people have posted issues with belkin adapters but I'm posting from the same adapter running ubuntu straight from the liveCD! ?!?!? but it wont work directly from the hard drive.. please help thanks.

---

### Post by kevdog on 2008-03-22
I'm not sure what the source of the error is -- Boot into ubuntu - no live CD.  Stick the CD in the driver after boot, and type sudo apt-cdrom add.  The sudo aptitude update.  It doesnt matter if you get errors during the update process.

---

### Post by vstrazz on 2008-03-22
thanks for the fast reply!

I'm booting from the hard disk then putting the cd in and running the commands. I go to run the linux header command (number 4) then install ndiswrapper and it never installs. 

looking through your thread it seems that another user had the same issue and you said it seemed that he didn't run the linux header command, so I'm assuming thats where my issue lies.

---

### Post by kevdog on 2008-03-22
Can you post the specific error you are getting that tells you that ndiswrapper is not getting installed?

---

### Post by vstrazz on 2008-03-22
vance@copmuter:~/ndiswrapper/ndiswrapper-1.48$ make
make -C driver
make[1]: Entering directory `/home/vance/ndiswrapper/ndiswrapper-1.48/driver'
make -C /usr/src/linux-headers-2.6.22-14-generic SUBDIRS=/home/vance/ndiswrapper/ndiswrapper-1.48/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  LD      /home/vance/ndiswrapper/ndiswrapper-1.48/driver/built-in.o
  CC [M]  /home/vance/ndiswrapper/ndiswrapper-1.48/driver/crt.o
  CC [M]  /home/vance/ndiswrapper/ndiswrapper-1.48/driver/hal.o
  CC [M]  /home/vance/ndiswrapper/ndiswrapper-1.48/driver/iw_ndis.o
  CC [M]  /home/vance/ndiswrapper/ndiswrapper-1.48/driver/loader.o
  CC [M]  /home/vance/ndiswrapper/ndiswrapper-1.48/driver/ndis.o
  CC [M]  /home/vance/ndiswrapper/ndiswrapper-1.48/driver/ntoskernel.o
  CC [M]  /home/vance/ndiswrapper/ndiswrapper-1.48/driver/ntoskernel_io.o
  CC [M]  /home/vance/ndiswrapper/ndiswrapper-1.48/driver/pe_linker.o
  CC [M]  /home/vance/ndiswrapper/ndiswrapper-1.48/driver/pnp.o
  CC [M]  /home/vance/ndiswrapper/ndiswrapper-1.48/driver/proc.o
  CC [M]  /home/vance/ndiswrapper/ndiswrapper-1.48/driver/rtl.o
  CC [M]  /home/vance/ndiswrapper/ndiswrapper-1.48/driver/wrapmem.o
  CC [M]  /home/vance/ndiswrapper/ndiswrapper-1.48/driver/wrapndis.o
  CC [M]  /home/vance/ndiswrapper/ndiswrapper-1.48/driver/wrapper.o
  CC [M]  /home/vance/ndiswrapper/ndiswrapper-1.48/driver/usb.o
  CC [M]  /home/vance/ndiswrapper/ndiswrapper-1.48/driver/divdi3.o
  LD [M]  /home/vance/ndiswrapper/ndiswrapper-1.48/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/vance/ndiswrapper/ndiswrapper-1.48/driver/ndiswrapper.mod.o
  LD [M]  /home/vance/ndiswrapper/ndiswrapper-1.48/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: Leaving directory `/home/vance/ndiswrapper/ndiswrapper-1.48/driver'
make -C utils
make[1]: Entering directory `/home/vance/ndiswrapper/ndiswrapper-1.48/utils'
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
loadndisdriver.c:15:20: error: stdlib.h: No such file or directory
loadndisdriver.c:16:19: error: stdio.h: No such file or directory
loadndisdriver.c:17:19: error: errno.h: No such file or directory
loadndisdriver.c:18:20: error: string.h: No such file or directory
loadndisdriver.c:19:20: error: libgen.h: No such file or directory
loadndisdriver.c:21:22: error: sys/mman.h: No such file or directory
loadndisdriver.c:23:23: error: sys/types.h: No such file or directory
loadndisdriver.c:24:23: error: sys/ioctl.h: No such file or directory
loadndisdriver.c:25:22: error: sys/stat.h: No such file or directory
loadndisdriver.c:26:20: error: unistd.h: No such file or directory
loadndisdriver.c:27:19: error: fcntl.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.3/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.3/include/limits.h:11,
                 from loadndisdriver.c:28:
/usr/lib/gcc/i486-linux-gnu/4.1.3/include/limits.h:122:61: error: limits.h: No such file or directory
loadndisdriver.c:29:19: error: ctype.h: No such file or directory
loadndisdriver.c:30:20: error: dirent.h: No such file or directory
loadndisdriver.c:31:20: error: syslog.h: No such file or directory
loadndisdriver.c:34:25: error: linux/major.h: No such file or directory
loadndisdriver.c:35:25: error: linux/ioctl.h: No such file or directory
In file included from loadndisdriver.c:37:
../driver/loader.h:24: error: expected specifier-qualifier-list before ‘size_t’
loadndisdriver.c: In function ‘load_file’:
loadndisdriver.c:67: error: ‘size_t’ undeclared (first use in this function)
loadndisdriver.c:67: error: (Each undeclared identifier is reported only once
loadndisdriver.c:67: error: for each function it appears in.)
loadndisdriver.c:67: error: expected ‘;’ before ‘size’
loadndisdriver.c:68: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:69: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:71: warning: implicit declaration of function ‘basename’
loadndisdriver.c:71: warning: initialization makes pointer from integer without a cast
loadndisdriver.c:73: warning: implicit declaration of function ‘open’
loadndisdriver.c:73: error: ‘O_RDONLY’ undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function ‘syslog’
loadndisdriver.c:75: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:75: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function ‘strerror’
loadndisdriver.c:75: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:76: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:79: warning: implicit declaration of function ‘fstat’
loadndisdriver.c:81: warning: implicit declaration of function ‘close’
loadndisdriver.c:84: error: ‘size’ undeclared (first use in this function)
loadndisdriver.c:86: warning: implicit declaration of function ‘mmap’
loadndisdriver.c:86: error: ‘PROT_READ’ undeclared (first use in this function)
loadndisdriver.c:86: error: ‘MAP_PRIVATE’ undeclared (first use in this function)
loadndisdriver.c:86: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:87: error: ‘MAP_FAILED’ undeclared (first use in this function)
loadndisdriver.c:93: warning: implicit declaration of function ‘strncpy’
loadndisdriver.c:93: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:95: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:96: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:69: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘parse_setting_line’:
loadndisdriver.c:109: warning: implicit declaration of function ‘isspace’
loadndisdriver.c:115: warning: implicit declaration of function ‘strchr’
loadndisdriver.c:115: warning: incompatible implicit declaration of built-in function ‘strchr’
loadndisdriver.c:115: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:117: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:117: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:118: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:138: warning: implicit declaration of function ‘strlen’
loadndisdriver.c:138: warning: incompatible implicit declaration of built-in function ‘strlen’
loadndisdriver.c: In function ‘read_conf_file’:
loadndisdriver.c:150: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:151: error: ‘FILE’ undeclared (first use in this function)
loadndisdriver.c:151: error: ‘config’ undeclared (first use in this function)
loadndisdriver.c:157: warning: implicit declaration of function ‘lstat’
loadndisdriver.c:158: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:158: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:158: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:160: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:163: warning: implicit declaration of function ‘sscanf’
loadndisdriver.c:163: warning: incompatible implicit declaration of built-in function ‘sscanf’
loadndisdriver.c:178: warning: implicit declaration of function ‘fopen’
loadndisdriver.c:178: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:182: warning: implicit declaration of function ‘fgets’
loadndisdriver.c:194: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:205: warning: implicit declaration of function ‘fclose’
loadndisdriver.c:150: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘load_bin_file’:
loadndisdriver.c:217: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:217: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:219: warning: implicit declaration of function ‘tolower’
loadndisdriver.c:221: warning: implicit declaration of function ‘chdir’
loadndisdriver.c:222: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:224: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:230: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:232: warning: implicit declaration of function ‘ioctl’
loadndisdriver.c:232: warning: implicit declaration of function ‘_IOW’
loadndisdriver.c:232: error: expected expression before ‘struct’
loadndisdriver.c: In function ‘load_driver’:
loadndisdriver.c:249: error: ‘DIR’ undeclared (first use in this function)
loadndisdriver.c:249: error: ‘driver_dir’ undeclared (first use in this function)
loadndisdriver.c:251: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:255: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:255: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:257: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:259: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:261: warning: implicit declaration of function ‘opendir’
loadndisdriver.c:267: warning: implicit declaration of function ‘malloc’
loadndisdriver.c:267: warning: incompatible implicit declaration of built-in function ‘malloc’
loadndisdriver.c:271: warning: implicit declaration of function ‘memset’
loadndisdriver.c:271: warning: incompatible implicit declaration of built-in function ‘memset’
loadndisdriver.c:272: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:280: warning: implicit declaration of function ‘readdir’
loadndisdriver.c:280: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:282: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:284: error: dereferencing pointer to incomplete type
loadndisdriver.c:287: warning: implicit declaration of function ‘stat’
loadndisdriver.c:287: error: dereferencing pointer to incomplete type
loadndisdriver.c:288: warning: implicit declaration of function ‘S_ISREG’
loadndisdriver.c:289: error: dereferencing pointer to incomplete type
loadndisdriver.c:294: warning: incompatible implicit declaration of built-in function ‘strlen’
loadndisdriver.c:294: error: dereferencing pointer to incomplete type
loadndisdriver.c:296: warning: implicit declaration of function ‘strcasecmp’
loadndisdriver.c:296: error: dereferencing pointer to incomplete type
loadndisdriver.c:299: error: dereferencing pointer to incomplete type
loadndisdriver.c:302: error: dereferencing pointer to incomplete type
loadndisdriver.c:303: error: dereferencing pointer to incomplete type
loadndisdriver.c:305: error: dereferencing pointer to incomplete type
loadndisdriver.c:311: error: dereferencing pointer to incomplete type
loadndisdriver.c:312: error: dereferencing pointer to incomplete type
loadndisdriver.c:313: warning: implicit declaration of function ‘strcpy’
loadndisdriver.c:313: warning: incompatible implicit declaration of built-in function ‘strcpy’
loadndisdriver.c:314: error: dereferencing pointer to incomplete type
loadndisdriver.c:317: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:318: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:321: error: dereferencing pointer to incomplete type
loadndisdriver.c:282: warning: unused variable ‘statbuf’
loadndisdriver.c:344: error: expected expression before ‘struct’
loadndisdriver.c:346: warning: implicit declaration of function ‘closedir’
loadndisdriver.c:348: warning: implicit declaration of function ‘free’
loadndisdriver.c:355: warning: implicit declaration of function ‘munmap’
loadndisdriver.c:355: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:355: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:357: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:357: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c: In function ‘get_device’:
loadndisdriver.c:367: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:370: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:370: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:373: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:374: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:376: warning: implicit declaration of function ‘snprintf’
loadndisdriver.c:376: warning: incompatible implicit declaration of built-in function ‘snprintf’
loadndisdriver.c:407: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:367: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘load_device’:
loadndisdriver.c:419: error: ‘DIR’ undeclared (first use in this function)
loadndisdriver.c:419: error: ‘dir’ undeclared (first use in this function)
loadndisdriver.c:423: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:423: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:424: warning: incompatible implicit declaration of built-in function ‘memset’
loadndisdriver.c:426: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:427: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:429: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:434: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:435: error: dereferencing pointer to incomplete type
loadndisdriver.c:436: error: dereferencing pointer to incomplete type
loadndisdriver.c:439: error: dereferencing pointer to incomplete type
loadndisdriver.c:447: error: expected expression before ‘struct’
loadndisdriver.c: In function ‘get_ioctl_device’:
loadndisdriver.c:464: error: ‘FILE’ undeclared (first use in this function)
loadndisdriver.c:464: error: ‘proc_misc’ undeclared (first use in this function)
loadndisdriver.c:472: warning: implicit declaration of function ‘strstr’
loadndisdriver.c:472: warning: incompatible implicit declaration of built-in function ‘strstr’
loadndisdriver.c:473: warning: implicit declaration of function ‘strtol’
loadndisdriver.c:473: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:483: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:483: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:488: warning: implicit declaration of function ‘unlink’
loadndisdriver.c:489: warning: implicit declaration of function ‘mknod’
loadndisdriver.c:489: error: ‘S_IFCHR’ undeclared (first use in this function)
loadndisdriver.c:489: error: ‘MISC_MAJOR’ undeclared (first use in this function)
loadndisdriver.c:490: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:495: error: ‘O_RDONLY’ undeclared (first use in this function)
loadndisdriver.c: In function ‘main’:
loadndisdriver.c:511: warning: implicit declaration of function ‘openlog’
loadndisdriver.c:511: error: ‘LOG_PERROR’ undeclared (first use in this function)
loadndisdriver.c:511: error: ‘LOG_CONS’ undeclared (first use in this function)
loadndisdriver.c:511: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:511: error: ‘LOG_DEBUG’ undeclared (first use in this function)
loadndisdriver.c:513: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:515: warning: implicit declaration of function ‘strncmp’
loadndisdriver.c:517: warning: implicit declaration of function ‘printf’
loadndisdriver.c:517: warning: incompatible implicit declaration of built-in function ‘printf’
loadndisdriver.c:527: warning: implicit declaration of function ‘atoi’
loadndisdriver.c:542: warning: implicit declaration of function ‘atof’
loadndisdriver.c:549: warning: implicit declaration of function ‘strcmp’
loadndisdriver.c:556: warning: incompatible implicit declaration of built-in function ‘sscanf’
loadndisdriver.c:590: warning: implicit declaration of function ‘closelog’
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/vance/ndiswrapper/ndiswrapper-1.48/utils'
make: *** [all] Error 2
vance@copmuter:~/ndiswrapper/ndiswrapper-1.48$ ndiswrapper -v
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found

---

### Post by kevdog on 2008-03-22
Yep -- looks like a header files problem.

What are you typing when you try to install the linux-header files

its linux-headers-`uname -r`

Those are backticks and not quotes.

---

### Post by vstrazz on 2008-03-22
I'm using copy and paste from the code supplied.

EDIT: sudo aptitude install build-essential linux-headers-`uname -r`
that code there.

what's really getting me confused is why I can sit here on blazing internet speeds while running off the liveCD but the hard drive install wont do anything... really weird.

---

### Post by kevdog on 2008-03-22
Well at least you its possible to get things working!!

Can you reboot possibly and try again --- something is missing here and I cant figure out what?

---

### Post by vstrazz on 2008-03-22
I've rebooted several times, i have to reboot to the hard drive just to try again lol.

I've went through the same thing over and over. I don't get it..

I think the problem lies somewhere in the apt-get update because it doesn't seem to be updating anything. it just tries to connect to the ubuntu sites and not really installing anything from the cd.

I really don't know though. I'm a php coder and I use a LAMP architecture at work, so I use linux a lot but never this in depth with a complete linux type desktop.

Is it possible that the cd I burned was incorrect? It installed fine from what I can tell.

---

### Post by kevdog on 2008-03-22
Can you post your 
/etc/apt/sources file

I think that is the correct file?

---

### Post by vstrazz on 2008-03-22
well, I used a guide I found somewhere on this board specifically for the F5D7050 belkin and it manually did the linux headers and it asked for the cd..

I'm now rockin and rollin. thanks for all your help kevdog. Im not sure what did it but i'm pretty sure its something to do with the linux headers not installing right until I went into usr/src.

I can't seem to find the guide again but I have saved it locally if anyone else is having issues with their belkin usb crapper.

EDIT: [http://ubuntuforums.org/showthread.php?t=400236&highlight=rt73+rt71](http://ubuntuforums.org/showthread.php?t=400236&highlight=rt73+rt71)

thats the one!

---

### Post by Astura on 2008-03-22
ndiswrapper -l
> 
astral@ubuntu:~$ ndiswrapper -l
bcmwl6 : driver installed
	device (14E4:4315) present




All goes good until the **dmesg** step:


dmesg
> 
[   40.056722] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   40.187165] ACPI: AC Adapter [ADP1] (on-line)
[   40.345560] ACPI: Battery Slot [BAT0] (battery present)
[   40.405271] sdhci: Secure Digital Host Controller Interface driver
[   40.405275] sdhci: Copyright(c) Pierre Ossman
[   40.573725] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[   40.573737] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[   40.573745] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   40.573751] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   40.573758] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[   40.573764] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   40.573772] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   40.573779] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   40.573786] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[   40.573795] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[   40.573815] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   40.573827] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   40.573833] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   40.573839] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   40.573846] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   40.573852] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   40.573865] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   40.573872] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   40.573878] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   40.573884] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   40.573890] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   40.573897] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   40.573904] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[   40.573911] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   40.573923] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   40.573930] ndiswrapper (load_sys_files:210): couldn't prepare driver 'bcmwl6'
[   40.574639] ndiswrapper (load_wrap_driver:112): couldn't load driver bcmwl6; check system log for messages from 'loadndisdriver'




Also, this seems odd:

iwconfig
> 
astral@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.



---

### Post by jedinite7 on 2008-03-22
I tried a couple of things to get this wireless working.

The first was to diable ssh service which allowed the boot process to get passed where it normally hangs.  Unfortunately, it then got hung up on something to do with mysql. 

The second thing I did was bootup without ndiswrapper in /etc/modules, which works fine, but then I have no wireless.  I then ran sudo modprobe ndiswrapper.  My wireless network came up in network manager and i was able to connect.  I am writing post using my wireless connection as I speak.  

So I might be doing things in the wrong order on bootup, which I have no idea how to change.  Or I need to figure out how to run that command after startup automatically.  Any help on either of these would be great.  Thanks.

---

### Post by kevdog on 2008-03-22
Astura

I think bcmwl6 is a Vista driver.  I think you want bcmwl5 which is an XP driver.  Correct me if I am wrong, but I'm recommending for you to find a different driver.

---

### Post by kevdog on 2008-03-22
jedinite7

I don't know about your first problem since you haven't posted enough details or posted any comments from the boot log that would suggest your problem.

As far as loading ndiswrapper on boot, why dont you add it to the list of startup modules in the /etc/modules file?

echo ndiswrapper | sudo tee -a /etc/modules

---

### Post by Astura on 2008-03-23
Kevdog,

Your right, the bcmwl6 is a vista driver, but I originaly tried the bcmwl5 driver and with that it read back that the hardware is not present. I went to the hp website and downloaded the broadcom driver directly for my laptop and it does read back that the hardware is present with the bcmwl6.

---

### Post by kevdog on 2008-03-23
Hmm, you would be the first to get bcmwl6 up and running.  Have you tried getting up to work with a simple unencrypted network?

Can you also post
lspci -nn | grep Network

---

### Post by Astura on 2008-03-23
astral@ubuntu:~$ lspci -nn | grep Network
04:00.0 Network controller [0280]: Broadcom Corporation BCM4310 USB Controller [14e4:4315] (rev 01)

---

### Post by jedinite7 on 2008-03-23
When I add ndiswrapper to /etc/modules, it fails to boot on the openssh step.  When that line is not in the file I boot fine and can then run sudo modprobe ndiswrapper and get wireless working.  I do not know which log files to look in to see where the error occurs.  let me know what those are and I can get you some more information.  Again I appreciate the help.

---

### Post by kevdog on 2008-03-23
jedinite -- I guess I missed something.  What is your problem with between openssh and ndiswrapper.  I'm missing something in your explanation


dmesg gives you the system log.

---

### Post by kevdog on 2008-03-23
Astura 

Any success?

---

### Post by ockron on 2008-03-24
I followed all the steps as you described it....

It worked brilliantly!!!!

Thank you so very, very much!!!

---

### Post by blokkendoos on 2008-03-27
Thanks kevdog!!
Your step by step instructions brought my RTL8185 card (alias smcwpci-g) alive. 
What was needed was not the latest WinXP drivers from SMC, but the originally supplied ones on the CD-ROM. I tested it by starting a live Sidux, configuring ndiswrapper with these 'old' drivers (net8185) and bingo!
Now I can go on.

Thanks!

pablo k

---

### Post by kevdog on 2008-03-27
Are the net8185 drivers equivalent to the Win98 drivers?

---

### Post by ian_33 on 2008-03-31
I followed your guide for my bcm4318 driver (64bit). Installed ndiswrapper, the driver, and it appeared when I used the command "sudo niswrapper -l". Then I blacklisted the bcm43xx and made sure the module contained ndiswrapper, as described. BUT, after reboot my network manager doesn't show an option for "wireless". Here is the result from the "lshw -C network" command:

```

*-network:0 UNCLAIMED         
description: Network controller      
product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller       
vendor: Broadcom Corporation      
physical id: 2       
bus info: pci@0000:06:02.0       
version: 02       
width: 32 bits       
clock: 33MHz      
capabilities: bus_master      
configuration: latency=64  

*-network:1       
description: Ethernet interface     
product: RTL-8139/8139C/8139C+    
vendor: Realtek Semiconductor Co., Ltd.       
physical id: 6
bus info: pci@0000:06:06.0       
logical name: eth0       
version: 10       
serial: 00:0f:b0:c4:40:29       
width: 32 bits       
clock: 33MHz       
capabilities: bus_master cap_list ethernet physical       
configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=128 maxlatency=64 mingnt=32 module=8139too multicast=yes

```

Please help, I've been trying to get this wireless to work for days. ](*,)

---

### Post by lswest on 2008-03-31
what happens if you do ```
sudo modprobe ndiswrapper
sudo ndiswrapper  -m
sudo echo "ndiswrapper" >> /etc/modules (only do this if "ndiswrapper" is not in the file already)
``` and then run ```
lshw -C network
``` again.

---

### Post by ian_33 on 2008-03-31
> lswest  	

what happens if you do

Code:
sudo modprobe ndiswrapper
sudo ndiswrapper  -m
sudo echo "ndiswrapper" >> /etc/modules (only do this if "ndiswrapper" is not in the file already)

and then run

Code:
lshw -C network

again.

Same result as before...

---

### Post by kevdog on 2008-03-31
Your device remains unclaimed -- are you using a 64 bit driver??  

Might need to post ndiswrapper -l

---

### Post by ian_33 on 2008-03-31
I am using the 64 bit Ubuntu (Gutsy), and just to make sure I had the 64 bit driver installed I went and downloaded it again from the site you referenced, and got the Air Force one package. I used ndiswrapper -e to remove the other one, then reinstalled this new version that had the 64bit .sys file in the same folder as the bcmwl5.inf file. But it looks like I am still not using the 64 bit driver?

Here are outputs:

sudo ndiswrapper -l 

```

bcmwl5 : driver installed        
device (14E4:4318) present (alternate driver: bcm43xx)

```

dmesg

```

...
[   38.504549] ndiswrapper version 1.45 loaded (smp=yes)
[   38.597869] ndiswrapper (check_nt_hdr:153): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[   38.597877] ndiswrapper (load_sys_files:216): couldn't prepare driver 'bcmwl5'
[   38.598350] ndiswrapper (load_wrap_driver:118): couldn't load driver bcmwl5; check system log for messages from 'loadndisdriver'
...

```

---

### Post by kevdog on 2008-03-31
Did I reference a 64 bit driver site?  Possibly I did unknowingly.  64 bit drivers for broadcom are hard to find.  Hopefully a winxp driver 64 bit is available.

---

### Post by ian_33 on 2008-03-31
Nevermind! When I restarted my computer the wireless was working! :)

I guess I must have been trying to use the 32 bit ones before.

---

### Post by vms66 on 2008-04-06
Hello
i'm in France and very beginner with linux. I chose Kubuntu 7.10 distribution.
i've just bought a dell Vostro 1700 with an mini PCI wifi card Broadcom BCM4328
 
After quite a lot of hours i get
[B]vignaux@DellVostro1700:~$ sudo lshw -C network
[sudo] password for vignaux:
  *-network UNCLAIMED
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:c8:f1:58
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=half latency=64 link=no module=b44 multicast=yes port=twisted pair speed=10MB/s[/B]

i've intalled ndiswrapper and the good pilot ( i hope so )
i have 
[B]sudo ndiswrapper -i bcmwl6.inf 
sudo ndiswrapper -l
bcmwl6 driver installed
device (14E4:4328) present[/B]

well....

another tip
[B]vignaux@DellVostro1700:~$ dmesg
[   28.268000] ndiswrapper version 1.45 loaded (smp=yes)
[   28.344000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   28.344000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   28.344000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   28.344000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   28.344000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   28.344000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[   28.344000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   28.344000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[   28.344000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   28.344000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   28.344000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   28.344000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   28.344000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[   28.344000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   28.344000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   28.344000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[   28.344000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   28.344000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[   28.344000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   28.344000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   28.344000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   28.344000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   28.344000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[   28.344000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   28.344000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   28.344000] ndiswrapper (load_sys_files:216): couldn't prepare driver 'bcmwl6'
[   28.344000] ndiswrapper (load_wrap_driver:118): couldn't load driver bcmwl6; check system log for messages from 'loadndisdriver'
[   28.352000] usbcore: registered new interface driver ndiswrapper[/B]

Please, can you help me?
Thanks

Remy

---

### Post by suman4674 on 2008-04-06
I am using following commands to install the Trendnet TEW-444UB/A USB Wireless .I am not getting any error.I can see the wireless Connection in Network settings and i have configured my ESSID correctly.Still i am not able to connect to internet.Any help will be appreciated

I removed the Device to reset the firmware and ran the below batch
lsusb
sudo rm -R /etc/ndiswrapper/*
cd Driver/
sudo ndiswrapper -i a*.inf
sudo modprobe ndiswrapper
sudo modprobe -r ndiswrapper
sudo ndiswrapper -i n*.inf
sudo modprobe ndiswrapper
lsusb
iwconfig
/*****the output on terminal ****/
~$ sudo ndiswrapper -l
athfmwdl : driver installed
net5523 : driver installed
device (157E:3006) present

~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

wlan0 IEEE 802.11g ESSID:"Kumar"
Mode:Managed Frequency:2.437 GHz Access Point: Not-Associated
Bit Rate:54 Mb/s
Power Managementff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

---

### Post by kevdog on 2008-04-06
Remy, Im not sure the bcmwl6.inf driver can be used since I believe this is a Vista driver if I remember correctly.  You want a winxp driver.  64 bit install?

---

### Post by kevdog on 2008-04-06
suman what you posted looks good!!  Proceed to connecting via the command line (link in signature).

---

### Post by peejaroni on 2008-04-07
I'm a total noob trying to install ndiswrapper to run my wpn111 netgear adapter. So far I am still stuck on getting ndiswrapper installed.

Here is what the terminal said,

pj@pj-desktop:~$
pj@pj-desktop:~$ sudo aptitude install build-essential linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "build-essential"
Couldn't find any package whose name or description matched "build-essential"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
pj@pj-desktop:~$ cd ndiswrapper-1.51tar -zxvf ndiswrapper-1.51.tar.tar
bash: cd: ndiswrapper-1.51tar: No such file or directory
pj@pj-desktop:~$ cd Desktop
pj@pj-desktop:~/Desktop$ tar -zxvf ndiswrapper-1.51.tar.tar
ndiswrapper-1.51/
ndiswrapper-1.51/AUTHORS
ndiswrapper-1.51/ChangeLog
ndiswrapper-1.51/INSTALL
ndiswrapper-1.51/Makefile
ndiswrapper-1.51/README
ndiswrapper-1.51/ndiswrapper.spec
ndiswrapper-1.51/ndiswrapper.8
ndiswrapper-1.51/loadndisdriver.8
ndiswrapper-1.51/utils/
ndiswrapper-1.51/utils/Makefile
ndiswrapper-1.51/utils/ndiswrapper
ndiswrapper-1.51/utils/loadndisdriver.c
ndiswrapper-1.51/utils/ndiswrapper-buginfo
ndiswrapper-1.51/driver/
ndiswrapper-1.51/driver/divdi3.c
ndiswrapper-1.51/driver/hal.c
ndiswrapper-1.51/driver/iw_ndis.c
ndiswrapper-1.51/driver/iw_ndis.h
ndiswrapper-1.51/driver/loader.c
ndiswrapper-1.51/driver/loader.h
ndiswrapper-1.51/driver/longlong.h
ndiswrapper-1.51/driver/Makefile
ndiswrapper-1.51/driver/crt.c
ndiswrapper-1.51/driver/ndis.c
ndiswrapper-1.51/driver/ndis.h
ndiswrapper-1.51/driver/ndiswrapper.h
ndiswrapper-1.51/driver/ntoskernel.c
ndiswrapper-1.51/driver/ntoskernel.h
ndiswrapper-1.51/driver/ntoskernel_io.c
ndiswrapper-1.51/driver/pe_linker.c
ndiswrapper-1.51/driver/pe_linker.h
ndiswrapper-1.51/driver/pnp.c
ndiswrapper-1.51/driver/pnp.h
ndiswrapper-1.51/driver/proc.c
ndiswrapper-1.51/driver/rtl.c
ndiswrapper-1.51/driver/usb.c
ndiswrapper-1.51/driver/usb.h
ndiswrapper-1.51/driver/winnt_types.h
ndiswrapper-1.51/driver/workqueue.c
ndiswrapper-1.51/driver/wrapmem.h
ndiswrapper-1.51/driver/wrapmem.c
ndiswrapper-1.51/driver/wrapper.c
ndiswrapper-1.51/driver/wrapndis.h
ndiswrapper-1.51/driver/wrapndis.c
ndiswrapper-1.51/driver/lin2win.h
ndiswrapper-1.51/driver/win2lin_stubs.S

pj@pj-desktop:~/Desktop$ cd ndiswrapper-1.51
pj@pj-desktop:~/Desktop/ndiswrapper-1.51$ sudo aptitude install subversion
**There was some stuff here**
pj@pj-desktop:~/Desktop/ndiswrapper-1.51$ make distclean
**There was some stuff here**
pj@pj-desktop:~/Desktop/ndiswrapper-1.51$ make
**//There was a bunch of stuff here**
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/pj/Desktop/ndiswrapper-1.51/utils'
make: *** [all] Error 2
pj@pj-desktop:~/Desktop/ndiswrapper-1.51$ sudo make install
**// there was a long list of errors and stuff here**
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/pj/Desktop/ndiswrapper-1.51/utils'
make: *** [install] Error 2
pj@pj-desktop:~/Desktop/ndiswrapper-1.51$ ndiswrapper -v
The program 'ndiswrapper' is currently not installed. You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found

I got rid of some stuff here, if you want to read it all please tell me.
Thanks for your help!

---

### Post by peejaroni on 2008-04-07
never mind, a friend showed me the error of my ways!

---

### Post by Lazy-buntu on 2008-04-11
I follow your guide since I was having problems connecting:

Same exact problem as before: I can see networks, but cannot connect. My wireless adapter is eth1, not wlan0 (even after creating /etc/iftab where it says wlan0 mac "my mac address for wireless card without quotes")

Still no wired connection.

With cat-5 cable plugged in, or without it plugged in (using wireless)...if I run dhclient I get the usual:

...Offer from 192.168.2.1 (my router)
...Request
....DHsomething
....same DHsomething
...Request
...Offer

same loop for basically as long as I let it run

I am getting DHCP offers for an IP address, but I guess ubuntu isn't accepting them? I'm out of ideas...

I've got my own thread here: [http://ubuntuforums.org/showthread.php?p=4699111#post4699111](http://ubuntuforums.org/showthread.php?p=4699111#post4699111)
Please post anything concerning my issue there =)

---

### Post by Feenix3k on 2008-04-12
Thanks for this guide. With it I was able to move from 6.06 t0 7.04. I now have depentable g connection on my Dell 5150

---

### Post by Feenix3k on 2008-04-14
This guide works well with Ubuntu 7.04, but when I upgraded to 7.10 it all stopped working. It would seem a kernel change broke the whole set up. So what tweaking would this need to work in 7.10 ? And with the new 8.04 coming in just about a week, can this be made to work on it too?

---

### Post by kevdog on 2008-04-14
Again ndiswrapper is a kernel module -- you compile it against the header files of the kernel version, and then insert the module into the kernel (modprobe ndiswrapper).  When updating kernel versions (such as changing to Gutsy or Hardy), you need to recompile against the new set of kernel headers and then reinsert it into the new kernel. I believe I have mentioned this a few times in this thread -- I might have to add this to the guide itself.

---

### Post by Feenix3k on 2008-04-15
I am a newbie to linux, i had no idea the ndiswrapper was a kernel module or that modprobe ndiswrapper, put it into the kernel. But Thanks for helping me learn

After redoing the procedure a few times I relized thar the ndiswrapper-utils was not loading. Once I got them loaded it worked'

---

### Post by kevdog on 2008-04-15
??
ndiswrapper-utils.  Where you attempting to use synaptic and install this from repository?  How did you realized the utils package wasn't loading and what did you do to correct it?

---

### Post by Feenix3k on 2008-04-15
> **kevdog said:**
> ??
ndiswrapper-utils.  Where you attempting to use synaptic and install this from repository?  How did you realized the utils package wasn't loading and what did you do to correct it?


I had to use synaptic to install utils, I had an error saying it was not found.

As for 7.10, I get the following trying to do the make step


feenix@James-Laptop:~/ndiswrapper$ cd ndiswrapper-1.48
feenix@James-Laptop:~/ndiswrapper/ndiswrapper-1.48$ make distclean
make -C driver clean
make[1]: Entering directory `/home/feenix/ndiswrapper/ndiswrapper-1.48/driver'
Makefile:35: *** Cannot find kernel version in /lib/modules/2.6.22-14-386/build, is it configured?.  Stop.
make[1]: Leaving directory `/home/feenix/ndiswrapper/ndiswrapper-1.48/driver'
make: *** [clean] Error 2
feenix@James-Laptop:~/ndiswrapper/ndiswrapper-1.48$

---

### Post by kevdog on 2008-04-15
Strange indeed.  Did you install the header files and build essential utilities?

---

### Post by Feenix3k on 2008-04-15
> **kevdog said:**
> Strange indeed.  Did you install the header files and build essential utilities?

I cut and paste line by line. So if one of the line did it it was suppose to be done.

---

### Post by kevdog on 2008-04-15
Glad you got it working.  When I wrote the guide the most recent version was 1.48.  I believe its all the way up to 1.52 now.  If and when you upgrade to Hardy, you will need to recompile and install ndiswrapper again.  I would go ahead and grab the 1.52 version and start from there.

---

### Post by Feenix3k on 2008-04-15
I did use the newest stable for 7.10, it gave the same error as the one I posted earlyer about not finding the kernel .

I am planning a duel linux Ubuntu boot of 7.10 with my 7.04. So I may be able to find the catch for it not working in 7.10

---

### Post by Feenix3k on 2008-04-15
Success in 7.10 getting the wirerless to work. I had to add the utilats as I stated before. But in 7.10 their is a helper file found under the ndiswrapper called ndisgtk. with this installed the diver was installed and the kernel error went away.

---

### Post by Feenix3k on 2008-04-27
Since 8.04 has come out they have removed bcm43xx and replaced it with b43 and ssb. I need to black list this driver so I can get the bcmwl5.inf to integrate into the main driver. 

*-network:1
       description: Network controller
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:90:4b:63:82:b3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

---

### Post by puifais on 2008-04-27
Hi Kevdog,

Thanks for referring me to this page.  It's been very helpful and I was able to follow everything on your original guide with no error.  However, when I verify using lshw -C network, I notice that it doesn't say anything about my newly installed D-link WUA-1340 USB Wireless Networking Adapter.  It just completely ignores the fact that I have a driver at all.  When I go to System > Administration > Windows Wireless Drivers, nowever, I can see my dr71wu driver showed up.  So obviously, the inf file was read and went in, but it's not being used to put my wireless to work :(  Since you seem to be asking people to post results of different commands, I'm gonna do that as well even though it takes up so much space.  Please let me know what else I can do to help you help me :)

> puifais@Fabian:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:19:db:74:9a:f8
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 latency=32 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:15:e9:4c:ab:c0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.44 multicast=yes wireless=IEEE 802.11g

> puifais@Fabian:~$ ndiswrapper -l
dr71wu : driver installed
	device (07D1:3C04) present (alternate driver: rt73usb)

> puifais@Fabian:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]

> puifais@Fabian:~$ lspci -n
00:00.0 0600: 1106:0204
00:00.1 0600: 1106:1204
00:00.2 0600: 1106:2204
00:00.3 0600: 1106:3204
00:00.4 0600: 1106:4204
00:00.7 0600: 1106:7204
00:01.0 0604: 1106:b188
00:0f.0 0104: 1106:3149 (rev 80)
00:0f.1 0101: 1106:0571 (rev 06)
00:10.0 0c03: 1106:3038 (rev 81)
00:10.1 0c03: 1106:3038 (rev 81)
00:10.2 0c03: 1106:3038 (rev 81)
00:10.3 0c03: 1106:3038 (rev 81)
00:10.4 0c03: 1106:3104 (rev 86)
00:11.0 0601: 1106:3227
00:11.5 0401: 1106:3059 (rev 60)
00:12.0 0200: 1106:3065 (rev 78)
00:18.0 0600: 1022:1100
00:18.1 0600: 1022:1101
00:18.2 0600: 1022:1102
00:18.3 0600: 1022:1103
01:00.0 0300: 1002:5159

> puifais@Fabian:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"07B407403370"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:12:0E:7D:AD:58   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=46/100  Signal level=-84 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

> puifais@Fabian:~$ iftab
bash: iftab: command not found

Thank you so much!

---

### Post by kevdog on 2008-04-27
Dont worry about the iftab file -- that Feisty and pre-distributions.  

You are running a usb device that does not connect through the pci bridge -- rather directly to the southbridge controller.  So, the command 
lspci (ls pci devices) will not work
lsusb (ls usb devices) does work, however this command doesnt provide a lot of useful output similar to lspci

ndiswrapper is technically a custom kernel module.  Its custom b/c you needed to compile it -- it doesnt come by default in the vanilla kernel

What you want to do is to make sure you dont have conflicting kernel modules loading -- that would be ndiswrapper, rt73usb, and possibly any other rt module.

To list the kernel modules currently loading in the user space
lsmod (list modules)

lsmod

You can post the results here to take a look at.

---

### Post by puifais on 2008-04-27
Here you go:

> puifais@Fabian:~$ lsmod
Module                  Size  Used by
af_packet              23812  2 
nls_iso8859_1           4992  0 
nls_cp437               6656  0 
vfat                   14464  0 
fat                    54556  1 vfat
isofs                  36388  0 
udf                    88612  0 
ipv6                  267780  8 
binfmt_misc            12808  1 
radeon                124192  2 
drm                    82580  3 radeon
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
cpufreq_conservative     8712  0 
cpufreq_stats           7104  0 
cpufreq_ondemand        9740  0 
cpufreq_userspace       5284  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2688  0 
video                  19856  0 
output                  4736  1 video
sbs                    15112  0 
sbshc                   7680  1 sbs
container               5632  0 
dock                   11280  0 
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
ndiswrapper           193564  0 
lp                     12324  0 
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
rt73usb                27136  0 
rt2x00usb              12800  1 rt73usb
rt2x00lib              22528  2 rt73usb,rt2x00usb
rfkill                  8592  1 rt2x00lib
input_polldev           5896  1 rt2x00lib
crc_itu_t               3072  1 rt2x00lib
mac80211              165652  2 rt2x00usb,rt2x00lib
usbhid                 31872  0 
cfg80211               15112  1 mac80211
hid                    38784  1 usbhid
usb_storage            73664  0 
libusual               19108  1 usb_storage
snd_via82xx            29464  3 
gameport               16008  1 snd_via82xx
snd_ac97_codec        101028  1 snd_via82xx
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11400  2 snd_via82xx,snd_pcm
snd_mpu401_uart         9728  1 snd_via82xx
evdev                  13056  3 
snd_seq_dummy           4868  0 
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  2 snd_mpu401_uart,snd_seq_midi
button                  9232  0 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                  4224  0 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
k8temp                  6656  0 
i2c_viapro              9876  0 
amd64_agp              13444  1 
agpgart                34760  2 drm,amd64_agp
snd                    56996  18 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_core               24832  1 i2c_viapro
soundcore               8800  1 snd
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
ata_generic             8324  0 
pata_acpi               8320  0 
floppy                 59588  0 
via_rhine              26632  0 
mii                     6400  1 via_rhine
ehci_hcd               37900  0 
uhci_hcd               27024  0 
pata_via               13316  2 
sata_via               12420  0 
usbcore               146028  9 ndiswrapper,rt73usb,rt2x00usb,usbhid,usb_storage,libusual,ehci_hcd,uhci_hcd
libata                159344  4 ata_generic,pata_acpi,pata_via,sata_via
scsi_mod              151436  5 usb_storage,sg,sr_mod,sd_mod,libata
thermal                16796  0 
processor              36872  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  5 


---

### Post by kevdog on 2008-04-27
I can see the problem

I not quizzing you, but I want you to re-read my post above, and then look at your lsmod list, and tell me what drivers are in conflict.

Again Im not quizzing you but teaching you how to debug your own wireless problems.  Once you see a problem you will have gained knowledge -- having me tell you directly doesn't teach you anything.

---

### Post by puifais on 2008-04-27
Yes, I can see the rt stuff which is an alternative driver for my wireless adapter.  But I don't really know how to uninstall it or whether to uninstall it cuz it might be a good idea to keep an alternative option?

Thanks

---

### Post by kevdog on 2008-04-27
Your not going to uninstall it -- you are going to prevent the alternate kernel modules from loading into the kernel at boot.  The files can be there, however just not inserted into the kernel.

---

### Post by puifais on 2008-04-27
That's an awesome solution!  How do I make the alternate kernel modules stop loading?  Something along the line of insmod and rmmod?  (I just googled it.  Don't actually know what these are, sorry)

---

### Post by kevdog on 2008-04-27
You remove them for the current session

sudo modprobe -r <module_name>

To make sure they don't load at boot for the successive times you turn the computer on, you blacklist the modules in the

/etc/modprobe.d/blacklist 

file.

---

### Post by puifais on 2008-04-27
That was it, yippeee!!  Thank you so much!

---

### Post by kevdog on 2008-04-28
Glad it worked, however, it would be great if you posted your solution for the next schlep that came across this link (not to mention it would help me out a lot since it would be one less example I would have to go through again :))

---

### Post by puifais on 2008-04-28
Will do.  Did you mean start a new thread or a summary of what I did right here?

---

### Post by kevdog on 2008-04-28
You can do either however its nice to give back to others when you find a good solution.  That's what is so good about the Ubuntu community.

---

### Post by vec on 2008-04-28
seems like everytime i need help i find the answer hehe, anyway here is what my problem was and how to fix it. 
[http://ubuntuforums.org/showthread.php?t=760568](http://ubuntuforums.org/showthread.php?t=760568)
in case anyone is having any problems with hp computer light not turning blue, there ya go :)

---

### Post by Dural on 2008-05-08
I installed ndiswrapper, ndiswrapper-utils, and the Windows Wireless Drivers application from the Ubuntu Hardy Heron CD using Synaptic Package Manager. I installed the Windows XP drivers for a Netgear WPN111. The light is currently blinking, but when I try to set up the wireless connection, it does not appear as an option in the Network Manager. I tried to look for wlan0, but it does not appear. 

I checked the Troubleshooter for Ndiswrapper on their site and they said that this occurs when the device is not present or an alternative driver is using the card, but I installed the right drivers. 

Here is the log that I got:
> testuser@testuser-desktop:~$ dmesg | grep ndiswrapper
[   35.145700] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   35.546531] ndiswrapper: driver athwpn (,12/05/2003,1.00.001) loaded
[   35.753136] usbcore: registered new interface driver ndiswrapper
[  140.884953] usbcore: deregistering interface driver ndiswrapper
[  140.892041] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  141.007161] ndiswrapper (wrap_pnp_start_usb_device:700): reset failed: -19
[  141.008804] ndiswrapper (load_wrap_driver:112): couldn't load driver netwpn11; check system log for messages from 'loadndisdriver'
[  141.204329] ndiswrapper (load_wrap_driver:112): couldn't load driver netwpn11; check system log for messages from 'loadndisdriver'
[  141.204347] usbcore: registered new interface driver ndiswrapper
[  147.410345] usbcore: deregistering interface driver ndiswrapper
[  147.420183] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  147.628544] ndiswrapper: driver netwpn11 (NETGEAR,09/26/2005,1.5.0.2102) loaded
[  147.629039] ndiswrapper (ZwQueryValueKey:2359): not fully implemented (yet)
[  147.972837] usbcore: registered new interface driver ndiswrapper
[  150.469860] usbcore: deregistering interface driver ndiswrapper
[  150.491166] ndiswrapper: device wlan0 removed
[  150.502177] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  150.691883] ndiswrapper: driver athwpn (,12/05/2003,1.00.001) loaded
[  161.520057] usbcore: registered new interface driver ndiswrapper
[  195.117743] usbcore: deregistering interface driver ndiswrapper
[  195.126212] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  195.241038] ndiswrapper: driver athwpn (,12/05/2003,1.00.001) loaded
[  202.942930] usbcore: registered new interface driver ndiswrapper
[ 2124.046992] usbcore: deregistering interface driver ndiswrapper
[ 2124.054393] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[ 2124.173612] ndiswrapper: driver netwpn11 (NETGEAR,09/26/2005,1.5.0.2102) loaded
[ 2124.174080] ndiswrapper (ZwQueryValueKey:2359): not fully implemented (yet)
[ 2129.964336] ndiswrapper (NdisWriteErrorLogEntry:191): log: C0001389, count: 4, return_address: f8d82bbb
[ 2129.964341] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0xde6e9800
[ 2129.964343] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0x28
[ 2129.964346] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0xf8b54000
[ 2129.964348] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0xf8b54000
[ 2129.964498] ndiswrapper (mp_init:216): couldn't initialize device: C0000001
[ 2129.964502] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
[ 2129.964508] ndiswrapper (mp_halt:259): device de6e8480 is not initialized - not halting
[ 2129.964510] ndiswrapper: device eth%d removed
[ 2129.964518] ndiswrapper: probe of 2-5:1.0 failed with error -22
[ 2129.964527] usbcore: registered new interface driver ndiswrapper
[ 2215.571819] usbcore: deregistering interface driver ndiswrapper
[ 2215.571900] ndiswrapper (ntoskernel_exit:2708): object f1256920(2) was not freed, freeing it now
[ 2215.578432] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[ 2215.693921] ndiswrapper: driver athwpn (,12/05/2003,1.00.001) loaded
[ 2223.396859] usbcore: registered new interface driver ndiswrapper


---

### Post by kevdog on 2008-05-08
Sounds like a driver issue to me:

[ 2129.964502] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
[ 2129.964508] ndiswrapper (mp_halt:259): device de6e8480 is not initialized - not halting
[ 2129.964510] ndiswrapper: device eth%d removed

is the wpn111 listed as a supported device on the ndiswrapper website?

Have you seen this tutorial?
[http://ubuntuforums.org/showthread.php?t=652910](http://ubuntuforums.org/showthread.php?t=652910)

---

### Post by bardu0708 on 2008-05-10
Ok, I read a lot of tutorials and forums now and things that work for other people just don't work for me.

First of all, I don't have any internet connection when I'm running Ubuntu 8.04 (I'm dual booting with Vista so that's how I'm online) so I try to do the first few steps (yes the cd-rom is in the drive):

[I]osiris@osiris-laptop:~$ sudo apt-cdrom add 
Bruker CD-ROM monteringspunkt /cdrom/ 
Avmonterer CD-ROM 
Venter på CD-en... 
Sett inn en disk i lagringsenheten og trykk Enter 
Monterer CD-ROM... 
E: Failed to mount the cdrom. 
osiris@osiris-laptop:~$ [/I]

And if I try the second command it says I'm not connected (no surprise there)

[I]osiris@osiris-laptop:~$ sudo aptitude install build-essential linux-headers-2.6.24-16-generic 
[sudo] password for osiris: 
Leser pakkelister ... Ferdig 
Skaper oversikt over avhengighetsforhold       
Reading state information ... Ferdig    
Reading extended state information      
Initializing package states ... Ferdig 
Writing extended state information ... Ferdig 
Building tag database ... Ferdig             
Couldn't find any package whose name or description matched "build-essential" 
Couldn't find any package whose name or description matched "build-essential" 
No packages will be installed, upgraded, or removed. 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
Need to get 0B of archives. After unpacking 0B will be used. 
Writing extended state information ... Ferdig 
Leser pakkelister ... Ferdig                 
Skaper oversikt over avhengighetsforhold       
Reading state information ... Ferdig    
Reading extended state information      
Initializing package states ... Ferdig 
Building tag database ... Ferdig      
osiris@osiris-laptop:~$ [/I]

This doesn't work either (as a result of the first error?)

If I go on with extracting the .tar (which is no problem) and distclean or make uninstall (am unsure what to do there, some say distclean and others make uninstall) I have no problems either.
But when I run sudo make I get a tonload of errors and warnings.

Can you tell me what I'm doing wrong?
Thanks in advance.

---

### Post by kevdog on 2008-05-10
I think the first thing to solve is why your CDrom can not be mounted.  If you can mount it and repeat the steps, Im fairly certain all your problems will go away.

---

### Post by nghia on 2008-05-15
hello i'm a newbie to unbuntu. 
i have an airlink awll3028.

i'm stuck. please help.

i followed the steps to compile and install ndiswrapper and i get this error message.

nghia@nghia-laptop:~/ndiswrapper/ndiswrapper-1.48$ make
make -C driver
make[1]: Entering directory `/home/nghia/ndiswrapper/ndiswrapper-1.48/driver'
make -C /usr/src/linux-headers-2.6.24-16-generic SUBDIRS=/home/nghia/ndiswrapper/ndiswrapper-1.48/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/nghia/ndiswrapper/ndiswrapper-1.48/driver/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[2]: *** [_module_/home/nghia/ndiswrapper/ndiswrapper-1.48/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/nghia/ndiswrapper/ndiswrapper-1.48/driver'
make: *** [all] Error 2
nghia@nghia-laptop:~/ndiswrapper/ndiswrapper-1.48$ 

any ideas anyone?

---

### Post by kevdog on 2008-05-15
Try compiling the latest 1.52 version.  Post if you have a problem.

---

### Post by nghia on 2008-05-15
thanks for the quick reply kevdog

tried the latest version, and success! thanks 

nghia@nghia-laptop:~/ndiswrapper-1.52$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-16-generic SMP mod_unload 586 
nghia@nghia-laptop:~/ndiswrapper-1.52$ 

i'm going to move forward and will post results.
thanks again.

---

### Post by nghia on 2008-05-15
yeah it works.. thanks everybody.

---

### Post by Fly135s on 2008-05-16
kevdog,
You rock!!!:guitar:
These directions used with version 1.52 allowed me to get a Belkin F5D8013 Wireless N PCMCIA card up and running with the drivers on the CD.  I am running Hardy and am quite the noob with Linux but am fluent with MS.  Many thanks.

Friar

---

### Post by imapostdoc on 2008-05-16
Hello kevdog and other experts,

I have followed your instructions and have been successful to install ndiwrapper 1.52 and the driver bcmwl5. This is what get (and I should)

$ lspci | grep Network
01:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-16-generic/misc/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-16-generic SMP mod_unload 586 

$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: ssb)

However, from this point I don't find 'wlan0' anywhere. These are the outputs
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
$ lshw -C network
  *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
...

what have I missed? I'm using Hardy Heron 8-04, installed freshly.
Thank you very much and best regards,
            Peter

---

### Post by kevdog on 2008-05-17
Try unloading some drivers:

sudo rmmod b43
sudo rmmod b44
sudo rmmod b43legacy 
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb
sudo modprobe b44


If that works, then to make it permanent (Just cut and paste this to the terminal) -- This way evertime you modprobe ndiswrapper (or if it gets modprobed at startup, the modules will be unloaded/loaded in the right order):

echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper

---

### Post by ThisisGeero on 2008-05-27
I'm trying to install a wg111v3 netgear wireless adapter onto one of our desktop computers.  But when I get to the "make" section of the instructions I receive this following error.  Any ideas? I'm extremely frustrated right now to say the very least. 



chung@chung-desktop:~$ cd ndiswrapper-1.49
chung@chung-desktop:~/ndiswrapper-1.49$ make
make -C driver
make[1]: Entering directory `/home/chung/ndiswrapper-1.49/driver'
make -C /usr/src/linux-headers-2.6.24-16-generic SUBDIRS=/home/chung/ndiswrapper-1.49/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/chung/ndiswrapper-1.49/driver/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[2]: *** [_module_/home/chung/ndiswrapper-1.49/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/chung/ndiswrapper-1.49/driver'
make: *** [all] Error 2

---

### Post by ThisisGeero on 2008-05-27
nvm didn't read the above posts.  thanks kevdog.

---

### Post by sharkey77 on 2008-05-28
WLAN0 shows as wired in network manager and lshw -C network

Now what?

> *-network:1
       description: [COLOR="Red"]Ethernet interface[/COLOR]
       product: RTL8180L 802.11b MAC
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@0000:02:09.0
       logical name: wlan0
       version: 20
       serial: 00:40:f4:5e:55:f8
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=ndiswrapper+netr8180 driverversion=1.52+OEM,01/28/2003,5.119.0127.2 latency=32 maxlatency=64 mingnt=32 module=ndiswrapper multicast=yes

iwconfig

> iwconfig
mediapc@MediaPC:~/ndiswrapper/ndiswrapper-1.53/driver$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     no wireless extensions.

mediapc@MediaPC:~/ndiswrapper/ndiswrapper-1.53/driver$ 

Thanks for your assistance.

---

### Post by kevdog on 2008-05-28
Sounds like a network manager bug.  If you do iwlist scan this should show the wireless networks. wlan0 since its an 80211b card is definitely wireless.  Is NW manager not working?

---

### Post by sharkey77 on 2008-05-28
Dmesg

>  21
[   32.192606] Pci: Setting Latency Timer Of Device 0000:00:1f.5 To 64
[   32.517924] Intel8x0_measure_ac97_clock: Measured 55031 Usecs
[   32.517929] Intel8x0: Clocking To 48000
[   34.803969] Loop: Module Loaded
[   34.871143] Lp: Driver Loaded But No Devices Found
[   35.082826] Ndiswrapper Version 1.52 Loaded (smp=yes, Preempt=no)
[   35.176724] Ndiswrapper: Driver Netr8180 (oem,01/28/2003,5.119.0127.2003) Loaded
[   35.177047] Acpi: Pci Interrupt 0000:02:09.0[a] -> Gsi 21 (level, Low) -> Irq 22
[   35.237069] Ndiswrapper: Using Irq 22
[   35.504800] Wlan0: Ethernet Device 00:40:f4:5e:55:f8 Using Ndis Driver: Netr8180, Version: 0x100, Ndis Version: 0x500, Vendor: 'realtek Rtl8180 Wireless Lan (mini-)pci Nic                           ', 10ec:8180.5.conf
[   35.504891] Usbcore: Registered New Interface Driver Ndiswrapper

---

### Post by sharkey77 on 2008-05-28
> **kevdog said:**
> Sounds like a network manager bug.  If you do iwlist scan this should show the wireless networks. wlan0 since its an 80211b card is definitely wireless.  Is NW manager not working?

Command?

```
iwlist scan
```

---

### Post by sharkey77 on 2008-05-28
output

> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning.

---

### Post by sharkey77 on 2008-05-28
The only thing I see that I may have done wrong is I have my driver directory as a sub directory to ndiswrapper instead of under home.

I don't think that would be a problem since the driver shows installed though.

Thanks again for your help.

---

### Post by sharkey77 on 2008-05-29
Bump before I go buy a new wireless card that I know works OTB :)

---

### Post by kevdog on 2008-05-30
Buy an atheros based card compatible with the madwifi drivers (check the madwifi website for possible cards).  I have one Atheros based card (in addition to 2 Broadcom cards), and it is my favorite -- worked truly OTB :)

---

### Post by marksbcss on 2008-06-03
1st Much grass and kudos to Kevdog.

I'm running Kubuntu 8.04.

I've gone through installation and troubleshooting of both the Airlink101 AWLC3028 cardbus (card) and AWLL3028 USB adapters, both using ndiswrapper. (I'm using the USB now.)

While you can down load the Windows 98 .inf files (8185 and/or 8187b, respectively) from the [www.realtek.com.tw](www.realtek.com.tw) site, you can just as easily use the files on the CDROM that comes with the adapters.

Installing and using the ndiswrapper gui ndisgtk (Someone else suggested this) seems to do most if not all of the gruntwork. 

Follow Wieman01's How-To for setting up the wlan0/wlan1 /etc/network/interfaces entries.

You may need to sudo /etc/init.d/networking restart to take care of a reported bug after boot, or put it in the .etc/rc.local (without sudo). That got the AWLC working. BTW ifdown wlan0 (or 1), ifup wlan0 (or 1) seems to work as well.

The AWLL at this point had a proper IP address but would not actually work. The trick turned out to be opening Knetworkmanager for manual configuration. It showed the wlan1 USB with the right IP address. Select the wlan1 by clicking on it. Then close knetworkmanager. (System settings network setttings, administrator, click on wlan1, close, [discard changes], also worked.)

Good luck

Mark

---

### Post by marksbcss on 2008-06-03
Disregard. I noticed a typo in my last message. After submitting a correction, I found I could just edit it.

Mark

---

### Post by brons2 on 2008-06-24
> **marksbcss said:**
> 1st Much grass and kudos to Kevdog.

I'm running Kubuntu 8.04.

I've gone through installation and troubleshooting of both the Airlink101 AWLC3028 cardbus (card) and AWLL3028 USB adapters, both using ndiswrapper. (I'm using the USB now.)

While you can down load the Windows 98 .inf files (8185 and/or 8187b, respectively) from the [www.realtek.com.tw](www.realtek.com.tw) site, you can just as easily use the files on the CDROM that comes with the adapters.

Installing and using the ndiswrapper gui ndisgtk (Someone else suggested this) seems to do most if not all of the gruntwork. 

Follow Wieman01's How-To for setting up the wlan0/wlan1 /etc/network/interfaces entries.

You may need to sudo /etc/init.d/networking restart to take care of a reported bug after boot, or put it in the .etc/rc.local (without sudo). That got the AWLC working. BTW ifdown wlan0 (or 1), ifup wlan0 (or 1) seems to work as well.

The AWLL at this point had a proper IP address but would not actually work. The trick turned out to be opening Knetworkmanager for manual configuration. It showed the wlan1 USB with the right IP address. Select the wlan1 by clicking on it. Then close knetworkmanager. (System settings network setttings, administrator, click on wlan1, close, [discard changes], also worked.)

Good luck

Mark

I used ndisgtk as well, and the Win98 driver from the CD that came with the card...success at last!

Now you've got me worried about rebooting though.  Argh.  Oh well, I suppose I'll keep my fingers crossed.  I am truly a Linux noobie so we'll see what happens.

---

### Post by sharkey77 on 2008-06-24
I bought a D-Link WDA-2320, worked out of the box.

---

### Post by otterstrom on 2008-06-29
Hi, I have Ubuntu 8.04 installed. I have been trying to get an Airlink 101 AWLH3028 Wireless card to work. I have read that some people got this card to work with the ndiswrapper version 1.52.

I followed the instructions on this thread with the exception of installing 1.52 instead of 1.48. I did not have any error messages. 

I skipped the instructions for /etc/iftab file since I have ubuntu 8.04. However I did try to follow the instructions for Modification of /etc/network/interfaces file because I was not having success. 

Even though I did not get any error messages, I was unable to get the wireless card working and now my wired ethernet card is not working either!

(also, once the steps are complete, is the wireless connection automatic, or do I have to connect using the n-m applet? If I have to connect, I do not know how. Also I turned off any encryption on my wireless router, but still not success)

When I enter the command lshw -C network, this is what I get:

  *-network  UNCLAIMED             
       description: Ethernet Controller
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Seminconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list 
       configuration: latency=32 maxlatency=64 mingnt=32

What is noticeably missing is "logical name: wlan0" I don't know why this is missing or if it is significant. Please Help!

---

### Post by kevdog on 2008-06-29
The big statement stating UNCLAIMED is b/c the driver is not claiming your device -- hence without claiming you will not get assigned a wlan0 interface.  What driver are you using -- realtek's are tricky?  What is output of 
ndiswrapper -l

---

### Post by otterstrom on 2008-06-29
Thanks for your quick reply

ndiswrapper -l yields:

net8187b : driver installed

(had I known this card was so tricky I would not have bought it!)

---

### Post by sisap on 2008-06-30
Hello.

I think I'm having same trouble like otterstrom, I'm using Hardy, and trying to use airlink 101 wireless USB. When I installed ndiswrapper, I didn't get any error message.

The differences are, when I ran ndiswrapper -l, I only get "net8187b : driver installed", I don't get any line such like "device (14E4:4320) present "

Also, lshw -C network, I don't even see "UNCLAIMED", I only see my default realteck wired lan card which I'm currently using.

FYI - 

sisap@sisap-laptop:~/driver$ ndiswrapper -l
net8187b : driver installed

sisap@sisap-laptop:~/driver$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:91:db:17
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=69.106.204.196 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes


sisap@sisap-laptop:~/driver$ echo "ndiswrapper" | sudo tee -a /etc/modules
ndiswrapper

sisap@sisap-laptop:~/driver$ dmesg|grep ndis
[   43.020710] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   43.070480] usbcore: registered new interface driver ndiswrapper


sisap@sisap-laptop:~/driver$ ls -l /etc/ndiswrapper/net8187b/
total 300
-rw-r--r-- 1 root root    648 2008-06-29 19:46 0BDA:8187.F.conf
-rw-r--r-- 1 root root    648 2008-06-29 19:46 0BDA:8189.F.conf
-rw-r--r-- 1 root root  14199 2008-06-29 19:46 net8187b.inf
-rw-r--r-- 1 root root 275968 2008-06-29 19:46 rtl8187b.sys


It would be really appreciate if you can give me any adivice.

Thanks.

---

### Post by kevdog on 2008-06-30
Are you using 32 or 64 bit ubuntu?

---

### Post by otterstrom on 2008-06-30
I am using 32 bit.

I installed Mythbuntu 8.04 initially then later installed the ubuntu desktop.

---

### Post by kevdog on 2008-06-30
Have you tried the win98 driver along with ndiswrapper instead of the winxp driver?  In the tutorial on page 1 I think I linked to a tutorial written by panurge that explained where to get this win98 driver.  I know it worked with Gutsy, I haven't had any feedback positive or negative in Hardy.  I know for 64 bit installs its problematic, but since you have a 32 bit install I believe it should work.

---

### Post by otterstrom on 2008-06-30
I read the same post as you described so I started off by trying the Win98 driver. Should I try the XP driver?

---

### Post by kevdog on 2008-06-30
Yes try the xp one - something is fishy here however!

---

### Post by otterstrom on 2008-07-01
Ok, I tried the winXP drivers and I think that I may be on the right track now. After going through the steps I enter the command lshw -C network, this is what I get:

*-network 
description: Wireless interface
product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
vendor: Realtek Seminconductor Co., Ltd.
physical id: 5
bus info: pci@0000:01:05.0
logical name: wlan0
version: 20
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ndiswrapper+net8185 driverversion=1.52+Airlink101,5.109 ip=192.168.0.100 latency=32 maxlatency=64 mingnt=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

This looks like I am on the right track :)
and when I click on the nm applet, there is an option for manual configuration that list a wireless option now. It shows both my unencrypted and encrypted routers that I have set up. But I cannot seem to connect to either.

Also, when I plug in an ethernet cable it is still not working either.

Thanks again for your help.

---

### Post by kevdog on 2008-07-01
Ok, if you have access to the router -- turn off all encrytpion for  now -- add it later.  Then try to make a manual connection


sudo ifconfig eth0 down
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
sudo iwconfig essid <essid of router>
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

What happens?

---

### Post by sisap on 2008-07-02
Hello.

Like I posted a few days ago, I'm also still having trouble on hardy. Anyway, after little more tries (after I did "make manuall connecton"), I got wireless connection.

But, there is still one more problem.
On shell command line, ping works fine, and also telnet to [www.yaho.com](www.yaho.com) 80 port works fine too, like belows.

sisap@sisap-laptop:~$ telnet [www.yahoo.com](www.yahoo.com) 80
Trying 209.131.36.158...
Connected to [www.yahoo-ht3.akadns.net](www.yahoo-ht3.akadns.net).
Escape character is '^]'.
^]

Problem is, my firefox v3.0 keep saying "Firefox is currently in offline mode and can't browse the Web"

I tried other ways to get around it, but stil have firfox "offline" problem. Again, telnet, ping all works fine, means wireless connection itslef is good. But I have no idrea why firefox keep saying "offline"

Any advice, please??

Thanks,

---

### Post by otterstrom on 2008-07-02
Success!

After getting the Airlink wireless card to work with the XP drivers,  I figured out that I was having a problem with my router. So after I solved that, I was able to connect without having to use the above mentioned manual commands. 

Thanks kevdog for all your help!!!!!!!!!!

(The wireless seems to be going very slow, perhaps that is a subject for a different thread.)

---

### Post by kevdog on 2008-07-02
sisap

Not sure that is very strange.  Can you just try the program lynx for a minute.  Its a command line browser.  You may need to install it first:

sudo aptitude install lynx

Then 

lynx [http://google.com](http://google.com)

What happens.

---

### Post by nyrb4life on 2008-07-02
Im trying to install my wusb300n linksys wireless card and im following this [http://ge.ubuntuforums.com/showthread.php?t=530772]("http://ge.ubuntuforums.com/showthread.php?t=530772").

I have amd 64 and my wireless card doesnt want to install. The drivers are installed but the card doesnt work. 

When I type in
```
sudo modprobe ndiswrapper
```
Nothing happens.

And when I type in
```
sudo dmesg | grep ndis
```
A load of text and stuff comes onto the screen. Such as "-a inffile <devid><driver> (dangerous)"

Please help me!!

---

### Post by Abu_Dayya on 2008-07-02
Hi kevdog

i'm trying to fix my friend wireless. i did the following:

- installed ndiswrapper and verified installation is correct
- installed inf file and verified it was installed
- loaded ndiswrapper into kernel. then loaded it in /etc/modules
- reboot
- ubuntu restricted driver manager detected bcm43xx as a driver, so i blacklisted it 
- reboot
- this is what i get now

```

maien@maien-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:14:22:a1:1d:59  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 

eth0:avahi Link encap:Ethernet  HWaddr 00:14:22:a1:1d:59  
          inet addr:169.254.4.109  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:10 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1474 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1474 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:74084 (72.3 KB)  TX bytes:74084 (72.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:ce:1d:75:ce  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-CE-1D-75-CE-00-00-00-00-00-00-00-00-00-00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

maien@maien-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:1
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 02
       serial: 00:14:22:a1:1d:59
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=32 module=ssb multicast=yes
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:ce:1d:75:ce
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
maien@maien-laptop:~$ clear

maien@maien-laptop:~$ sudo ndiswrapper -l
[sudo] password for maien: 
bcmwl5 : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)
maien@maien-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:22:a1:1d:59  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 

eth0:avahi Link encap:Ethernet  HWaddr 00:14:22:a1:1d:59  
          inet addr:169.254.4.109  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:10 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1474 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1474 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:74084 (72.3 KB)  TX bytes:74084 (72.3 KB)

maien@maien-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:1
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 02
       serial: 00:14:22:a1:1d:59
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=32 module=ssb multicast=yes
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:ce:1d:75:ce
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
maien@maien-laptop:~$ lspci | grep -i network
02:01.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
maien@maien-laptop:~$ 


```


what to do now?
thanks

---

### Post by kevdog on 2008-07-02
Abu

Do a search for a wiki written by Jamie Jackson -- Feisty no Fluff.  It contains a workaround for the Hardy bug to avoid loading the b43-pci-bridge driver at boot.  Its an easy solution.

---

### Post by sisap on 2008-07-02
kevdog, I'm the one who is struggling on hardy. I googled and found this link

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/191889](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/191889)

Sounds like it firefox3 bug on hardy, I installed opera, it works fine now.

So now I'm moving to WPA2 encryption, good luck to me :)

Again, thanks for your help :)

---

### Post by kevdog on 2008-07-02
Yes its a bug involving network manager conflicting with firefox.  Thanks for shooting that one down.  Here was the proposed workaround which is kind of a hack:

 I've found a kludgy "fix" for this (that doesn't just involve removing nm, since it's wireless and wired handling are nice). In my case, I have a Inspiron 2200 with wifi set via ndiswrapper (which works fine) and an aircard (Verizon PC5740) which worked except for the "Offline mode" problem. So it's the case where if I don't have wifi, and dial via CDMA, I get the "Work Offline" stuff going on.

     So, if I go into /etc/dbus-1/system.d/NetworkManager.conf, I inserted in line 18 (all on one line):
<deny send_interface="org.freedesktop.NetworkManager" send_member="state"/>

     (That's in the 'policy at_console="true" ' section of the file in case yours is arranged a little differently for whatever reason.)

     This file seems to be checked on-the-fly, I could change this and see an immediate effect on firefox (although I rebooted to check for side effects).

     Consequences:
     This blocks firefox and any other app's attempt to get the online/offline state from NetworkManager, which makes it (and probably any other apps that try to check NetworkManager) decide Networkmanager is not there and assume online state. It ALSO blocks nm-applets access to this though...
     Since nm-applet can't get the online/offline state from NetworkManager either, it doesn't show online state properly (it'll show the exclamation mark while the network is up and running fine for static IP wifi and ethernet)... For regular ol' DHCP wifi, it does still show the signal bars (since blocking "status" doesn't block wifi signal strength info).
     Also, under "manual configuration" the "Roaming mode" text changes to "This network interface is not configured", and the checked "Roaming mode" checkboxes change to uncheckd "Enable this connection" checkboxes. But the interface seems consistent and to behave itself. Problem solved as far as I'm concerned, until I got to NetworkManager 0.7!

---

### Post by ZippyP on 2008-07-03
THANK YOU Kevdog!!!


With posts like this I'm learning Linux pretty fast.  This was one of the most helpful posts I have used so far.  I placed the Ndiswrpper ver. 1.53 on a Dell 1150 with the Broadcom standard wired network connection and XUbuntu.  I tried two other times and failed until I used your directions.  It worked the first time and My neighbors laptop internet connection is working great.
Well written... Great Work...=D> Bravo!

I do have one question.  Will Ndiswrapper work with any type of windows drivers such as a TV tuner card being used with Myth TV?  If so this will save many more hours trying to get one of my cards working since there is no proper working Linux drivers for it.

Thanks again.

---

### Post by kevdog on 2008-07-03
ndiswrapper is only for wireless devices -- nothing more -- sorry!

---

### Post by ZippyP on 2008-07-03
Kevdog, 
Is there a general wrapper for linux? It would be nice if there was one since it would make it easy for some non Linux drivers to be useful.  Anyway This wrapper saved my bottom with this old laptop of my neighbors.  The thing works great.

Thanks again and take care.

ZippyP

---

### Post by kevdog on 2008-07-03
Don't know of any general wrapper program?  Most things don't need a wrapper.  MythTV is a very well established project -- they don't list tvtuner cards on their website that work with the project?

---

### Post by ZippyP on 2008-07-03
Hello again,

They have been working on a patch for my card for some time now in v4l, but so far after more than a month of messing with it, it still does not work.  The card is made by TechnoTrend. TT-3200 S2 (stb0899) is what they call it on the forums.  It is the patches that do not work, or user error on my part. I am a satellite broadcast engineer and this card has quite a few formats that I could use to monitor some client's uplinks.  So far I can get it to work in, forgive me, XP pro, but not in Linux.

Thanks

ZippyP

---

### Post by kevdog on 2008-07-04
Not sure, may want to make a post outside of this thread somewhere.

---

### Post by ktconsulting on 2008-07-06
Extract from above: "and place the file in the ~/ndiswrapper directory"  How do I create a directory?

---

### Post by kevdog on 2008-07-06
cd ~
mkdir ndiswrapper
cd ndiswrapper

---

### Post by slstokes on 2008-07-16
Hi. I am brand new to Ubuntu. It installed great except the wireless. I am following these instructions, very carefully (I think) and ran into an error. I am not very linux savvy at all, so I am including the terminal output from my work. I do appologize that it's so long, but want you to see what I've done. There were errors with the make install of ndiswrapper and I got a message 'no ndiswrapper utils found'. I hope you can tell me what I did wrong and how I can fix it. You will see I did the distclean and make commands twice (second time after I got the error), I hope that didn't cause further issues.

Thanks! 

Sharon

from my terminal session:
dave@(none):~/ndiswrapper$ tar -zxvf ndiswrapper-1.48.tar.gz
ndiswrapper-1.48/
ndiswrapper-1.48/Makefile
ndiswrapper-1.48/utils/
ndiswrapper-1.48/utils/Makefile
ndiswrapper-1.48/utils/loadndisdriver.c
ndiswrapper-1.48/utils/ndiswrapper
ndiswrapper-1.48/utils/ndiswrapper-buginfo
ndiswrapper-1.48/loadndisdriver.8
ndiswrapper-1.48/README
ndiswrapper-1.48/ndiswrapper.8
ndiswrapper-1.48/driver/
ndiswrapper-1.48/driver/wrapndis.c
ndiswrapper-1.48/driver/wrapndis.h
ndiswrapper-1.48/driver/Makefile
ndiswrapper-1.48/driver/lin2win.h
ndiswrapper-1.48/driver/winnt_types.h
ndiswrapper-1.48/driver/crt.c
ndiswrapper-1.48/driver/hal.c
ndiswrapper-1.48/driver/pnp.c
ndiswrapper-1.48/driver/pnp.h
ndiswrapper-1.48/driver/rtl.c
ndiswrapper-1.48/driver/usb.c
ndiswrapper-1.48/driver/usb.h
ndiswrapper-1.48/driver/divdi3.c
ndiswrapper-1.48/driver/ndiswrapper.h
ndiswrapper-1.48/driver/iw_ndis.c
ndiswrapper-1.48/driver/iw_ndis.h
ndiswrapper-1.48/driver/ndis.c
ndiswrapper-1.48/driver/ndis.h
ndiswrapper-1.48/driver/ntoskernel_io.c
ndiswrapper-1.48/driver/proc.c
ndiswrapper-1.48/driver/pe_linker.c
ndiswrapper-1.48/driver/pe_linker.h
ndiswrapper-1.48/driver/loader.c
ndiswrapper-1.48/driver/loader.h
ndiswrapper-1.48/driver/ntoskernel.c
ndiswrapper-1.48/driver/ntoskernel.h
ndiswrapper-1.48/driver/wrapmem.c
ndiswrapper-1.48/driver/wrapmem.h
ndiswrapper-1.48/driver/wrapper.c
ndiswrapper-1.48/driver/longlong.h
ndiswrapper-1.48/driver/win2lin_stubs.S
ndiswrapper-1.48/driver/workqueue.c
ndiswrapper-1.48/AUTHORS
ndiswrapper-1.48/INSTALL
ndiswrapper-1.48/ndiswrapper.spec
ndiswrapper-1.48/ChangeLog
dave@(none):~/ndiswrapper$ cd ndiswrapper1.48
bash: cd: ndiswrapper1.48: No such file or directory
dave@(none):~/ndiswrapper$ cd ndiswrapper-1.48
dave@(none):~/ndiswrapper/ndiswrapper-1.48$ make distclean
make -C driver clean
make[1]: Entering directory `/home/dave/ndiswrapper/ndiswrapper-1.48/driver'
rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapper.o usb.o divdi3.o usb.o win2lin_stubs.o \
	   divdi3.o workqueue.o .*.ko.cmd .*.o.cmd  compat.h \
	   ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers
make[1]: Leaving directory `/home/dave/ndiswrapper/ndiswrapper-1.48/driver'
make -C utils clean
make[1]: Entering directory `/home/dave/ndiswrapper/ndiswrapper-1.48/utils'
rm -f *~ *.o loadndisdriver
make[1]: Leaving directory `/home/dave/ndiswrapper/ndiswrapper-1.48/utils'
rm -f *~
rm -fr ndiswrapper-1.48 ndiswrapper-1.48.tar.gz patch-stamp
make -C driver distclean
make[1]: Entering directory `/home/dave/ndiswrapper/ndiswrapper-1.48/driver'
rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapper.o usb.o divdi3.o usb.o win2lin_stubs.o \
	   divdi3.o workqueue.o .*.ko.cmd .*.o.cmd  compat.h \
	   ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers
rm -f *_exports.h .\#* win2lin_stubs.h built-in.o
make[1]: Leaving directory `/home/dave/ndiswrapper/ndiswrapper-1.48/driver'
make -C utils distclean
make[1]: Entering directory `/home/dave/ndiswrapper/ndiswrapper-1.48/utils'
rm -f *~ *.o loadndisdriver
rm -f .\#*
make[1]: Leaving directory `/home/dave/ndiswrapper/ndiswrapper-1.48/utils'
rm -f .\#*
dave@(none):~/ndiswrapper/ndiswrapper-1.48$ make
make -C driver
make[1]: Entering directory `/home/dave/ndiswrapper/ndiswrapper-1.48/driver'
make -C /usr/src/linux-headers-2.6.24-19-generic SUBDIRS=/home/dave/ndiswrapper/ndiswrapper-1.48/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/dave/ndiswrapper/ndiswrapper-1.48/driver/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[2]: *** [_module_/home/dave/ndiswrapper/ndiswrapper-1.48/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/dave/ndiswrapper/ndiswrapper-1.48/driver'
make: *** [all] Error 2
dave@(none):~/ndiswrapper/ndiswrapper-1.48$ sudo make install
sudo: unable to resolve host (none)
[sudo] password for dave: 
Sorry, try again.
[sudo] password for dave: 
make -C driver install
make[1]: Entering directory `/home/dave/ndiswrapper/ndiswrapper-1.48/driver'
make -C /usr/src/linux-headers-2.6.24-19-generic SUBDIRS=/home/dave/ndiswrapper/ndiswrapper-1.48/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/dave/ndiswrapper/ndiswrapper-1.48/driver/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[2]: *** [_module_/home/dave/ndiswrapper/ndiswrapper-1.48/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/dave/ndiswrapper/ndiswrapper-1.48/driver'
make: *** [install] Error 2
dave@(none):~/ndiswrapper/ndiswrapper-1.48$ ndiswrapper -v
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found
dave@(none):~/ndiswrapper/ndiswrapper-1.48$ ndiswrapper -v
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found
dave@(none):~/ndiswrapper/ndiswrapper-1.48$ sudo apt-get install ndiswrapper-common
sudo: unable to resolve host (none)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed:
  ndiswrapper-common
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/11.4kB of archives.
After this operation, 94.2kB of additional disk space will be used.
Selecting previously deselected package ndiswrapper-common.
(Reading database ... 97756 files and directories currently installed.)
Unpacking ndiswrapper-common (from .../ndiswrapper-common_1.50-1ubuntu1_all.deb) ...
Setting up ndiswrapper-common (1.50-1ubuntu1) ...
dave@(none):~/ndiswrapper/ndiswrapper-1.48$ ndiswrapper -v
Error: no ndiswrapper utils found!
dave@(none):~/ndiswrapper/ndiswrapper-1.48$ cd ~
dave@(none):~$ mkdir driver
dave@(none):~$ cd driver
dave@(none):~/driver$ sudo ndiwrapper -i *****.inf
sudo: unable to resolve host (none)
sudo: ndiwrapper: command not found
dave@(none):~/driver$ sudo ndiswrapper -i *****.inf
sudo: unable to resolve host (none)
Error: no ndiswrapper utils found!
dave@(none):~/driver$ cd~
bash: cd~: command not found
dave@(none):~/driver$ cd ~
dave@(none):~$ cd ndiswrapper
dave@(none):~/ndiswrapper$ ndiswrapper -v
Error: no ndiswrapper utils found!
dave@(none):~/ndiswrapper$ sudo distclean
sudo: unable to resolve host (none)
sudo: distclean: command not found
dave@(none):~/ndiswrapper$ cd ndiswrapper-1.48
dave@(none):~/ndiswrapper/ndiswrapper-1.48$ make distclean
make -C driver clean
make[1]: Entering directory `/home/dave/ndiswrapper/ndiswrapper-1.48/driver'
rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapper.o usb.o divdi3.o usb.o win2lin_stubs.o \
	   divdi3.o workqueue.o .*.ko.cmd .*.o.cmd  compat.h \
	   ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers
make[1]: Leaving directory `/home/dave/ndiswrapper/ndiswrapper-1.48/driver'
make -C utils clean
make[1]: Entering directory `/home/dave/ndiswrapper/ndiswrapper-1.48/utils'
rm -f *~ *.o loadndisdriver
make[1]: Leaving directory `/home/dave/ndiswrapper/ndiswrapper-1.48/utils'
rm -f *~
rm -fr ndiswrapper-1.48 ndiswrapper-1.48.tar.gz patch-stamp
make -C driver distclean
make[1]: Entering directory `/home/dave/ndiswrapper/ndiswrapper-1.48/driver'
rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapper.o usb.o divdi3.o usb.o win2lin_stubs.o \
	   divdi3.o workqueue.o .*.ko.cmd .*.o.cmd  compat.h \
	   ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers
rm -f *_exports.h .\#* win2lin_stubs.h built-in.o
make[1]: Leaving directory `/home/dave/ndiswrapper/ndiswrapper-1.48/driver'
make -C utils distclean
make[1]: Entering directory `/home/dave/ndiswrapper/ndiswrapper-1.48/utils'
rm -f *~ *.o loadndisdriver
rm -f .\#*
make[1]: Leaving directory `/home/dave/ndiswrapper/ndiswrapper-1.48/utils'
rm -f .\#*
dave@(none):~/ndiswrapper/ndiswrapper-1.48$ nake
bash: nake: command not found
dave@(none):~/ndiswrapper/ndiswrapper-1.48$ make
make -C driver
make[1]: Entering directory `/home/dave/ndiswrapper/ndiswrapper-1.48/driver'
make -C /usr/src/linux-headers-2.6.24-19-generic SUBDIRS=/home/dave/ndiswrapper/ndiswrapper-1.48/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/dave/ndiswrapper/ndiswrapper-1.48/driver/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[2]: *** [_module_/home/dave/ndiswrapper/ndiswrapper-1.48/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/dave/ndiswrapper/ndiswrapper-1.48/driver'
make: *** [all] Error 2
dave@(none):~/ndiswrapper/ndiswrapper-1.48$ make
make -C driver
make[1]: Entering directory `/home/dave/ndiswrapper/ndiswrapper-1.48/driver'
make -C /usr/src/linux-headers-2.6.24-19-generic SUBDIRS=/home/dave/ndiswrapper/ndiswrapper-1.48/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  LD      /home/dave/ndiswrapper/ndiswrapper-1.48/driver/built-in.o
  CC [M]  /home/dave/ndiswrapper/ndiswrapper-1.48/driver/crt.o
  CC [M]  /home/dave/ndiswrapper/ndiswrapper-1.48/driver/hal.o
  CC [M]  /home/dave/ndiswrapper/ndiswrapper-1.48/driver/iw_ndis.o
  CC [M]  /home/dave/ndiswrapper/ndiswrapper-1.48/driver/loader.o
  CC [M]  /home/dave/ndiswrapper/ndiswrapper-1.48/driver/ndis.o
  CC [M]  /home/dave/ndiswrapper/ndiswrapper-1.48/driver/ntoskernel.o
  CC [M]  /home/dave/ndiswrapper/ndiswrapper-1.48/driver/ntoskernel_io.o
  CC [M]  /home/dave/ndiswrapper/ndiswrapper-1.48/driver/pe_linker.o
  CC [M]  /home/dave/ndiswrapper/ndiswrapper-1.48/driver/pnp.o
  CC [M]  /home/dave/ndiswrapper/ndiswrapper-1.48/driver/proc.o
/home/dave/ndiswrapper/ndiswrapper-1.48/driver/proc.c: In function â&#128;&#152;wrap_procfs_initâ&#128;&#153;:
/home/dave/ndiswrapper/ndiswrapper-1.48/driver/proc.c:511: error: â&#128;&#152;proc_netâ&#128;&#153; undeclared (first use in this function)
/home/dave/ndiswrapper/ndiswrapper-1.48/driver/proc.c:511: error: (Each undeclared identifier is reported only once
/home/dave/ndiswrapper/ndiswrapper-1.48/driver/proc.c:511: error: for each function it appears in.)
/home/dave/ndiswrapper/ndiswrapper-1.48/driver/proc.c: In function â&#128;&#152;wrap_procfs_removeâ&#128;&#153;:
/home/dave/ndiswrapper/ndiswrapper-1.48/driver/proc.c:538: error: â&#128;&#152;proc_netâ&#128;&#153; undeclared (first use in this function)
make[3]: *** [/home/dave/ndiswrapper/ndiswrapper-1.48/driver/proc.o] Error 1
make[2]: *** [_module_/home/dave/ndiswrapper/ndiswrapper-1.48/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/dave/ndiswrapper/ndiswrapper-1.48/driver'
make: *** [all] Error 2
dave@(none):~/ndiswrapper/ndiswrapper-1.48$ ndiswrapper -v
Error: no ndiswrapper utils found!
dave@(none):~/ndiswrapper/ndiswrapper-1.48$

---

### Post by kevdog on 2008-07-17
Did you install the linux header files?

---

### Post by slstokes on 2008-07-17
> **kevdog said:**
> Did you install the linux header files?

Is that the following?  

4. sudo aptitude install build-essential linux-headers-`uname -r`

If so, yes I did it. Should I try it again? Would I do all four steps again, or just this one?

---

### Post by kevdog on 2008-07-17
Try to install the latest ndiswrapper version -- I believe its 1.52.  You only need the linux-headers-$(uname -r) part.

---

### Post by slstokes on 2008-07-17
> **kevdog said:**
> Try to install the latest ndiswrapper version -- I believe its 1.52.  You only need the linux-headers-$(uname -r) part.

Thanks, that worked and the driver is installed now. I am connecting to the network now, but for some reason I have no internet. (My two other PCs are connecting fine) Also the network connection is very poor when it was good under the old OS (Linspire 6). Are there additional settings to get the internet and improve the connection? Thanks for your help and patience!

Sharon

---

### Post by kevdog on 2008-07-17
I dont know what you mean by no internet?  That would signify either a route (gateway designation problem) or more likely a dns related problem.

---

### Post by slstokes on 2008-07-17
> **kevdog said:**
> I dont know what you mean by no internet?  That would signify either a route (gateway designation problem) or more likely a dns related problem.

Well it doesn't help that I don't know networking.:) The icon in the upper right corner shows it's connected to my wireless network (@31%). When I launch Firefox,I get invalid address for everything I try. I have went into Network manager and set the DNS setting to match my other computers. Maybe there's something else in there that I don't have right. 

I have a book 'Peter van der Linden's Guide to Linux' and going through his list of things to check. (Like ifconfig, dmesg -C, iwconfig, route, dhclient) It all looks good until I get to ping. This is my output I tried it with both the name and IP of the router):

[COLOR="Sienna"]dave@(none):~$ ping -c 10 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.103 icmp_seq=1 Destination Host Unreachable
From 192.168.1.103 icmp_seq=2 Destination Host Unreachable
From 192.168.1.103 icmp_seq=3 Destination Host Unreachable
From 192.168.1.103 icmp_seq=4 Destination Host Unreachable
From 192.168.1.103 icmp_seq=5 Destination Host Unreachable
From 192.168.1.103 icmp_seq=6 Destination Host Unreachable
From 192.168.1.103 icmp_seq=7 Destination Host Unreachable
From 192.168.1.103 icmp_seq=8 Destination Host Unreachable
From 192.168.1.103 icmp_seq=9 Destination Host Unreachable
From 192.168.1.103 icmp_seq=10 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
10 packets transmitted, 0 received, +10 errors, 100% packet loss, time 9025ms
, pipe 3
dave@(none):~$ ping -c 10 stokesnet
PING stokesnet (192.168.1.1) 56(84) bytes of data.
From none.local (192.168.1.103) icmp_seq=1 Destination Host Unreachable
From none.local (192.168.1.103) icmp_seq=2 Destination Host Unreachable
From none.local (192.168.1.103) icmp_seq=3 Destination Host Unreachable

--- stokesnet ping statistics ---
10 packets transmitted, 0 received, +3 errors, 100% packet loss, time 69116ms
, pipe 3
dave@(none):~$[/COLOR] 

 
I am a little confused because I don't understand how the computer appears to be communicating with the router (based on the icon on the desktop) but the ping says host is unreachable. Can you help me understand the problem?

---

### Post by kevdog on 2008-07-17
It doesnt look like you are actually connected, rather the your ip address is assigned out of the computer cache than from the router.  Sounds like you need to troubleshoot via a manual connection:

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by slstokes on 2008-07-18
> **kevdog said:**
> Sounds like you need to troubleshoot via a manual connection:

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

Yes, I had followed that document under the unencrypted connection instructions. I did not do the instructions at the bottom to connect at boot because that appeared to be optional (plus when I rebooted it was attempting to connect so I thought that must already be in place for me). 

Before I installed ndiswrapper I had messed around in the Network Manger and entered the settings for my network. Did that override the manual instructions that I followed after that? I am going to do the 'lshw -C network' again to make sure the driver is listed, maybe there is still a problem with the driver. Do you have any other suggestions?

---

### Post by Morty007 on 2008-07-18
> **slstokes said:**
> Well it doesn't help that I don't know networking.:) The icon in the upper right corner shows it's connected to my wireless network (@31%). When I launch Firefox,I get invalid address for everything I try. I have went into Network manager and set the DNS setting to match my other computers. Maybe there's something else in there that I don't have right. 

I have a book 'Peter van der Linden's Guide to Linux' and going through his list of things to check. (Like ifconfig, dmesg -C, iwconfig, route, dhclient) It all looks good until I get to ping. This is my output I tried it with both the name and IP of the router):

[COLOR="Sienna"]dave@(none):~$ ping -c 10 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.103 icmp_seq=1 Destination Host Unreachable
From 192.168.1.103 icmp_seq=2 Destination Host Unreachable
From 192.168.1.103 icmp_seq=3 Destination Host Unreachable
From 192.168.1.103 icmp_seq=4 Destination Host Unreachable
From 192.168.1.103 icmp_seq=5 Destination Host Unreachable
From 192.168.1.103 icmp_seq=6 Destination Host Unreachable
From 192.168.1.103 icmp_seq=7 Destination Host Unreachable
From 192.168.1.103 icmp_seq=8 Destination Host Unreachable
From 192.168.1.103 icmp_seq=9 Destination Host Unreachable
From 192.168.1.103 icmp_seq=10 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
10 packets transmitted, 0 received, +10 errors, 100% packet loss, time 9025ms
, pipe 3
dave@(none):~$ ping -c 10 stokesnet
PING stokesnet (192.168.1.1) 56(84) bytes of data.
From none.local (192.168.1.103) icmp_seq=1 Destination Host Unreachable
From none.local (192.168.1.103) icmp_seq=2 Destination Host Unreachable
From none.local (192.168.1.103) icmp_seq=3 Destination Host Unreachable

--- stokesnet ping statistics ---
10 packets transmitted, 0 received, +3 errors, 100% packet loss, time 69116ms
, pipe 3
dave@(none):~$[/COLOR] 

 
I am a little confused because I don't understand how the computer appears to be communicating with the router (based on the icon on the desktop) but the ping says host is unreachable. Can you help me understand the problem?

Sharon,

I had the same problem and could never get wireless working. I suggest trying Linux Mint. It's based on ubuntu and already has ndiswrapper installed. I think you'll find it much easier.

---

### Post by kevdog on 2008-07-19
Need to try manual unencrypted connection first -- settings will not hold between boots.

---

### Post by onewithnature83 on 2008-07-20
31 pages on this thread? I will give props on the ndiswrapper how-to.

but linux drivers are an option too.

[https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b)

--TJ

---

### Post by kevdog on 2008-07-20
I never said they were not.  In fact many linux built-in drivers work well, however there are not that many built-into the kernel.  I love madwifi drivers, however even these are custom compiled kernel modules.

---

### Post by slstokes on 2008-07-21
> **kevdog said:**
> Need to try manual unencrypted connection first -- settings will not hold between boots.

I tried that and it was pulling in the correct settings but still did not work right. So I then did try LinuxMint as another poster suggested (really liked it btw) and had the same problem. It was getting the router IP, the DSN IPs etc, but was not working properly so I decided to try a different USB wifi adapter (SMC) and got connected right away. The Linksys adapter had been working right up the the minute I installed Ubuntu, so I guess it was a coincidence that it went bad at that time. Weird. Thanks much for the help on this!

Sharon

---

