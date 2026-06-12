---
title: "wireless not connecting"
date: 2008-06-14
forum: Networking &amp; Wireless
---

### Post by jtmedin on 2008-06-14
Have a compaq 2580us with built in wireless & router with WPA ... .
Unable to connect using 8.04 :-(.
Evidently sees the wireless hardware since i can manually configure the ssid, wpa ... but no connect. 
Anyone got any ideas?
What am i doing wrong? TIA

---

### Post by pytheas22 on 2008-06-14
We need to know the chipset of your card.  Please post the output of:
```

lspci
lsusb
lshw -C Network
```

---

### Post by jtmedin on 2008-06-15
> **pytheas22 said:**
> We need to know the chipset of your card.  Please post the output of:
```

lspci
lsusb
lshw -C Network
```
lspci:
00:00.0 Host bridge: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:0b.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0b.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0b.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M

lsucb:
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

lshw -C Network:
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0d:9d:5d:dc:df
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=natsemi driverversion=2.1 ip=192.168.1.101 latency=90 maxlatency=52 mingnt=11 module=natsemi multicast=yes
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:43:0a:5b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


Hope that helps

---

### Post by pytheas22 on 2008-06-15
Coincidentally, I have the same chipset, Broadcom 4306, in one of my machines.  It has a lot of issues in Hardy because Ubuntu started using the next-generation Broadcom driver even though it doesn't really work for many people.  These steps should allow you to revert to the older, more reliable Broadcom driver.

1. enable old driver and blacklist new one:
```

sudo -s
sed -e 's/bcm43xx/b43/' /etc/modprobe.d/blacklist
echo 'blacklist b43legacy' >> /etc/modprobe.d/blacklist
echo 'blacklist ssb' >> /etc/modprobe.d/blacklist
echo 'blacklist b43legacy ssb' >> /etc/modprobe.d/blacklist
echo 'blacklist b43 ssb' >> /etc/modprobe.d/blacklist
```

2. install and extract firmware for older driver:
```

apt-get install bcm43xx-fwcutter
```

when you're asked if the firmware should be automatically fetched, be sure to say yes

3. reboot and see if you have better luck.  Please reply with your results.

---

### Post by jtmedin on 2008-06-15
Ok did step 1 & get this in /etc/modprob.d/blacklist:
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

blacklist b431egacy
blacklist ssb
blacklist b431egacy ssb
blacklist b43 ssb




Ok ran step 2 & got:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  bcm43xx-fwcutter
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 25.8kB of archives.
After this operation, 119kB of additional disk space will be used.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe bcm43xx-fwcutter 1:006-
  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/b/bcm43xx-fwcutter/bcm43xx-fwcutter_006-3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/b/bcm43xx-fwcutter/bcm43xx-fwcutter_006-3_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

Did not get asked about auto fetch
Rebooted & still have no conection

---

### Post by pytheas22 on 2008-06-16
Did you have an Internet connection when you ran the second step?  If so, please run the command:

```
sudo apt-get update
```

and try running step 2 again.  There may have been some weird problem with the server that was causing it not to find the package, or you could have a problem with apt-get.  I can download it now without a problem.  It would probably also worked if you just clicked this [link]("http://us.archive.ubuntu.com/ubuntu/pool/universe/b/bcm43xx-fwcutter/bcm43xx-fwcutter_006-3_i386.deb") to download the package without using aptitude.

If you can't get Internet access on your Ubuntu machine, you can still do what you need, but it will be a little more complicated.  Please let me know if that's the case and I'll give you the steps.

---

### Post by jtmedin on 2008-06-16
It just occured to me that step2 probably requires internet access. I will try & connect with a cable tonite & perhaps that will change the results.
Also in step1 i mistyped one of the echo's & used gedit to delete that line from /etc/modprobe.d/blacklist hope that is ok.

---

### Post by jtmedin on 2008-06-16
It just occured to me that step2 probably requires internet access. I will try & connect with a cable tonite & perhaps that will change the results.
Also in step1 i mistyped one of the echo's & used gedit to delete that line from /etc/modprobe.d/blacklist hope that is ok.

---

### Post by pytheas22 on 2008-06-16
> Also in step1 i mistyped one of the echo's & used gedit to delete that line from /etc/modprobe.d/blacklist hope that is ok.

Yes, that's fine.  You could have used gedit to do the whole blacklisting thing but I just gave the commands because the instructions are more exact that way.

And yes, not having an Internet connection is the reason that step 2 failed.  Plug in and try it again.

---

### Post by jtmedin on 2008-06-16
Ok got a wired internet connection & did step2 again. Worked a lot better but too fast for me to comprehend. It did ask about auto fetch of firmware.

Rebooted & clicked on network icon, specified the wireless network to connect to. Entered the ssid security 'PWA', password, tkip & connect. Got the round & round icon but in the end no connection :-(.

---

### Post by pytheas22 on 2008-06-16
hmmmm

could you post the output of these again please:
```

iwconfig
lshw -C Network
ls /lib/firmware
sudo modprobe --verbose bcm43xx
sudo rmmod --verbose b43
```

---

### Post by jtmedin on 2008-06-18
> **pytheas22 said:**
> hmmmm

could you post the output of these again please:
```

iwconfig
lshw -C Network
ls /lib/firmware
sudo modprobe --verbose bcm43xx
sudo rmmod --verbose b43
```

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sudo lshw -C Network
[sudo] password for ted: 
  *-network:0 UNCLAIMED   
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64
  *-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0d:9d:5d:dc:df
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=full ip=10.0.0.100 latency=90 link=yes maxlatency=52 mingnt=11 module=natsemi multicast=yes port=twisted pair speed=100MB/s

ted@tm-laptop:~$ ls /lib/firmware
2.6.24-16-generic     bcm43xx_initval05.fw    bcm43xx_microcode2.fw
2.6.24-18-generic     bcm43xx_initval06.fw    bcm43xx_microcode4.fw
2.6.24-19-generic     bcm43xx_initval07.fw    bcm43xx_microcode5.fw
bcm43xx_initval01.fw  bcm43xx_initval08.fw    bcm43xx_pcm4.fw
bcm43xx_initval02.fw  bcm43xx_initval09.fw    bcm43xx_pcm5.fw
bcm43xx_initval03.fw  bcm43xx_initval10.fw
bcm43xx_initval04.fw  bcm43xx_microcode11.fw

ted@tm-laptop:~$ sudo modprobe --verbose bcm43xx
insmod /lib/modules/2.6.24-19-generic/kernel/net/ieee80211/ieee80211_crypt.ko 
insmod /lib/modules/2.6.24-19-generic/kernel/net/ieee80211/ieee80211.ko 
insmod /lib/modules/2.6.24-19-generic/kernel/net/ieee80211/softmac/ieee80211softmac.ko 
insmod /lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/bcm43xx/bcm43xx.ko 

ted@tm-laptop:~$ sudo rmmod --verbose b43[/CODE][/QUOTE]
ERROR: Module QUOTE] does not exist in /proc/modules
----> NOT SURE HOW I CAME UP WITH [/CODE][/QUOTE]

ted@tm-laptop:~$ sudo rmmod --verbose b43
ERROR: Module b43 does not exist in /proc/modules

---

### Post by jtmedin on 2008-06-18
Well color me confused, i thought i would try again to connect wireless. It connected, the only thing i did different was under security type i left the default on rather than select tkip.


Thanks so much for ur help :-).

