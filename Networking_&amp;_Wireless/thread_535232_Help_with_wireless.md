---
title: "Help with wireless"
date: 2007-08-26
forum: Networking &amp; Wireless
---

### Post by SexyPastry on 2007-08-26
I'm a new user to linux i am using the Ubuntu 6.06LTS version of ubuntu and for some reason i installed it on my labtop and can not get it to work it detects the card but wont activate it will someone help me out here?

---

### Post by kevdog on 2007-08-26
You need to tell us more about your wireless card.  Hopefully you can post the following:

lspci -nn
lshw -C network

Can I eat your pastry?

---

### Post by SexyPastry on 2007-08-26
carmine@carmine-laptop:~$ lspci -nn
0000:00:00.0 0600: 8086:2580 (rev 0e)
0000:00:01.0 0604: 8086:2581 (rev 0e)
0000:00:1c.0 0604: 8086:2660 (rev 03)
0000:00:1d.0 0c03: 8086:2658 (rev 03)
0000:00:1d.1 0c03: 8086:2659 (rev 03)
0000:00:1d.2 0c03: 8086:265a (rev 03)
0000:00:1d.3 0c03: 8086:265b (rev 03)
0000:00:1d.7 0c03: 8086:265c (rev 03)
0000:00:1e.0 0604: 8086:244e (rev d3)
0000:00:1e.2 0401: 8086:266e (rev 03)
0000:00:1e.3 0703: 8086:266d (rev 03)
0000:00:1f.0 0601: 8086:2640 (rev 03)
0000:00:1f.1 0101: 8086:266f (rev 03)
0000:00:1f.3 0c05: 8086:266a (rev 03)
0000:01:00.0 0300: 1002:3150
0000:0b:00.0 0607: 104c:8031
0000:0b:00.2 0c00: 104c:8032
0000:0b:00.3 0180: 104c:8033
0000:0b:00.4 0805: 104c:8034
0000:0b:02.0 0200: 10ec:8139 (rev 10)
0000:0b:03.0 0280: 14e4:4318 (rev 02)
carmine@carmine-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0 DISABLED
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0b:02.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:de:63:7a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too multicast=yes
       resources: ioport:5000-50ff iomemory:b0209400-b02094ff irq:50
  *-network:1
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0b:03.0
       logical name: eth1
       version: 02
       serial: 00:14:a5:1a:a9:72
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:b0206000-b0207fff irq:177

You can eat me only if you get this working!:lolflag:

---

### Post by kevdog on 2007-08-26
Ok -- no problem about getting your device working -- and I am hungry.  Anyway do you have Windows XP drivers for the device or have access to them??

Looks like you have an internet wired connection already, is that true??

Last thing can you post lspci -nn (only if you dont have the windows xp drivers)?

---

### Post by SexyPastry on 2007-08-26
I dont have access to windows xp drivers. And I did post the the lspci -nn output. ;)

---

### Post by kevdog on 2007-08-26
Sorry about that -- is this a linksys device?? or some other manufacturer?

---

### Post by SexyPastry on 2007-08-26
realtek i believe arent u looking at the info that I gave you. :p

---

### Post by kevdog on 2007-08-26
Hold on -- I was assuming by the title of your thread (Help with wireless) that you wanted your wireless card to work?

This actually is your wireless device - the rtl is your wired device.:

*-network:1
description: Wireless interface
product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 3
bus info: pci@0b:03.0
logical name: eth1
version: 02
serial: 00:14:a5:1a:a9:72
width: 32 bits
clock: 33MHz
capabilities: bus_master ethernet physical wireless
configuration: broadcast=yes driver=bcm43xx multicast=yes wireless=IEEE 802.11b/g
resources: iomemory:b0206000-b0207fff irq:177

---

### Post by SexyPastry on 2007-08-26
Oh... I think thats an intel chipset wireless card. For some reason it doesnt connect and when i restart the computer it deactivates the wireless device as well. I don't know whats wrong with it.

