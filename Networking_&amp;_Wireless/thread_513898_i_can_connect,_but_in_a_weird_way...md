---
title: "i can connect, but in a weird way..?"
date: 2007-07-31
forum: Networking &amp; Wireless
---

### Post by tmdowner on 2007-07-31
I'm new to ubuntu (7.04), but I've used suse for about six years now.  I've changed distros for various reasons.

In any case, my laptop has a broadcom wireless g54 cardbus adapter (BCM4306), and I'm using ndiswrapper to connect (although I'm aware that there are now native drivers for this card).  Once I get connected, everything works quite well.

However, in order to connect, I first have to go to "Manual configuration" in the network manager, then disable and re-enable eth0 (wired, not connected to internet).  After that, I have to go to "create new wireless network," accept the default settings, and THEN go back and click on the original linksys network.  While the linksys network shows up upon booting the computer, the laptop will not connect to the network until I go through this process... EVERY TIME.

Obviously, this is due to something in my settings.. but I have no idea what it could be, nor what config files to post here to show the appropriate settings (and, hopefully, the conflict that is causing this).  

I wouldn't mind this too terribly much, but my girlfriend also uses this computer, and frankly loses interest if something like connecting to the network takes more than a couple clicks.  

I'm stumped.  Anyone know what's going on?

---

### Post by kevdog on 2007-07-31
If you could list a few things it might help

lshw -C network
/etc/network/interfaces
ndiswrapper -v
ndiswrapper -l
modinfo ndiswrapper
lspci -nn

Thanks

---

### Post by tmdowner on 2007-07-31
here we are.  Thanks for any help!


```

tmdown@tmdown-laptop:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 78
       serial: 00:0b:db:07:b8:66
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=32 link=no maxlatency=10 mingnt=10 multicast=yes port=MII speed=10MB/s
       resources: ioport:ec80-ecff iomemory:f8fffc00-f8fffc7f irq:11
  *-network
       description: 802.11b CardBus
       vendor: Broadcom
       physical id: 0
       version: 8.0
       slot: Socket 0
       resources: irq:11
  *-network:1
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 3
       bus info: pci@02:03.0
       logical name: wifi0
       version: 01
       serial: 00:11:f9:fd:36:39
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3.1) latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11a
       resources: iomemory:f8fe0000-f8feffff irq:5
  *-network
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@03:00.0
       logical name: eth1
       version: 03
       serial: 00:0d:0b:5c:ee:2e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 firmware=BUFFALO INC.,11/01/2005, 3.104. latency=64 link=yes multicast=yes wireless=IEEE 802.11g
       resources: iomemory:f4000000-f4001fff irq:11
tmdown@tmdown-laptop:~$ 
tmdown@tmdown-laptop:~$ 
``````

tmdown@tmdown-laptop:~$ 
tmdown@tmdown-laptop:~$ 
tmdown@tmdown-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp






auto eth0

``````

tmdown@tmdown-laptop:~$ ndiswrapper -v
utils Error: no version specified!
driver version:        1.38
vermagic:       2.6.20-16-generic SMP mod_unload 586 
tmdown@tmdown-laptop:~$ 

tmdown@tmdown-laptop:~$ ndiswrapper -l
netcbg54 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)

``````

tmdown@tmdown-laptop:~$ 
tmdown@tmdown-laptop:~$ modinfo ndiswrapper
filename:       /lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko
license:        GPL
version:        1.38
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     BAC0B2B6ECA821BB17E1CCA
depends:        usbcore
vermagic:       2.6.20-16-generic SMP mod_unload 586 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)

``````

tmdown@tmdown-laptop:~$ 
tmdown@tmdown-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82830 830 Chipset Host Bridge [8086:3575] (rev 04)
00:01.0 PCI bridge [0604]: Intel Corporation 82830 830 Chipset AGP Bridge [8086:3576] (rev 04)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB (Hub #1) [8086:2482] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 42)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801CAM ISA Bridge (LPC) [8086:248c] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801CAM IDE U100 [8086:248a] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801CA/CAM AC'97 Audio Controller [8086:2485] (rev 02)
00:1f.6 Modem [0703]: Intel Corporation 82801CA/CAM AC'97 Modem Controller [8086:2486] (rev 02)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility M6 LY [1002:4c59]
02:00.0 Ethernet controller [0200]: 3Com Corporation 3c905C-TX/TX-M [Tornado] [10b7:9200] (rev 78)
02:01.0 CardBus bridge [0607]: Texas Instruments PCI1420 [104c:ac51]
02:01.1 CardBus bridge [0607]: Texas Instruments PCI1420 [104c:ac51]
02:03.0 Ethernet controller [0200]: Atheros Communications, Inc. AR5212 802.11abg NIC [168c:0013] (rev 01)
03:00.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
tmdown@tmdown-laptop:~$ 

```