---

### Post by pytheas22 on 2008-06-18
I'm glad to hear that it's working now.  I was stumped earlier as to why it was not because everything appeared to be in order.

---

### Post by jtmedin on 2008-06-18
Well i am back to being confused. I was connected wired. Unplugged the wired & clicked on the network icon. Then went to our router address & was able to connect. Rebooted & now i can no longer connect. What are the steps to use to connect to our router wireless.

---

### Post by pytheas22 on 2008-06-18
Make sure the bcm43xx module is loaded:

sudo modprobe bcm43xx

and b43/b43 legacy are unloaded:

sudo rmmod b43 b43legacy

they should be automatically, but maybe they're not for some reason, which is easy enough to fix if that's the case.

Otherwise, you say it worked before after you'd connected with the ethernet cable first.  Can you try reproducing that?  In other words, plug the cable in and connect, then unplug it and try the wireless again.

Also did you use the same security option as when you were able to connect the first time?

---

### Post by jtmedin on 2008-06-19
sudo modprobe bcm43xx

produced nothing

sudo rmmod b43 b43legacy
 error:module b43 does not exist in /proc/modules
 error:module b43legacy does not exist in  /proc/modules

Yes i did reboot with wired connection & then removed wired.
clicked on the network icon (not sure but belive a right click) & got nothing. The first time when it worked i got several wireless sites from the neighborhood & clicked on our site. Set up the security & it connected. While i was composing this msg on another pc i left ubuntu on the notebook running. Guess what, when i clicked on the network icon there were all the neighborhood wireless networks including ours. Clicked on our network & didnt connect. Went back & clicked on the network icon then clicked on 'connect to other wireless network'. Specified our ssid & security & it connected :-). So got any ideas what i am doing wrong? TIA