---

### Post by kevdog on 2007-08-26
Im really confused what you mean and what device you want to get working.

lshw -C network
produced two devices:

#1 A Realtek wired NIC
#2 A Broadcom wireless device

None of the devices listed were an intel card or intel chipset.  At this point Im not sure what device you want to get up and working :confused:

---

### Post by SexyPastry on 2007-08-26
Option #2 with wireless device.  Sorry about that.

---

### Post by kevdog on 2007-08-26
So not to be mean is this broadcom wireless device an internal card or an external card like a linksys or some other brand?

---

### Post by SexyPastry on 2007-08-26
internal card

---

### Post by kevdog on 2007-08-26
Ok, hopefully these drivers will do the trick -- I had to find them.  This is what I want you to do with them:

cd ~
mkdir driver

Download the file below.  Somehow I need you to place this in your ~ directory or home directory.
Then do the following:
tar zxvf broadcom4318.tar.gz
cd broadcom4318
cp * ~/driver
cd ~
rm -R broadcom4318

This will put your WinXP driver files into ~/driver

Let me know if this is OK, and then I will send you the full instructions on how to use these!

---

### Post by SexyPastry on 2007-08-26
It is ok that i do not have that windows xp drivers right i can just do wut u said and hopefully it will work.

Right?


I did exactly what you said now what do I do from here?

---

### Post by kevdog on 2007-08-26
The rest of the instructions (assuming you have a wired ethernet connection):
[SIZE="4"]**NDISWRAPPER SVN INSTALLATION**[/SIZE]
***Requirements - A working internet connection

```
sudo aptitude update
sudo aptitude upgrade
sudo aptitude install subversion build-essential linux-headers-`uname -r`

```
Subversion is the utility that we can use to download the svn version of ndiswrapper.  The other two packages are so we can compile from source.

Ok lets grab the ndiswrapper svn sources, compile and install them:
```

cd ~
mkdir ndiswrapper_svn
svn co https://ndiswrapper.svn.sourceforge.net/svnroot/ndiswrapper/trunk/ndiswrapper ~/ndiswrapper_svn
cd ndiswrapper_svn
svn up
make distclean
make
sudo make install

```

Verify installation with
```
ndiswrapper -v
```

The output should be something like the following (note at the time of authoring this guide the svn version was 1.48rc1, this may be different than what you get):
```

utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.48rc1
vermagic:       2.6.20-16-generic SMP mod_unload 586

```

[SIZE="4"][B]
Installation of Windows Driver within Ndiswrapper-- You may follow a different procedure based on your setup[/B][/SIZE]
Next create and place your Windows XP wireless driver into ~/driver:
```
cd ~
mkdir driver
cd driver
```

Ensuring the ***.sys and ***.inf file for the WinXP driver are in the~/driver directory:
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
dmesg | tail -n 50
```
and look for something like the following (here is my output):
```