---

### Post by kevdog on 2007-07-31
Do you have two wireless interfaces??? I see wifi0 that uses an atheros chipset.  Do you use this device?

Have you blacklisted bcm43xx in /etc/modprobe.d/blacklist??

Usually ndiswrapper expects the device to have the wlan0 interface, but your broadcom device is listed at eth1.

What does 
/etc/iftab
/etc/modprobe.d/ndiswrapper
show??

I think we can take some unnecessary interface adapters and remove them from the interfaces file to speed up the boot process.

---

### Post by tmdowner on 2007-07-31
The atheros card has never functioned correctly; it was the reason I bought the buffalo.  I've merely been too lazy to open up the laptop and remove it, since it's never caused any problems.

The bcm43xx driver is blacklisted. 

Thanks again for your help.

```

tmdown@tmdown-laptop:~$ 
tmdown@tmdown-laptop:~$ cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:0b:db:07:b8:66 arp 1
ath0 mac 00:11:f9:fd:36:39 arp 1
eth1 mac 00:0d:0b:5c:ee:2e arp 1
tmdown@tmdown-laptop:~$ 
tmdown@tmdown-laptop:~$ 
tmdown@tmdown-laptop:~$ 
tmdown@tmdown-laptop:~$ 
tmdown@tmdown-laptop:~$ cat /etc/modprobe.d/ndiswrapper
alias wlan0 ndiswrapper
alias wifi0 ndiswrapper
tmdown@tmdown-laptop:~$ 

```

---

### Post by kevdog on 2007-07-31
Ok so lets try some things:

Edit the /etc/iftab file
Change eth1 to wlan0