---

### Post by pytheas22 on 2008-06-19
I don't really know what to make of that behavior other than that Network Manager is doing something flaky.  You could try using a different wireless manager like [wicd]("http://wicd.sourceforge.net") to see if it is just NM that gives erratic results (I would kill NM first with the command "sudo kill $(ps -e | grep Network)" first).  Or you could set up the interface to automatically connect to your network whenever it comes up, which might be the equivalent of the "connect to other wireless network" option.

I would give wicd a shot first though.  I have had weird behavior from NM with my Broadcom wireless card in the past.

---

### Post by jtmedin on 2008-06-19
Think i found out how to start the wireless.
did ur two modprobe suggestions & the wireless came up & i was able to connect via 'connect to other wireless ... ' :-)
Thanks

---

### Post by pytheas22 on 2008-06-19
Glad to hear you seem finally to have solved it.  I don't know why you need to run those commands to get it to work, but at least it does.

If you add "bcm43xx" to the file /etc/modules, you shouldn't have to load it manually each time.  If that doesn't work you could also write a script to run at boot to automatically perform the commands you need to get the wireless up.

---

### Post by jtmedin on 2008-06-19
Turn out all i need is the first:sudo modprobe bcm43xx

To get it going :-). Thanks

---

### Post by jtmedin on 2008-07-04
Ok have the bcm43xx code running but the xfer rate is very poor. goes from 345b/s to 57kB/s & all points between. Do you have that experience on ur machine with the broadcom hardware? TIA

---

### Post by pytheas22 on 2008-07-04
My Broadcom card gets decent transfer rates, although I do notice that sometimes it wants to use 1MB/s rates instead of 11MB/s (the maximum supported by bcm43xx).  If iwconfig reports a low rate, try:
```

sudo iwconfig eth1 rate 11M
```

and it might make a difference.

If not and this is a major problem for you, you can use ndiswrapper instead of bcm43xx.

---

### Post by ShaxxiE on 2008-08-18
Ive still got the same problem which i cant sort out...

Not sure if anyone else is experiencing the same issue.

---

### Post by pytheas22 on 2008-08-18
> Ive still got the same problem which i cant sort out...

Not sure if anyone else is experiencing the same issue.

You mean a problem with flaky transfer rates?  If so, does "sudo iwconfig eth1 rate 11M" help?  If not, please post the output of:

```
lshw -C Network
lspci -nn
```

---

### Post by ShaxxiE on 2008-08-18
> **pytheas22 said:**
> You mean a problem with flaky transfer rates?  If so, does "sudo iwconfig eth1 rate 11M" help?  If not, please post the output of:

```
lshw -C Network
lspci -nn
```

Nope... i cant even connect to my wireless (i can see it and it has a very good signal, currently 79%), ive read through and tried endless posts on this forum.  Ive got a post going on at [http://ubuntuforums.org/showthread.php?t=893491]("http://ubuntuforums.org/showthread.php?t=893491")

Here is the output to the code you requested:

```
root@shaheen-desktop:~# lshw -C Network
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:1
       description: Ethernet interface
       product: 3c940 10/100/1000Base-T [Marvell]
       vendor: 3Com Corporation
       physical id: e
       bus info: pci@0000:00:0e.0
       logical name: eth0
       version: 12
       serial: 00:50:8d:f7:0f:16
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.13 duplex=full firmware=N/A ip=192.168.1.10 latency=32 link=yes maxlatency=31 mingnt=23 module=skge multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0c:41:13:a6:2b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
root@shaheen-desktop:~# 

```

and the second part:

```
root@shaheen-desktop:~# lspci -nn
00:00.0 Host bridge [0600]: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge [1106:3188] (rev 01)
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South] [1106:b188]
00:07.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) [104c:8024]
00:08.0 Multimedia audio controller [0401]: Creative Labs SB Audigy [1102:0004] (rev 05)
00:0a.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)
00:0c.0 Multimedia video controller [0400]: Brooktree Corporation Bt878 Video Capture [109e:036e] (rev 11)
00:0c.1 Multimedia controller [0480]: Brooktree Corporation Bt878 Audio Capture [109e:0878] (rev 11)
00:0d.0 RAID bus controller [0104]: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller [1095:3114] (rev 02)
00:0e.0 Ethernet controller [0200]: 3Com Corporation 3c940 10/100/1000Base-T [Marvell] [10b7:1700] (rev 12)
00:0f.0 RAID bus controller [0104]: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller [1106:3149] (rev 80)
00:0f.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06)
00:10.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.3 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.4 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 86)
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South] [1106:3227]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV36.2 [GeForce FX 5700] [10de:0342] (rev a1)

```

Hope you can help.... :)

