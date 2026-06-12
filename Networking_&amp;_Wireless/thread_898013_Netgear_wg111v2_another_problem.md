---
title: "Netgear wg111v2 another problem"
date: 2008-08-22
forum: Networking &amp; Wireless
---

### Post by coolercooler on 2008-08-22
Hi all, hope someone can help.

Lost wireless settings in Ubuntu 8.04.1, when i installed Ubuntu 8.04 it recognized my Netgear  WG111v2 wireless card and set it up for me no problems, but I kept geting problems with it, cuting off or freezing if I pluged in ethernet cable in the nic card installed in pci slot. i started playing around with the settings, I've lost all my settings and Ubuntu doesn't even recognize that there's a wireless adapter attached to the computer.

I then decided to go the Ndiswrapper route. I seemed to have done everything right as the blue light is now flashing on my wireless adapter which it never did before and in System - Administrator - Network it sees that there's a wireless signal and gives me the signal strength. I've set up the correct encryption but can't connect to the internet. I can't even connect to the router eventhough in Network it seems to recognize that my wireless adapter is there.  Dos anybody know what I'm doing wrong with Ndiswrapper? or maybe you could tell me how to get Ubuntu to set up the wireless adapter again like it did at the install stage reverting back to original settings.

Thanks

---

### Post by pytheas22 on 2008-08-22
I have the same card and had the same problems using the default driver (p54usb)--it crashed a lot for no reason.  I got it working better in ndiswrapper, but it was really confusing figuring out which Windows drivers to use, because Netgear apparently has several devices sold as WG111v2 and they all require different drivers.  I ended up having to use Windows [drivers for the WG111]("http://kbserver.netgear.com/release_notes/D102534.asp") to get my device going with ndiswrapper.

If you could please post the output of these commands, we might be able to help figure it out:
```

ndiswrapper -l
lshw -C Network
lsusb
```

Also, if you want to get things back to where they were originally (using the default driver), you have to remove the modules p54usb and p54common from your /etc/modprobe.d/blacklist file, then run:
```

sudo rmmod ndiswrapper
sudo modprobe p54usb
sudo modprobe p54common
```

But as I said, at least for me, ndiswrapper was the way to go with this device.

---

### Post by coolercooler on 2008-08-23
Thanks for the reply.

This is the log from those codes.


```

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card
-----------------------------------------------------------

``````

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: Netelligent 10/100 TX PCI UTP
       vendor: Compaq Computer Corporation
       physical id: 2
       bus info: pci@0000:01:02.0
       logical name: eth0
       version: 10
       serial: 00:50:8b:f8:68:d1
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical
       configuration: broadcast=yes driver=tlan latency=64 module=tlan multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:18:4d:bb:54:26
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net111v2 driverversion=1.52+NETGEAR Inc.,3/16/2006,5.12 ip=192.168.135.5 multicast=yes wireless=IEEE 802.11g
---------------------------------------------------------

``````
lsusb

Bus 001 Device 019: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)
Bus 001 Device 001: ID 0000:0000  
coolfi@home network:~$ 
---------------------------------------------------------
```


I think I maybe have done something else wrong, the only other thing I did was installed internet connection sharing, when it was working intermittently, but followed instruction properly and didn't get any errors, so don't see why that should be a problem.

---

### Post by pytheas22 on 2008-08-23
Please post again:
```

ndiswrapper -l
```

