---
title: "DELL XPS Gen2 WLAN 1450 Help?"
date: 2007-08-31
forum: Networking &amp; Wireless
---

### Post by darkbluexplorer on 2007-08-31
ok i have done a good bit of studying. I have a dell xps gen2 and a 1450 wlan minipc card. have tried several things and it keeps telling me my hardware is not present. i have checked the bios and everything. it works in xp and is enable so i am at a loss.. granted i am an ubuntu n00b! so help please?

---

### Post by kevdog on 2007-08-31
Can you be more specific in what you have tried??  Likely you will need ndiswrapper + winxp drivers for the internal card.  To see if hardware is recognized, please post:

lspci -nn
lshw -C network

---

### Post by darkbluexplorer on 2007-08-31
I have tryed ndiswrapper with the xp drivers. i have tried the drivers that were listed on here. i blacklisted the driver that ubuntu had listed as the alt driver for the card even though the card didnt work. i installed the ndiswrapper gui trhough the add/remove programs and now i cant remove that driver.

---

### Post by kevdog on 2007-08-31
I dont know if you have an internet connection on your computer or not, so I  am gointg to assume you do not.  The first is ndiswrapper removal instructions -- then second are installation instructions.  Read the entire instructions about 3 times before doing anything:

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



We are grabbing ndiswrapper-1.48-rc1



***The following section will work if you have an internet connection

*** If you do not have an internet connection, on a different computer you will need to download the ndiswrapper source file from: 

[http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.48rc1.tar.gz](http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.48rc1.tar.gz)

Please place this file on a flash drive (USB Flash drive), transfer it to the Ubuntu machine, and then place it in the ~/ndiswrapper directory.  Continue with the next following set of instructions

```
cd ~

mkdir ndiswrapper

wget http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.48rc1.tar.gz -O ~/ndiswrapper/ndiswrapper-1.48rc1.tar.gz 

cd ndiswrapper


```



Extract, compile, and install ndiswrapper

```
tar -zxvf ndiswrapper-1.48rc1.tar.gz

cd ndiswrapper-1.48rc1

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

version:        1.48rc1

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

---

### Post by darkbluexplorer on 2007-09-05
wow thank you for that write up i will try it when i get home tonight! you may have saved me from having to call a professional! :)
EDIT: IT did work TYVM!! FINALY stuff is going my way :)

---