Thanks in advance

---

### Post by pytheas22 on 2008-08-19
I browsed through your other thread with Ayuthia.  I'm not sure if you have it solved yet.  You do need to make sure that you use 64-bit Windows drivers with ndiswrapper if you go that route.

Another route is to use bcm43xx, an older version of the Broadcom driver--I don't think Ayuthia had you try this, but I know that it works for Broadcom 4306 as I have the same card.  To use that driver, run:
```

sudo -s
sed 's/blacklist bcm43xx/#blacklist bcm43xx/g' /etc/modprobe.d/blacklist
apt-get install bcm43xx-fwcutter
```

You will be prompted to download firmware automatically.  Say yes.  Then reboot.  After reboot, run these commands:
```

sudo modprobe -r b44 b43 b43legacy ssb ndiswrapper bcm43xx
sudo modprobe bcm43xx
sudo ifconfig eth1 up
```

Then see if you can connect.  If it works, let me know and we can make the solution permanent--for the time being, you'd have to run the "sudo modprobe -r b44 b43 b43legacy ssb ndiswrapper bcm43xx" after each reboot to get the wireless up.

---

### Post by ShaxxiE on 2008-08-19
> **pytheas22 said:**
> I browsed through your other thread with Ayuthia.  I'm not sure if you have it solved yet.  You do need to make sure that you use 64-bit Windows drivers with ndiswrapper if you go that route.

Another route is to use bcm43xx, an older version of the Broadcom driver--I don't think Ayuthia had you try this, but I know that it works for Broadcom 4306 as I have the same card.  To use that driver, run:
```

sudo -s
sed 's/blacklist bcm43xx/#blacklist bcm43xx/g' /etc/modprobe.d/blacklist
apt-get install bcm43xx-fwcutter
```

You will be prompted to download firmware automatically.  Say yes.  Then reboot.  After reboot, run these commands:
```

sudo modprobe -r b44 b43 b43legacy ssb ndiswrapper bcm43xx
sudo modprobe bcm43xx
sudo ifconfig eth1 up
```

Then see if you can connect.  If it works, let me know and we can make the solution permanent--for the time being, you'd have to run the "sudo modprobe -r b44 b43 b43legacy ssb ndiswrapper bcm43xx" after each reboot to get the wireless up.