(it's a lowercase L).  I think you may have made a typo the first time.  Please also post:
```

sudo modprobe ndiswrapper
dmesg | grep ndis
```

---

### Post by coolercooler on 2008-08-23
Ok heres what came up with those commands, however since then I tried to install few of the drivers, the link you provided to driver didn't work, ndiswrapper reported device not present, but the signal was full but it just would not get the ip address, then installed the windows 98 driver shown in the log, that connected and had an ip address but no traffic just error page not found.

I then disabled ipmasq and ran option2 on startup to recover the system, just in case it was internet connection sharing I ran earlier from this tut, [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370).  It went through series of stuff and upon boot, the internet worked but the signal is low and I can't connect with wep, just without security.

The internet sharing is a must and so is wep.  Same thing happened again when ran internet sharing second time, but the problem only occurs on reboot, until then sharing works.
```
  ndiswrapper -l
net111v2 : driver installed
	device (0846:6A00) present (alternate driver: rtl8187)
coolfi@home:~$ sudo modprobe ndiswrapper
```
```
 Nothing showed up on modprobe ndiswrapper
```
```
 grep ndis
[   85.324916] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   85.934442] ndiswrapper: driver net111v2 (NETGEAR Inc.,3/16/2006,5.1213.06.0316) loaded
[   96.927993] usbcore: registered new interface driver ndiswrapper
 
```

Thanks

---

### Post by pytheas22 on 2008-08-23
You've got a different version of the WG111v2 than me.  Mine has a prism chipset; yours apparently has Realtek.

The [ndiswrapper site]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_m-n/") says this for your card:

> #
Card Netgear WG111v2 Wireless USB Adapter

    *
      Chipset: Realtek
    *
      usbid: 0846:6a00 Netgear, Inc. WG111 WiFi (v2)
    *
      Kernel: 2.6.20-16-generic This kernel comes with ndiswrapper module in place so I had to delete it. You can find the module with ‘locate ndiswrapper.ko’
    *
      Distro: Ubuntu Feisty Fawn
    *
      Driver download from: [http://kbserver.Netgear.com/release_notes/d103125.asp](http://kbserver.Netgear.com/release_notes/d103125.asp)
    *
      Driver link: [ftp://downloads.Netgear.com/files/wg111v2_3_3_0_setup.zip](ftp://downloads.Netgear.com/files/wg111v2_3_3_0_setup.zip)
    *
      Installation: Used unzip to extract the setup program and then wine (NOTE: set winecfg | win98) to install the utilities that places the driver into ~.wine/drive_c/Programfiler/Netgear/WG111v2/Driver/Win98Me . Setting wine to win98 gives me win98 drivers. I tried the winXP drivers without success.
    *
      Driver version: driver net111v2 (Netgear Inc.,02/07/2007,5.1283.0207.2007)
    *
      WINXP driver does not work although it installs fine and also discovers some networks while scanning with ‘iwlist scan’.
    *
      ndiswrapper version: Installed ndiswrapper from svn sources, revision 2427. Older versions of this driver did crash my system and freeze it completely when unloading the ndiswrapper module or when removing the USB wireless adapter. New version does not crash my system.

So you may want to try using the drivers from the links above, if you haven't already.

Also, I'm not sure how well Internet-connection sharing is going to work with ndiswrapper.  It may work, but it may not, due to limitations in what ndiswrapper can do--it only supports ad-hoc and managed modes.  If your ICS setup required master (hostap) mode, ndiswrapper won't support it, since it uses Windows drivers and they don't support it (or if they do, there is no documentation for it).

But I'll try to follow up on this more (not much time right now) and see if I can give you better advice.  If I don't respond within a few days, please bump the thread.

---

### Post by coolercooler on 2008-08-24
Thanks for all that, but those links for an .exe windows application file, how do I get the driver?

I did try extracting it from installed XP, but those didn't work.

---

### Post by pytheas22 on 2008-08-24
I looked through that Internet connection sharing guide that you linked to.  It should work fine with ndiswrapper, so don't worry about that.  I was afraid that the guide was requiring you to do advanced things with your wireless card, but it should not be a problem to do what you need under ndiswrapper.

I would try installing the Windows drivers that I linked to in my last post, since according to the ndiswrapper site they work.  Then try reenabling ICS and connecting using WEP.  If you still have problems, please reboot, run these commands and post the output:
```

sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
iwlist scan
dmesg | grep -e ndis -e wlan

```

and please tell me the name of your network--I'll give you commands to connect manually to see if that makes a difference.

You may also want to connect using [wicd]("http://wicd.sourceforge.net") instead of Network Manager; it may give better results if you're having trouble with WEP.

---

### Post by coolercooler on 2008-08-25
Finally found a driver that works (touch wood), had to download it from Realtek somewhere in far~east, no blinking light but works.  Wep only with wicd and not with network manager.

Now though the only problem I have is internet sharing, when I follow those instructions, everything works fine until I restart pc then nothing works no internet or anyhting else, I've also used firestarter also fails to send trafic to nic but internet works.

Thanks for getting me this far.

---

### Post by pytheas22 on 2008-08-25
The next time you reboot and everything is broken, please post the output of the following so we can figure out what's wrong:
```

lshw -C Network
dmesg
```

The last command's output will be very long, but it will be useful.

---

### Post by coolercooler on 2008-08-25
Ok m8, here are results of those commands.

Ok first after I boot the pc this IS what I get.  No internet and no sharing

```
  lshw -C Network
  *-network               
       description: Ethernet interface
       product: Netelligent 10/100 TX PCI UTP
       vendor: Compaq Computer Corporation
       physical id: 2
       bus info: pci@0000:01:02.0
       logical name: eth0
       version: 10
       serial: 00:50:8b:f8:68:d1
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical
       configuration: broadcast=yes driver=tlan ip=192.168.0.1 latency=64 module=tlan multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:18:4d:bb:54:26
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.135.6 multicast=yes wireless=IEEE 802.11g
```

```
 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=3919 DPT=53 LEN=40 
[  704.690496] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=39318 DPT=53 LEN=40 
[  704.692438] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=59912 DPT=53 LEN=46 
[  704.693845] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=22384 DPT=53 LEN=46 
[  704.695306] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=2821 DPT=53 LEN=46 
[  704.696720] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=38828 DPT=53 LEN=46 
[  704.698644] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=16463 DPT=53 LEN=46 
[  704.699878] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=13625 DPT=53 LEN=46 
[  704.700881] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=30758 DPT=53 LEN=46 
[  704.701766] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=30005 DPT=53 LEN=46 
[  709.702971] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=33345 DPT=53 LEN=43 
[  709.705008] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=40896 DPT=53 LEN=43 
[  709.707046] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=21272 DPT=53 LEN=43 
[  709.708980] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=28004 DPT=53 LEN=43 
[  709.711249] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=35689 DPT=53 LEN=42 
[  709.712688] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=65066 DPT=53 LEN=42 
[  709.714109] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=7307 DPT=53 LEN=42 
[  709.715579] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=47381 DPT=53 LEN=42 
[  709.717602] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=58242 DPT=53 LEN=40 
[  709.719061] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=57647 DPT=53 LEN=40 
[  709.720548] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=17025 DPT=53 LEN=40 
[  709.721982] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=32462 DPT=53 LEN=40 
[  709.723924] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=21894 DPT=53 LEN=46 
[  709.725331] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=26134 DPT=53 LEN=46 
[  709.726789] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=1498 DPT=53 LEN=46 
[  709.728204] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=20342 DPT=53 LEN=46 
[  709.730110] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=47973 DPT=53 LEN=46 
[  709.731557] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=26140 DPT=53 LEN=46 
[  709.732536] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=29544 DPT=53 LEN=46 
[  709.733547] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=56450 DPT=53 LEN=46 
[  714.733977] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=45007 DPT=53 LEN=43 
[  714.735994] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=22189 DPT=53 LEN=43 
[  714.738039] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=30480 DPT=53 LEN=43 
[  714.739286] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=29369 DPT=53 LEN=43 
[  714.741485] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=14486 DPT=53 LEN=42 
[  714.742358] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=22511 DPT=53 LEN=42 
[  714.743266] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=14151 DPT=53 LEN=42 
[  714.744090] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=10369 DPT=53 LEN=42 
[  714.746043] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=61354 DPT=53 LEN=40 
[  714.746919] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=35177 DPT=53 LEN=40 
[  714.747853] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=19781 DPT=53 LEN=40 
[  714.749035] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=45431 DPT=53 LEN=40 
[  714.751279] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=20270 DPT=53 LEN=46 
[  714.752098] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=50826 DPT=53 LEN=46 
[  714.753030] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51762 DPT=53 LEN=46 
[  714.753913] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=56781 DPT=53 LEN=46 
[  714.755827] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=37313 DPT=53 LEN=46 
[  714.756695] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=1406 DPT=53 LEN=46 
[  714.757637] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=23484 DPT=53 LEN=46 
[  714.758494] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=22087 DPT=53 LEN=46 
[  719.759055] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=11299 DPT=53 LEN=43 
[  719.761070] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=46262 DPT=53 LEN=43 
[  719.763140] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=12933 DPT=53 LEN=43 
[  719.765056] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=23244 DPT=53 LEN=43 
[  719.766970] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=21145 DPT=53 LEN=42 
[  719.768378] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=33583 DPT=53 LEN=42 
[  719.770000] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=23775 DPT=53 LEN=42 
[  719.771439] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=6825 DPT=53 LEN=42 
[  719.773323] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=4687 DPT=53 LEN=40 
[  719.774742] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=64945 DPT=53 LEN=40 
[  719.776156] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=52151 DPT=53 LEN=40 
[  719.777620] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=4041 DPT=53 LEN=40 
[  719.779501] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=29848 DPT=53 LEN=46 
[  719.780926] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=50258 DPT=53 LEN=46 
[  719.782380] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=63340 DPT=53 LEN=46 
[  719.783796] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=31992 DPT=53 LEN=46 
[  719.785726] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51668 DPT=53 LEN=46 
[  719.786620] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=33576 DPT=53 LEN=46 
[  719.788975] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=19816 DPT=53 LEN=46 
[  719.789848] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=17808 DPT=53 LEN=46 
[  724.791260] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=34956 DPT=53 LEN=43 
[  724.793373] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=8580 DPT=53 LEN=43 
[  724.795393] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=8792 DPT=53 LEN=43 
[  724.797350] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=22354 DPT=53 LEN=43 
[  724.799223] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=12166 DPT=53 LEN=42 
[  724.800653] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=50934 DPT=53 LEN=42 
[  724.802124] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=24057 DPT=53 LEN=42 
[  724.803550] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=20931 DPT=53 LEN=42 
[  724.805801] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=13934 DPT=53 LEN=40 
[  724.807229] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=45787 DPT=53 LEN=40 
[  724.808852] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=30001 DPT=53 LEN=40 
[  724.810321] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=27287 DPT=53 LEN=40 
[  724.812204] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=65263 DPT=53 LEN=46 
[  724.813663] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=33027 DPT=53 LEN=46 
[  724.815086] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=11395 DPT=53 LEN=46 
[  724.816497] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=45395 DPT=53 LEN=46 
[  724.818362] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=54400 DPT=53 LEN=46 
[  724.819195] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=36705 DPT=53 LEN=46 
[  724.820133] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=47199 DPT=53 LEN=46 
[  724.820996] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=41217 DPT=53 LEN=46 
[  729.822258] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=33650 DPT=53 LEN=43 
[  729.824424] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=64409 DPT=53 LEN=43 
[  729.826277] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=59916 DPT=53 LEN=43 
[  729.830246] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=9270 DPT=53 LEN=43 
[  729.832331] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=62677 DPT=53 LEN=42 
[  729.833816] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=43887 DPT=53 LEN=42 
[  729.835243] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=21949 DPT=53 LEN=42 
[  729.836715] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=39689 DPT=53 LEN=42 
[  729.838574] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=34878 DPT=53 LEN=40 
[  729.840012] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=18241 DPT=53 LEN=40 
[  729.841452] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=34468 DPT=53 LEN=40 
[  729.842872] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=45675 DPT=53 LEN=40 
[  729.844787] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=28993 DPT=53 LEN=46 
[  729.846201] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=18005 DPT=53 LEN=46 
[  729.847952] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=50042 DPT=53 LEN=46 
[  729.849413] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=7808 DPT=53 LEN=46 
[  729.851310] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=8093 DPT=53 LEN=46 
[  729.852763] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=30716 DPT=53 LEN=46 
[  729.853690] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=45585 DPT=53 LEN=46 
[  729.854516] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=23544 DPT=53 LEN=46 
[  734.855376] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=32222 DPT=53 LEN=43 
[  734.857439] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=57312 DPT=53 LEN=43 
[  734.859450] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=17084 DPT=53 LEN=43 
[  734.861435] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=31555 DPT=53 LEN=43 
[  734.863344] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=13097 DPT=53 LEN=42 
[  734.865159] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=3705 DPT=53 LEN=42 
[  734.866595] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=42834 DPT=53 LEN=42 
[  734.868053] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=19500 DPT=53 LEN=42 
[  734.869960] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=60220 DPT=53 LEN=40 
[  734.871381] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=4662 DPT=53 LEN=40 
[  734.872808] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=6418 DPT=53 LEN=40 
[  734.874230] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=1924 DPT=53 LEN=40 
[  734.876290] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=13488 DPT=53 LEN=46 
[  734.877716] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=3732 DPT=53 LEN=46 
[  734.879126] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=2130 DPT=53 LEN=46 
[  734.880588] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=7974 DPT=53 LEN=46 
[  734.882467] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=37378 DPT=53 LEN=46 
[  734.883356] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=18885 DPT=53 LEN=46 
[  734.884326] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=2082 DPT=53 LEN=46 
[  734.885212] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=3475 DPT=53 LEN=46 
[  739.886603] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=53329 DPT=53 LEN=43 
[  739.888795] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=13073 DPT=53 LEN=43 
[  739.890834] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=47387 DPT=53 LEN=43 
[  739.892957] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=22451 DPT=53 LEN=43 
[  739.894845] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=11526 DPT=53 LEN=42 
[  739.896313] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=42008 DPT=53 LEN=42 
[  739.897720] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=22244 DPT=53 LEN=42 
[  739.899180] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=65399 DPT=53 LEN=42 
[  739.901091] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=54752 DPT=53 LEN=40 
[  739.902601] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=53428 DPT=53 LEN=40 
[  739.904067] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=59649 DPT=53 LEN=40 
[  739.905499] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=36767 DPT=53 LEN=40 
[  739.907409] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=43536 DPT=53 LEN=46 
[  739.908836] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=54899 DPT=53 LEN=46 
[  739.910258] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=50072 DPT=53 LEN=46 
[  739.911713] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=13795 DPT=53 LEN=46 
[  739.913722] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=17353 DPT=53 LEN=46 
[  739.914587] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=58594 DPT=53 LEN=46 
[  739.915523] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=34524 DPT=53 LEN=46 
[  739.916715] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=11602 DPT=53 LEN=46 
[  745.063518] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=61362 DPT=53 LEN=43 
[  745.065396] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=35650 DPT=53 LEN=43 
[  745.066886] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=41004 DPT=53 LEN=43 
[  745.068315] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=33375 DPT=53 LEN=43 
[  745.070232] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=43517 DPT=53 LEN=42 
[  745.071690] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=29657 DPT=53 LEN=42 
[  745.073113] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=15602 DPT=53 LEN=42 
[  745.074675] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=34705 DPT=53 LEN=42 
[  745.076610] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=42211 DPT=53 LEN=40 
[  745.078022] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=53934 DPT=53 LEN=40 
[  745.079494] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=29253 DPT=53 LEN=40 
[  745.081103] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=22095 DPT=53 LEN=40 
[  745.083439] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=18971 DPT=53 LEN=46 
[  745.085080] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51254 DPT=53 LEN=46 
[  745.086563] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=32299 DPT=53 LEN=46 
[  745.088002] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=56974 DPT=53 LEN=46 
[  745.089894] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=13624 DPT=53 LEN=46 
[  745.091359] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=30508 DPT=53 LEN=46 
[  745.092356] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=62995 DPT=53 LEN=46 
[  745.093239] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=46069 DPT=53 LEN=46 
[  750.239592] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=60234 DPT=53 LEN=43 
[  750.241809] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=54802 DPT=53 LEN=43 
[  750.243781] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=43525 DPT=53 LEN=43 
[  750.245748] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=11172 DPT=53 LEN=43 
[  750.247989] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=12837 DPT=53 LEN=42 
[  750.249563] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=45997 DPT=53 LEN=42 
[  750.251009] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=57818 DPT=53 LEN=42 
[  750.252437] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=52026 DPT=53 LEN=42 
[  750.254396] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=40435 DPT=53 LEN=40 
[  750.255824] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=59837 DPT=53 LEN=40 
[  750.257256] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=41736 DPT=53 LEN=40 
[  750.258821] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=31336 DPT=53 LEN=40 
[  750.260762] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=32864 DPT=53 LEN=46 
[  750.262208] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=31170 DPT=53 LEN=46 
[  750.263649] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=65426 DPT=53 LEN=46 
[  750.265075] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=19498 DPT=53 LEN=46 
[  750.267022] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=13061 DPT=53 LEN=46 
[  750.268531] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=48884 DPT=53 LEN=46 
[  750.269520] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=20331 DPT=53 LEN=46 
[  750.270402] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=37795 DPT=53 LEN=46 
[  755.271705] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=53894 DPT=53 LEN=43 
[  755.273800] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=16803 DPT=53 LEN=43 
[  755.275817] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=16473 DPT=53 LEN=43 
[  755.277755] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=45567 DPT=53 LEN=43 
[  755.279760] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=55926 DPT=53 LEN=42 
[  755.281214] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=9114 DPT=53 LEN=42 
[  755.282638] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=54372 DPT=53 LEN=42 
[  755.284062] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=15387 DPT=53 LEN=42 
[  755.286053] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=40474 DPT=53 LEN=40 
[  755.287639] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=39094 DPT=53 LEN=40 
[  755.289092] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=3510 DPT=53 LEN=40 
[  755.290538] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=44382 DPT=53 LEN=40 
[  755.292602] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=14273 DPT=53 LEN=46 
[  755.294063] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=27279 DPT=53 LEN=46 
[  755.295492] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=48765 DPT=53 LEN=46 
[  755.297004] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=60206 DPT=53 LEN=46 
[  755.298904] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=55201 DPT=53 LEN=46 
[  755.299771] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=15324 DPT=53 LEN=46 
[  755.300843] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=11794 DPT=53 LEN=46 
[  755.301701] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=64932 DPT=53 LEN=46 
[  760.504783] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=54647 DPT=53 LEN=43 
[  760.506919] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=26570 DPT=53 LEN=43 
[  760.508954] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=42345 DPT=53 LEN=43 
[  760.510888] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=14620 DPT=53 LEN=43 
[  760.512769] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=34371 DPT=53 LEN=42 
[  760.514192] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=22989 DPT=53 LEN=42 
[  760.515620] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=36313 DPT=53 LEN=42 
[  760.517079] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=33438 DPT=53 LEN=42 
[  760.519145] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=22095 DPT=53 LEN=40 
[  760.520600] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=32836 DPT=53 LEN=40 
[  760.522039] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=60186 DPT=53 LEN=40 
[  760.523450] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=9262 DPT=53 LEN=40 
[  760.525496] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=2644 DPT=53 LEN=46 
[  760.527058] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=21533 DPT=53 LEN=46 
[  760.528520] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=43607 DPT=53 LEN=46 
[  760.529957] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=14588 DPT=53 LEN=46 
[  760.531847] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=48001 DPT=53 LEN=46 
[  760.532728] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=6995 DPT=53 LEN=46 
[  760.533737] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=10436 DPT=53 LEN=46 
[  760.534619] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=53855 DPT=53 LEN=46 
[  765.684855] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=65273 DPT=53 LEN=43 
[  765.687007] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=10478 DPT=53 LEN=43 
[  765.688886] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=20705 DPT=53 LEN=43 
[  765.690799] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=63 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=32097 DPT=53 LEN=43 
[  765.692713] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=30413 DPT=53 LEN=42 
[  765.694297] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=24457 DPT=53 LEN=42 
[  765.695744] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=3298 DPT=53 LEN=42 
[  765.697185] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=39090 DPT=53 LEN=42 
[  765.699432] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=20742 DPT=53 LEN=40 
[  765.700877] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=63030 DPT=53 LEN=40 
[  765.702313] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=57044 DPT=53 LEN=40 
[  765.703729] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=10903 DPT=53 LEN=40 
[  765.705657] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=57567 DPT=53 LEN=46 
[  765.707059] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=19704 DPT=53 LEN=46 
[  765.708535] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=21404 DPT=53 LEN=46 
[  765.709964] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=7133 DPT=53 LEN=46 
[  765.711876] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=30844 DPT=53 LEN=46 
[  765.713436] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=47169 DPT=53 LEN=46 
[  765.714436] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=29250 DPT=53 LEN=46 
[  765.715245] IN= OUT=wlan0 SRC=192.168.135.6 DST=192.168.135.1 LEN=66 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=33083 DPT=53 LEN=46 
```

then I type these commands, and internet starts working but no internt sharing.

#ifconfig eth0 192.168.0.1
# iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE
# echo 1 > /proc/sys/net/ipv4/ip_forward
# dpkg-reconfigure ipmasq..........( first option click yes, then ok, then select option "After network interfaces are brought up"

# ifconfig eth0 192.168.0.1
# iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE

Results after

```
 lshw -C Network
  *-network               
       description: Ethernet interface
       product: Netelligent 10/100 TX PCI UTP
       vendor: Compaq Computer Corporation
       physical id: 2
       bus info: pci@0000:01:02.0
       logical name: eth0
       version: 10
       serial: 00:50:8b:f8:68:d1
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical
       configuration: broadcast=yes driver=tlan ip=192.168.0.1 latency=64 module=tlan multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:18:4d:bb:54:26
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.135.6 multicast=yes wireless=IEEE 802.11g
 
``` 
```
 00 SYN URGP=0 
[ 1530.572503] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=213.112.49.202 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=38179 DF PROTO=TCP SPT=2005 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1532.464515] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.103.150.8 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=5505 DF PROTO=TCP SPT=2003 DPT=14000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1533.571293] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=213.112.49.202 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=38181 DF PROTO=TCP SPT=2005 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1533.625494] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=85.228.74.67 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=13153 DF PROTO=TCP SPT=2006 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1536.514780] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=82.155.162.62 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=2236 DF PROTO=TCP SPT=2004 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1536.624771] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=85.228.74.67 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=13155 DF PROTO=TCP SPT=2006 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1536.742506] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.74.24.15 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=29401 DF PROTO=TCP SPT=2007 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1539.570242] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=213.112.49.202 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=38183 DF PROTO=TCP SPT=2005 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1539.741109] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.74.24.15 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=29403 DF PROTO=TCP SPT=2007 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1539.795153] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.103.150.8 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=15974 DF PROTO=TCP SPT=2008 DPT=14000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1542.623682] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=85.228.74.67 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=13157 DF PROTO=TCP SPT=2006 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1542.794587] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.103.150.8 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=15976 DF PROTO=TCP SPT=2008 DPT=14000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1543.797074] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=82.155.162.62 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=48278 DF PROTO=TCP SPT=2009 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1545.740092] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.74.24.15 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=29405 DF PROTO=TCP SPT=2007 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1546.795907] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=82.155.162.62 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=48280 DF PROTO=TCP SPT=2009 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1546.798455] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=213.112.49.202 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=28146 DF PROTO=TCP SPT=2010 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1548.793560] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.103.150.8 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=15978 DF PROTO=TCP SPT=2008 DPT=14000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1549.797362] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=213.112.49.202 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=28148 DF PROTO=TCP SPT=2010 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1549.799837] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=85.228.74.67 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=9375 DF PROTO=TCP SPT=2011 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1552.794827] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=82.155.162.62 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=48282 DF PROTO=TCP SPT=2009 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1552.798754] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=85.228.74.67 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=9377 DF PROTO=TCP SPT=2011 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1552.801275] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.74.24.15 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=30479 DF PROTO=TCP SPT=2012 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1555.796294] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=213.112.49.202 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=28150 DF PROTO=TCP SPT=2010 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1555.800191] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.74.24.15 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=30481 DF PROTO=TCP SPT=2012 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1555.802612] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.103.150.8 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=56822 DF PROTO=TCP SPT=2013 DPT=14000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1558.797756] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=85.228.74.67 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=9379 DF PROTO=TCP SPT=2011 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1558.801677] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.103.150.8 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=56824 DF PROTO=TCP SPT=2013 DPT=14000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1559.803913] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=82.155.162.62 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=51811 DF PROTO=TCP SPT=2014 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1561.106858] IN= OUT=eth0 SRC=192.168.135.6 DST=66.102.9.99 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=61826 DF PROTO=TCP SPT=58263 DPT=80 WINDOW=365 RES=0x00 ACK PSH FIN URGP=0 
[ 1561.799216] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.74.24.15 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=30483 DF PROTO=TCP SPT=2012 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1562.174730] IN= OUT=eth0 SRC=192.168.135.6 DST=66.102.9.99 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=11732 DF PROTO=TCP SPT=58264 DPT=80 WINDOW=365 RES=0x00 ACK PSH FIN URGP=0 
[ 1562.803038] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=82.155.162.62 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=51813 DF PROTO=TCP SPT=2014 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1562.805485] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=213.112.49.202 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=40143 DF PROTO=TCP SPT=2015 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1563.102627] IN= OUT=eth0 SRC=192.168.135.6 DST=66.102.9.99 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=27959 DF PROTO=TCP SPT=58262 DPT=80 WINDOW=716 RES=0x00 ACK PSH FIN URGP=0 
[ 1564.800679] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.103.150.8 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=56826 DF PROTO=TCP SPT=2013 DPT=14000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1565.804513] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=213.112.49.202 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=40145 DF PROTO=TCP SPT=2015 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1565.807154] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=85.228.74.67 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=5290 DF PROTO=TCP SPT=2016 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1568.801988] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=82.155.162.62 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=51815 DF PROTO=TCP SPT=2014 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1568.805890] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=85.228.74.67 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=5292 DF PROTO=TCP SPT=2016 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1568.808443] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.74.24.15 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=47079 DF PROTO=TCP SPT=2017 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1571.803425] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=213.112.49.202 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=40147 DF PROTO=TCP SPT=2015 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1571.807350] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.74.24.15 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=47081 DF PROTO=TCP SPT=2017 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1571.809814] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.103.150.8 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=49878 DF PROTO=TCP SPT=2018 DPT=14000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1574.804902] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=85.228.74.67 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=5294 DF PROTO=TCP SPT=2016 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1574.808796] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.103.150.8 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=49880 DF PROTO=TCP SPT=2018 DPT=14000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1575.811001] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=82.155.162.62 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=26171 DF PROTO=TCP SPT=2019 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1577.806340] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.74.24.15 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=47083 DF PROTO=TCP SPT=2017 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1578.810158] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=82.155.162.62 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=26173 DF PROTO=TCP SPT=2019 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1578.812645] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=213.112.49.202 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=12253 DF PROTO=TCP SPT=2020 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1580.807809] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.103.150.8 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=49882 DF PROTO=TCP SPT=2018 DPT=14000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1581.811616] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=213.112.49.202 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=12255 DF PROTO=TCP SPT=2020 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1581.814437] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=85.228.74.67 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=11097 DF PROTO=TCP SPT=2021 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1584.809089] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=82.155.162.62 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=26175 DF PROTO=TCP SPT=2019 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1584.814003] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=85.228.74.67 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=11099 DF PROTO=TCP SPT=2021 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1584.816464] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.74.24.15 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=4908 DF PROTO=TCP SPT=2022 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1587.810555] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=213.112.49.202 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=12257 DF PROTO=TCP SPT=2020 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1587.815477] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.74.24.15 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=4910 DF PROTO=TCP SPT=2022 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1587.818256] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.103.150.8 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=46421 DF PROTO=TCP SPT=2023 DPT=14000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1590.813027] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=85.228.74.67 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=11101 DF PROTO=TCP SPT=2021 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1590.816941] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.103.150.8 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=46423 DF PROTO=TCP SPT=2023 DPT=14000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1591.940684] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=82.155.162.62 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=65064 DF PROTO=TCP SPT=2024 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1593.814464] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.74.24.15 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=4912 DF PROTO=TCP SPT=2022 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1594.940270] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=82.155.162.62 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=65066 DF PROTO=TCP SPT=2024 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1594.993545] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=213.112.49.202 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=19385 DF PROTO=TCP SPT=2025 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1596.816002] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.103.150.8 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=46425 DF PROTO=TCP SPT=2023 DPT=14000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1597.992786] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=213.112.49.202 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=19387 DF PROTO=TCP SPT=2025 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1598.048767] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=85.228.74.67 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=8787 DF PROTO=TCP SPT=2026 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1600.939251] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=82.155.162.62 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=65068 DF PROTO=TCP SPT=2024 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1601.048135] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=85.228.74.67 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=8789 DF PROTO=TCP SPT=2026 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1601.162519] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.74.24.15 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=49304 DF PROTO=TCP SPT=2027 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1603.991654] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=213.112.49.202 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=19389 DF PROTO=TCP SPT=2025 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1604.161627] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.74.24.15 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=49306 DF PROTO=TCP SPT=2027 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1604.218708] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.103.150.8 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=64053 DF PROTO=TCP SPT=2028 DPT=14000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1607.047118] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=85.228.74.67 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=8791 DF PROTO=TCP SPT=2026 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1607.218097] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.103.150.8 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=64055 DF PROTO=TCP SPT=2028 DPT=14000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1608.220339] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=82.155.162.62 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=15262 DF PROTO=TCP SPT=2029 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1610.160558] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.74.24.15 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=49308 DF PROTO=TCP SPT=2027 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1611.219371] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=82.155.162.62 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=15264 DF PROTO=TCP SPT=2029 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1611.222081] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=213.112.49.202 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=16415 DF PROTO=TCP SPT=2030 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1613.217029] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.103.150.8 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=64057 DF PROTO=TCP SPT=2028 DPT=14000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1614.220850] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=213.112.49.202 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=16417 DF PROTO=TCP SPT=2030 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1614.224056] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=85.228.74.67 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=55491 DF PROTO=TCP SPT=2031 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1617.218260] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=82.155.162.62 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=15266 DF PROTO=TCP SPT=2029 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1617.223172] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=85.228.74.67 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=55493 DF PROTO=TCP SPT=2031 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1617.225581] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.74.24.15 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=7438 DF PROTO=TCP SPT=2032 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1620.219720] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=213.112.49.202 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=16419 DF PROTO=TCP SPT=2030 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1620.224629] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.74.24.15 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=7440 DF PROTO=TCP SPT=2032 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1620.227071] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.103.150.8 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=2309 DF PROTO=TCP SPT=2033 DPT=14000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1623.222182] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=85.228.74.67 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=55495 DF PROTO=TCP SPT=2031 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1623.226088] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.103.150.8 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=2311 DF PROTO=TCP SPT=2033 DPT=14000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1624.228414] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=82.155.162.62 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=12362 DF PROTO=TCP SPT=2034 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1624.587408] IN= OUT=eth0 SRC=192.168.135.6 DST=66.102.9.99 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=61827 DF PROTO=TCP SPT=58263 DPT=80 WINDOW=365 RES=0x00 ACK PSH FIN URGP=0 
[ 1626.223647] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.74.24.15 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=7442 DF PROTO=TCP SPT=2032 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1626.679145] IN= OUT=eth0 SRC=192.168.135.6 DST=66.102.9.99 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=11733 DF PROTO=TCP SPT=58264 DPT=80 WINDOW=365 RES=0x00 ACK PSH FIN URGP=0 
[ 1627.227464] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=82.155.162.62 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=12364 DF PROTO=TCP SPT=2034 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1627.229988] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=213.112.49.202 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=2718 DF PROTO=TCP SPT=2035 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1628.630937] IN= OUT=eth0 SRC=192.168.135.6 DST=66.102.9.99 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=27960 DF PROTO=TCP SPT=58262 DPT=80 WINDOW=716 RES=0x00 ACK PSH FIN URGP=0 
[ 1629.225103] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.103.150.8 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=2313 DF PROTO=TCP SPT=2033 DPT=14000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1630.228920] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=213.112.49.202 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=2720 DF PROTO=TCP SPT=2035 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1630.231455] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=85.228.74.67 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=46631 DF PROTO=TCP SPT=2036 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1633.226403] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=82.155.162.62 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=12366 DF PROTO=TCP SPT=2034 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1633.230285] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=85.228.74.67 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=46633 DF PROTO=TCP SPT=2036 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1633.233052] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.74.24.15 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=41396 DF PROTO=TCP SPT=2037 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1636.227840] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=213.112.49.202 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=2722 DF PROTO=TCP SPT=2035 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1636.231770] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.74.24.15 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=41398 DF PROTO=TCP SPT=2037 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1636.234203] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.103.150.8 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=16952 DF PROTO=TCP SPT=2038 DPT=14000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1639.229295] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=85.228.74.67 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=46635 DF PROTO=TCP SPT=2036 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1639.233214] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.103.150.8 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=16954 DF PROTO=TCP SPT=2038 DPT=14000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1640.235432] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=82.155.162.62 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=1735 DF PROTO=TCP SPT=2039 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1642.230734] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.74.24.15 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=41400 DF PROTO=TCP SPT=2037 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1643.234572] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=82.155.162.62 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=1737 DF PROTO=TCP SPT=2039 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1643.237276] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=213.112.49.202 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=2262 DF PROTO=TCP SPT=2040 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1645.232219] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.103.150.8 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=16956 DF PROTO=TCP SPT=2038 DPT=14000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1646.236041] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=213.112.49.202 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=2264 DF PROTO=TCP SPT=2040 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1646.238751] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=85.228.74.67 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=29381 DF PROTO=TCP SPT=2041 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1649.233504] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=82.155.162.62 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=1739 DF PROTO=TCP SPT=2039 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1649.237434] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=85.228.74.67 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=29383 DF PROTO=TCP SPT=2041 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1649.240506] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.74.24.15 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=26223 DF PROTO=TCP SPT=2042 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1652.234969] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=213.112.49.202 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=2266 DF PROTO=TCP SPT=2040 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1652.239856] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.74.24.15 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=26225 DF PROTO=TCP SPT=2042 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1652.242292] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.103.150.8 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=15177 DF PROTO=TCP SPT=2043 DPT=14000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1655.236446] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=85.228.74.67 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=29385 DF PROTO=TCP SPT=2041 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1655.241345] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.103.150.8 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=15179 DF PROTO=TCP SPT=2043 DPT=14000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1656.293714] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=82.155.162.62 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=11587 DF PROTO=TCP SPT=2044 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1658.238886] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.74.24.15 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=26227 DF PROTO=TCP SPT=2042 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1659.292720] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=82.155.162.62 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=11589 DF PROTO=TCP SPT=2044 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1659.356622] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=213.112.49.202 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=5194 DF PROTO=TCP SPT=2045 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1661.240339] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.103.150.8 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=15181 DF PROTO=TCP SPT=2043 DPT=14000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1662.356150] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=213.112.49.202 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=5196 DF PROTO=TCP SPT=2045 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1664.411219] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=85.228.74.67 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=2300 DF PROTO=TCP SPT=2046 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1665.291620] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=82.155.162.62 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=11591 DF PROTO=TCP SPT=2044 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1667.410223] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=85.228.74.67 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=2302 DF PROTO=TCP SPT=2046 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1667.526782] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.74.24.15 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=53513 DF PROTO=TCP SPT=2047 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1668.355062] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=213.112.49.202 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=5198 DF PROTO=TCP SPT=2045 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1670.525682] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.74.24.15 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=53515 DF PROTO=TCP SPT=2047 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1670.650051] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.103.150.8 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=15674 DF PROTO=TCP SPT=2048 DPT=14000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1673.409160] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=85.228.74.67 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=2304 DF PROTO=TCP SPT=2046 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1673.649099] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.103.150.8 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=15676 DF PROTO=TCP SPT=2048 DPT=14000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1674.651278] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=82.155.162.62 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=9499 DF PROTO=TCP SPT=2049 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1676.524583] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.74.24.15 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=53517 DF PROTO=TCP SPT=2047 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1677.650400] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=82.155.162.62 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=9501 DF PROTO=TCP SPT=2049 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1677.653323] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=213.112.49.202 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=56649 DF PROTO=TCP SPT=2050 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1679.648027] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.103.150.8 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=15678 DF PROTO=TCP SPT=2048 DPT=14000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1680.652887] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=213.112.49.202 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=56651 DF PROTO=TCP SPT=2050 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1680.655425] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=85.228.74.67 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=48108 DF PROTO=TCP SPT=2051 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1683.649303] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=82.155.162.62 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=9503 DF PROTO=TCP SPT=2049 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1683.654229] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=85.228.74.67 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=48110 DF PROTO=TCP SPT=2051 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1683.656658] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.74.24.15 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=30570 DF PROTO=TCP SPT=2052 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1686.651796] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=213.112.49.202 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=56653 DF PROTO=TCP SPT=2050 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1686.655675] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.74.24.15 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=30572 DF PROTO=TCP SPT=2052 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1686.658467] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.103.150.8 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=18052 DF PROTO=TCP SPT=2053 DPT=14000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1689.653243] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=85.228.74.67 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=48112 DF PROTO=TCP SPT=2051 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1689.657170] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.103.150.8 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=18054 DF PROTO=TCP SPT=2053 DPT=14000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1690.659408] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=82.155.162.62 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=58375 DF PROTO=TCP SPT=2054 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1692.654720] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.74.24.15 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=30574 DF PROTO=TCP SPT=2052 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1693.658520] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=82.155.162.62 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=58377 DF PROTO=TCP SPT=2054 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1693.661086] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=213.112.49.202 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=50052 DF PROTO=TCP SPT=2055 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1695.656176] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.103.150.8 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=18056 DF PROTO=TCP SPT=2053 DPT=14000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1696.659985] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=213.112.49.202 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=50054 DF PROTO=TCP SPT=2055 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1696.662560] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=85.228.74.67 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=23403 DF PROTO=TCP SPT=2056 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1699.657438] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=82.155.162.62 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=58379 DF PROTO=TCP SPT=2054 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1699.661336] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=85.228.74.67 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=23405 DF PROTO=TCP SPT=2056 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1699.663737] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.74.24.15 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=55470 DF PROTO=TCP SPT=2057 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1702.658902] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=213.112.49.202 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=50056 DF PROTO=TCP SPT=2055 DPT=12000 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1702.662807] IN=eth0 OUT=wlan0 SRC=192.168.0.150 DST=79.74.24.15 LEN=60 TOS=0x
```

---

### Post by pytheas22 on 2008-08-25
How are you trying to share the connection--is your ethernet card interfaced with the Internet while other machines connect to you through the wireless, or is it the other way around?

---

### Post by coolercooler on 2008-08-26
The other machine is connected to Ethernet via cable, I can ping it and ftp to it, and would like to share the wireless.

---

### Post by pytheas22 on 2008-08-26
hmmm, I don't really know what could be wrong if you're able to share ftp but not http access.  But I also don't know very much about iptables and all that--I suspect that you need to make sure that traffic on port 80 (http) is forwarded between the two interfaces.

I'll keep thinking about this, but I'm not sure I'll be able to give you a good answer on why the forwarding isn't working.  As far as I know, there's no reason that it shouldn't work under ndiswrapper if it worked using the native driver.  You may want to start a new thread to get more attention from people who understand iptables better.

---

### Post by coolercooler on 2008-08-27
OK thanks m8, if anything comes to ya, just post it here.

I however think it's one of three things, bug in ubuntu os, a problem in the config file somewhere, or it might be this "wmaster0: unknown hardware address type 801" appeared from somewhere in the ifconfig list, it's not there by default but comes after messing around with internet sharing.

But most likely a bug, that thinks eth0 is internet connection.  

Much appreciated.

---