[22409.584000] ndiswrapper version 1.48rc1 loaded (smp=yes)
[22409.604000] ndiswrapper: driver lsbcmnds (Cisco-Linksys ,LLC.,02/19/2004, 3.50.21.11) loaded
[22409.604000] ACPI: PCI Interrupt 0000:06:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[22409.616000] ndiswrapper: using IRQ 11
[22409.960000] wlan0: ethernet device 00:12:17:35:17:10 using NDIS driver: lsbcmnds, version: 0x332150b, NDIS version: 0x500, vendor: 'NDIS Network Adapter', 14E4:4320.5.conf
[22409.960000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
[22409.960000] usbcore: registered new interface driver ndiswrapper

```

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
In addition, please **turn off** any (WEP/WPA/MAC filtering) that may be present in the router.  This is to confirm that the basic ndiswrapper setup can connect to an unencrypted network.  Instructions how to configure for WEP/WPA encryption are included in another separate guide. 

______________________________________________________________________________________________________
**[SIZE="4"]Additional Steps that may be needed if your card still can not connect to your network after rebooting[/SIZE]**

Ndiswrapper by default assumes your card to be assigned to the interface wlan0 -- this may or may not be the case.

Below are some strategies that I have used to ensure that your wireless device is assigned to the wlan0 interface.

[U]
[SIZE="3"]**Verification/Modification of /etc/iftab file**[/SIZE][/U]

The /etc/iftab file acts to permanently associate a given MAC Address with an interface name.  Additions in this file are only necessary if you need to lock down the interface name with a MAC Address.  First discover what interface name is currently associated to your network card MAC Address:
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

**[SIZE="2"]Case #1 - Comment all the associations listed in your /etc/iftab file[/SIZE]** -- Allow the computer to assign them internally at boot time.  _This solution is applicable to the majority of users_  An example of how to accomplish this:  

```

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

#eth1 mac 00:12:17:35:17:10 arp 1

```

Because the association of eth1 with the MAC Address was commented, the computer will internally and automatically make the association of an interface name with the MAC address.  This process of associating wlan0 with the networking device's MAC Address should work about 99% of the time.  If for some reason it does not, proceed to step #2.

**[SIZE="2"]Case #2 - Manually make the inteface name - MAC Address association[/SIZE]**.  You need to ensure there is _only one MAC address associated with one interface name_.

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

_[SIZE="3"]**Modification of /etc/network/interfaces file**[/SIZE]_

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

Only the names mentioned with this command need to be listed in the /etc/network/interfaces file -- in this case only wlan0 (along with the loopback address).

First backup your current interface file configuration in case something goes wrong:
```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
```

To modify your /etc/network/interfaces file:
```
gksu gedit /etc/network/interfaces
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

Further modifications may be needed to this file, depending if you need to run your card in roaming mode (convenient with laptops that often connect to different routers of networks), need to configure your card with static IP address, desire to set WEP/WPA authentication parameters manually, etc.  Again there are many possibilities at this point, far too many to list the different permutations, however this gives you a basic starting point.

---

### Post by SexyPastry on 2007-08-26
I have trouble with a certain step.

```
armine@carmine-laptop:~/ndiswrapper_svn$ svn up
At revision 2450.
carmine@carmine-laptop:~/ndiswrapper_svn$ make distclean
make -C driver clean
make[1]: Entering directory `/home/carmine/ndiswrapper_svn/driver'
Makefile:35: *** Cannot find kernel version in /lib/modules/2.6.15-23-386/build, is it configured?.  Stop.
make[1]: Leaving directory `/home/carmine/ndiswrapper_svn/driver'
make: *** [clean] Error 2
carmine@carmine-laptop:~/ndiswrapper_svn$ make
make -C driver
make[1]: Entering directory `/home/carmine/ndiswrapper_svn/driver'
Makefile:35: *** Cannot find kernel version in /lib/modules/2.6.15-23-386/build, is it configured?.  Stop.
make[1]: Leaving directory `/home/carmine/ndiswrapper_svn/driver'
make: *** [all] Error 2
carmine@carmine-laptop:~/ndiswrapper_svn$ sudo make install
make -C driver install
make[1]: Entering directory `/home/carmine/ndiswrapper_svn/driver'
Makefile:35: *** Cannot find kernel version in /lib/modules/2.6.15-23-386/build, is it configured?.  Stop.
make[1]: Leaving directory `/home/carmine/ndiswrapper_svn/driver'
make: *** [install] Error 2
carmine@carmine-laptop:~/ndiswrapper_svn$
carmine@carmine-laptop:~/ndiswrapper_svn$ ndiswrapper -v
bash: ndiswrapper: command not found

```

---

### Post by kevdog on 2007-08-26
Did you do the following??:

```
sudo aptitude install linux-headers-`uname -r`
```

---