Tried it just now - re-booted and i still cannot connect... :(

---

### Post by pytheas22 on 2008-08-19
After you reboot and run these commands:
```

sudo modprobe -r b44 b43 b43legacy ssb ndiswrapper bcm43xx
sudo modprobe bcm43xx
sudo ifconfig eth1 up
```

what is the output of:
```

lshw -C Network
dmesg | grep bcm
```

---

### Post by ShaxxiE on 2008-08-19
> **pytheas22 said:**
> After you reboot and run these commands:
```

sudo modprobe -r b44 b43 b43legacy ssb ndiswrapper bcm43xx
sudo modprobe bcm43xx
sudo ifconfig eth1 up
```

what is the output of:
```

lshw -C Network
dmesg | grep bcm
```

Ok here goes

I still cant connect to my wireless network...

Here is the output as requested:

```
shaheen@shaheen-desktop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth1
       version: 02
       serial: 00:0c:41:13:a6:2b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.24-19-generic latency=32 module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
  *-network:1
       description: Ethernet interface
       product: 3c940 10/100/1000Base-T [Marvell]
       vendor: 3Com Corporation
       physical id: e
       bus info: pci@0000:00:0e.0
       logical name: eth0
       version: 12
       serial: 00:50:8d:f7:0f:16
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=skge driverversion=1.13 firmware=N/A ip=192.168.1.10 latency=32 maxlatency=31 mingnt=23 module=skge multicast=yes
shaheen@shaheen-desktop:~$ dmesg | grep bcm
[ 6463.815891] bcm43xx driver
[ 6464.530605] bcm43xx: Radio enabled by hardware
[ 6464.581336] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-2.6.24/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1112
[ 6464.581358] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-2.6.24/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1112
[ 6464.581461] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-2.6.24/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1112
[ 6464.581471] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-2.6.24/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1112
[ 6464.581479] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-2.6.24/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1112
[ 6464.581488] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-2.6.24/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1112
[ 6464.581496] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-2.6.24/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1112
[ 6464.581504] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-2.6.24/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1112
[ 6464.581513] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-2.6.24/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1114
[ 6464.581521] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-2.6.24/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1114
[ 6464.581530] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-2.6.24/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1114
[ 6464.581538] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-2.6.24/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1114
[ 6791.625532] bcm43xx driver
[ 6792.264248] bcm43xx: Radio enabled by hardware
[ 6792.310949] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-2.6.24/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1112
[ 6792.310972] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-2.6.24/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1112
[ 6792.310981] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-2.6.24/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1112
[ 6792.310990] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-2.6.24/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1112
[ 6792.310999] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-2.6.24/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1112
[ 6792.311007] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-2.6.24/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1112
[ 6792.311016] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-2.6.24/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1112
[ 6792.311024] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-2.6.24/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1112
[ 6792.311033] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-2.6.24/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1114
[ 6792.311041] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-2.6.24/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1114
[ 6792.311050] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-2.6.24/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1114
[ 6792.311058] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-2.6.24/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1114
shaheen@shaheen-desktop:~$ 

```

looks like something is wrong....

---

### Post by pytheas22 on 2008-08-19
It looks like possibly a problem with the firmware that you installed for the bcm43xx driver.  Do you know which file you extracted it from?  You may want to try removing it with:
```

sudo rm /lib/firmware/bcm*fw
```

And then reinstall the firmware again by redownloading the bcm43xx-fwcutter package:
```

sudo apt-get remove --purge bcm43xx-fwcutter
sudo apt-get install bcm43xx-fwcutter
```

After it finishes downloading, it should ask you if you want to also automatically download and extract the firmware.  Say yes.  The firmware that it downloads works well on my computer with my 4306 chip.

After you get the new firmware, please reboot, run the same commands again to remove the b43 module etc., then look at "dmesg | grep bcm" again.  Does it still mention the errors about "incomplete keycode...?"

If might also be a problem with the module itself.  Which kernel are you running (in other words, what is the output of "uname -r")?  You didn't build it yourself, did you?

---

### Post by ShaxxiE on 2008-08-20
Hello

Wow built it myself? I wish!! - No im completely new to Linux and i don't have a clue how to build anything.

I did what you said and i downloaded the new fwcutter:


> ```
sudo apt-get remove --purge bcm43xx-fwcutter
sudo apt-get install bcm43xx-fwcutter
```

and also the bit below that.. and then i did what you said in the previous post on P3... The output is below:

```
shaheen@shaheen-desktop:~$ sudo modprobe -r b44 b43 b43legacy ssb ndiswrapper bcm43xx
shaheen@shaheen-desktop:~$ sudo modprobe bcm43xx
shaheen@shaheen-desktop:~$ sudo ifconfig eth1 up
shaheen@shaheen-desktop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth1
       version: 02
       serial: 00:0c:41:13:a6:2b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.24-19-generic latency=32 module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
  *-network:1
       description: Ethernet interface
       product: 3c940 10/100/1000Base-T [Marvell]
       vendor: 3Com Corporation
       physical id: e
       bus info: pci@0000:00:0e.0
       logical name: eth0
       version: 12
       serial: 00:50:8d:f7:0f:16
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=skge driverversion=1.13 firmware=N/A ip=192.168.1.10 latency=32 maxlatency=31 mingnt=23 module=skge multicast=yes
shaheen@shaheen-desktop:~$ dmesg | grep bcm
[   64.204390] ndiswrapper: driver bcmwl564 (,10/01/2002,3.70.17.5) loaded
[   64.333514] wlan0: ethernet device 00:0c:41:13:a6:2b using NDIS driver: bcmwl564, version: 0x3461105, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4320.5.conf
[  564.298874] bcm43xx driver
[  564.554185] bcm43xx: Radio enabled by hardware
[  564.574978] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-2.6.24/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1112
[  564.574987] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-2.6.24/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1112
[  564.574991] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-2.6.24/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1112
[  564.574995] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-2.6.24/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1112
[  564.574998] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-2.6.24/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1112
[  564.575002] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-2.6.24/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1112
[  564.575005] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-2.6.24/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1112
[  564.575009] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-2.6.24/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1112
[  564.575012] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-2.6.24/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1114
[  564.575016] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-2.6.24/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1114
[  564.575019] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-2.6.24/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1114
[  564.575022] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-2.6.24/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1114
shaheen@shaheen-desktop:~$ 

```

Looks like something is still wrong!!

S

---

### Post by pytheas22 on 2008-08-20
hmmm, yeah, I don't know why but there seems to be a problem with the bcm43xx module that you have.  As I've mentioned, that seems really strange to me because I have the same exact wireless card (14e4:4320) and the bcm43xx driver works fine.

I know you've already tried ndiswrapper, but if you want to give it another shot, I know that these steps work (at least, barring anything weird going on), as I just got done helping someone else with (once again) the same exact card (he also had some weird issues with bcm43xx, incidentally, which is why we went to ndiswrapper): 
```

sudo -s
echo 'blacklist bcm43xx' >> /etc/modprobe.d/blacklist
echo 'ndiswrapper' >> /etc/modules
apt-get remove --purge ndiswrapper*
apt-get install ndiswrapper*
wget http://burnthesorbonne.com/files/4320_drivers.tar.gz
tar -xzvf 4320*
ndiswrapper -i bcmwl5a.inf
```

Then reboot.  If the wireless still doesn't work, run:
```

sudo modprobe -r b43 b44 b43legacy ssb ndiswrapper bcm43xx
sudo modprobe ndiswrapper
```

and it should.

If this still doesn't help, you may want to consider reinstalling Ubuntu, because something weird may be going on.  Otherwise, if you want to try to troubleshoot ndiswrapper, post:
```

ndiswrapper -l
dmesg | grep ndis
lshw -C Network
```

---

### Post by ricksterinps on 2008-09-08
> **pytheas22 said:**
> I browsed through your other thread with Ayuthia.  I'm not sure if you have it solved yet.  You do need to make sure that you use 64-bit Windows drivers with ndiswrapper if you go that route.

Another route is to use bcm43xx, an older version of the Broadcom driver--I don't think Ayuthia had you try this, but I know that it works for Broadcom 4306 as I have the same card.  To use that driver, run:
```

sudo -s
sed 's/blacklist bcm43xx/#blacklist bcm43xx/g' /etc/modprobe.d/blacklist
apt-get install bcm43xx-fwcutter
```

You will be prompted to download firmware automatically.  Say yes.  Then reboot.  After reboot, run these commands:
```

sudo modprobe -r b44 b43 b43legacy ssb ndiswrapper bcm43xx
sudo modprobe bcm43xx
sudo ifconfig eth1 up
```

Then see if you can connect.  If it works, let me know and we can make the solution permanent--for the time being, you'd have to run the "sudo modprobe -r b44 b43 b43legacy ssb ndiswrapper bcm43xx" after each reboot to get the wireless up.


Hello,

The "sudo modprobe -r b44 b43 b43legacy ssb ndiswrapper bcm43xx" code ended up getting my wireless working and you mentioned in your post that if it did, you would let them know how to make it permanent.  

What do I need to do so that I don't need to do this each time it starts.

Thanks

---

### Post by pytheas22 on 2008-09-08
I'm glad those commands worked for you.  To write a script so that those commands get run automatically at boot, first open up a blank file:
```

sudo gedit /etc/init.d/wifi-fix.sh
```

Then add these lines to it:
```

#!/bin/bash
#this script unloads modules that conflict with bcm43xx; see http://ubuntuforums.org/showthread.php?t=829327&page=4 for details

modprobe -r b44 b43 b43legacy ssb ndiswrapper bcm43xx
modprobe bcm43xx
ifconfig eth1 up
```

Then save and close the file, and run this so that the computer will know to run the script at boot:
```

cd /etc/init.d
sudo -s
chmod +x wifi-fix.sh
update-rc.d wifi-fix.sh defaults
```

Thereafter you should be able to reboot and have the wireless working automatically.  If not, let me know.

---

### Post by ricksterinps on 2008-09-11
Thanks.  That worked perfectly.

---