Edit the /etc/modprobe.d/ndiswrapper file
Comment (#) out the line with wifi0

Look at /etc/modules
Make sure there is one line listed that states ndiswrapper

Next comment out or remove the eth1 and eth2 lines in /etc/network/interfaces.  These interface names are not being used so you might as well get rid of them to speed up the booting process.

Are you using network manager to connect??? Yes I think you are sorry,  Is roaming mode enabled?

---

### Post by tmdowner on 2007-07-31
> 
Ok so lets try some things:

Edit the /etc/iftab file
Change eth1 to wlan0

Edit the /etc/modprobe.d/ndiswrapper file
Comment (#) out the line with wifi0

Look at /etc/modules
Make sure there is one line listed that states ndiswrapper

Next comment out or remove the eth1 and eth2 lines in /etc/network/interfaces. These interface names are not being used so you might as well get rid of them to speed up the booting process.

Are you using network manager to connect??? Yes I think you are sorry, Is roaming mode enabled?


There wasn't an ndiswrapper line in /etc/modules.  I added one.  Yes, I am using network manager, and roaming mode is enabled.

After doing this and rebooting, I no longer have to go to "manual configuration," but I still have to create a null network (that is, go to "create new wireless network") before I can connect to the linksys network.  So I guess we're halfway there :p 

Any idea why it won't connect without first making a null network?  Would it perhaps be easier without network manager?  This is really the first time I've tried to configure linux with wireless, and I have no idea what I'm doing, honestly.  I didn't have any problem with the other box, though, which has a USB receiver.

Thanks!

---

### Post by tmdowner on 2007-08-01
bump.

Anyone have a clue what's going on here?

---

### Post by noob12 on 2007-08-02
If you want to use NetworkManager to manage the device in roaming mode, take wlan0 out of /etc/network/interfaces.  Equivalently, in NetworkManager set the mode to roaming on that interface.

---

### Post by kevdog on 2007-08-02
Ive seen this problem with one other user before, and it was solved by downloading the svn sources of ndiswrapper, then uninstalling the 1.38 version and then installing the svn version (which I think at the time of this writing is 1.48rc1).  

Lets take some baby steps.
Get your wireless or wired conection up and working -- just connect to the internet.

Then do the following at the command line:
```
sudo aptitude update
sudo aptitude upgrade
sudo aptitude install subversion build-essential linux-headers-`uname -r`

```
Subversion is the utility that we can use to download the svn version of ndiswrapper.  The other two packages are so we can compile from source.

Ok lets grab the ndiswrapper svn sources and compile (but not install them):
```

cd ~
svn co https://ndiswrapper.svn.sourceforge.net/svnroot/ndiswrapper ~/ndiswrapper_svn
cd ndiswrapper_svn
svn up
make distclean
make
```

Ok before installing the new ndiswrapper packages we need to uninstall the old version completely. Dont worry if some of these commands dont do anything or seem not to work -- some may be repetitive.

```
sudo rm /etc/modprobe.d/ndiswrapper
sudo rmmod ndiswrapper
sudo rm -rf /etc/ndiswrapper/*
sudo aptitude purge ndiswrapper
sudo rm /usr/sbin/ndiswrapper
sudo rm /sbin/loadndisdriver
sudo rm /lib/modules/`uname -r`/misc/ndiswrapper.ko
```

Ok that should have about killed the old ndiswrapper version.  Now lets install the new version:
```
cd ~/ndiswrapper_svn
sudo make install
```

Timeout:
Check if everything went OK
```
ndiswrapper -v
```
This should return version 1.48rc1 or something similar.  If not stop and do not proceed.

OK, lets load the WinXP driver you have into ndiswrapper
```
cd <to whatever directory you have the ***.inf and ***.sys files for the Win XP driver>
sudo ndiswrapper -i ***.inf
```

Verify that this was installed correctly:
```
ndiswrapper -l
```
Make sure you have only one driver listed.  If you have more stop.  Also make sure you have the bcm43xx module blacklisted in /etc/modprobe.d/blacklist.  If you dont, use the following command to add it to the file: echo "blacklist bcm43xx" | sudo tee -a /etc/modprobe.d/blacklist

Ok lets load the ndiswrapper module into the kernel
```
sudo depmod -a
sudo modprobe -v ndiswrapper
```

Verify installation with:
```
sudo modprobe -l ndiswrapper
modinfo ndiswrapper
```

Then lets finish up:
```
sudo ndiswrapper -m
```

Add the following to /etc/modules (if not already done so, do not have the same line listed more than once):
echo ndiswrapper | sudo tee -a /etc/modules

Next, assuming you are going to use network manager, lets edit the configuration file:
```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
sudo gksu gedit /etc/network/interfaces
```

Have the interfaces file look only like the following:
```
auto lo
iface lo inet loopback
```

Next edit you iftab file
```
gksu gedit /etc/iftab
```

Change the following
> eth1 mac 00:0d:0b:5c:ee:2e arp 1 
to
```
wlan0 mac 00:0d:0b:5c:ee:2e arp 1
```

Reboot

After you startup, 
System->Administration->Network 
Select the wireless interface, hit properties, and make sure roaming mode is enabled.

Also make sure if you are using a router that WPA,WEP,MAC filtering is turned off, and that your SSID is being broadcast (can change these things later).

Then
```
sudo /etc/init.d/networking restart
```

To see if you have a connection
```
ifconfig -a wlan0
```

Look for an IP address 192.168.x.xx

Good luck

---

### Post by tmdowner on 2007-08-02
hey, everything works great!  Thanks for the help!

---

### Post by noob12 on 2007-08-02
Great stuff kevdog.

---

