---
title: "Wireless connection present, but cannot connect - Broadcom BCM4306 Ubuntu 8.04 Hardy"
date: 2008-08-18
forum: Networking &amp; Wireless
---

### Post by ShaxxiE on 2008-08-18
Hi

Im a complete n00b to Linux, i have never used it before but i feel im just, very slowly, kinda getting there - I installed the latest Ubuntu 8.04 Hardy Heron last night.  So if you wish to reply...please bear in mind to dumb things down a bit.... ok then a lot!

**My Problem:**
I can see my wireless signal being broadcast, it has 100% strength, but i cannot connect to it.  

Ok so i happen to be very unlucky and i have the following wireless card:

> 
00:0a.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

Firstly i followed this post but it didn't work:

**[http://ubuntuforums.org/showthread.php?t=779754]("http://ubuntuforums.org/showthread.php?t=779754")**

From here I followed the no-fluff documentation:
[B]
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff")[/B]

the only bits that didnt work for me were in the **'Trying It Temporarily'** section.

```
sudo rmmod b43
sudo rmmod b44

``` 

Where i got the the following errors:

> ERROR: Module b43 does not exist in /proc/modules
ERROR: Module b44 does not exist in /proc/modules


However after following this guide (ALL THE WAY, even through the NO LUCK section) i am still left with not being able to connect to my wireless network, which still has 100% strength.  

Ive looked and looked through the posts, one post lead to another and before i know it i have somehow managed to install the "Advance Desktop Settings" to get my screen into a cube.

I have ensured that i have entered the correct Wireless Password, and also ensured i have selected the correct encryption type, which is WPA2.

Anyway help would be appreciated, and please remember to dumb it down as i am an absolute beginner.

Thank you

---

### Post by Ayuthia on 2008-08-18
> **ShaxxiE said:**
> 
the only bits that didnt work for me were in the **'Trying It Temporarily'** section.

```
sudo rmmod b43
sudo rmmod b44

``` 

Where i got the the following errors:
```
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module b44 does not exist in /proc/modules 
```
You don't need to worry about those error messages.  It is just saying that your system was not currently using those modules.  If I recall correctly, your card is a b43legacy instead of b43.  And yes, the 4306 card seems to be having a lot of problems lately.


> I have ensured that i have entered the correct Wireless Password, and also ensured i have selected the correct encryption type, which is WPA2.

Have you tried turning off your encryption and checking to see if you can connect?  I am not suggesting that this should be done permanenty, but to try and see if the wireless driver is having problems with connecting using WPA2.

---

### Post by ShaxxiE on 2008-08-18
Seems like im messed things up even more - i ended up blacklisting some of the drivers, so i don't have no wireless at all in the top right hand side of the desktop. - and therefore i cant follow the instructions above re getting rid of the WPA2.

I followed the instructions on this post:

[http://ubuntuforums.org/showthread.php?t=829327]("http://ubuntuforums.org/showthread.php?t=829327")

Below are some more details:

```
lspci
```

still shows my wireless is there:

> 00:0a.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)


And typing the following i get:

```
iwconfig
```

> root@shaheen-desktop:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


--------------------------------------

```
lshw -C Network
```

> root@shaheen-desktop:~# lshw -C Network
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


--------------------------------------

```
ls /lib/firmware

```

> root@shaheen-desktop:~# ls /lib/firmware
2.6.24-19-generic  bcm43xx_initval01.fw  bcm43xx_initval04.fw  bcm43xx_initval07.fw  bcm43xx_initval10.fw    bcm43xx_microcode4.fw  bcm43xx_pcm5.fw
b43                bcm43xx_initval02.fw  bcm43xx_initval05.fw  bcm43xx_initval08.fw  bcm43xx_microcode11.fw  bcm43xx_microcode5.fw
b43legacy          bcm43xx_initval03.fw  bcm43xx_initval06.fw  bcm43xx_initval09.fw  bcm43xx_microcode2.fw   bcm43xx_pcm4.fw


--------------------------------------

Ahhhghh!! :/

---

### Post by ShaxxiE on 2008-08-18
Ok i deblacklisted all the drivers and ive got my wireless showing again, but still in a loop of endless non connections.

I have just set no security, and still i cant connect :(

---

### Post by Ayuthia on 2008-08-18
> **ShaxxiE said:**
> 

ls /lib/firmware

```
root@shaheen-desktop:~# ls /lib/firmware
2.6.24-19-generic bcm43xx_initval01.fw bcm43xx_initval04.fw bcm43xx_initval07.fw bcm43xx_initval10.fw bcm43xx_microcode4.fw bcm43xx_pcm5.fw
b43 bcm43xx_initval02.fw bcm43xx_initval05.fw bcm43xx_initval08.fw bcm43xx_microcode11.fw bcm43xx_microcode5.fw
b43legacy bcm43xx_initval03.fw bcm43xx_initval06.fw bcm43xx_initval09.fw bcm43xx_microcode2.fw bcm43xx_pcm4.fw 
```


The information above does not look correct.  It looks like the bcm43xx firmware has been copied into b43 and b43legacy.  This could be causing the problems that you are having.  Let's try and see if we can get it working with the old bcm43xx:
```
sudo modprobe -r b43 b44 ssb ndiswrapper wl bcm43xx
sudo depmod -ae
sudo modprobe bcm43xx
sudo ifconfig wlan0 up
sudo dhclient -r
sudo iwconfig wlan0 essid name-of-router
sudo dhclient wlan0

```

---

### Post by ShaxxiE on 2008-08-18
> **Ayuthia said:**
> 
```
sudo modprobe -r b43 b44 ssb ndiswrapper wl bcm43xx
sudo depmod -ae
sudo modprobe bcm43xx
sudo ifconfig wlan0 up
sudo dhclient -r
sudo iwconfig wlan0 essid name-of-router
sudo dhclient wlan0

```

Hello and thanks for your reply.

I still have no joy.... :( - Here is what i typed in and the corresponding results.  Sometimes i pressed 'Enter' and nothing seems like it happened...

```
root@shaheen-desktop:~# sudo modprobe -r b43 b44 ssb ndiswrapper wl bcm43xx
FATAL: Module ssb is in use.
root@shaheen-desktop:~# sudo depmod -ae
root@shaheen-desktop:~# sudo modprobe bcm43xx
root@shaheen-desktop:~# sudo ifconfig wlan0 up
root@shaheen-desktop:~# sudo dhclient -r
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:0c:41:13:a6:2b
Sending on   LPF/wlan0/00:0c:41:13:a6:2b
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Listening on LPF/eth0/00:50:8d:f7:0f:16
Sending on   LPF/eth0/00:50:8d:f7:0f:16
Sending on   Socket/fallback
root@shaheen-desktop:~# sudo iwconfig wlan0 essid CaRRoT
root@shaheen-desktop:~# sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:0c:41:13:a6:2b
Sending on   LPF/wlan0/00:0c:41:13:a6:2b
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

``` 

Hope this is useful - by the way my SSID is CaRRoT

---

### Post by Ayuthia on 2008-08-18
Ok.  Let's try the ndiswrapper route.  Check and see if ndiswrapper shows that the device is present by doing:
```
ndiswrapper -l
```
It should show something like:
```
bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: ssb)

```

If it does, please try the following:
```
sudo modprobe -r b43 b44 ssb wl ndiswrapper bcm43xx
sudo depmod -ae
sudo modprobe ndiswrapper
```
If all goes well, you will not get any messages back.  If that is the case:
```
sudo dhclient -r wlan0
sudo iwconfig wlan0 essid CaRRoT
sudo dhclient wlan0
```

---

### Post by ShaxxiE on 2008-08-18
Hi Again

Thanks for responding so quickly, i appreciate it.

I did as you said and here is the log from Terminal:

```
shaheen@shaheen-desktop:~$ sudo -s
[sudo] password for shaheen: 
root@shaheen-desktop:~# ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: ssb)
root@shaheen-desktop:~# sudo modprobe -r b43 b44 ssb wl ndiswrapper bcm43xx
FATAL: Module ssb is in use.
root@shaheen-desktop:~# sudo depmod -ae
root@shaheen-desktop:~# sudo modprobe ndiswrapper
root@shaheen-desktop:~# sudo dhclient -r wlan0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:0c:41:13:a6:2b
Sending on   LPF/wlan0/00:0c:41:13:a6:2b
Sending on   Socket/fallback
root@shaheen-desktop:~# sudo iwconfig wlan0 essid CaRRoT
root@shaheen-desktop:~# sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:0c:41:13:a6:2b
Sending on   LPF/wlan0/00:0c:41:13:a6:2b
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
root@shaheen-desktop:~# 

```

It still does not work, i wish i knew whats wrong... Ive learnt so much with this on-going battle.  Im tempted to buy a WLAN card for £10 on e-bay but i dont want to give in just yet...

Im just going to try re-booting now and see what happens..

Thanks again for your help so far! Im sure we can get this sorted!! :)

---

### Post by ShaxxiE on 2008-08-18
I have re-booted, still no joy....

---

### Post by Ayuthia on 2008-08-18
> **ShaxxiE said:**
> I have re-booted, still no joy....

Ok, it looks like we have a problem with ssb.  Can you provide the results of:
```
lsmod|grep ssb
```

---

### Post by ShaxxiE on 2008-08-18
Here it is:

```
shaheen@shaheen-desktop:~$ lsmod|grep ssb
ssb                    39428  1 b43legacy

```

I just tried WICD also - that was a bit buggy and the WICD screen kept going grey.  Im happy with the ol Network Manager :)

---

### Post by Ayuthia on 2008-08-18
> **ShaxxiE said:**
> Here it is:

```
shaheen@shaheen-desktop:~$ lsmod|grep ssb
ssb                    39428  1 b43legacy

```

I just tried WICD also - that was a bit buggy and the WICD screen kept going grey.  Im happy with the ol Network Manager :)

I forgot that you have the b43legacy module.  Try this:
```
sudo modprobe -r b43 b43legacy b44 ssb wl ndiswrapper bcm43xx
sudo depmod -ae
sudo modprobe ndiswrapper
```
Then if all went well:
```
sudo dhclient -r wlan0
sudo iwconfig wlan0 essid CaRRoT
sudo dhclient wlan0
```
Hopefully, we will get better results.

---

### Post by ShaxxiE on 2008-08-18
Nope... What happens now is that the wireless has completely gone after entering the above code.

here is what i entered and the output:

```
root@shaheen-desktop:~# sudo modprobe -r b43 b43legacy b44 ssb wl ndiswrapper bcm43xx
root@shaheen-desktop:~# sudo depmod -ae
root@shaheen-desktop:~# sudo modprobe ndiswrapper
root@shaheen-desktop:~# sudo dhclient -r wlan0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Bind socket to interface: No such device
root@shaheen-desktop:~# sudo iwconfig wlan0 essid CaRRoT
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.
root@shaheen-desktop:~# sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
root@shaheen-desktop:~# 

```

I also rebooted my machine - my wireless was back, i then entered the code, now wireless gone.... im sure if i re-boot my wireless will show again.

Thanks again for your quick replies! :)

---

### Post by Ayuthia on 2008-08-18
> **ShaxxiE said:**
> Nope... What happens now is that the wireless has completely gone after entering the above code.

here is what i entered and the output:

```
root@shaheen-desktop:~# sudo modprobe -r b43 b43legacy b44 ssb wl ndiswrapper bcm43xx
root@shaheen-desktop:~# sudo depmod -ae
root@shaheen-desktop:~# sudo modprobe ndiswrapper
root@shaheen-desktop:~# sudo dhclient -r wlan0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Bind socket to interface: No such device
root@shaheen-desktop:~# sudo iwconfig wlan0 essid CaRRoT
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.
root@shaheen-desktop:~# sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
root@shaheen-desktop:~# 

```

I also rebooted my machine - my wireless was back, i then entered the code, now wireless gone.... im sure if i re-boot my wireless will show again.

Thanks again for your quick replies! :)

Ok.  It sounds like ndiswrapper does not like something since wlan0 did not come up.  How about replacing wlan0 with eth1?  See if that works.  If it does not, you can try reinstalling the b43legacy firmware:
```
sudo mv /lib/firmware/b43 $HOME
sudo mv /lib/firmware/b43legacy $HOME
sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh
```
I am assuming that you have a working wired connection in Ubuntu.

By the way, the first two commands are going to move the /lib/firmware/b43 and b43legacy folders to your home directory.  Then the final command will install the firmware for the b43* modules again.  I am also assuming that you have installed b43-fwcutter from the repositories or enabled it from System->Administration->Hardware Drivers.

---

### Post by ShaxxiE on 2008-08-18
:(

```
root@shaheen-desktop:~# sudo modprobe -r b43 b43legacy b44 ssb wl ndiswrapper bcm43xx
root@shaheen-desktop:~# sudo depmod -ae
root@shaheen-desktop:~# sudo modprobe ndiswrapper
root@shaheen-desktop:~# sudo dhclient -r eth1
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Bind socket to interface: No such device
root@shaheen-desktop:~# sudo iwconfig eth1 essid CaRRoT
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth1 ; No such device.
root@shaheen-desktop:~# sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device

```

Just to let you know the line you provided in the code 

> sudo modprobe -r b43 b44 ssb ndiswrapper wl bcm43xx


Gets rid of my wireless connection altogether - until I re-boot Ubuntu.

[LIST]
[*]I do have a wired connection (going upstairs into my brother's room, im really worried someone will trip over it....)
[/LIST]

[LIST]
[*]I also have b43-fwcutter (i have just marked it for re-install, and re-installed it, in case the previous installation was messed) - I cannot install it from *System --> Administration --> Hardware Drivers* because it is not in the list, the only one in the list is my Nvidia graphics card driver.
[/LIST]

[LIST]
[*]I have, again, tried to connect with an open network (i got rid of the WPA2 for a little while) - Again, it didnt connect.
[/LIST]


Because the line:

```
sudo modprobe -r b43 b44 ssb ndiswrapper wl bcm43xx
```


got rid of my wireless altogether, i will now re-boot my comp and try 

```
sudo mv /lib/firmware/b43 $HOME
sudo mv /lib/firmware/b43legacy $HOME
sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh
```

whilst the wireless connection is present.

Will post results in a mo.

S

---

### Post by ShaxxiE on 2008-08-18
Hello

```
root@shaheen-desktop:~# sudo mv /lib/firmware/b43 $HOME
root@shaheen-desktop:~# sudo mv /lib/firmware/b43legacy $HOME
root@shaheen-desktop:~# sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh--03:40:46--  http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o
           => `wl_apsta-3.130.20.0.o'
Resolving downloads.openwrt.org... 195.56.146.238
Connecting to downloads.openwrt.org|195.56.146.238|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 652,866 (638K) [application/x-object]

100%[========================================>] 652,866        1.17M/s             

03:40:47 (1.17 MB/s) - `wl_apsta-3.130.20.0.o' saved [652866/652866]

--03:40:47--  http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2
           => `broadcom-wl-4.80.53.0.tar.bz2'
Resolving downloads.openwrt.org... 195.56.146.238
Connecting to downloads.openwrt.org|195.56.146.238|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 904,072 (883K) [application/x-tar]

100%[========================================>] 904,072        1.37M/s             

03:40:47 (1.36 MB/s) - `broadcom-wl-4.80.53.0.tar.bz2' saved [904072/904072]

This file is recognised as:
  ID         :  FW10
  filename   :  wl_apsta.o
  version    :  295.14
  MD5        :  e08665c5c5b66beb9c3b2dd54aa80cb3
Extracting b43legacy/ucode2.fw
Extracting b43legacy/ucode4.fw
Extracting b43legacy/ucode5.fw
Extracting b43legacy/ucode11.fw
Extracting b43legacy/pcm4.fw
Extracting b43legacy/pcm5.fw
Extracting b43legacy/a0g0bsinitvals2.fw
Extracting b43legacy/b0g0bsinitvals5.fw
Extracting b43legacy/a0g0initvals5.fw
Extracting b43legacy/a0g1bsinitvals5.fw
Extracting b43legacy/a0g0initvals2.fw
Extracting b43legacy/a0g1initvals5.fw
Extracting b43legacy/b0g0bsinitvals2.fw
Extracting b43legacy/b0g0initvals5.fw
Extracting b43legacy/b0g0initvals2.fw
Extracting b43legacy/a0g0bsinitvals5.fw
broadcom-wl-4.80.53.0/
broadcom-wl-4.80.53.0/kmod/
broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o
broadcom-wl-4.80.53.0/kmod/wl_apsta.o
broadcom-wl-4.80.53.0/nas
broadcom-wl-4.80.53.0/wl
broadcom-wl-4.80.53.0/WHERE_FROM
broadcom-wl-4.80.53.0/libbcmcrypto.so
This file is recognised as:
  ID         :  FW11
  filename   :  wl_apsta_mimo.o
  version    :  351.126
  MD5        :  722e2e0d8cc04b8f118bb5afe6829ff9
Extracting b43/ucode4.fw
Extracting b43/ucode5.fw
Extracting b43/ucode11.fw
Extracting b43/ucode13.fw
Extracting b43/pcm4.fw
Extracting b43/pcm5.fw
Extracting b43/b0g0initvals4.fw
Extracting b43/b0g0bsinitvals4.fw
Extracting b43/a0g0initvals4.fw
Extracting b43/a0g0bsinitvals4.fw
Extracting b43/b0g0initvals5.fw
Extracting b43/b0g0bsinitvals5.fw
Extracting b43/a0g0initvals5.fw
Extracting b43/a0g1initvals5.fw
Extracting b43/a0g0bsinitvals5.fw
Extracting b43/a0g1bsinitvals5.fw
Extracting b43/lp0initvals13.fw
Extracting b43/lp0bsinitvals13.fw
Extracting b43/b0g0initvals13.fw
Extracting b43/b0g0bsinitvals13.fw
Extracting b43/a0g1initvals13.fw
Extracting b43/a0g1bsinitvals13.fw
```

So this is what i got - It installed ok, but still cant connect to CaRRoT :(

When i put my mouse over the two black computer screens icon in my tray when its trying to connect to the WLAN, it says 

> Waiting for key for the wireless network 'CaRRoT'

Im starting to think my wireless card is faulty, but it does work on XP!! ??

---

### Post by Ayuthia on 2008-08-18
> **ShaxxiE said:**
> 
Im starting to think my wireless card is faulty, but it does work on XP!! ??

Well, it is looking like Ubuntu does not like it.  Can you do me a favor and post the results of the following:
```
lspci -nnmkvd 14e4:*
uname -a
```

I am going to see if I can find a driver for NDISwrapper for you.  When you loaded ndiswrapper, I am guessing that ndiswrapper did not like the windows driver.

The information I am asking for is going to provide more information about your wireless card and also give me the kernel information that you are using.

---

### Post by ShaxxiE on 2008-08-18
Ok thank you :)

here are the results: (i dont think the first one worked)

> shaheen@shaheen-desktop:~$ lspci -nnmkvd 14e4:*
lspci: invalid option -- k
Usage: lspci [<switches>]

-v		Be verbose
-n		Show numeric ID's
-nn		Show both textual and numeric ID's (names & numbers)
-b		Bus-centric view (PCI addresses and IRQ's instead of those seen by the CPU)
-x		Show hex-dump of the standard portion of config space
-xxx		Show hex-dump of the whole config space (dangerous; root only)
-xxxx		Show hex-dump of the 4096-byte extended config space (root only)
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]	Show only devices in selected slots
-d [<vendor>]:[<device>]	Show only selected devices
-t		Show bus tree
-m		Produce machine-readable output
-i <file>	Use specified ID database instead of /usr/share/misc/pci.ids.gz
-D		Always show domain numbers
-M		Enable `bus mapping' mode (dangerous; root only)
-P <dir>	Use specified directory instead of /proc/bus/pci
-F <file>	Read configuration data from given file
-G		Enable PCI access debugging

And the second code:

> shaheen@shaheen-desktop:~$ uname -a
Linux shaheen-desktop 2.6.24-19-generic #1 SMP Fri Jul 11 21:01:46 UTC 2008 x86_64 GNU/Linux


---

### Post by Ayuthia on 2008-08-18
I am not for sure why you received the error.  Can you just post the results of lspci -nnm?

---

### Post by ShaxxiE on 2008-08-19
> **Ayuthia said:**
> I am not for sure why you received the error.  Can you just post the results of lspci -nnm?

Here it is :

```
shaheen@shaheen-desktop:~$ lspci -nnm
00:00.0 "Host bridge [0600]" "VIA Technologies, Inc. [1106]" "VT8385 [K8T800 AGP] Host Bridge [3188]" -r01 "ABIT Computer Corp. [147b]" "Unknown device [1406]"
00:01.0 "PCI bridge [0604]" "VIA Technologies, Inc. [1106]" "VT8237 PCI bridge [K8T800/K8T890 South] [b188]" "" ""
00:07.0 "FireWire (IEEE 1394) [0c00]" "Texas Instruments [104c]" "TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) [8024]" -p10 "ABIT Computer Corp. [147b]" "Unknown device [1406]"
00:08.0 "Multimedia audio controller [0401]" "Creative Labs [1102]" "SB Audigy [0004]" -r05 "Creative Labs [1102]" "Unknown device [2005]"
00:0a.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4306 802.11b/g Wireless LAN Controller [4320]" -r02 "Linksys [1737]" "Unknown device [0013]"
00:0c.0 "Multimedia video controller [0400]" "Brooktree Corporation [109e]" "Bt878 Video Capture [036e]" -r11 "Hauppauge computer works Inc. [0070]" "WinTV Series [13eb]"
00:0c.1 "Multimedia controller [0480]" "Brooktree Corporation [109e]" "Bt878 Audio Capture [0878]" -r11 "Hauppauge computer works Inc. [0070]" "WinTV Series [13eb]"
00:0d.0 "RAID bus controller [0104]" "Silicon Image, Inc. [1095]" "SiI 3114 [SATALink/SATARaid] Serial ATA Controller [3114]" -r02 "Silicon Image, Inc. [1095]" "SiI 3114 SATARaid Controller [6114]"
00:0e.0 "Ethernet controller [0200]" "3Com Corporation [10b7]" "3c940 10/100/1000Base-T [Marvell] [1700]" -r12 "ABIT Computer Corp. [147b]" "Unknown device [1406]"
00:0f.0 "RAID bus controller [0104]" "VIA Technologies, Inc. [1106]" "VIA VT6420 SATA RAID Controller [3149]" -r80 "ABIT Computer Corp. [147b]" "Unknown device [1406]"
00:0f.1 "IDE interface [0101]" "VIA Technologies, Inc. [1106]" "VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [0571]" -r06 -p8a "ABIT Computer Corp. [147b]" "Unknown device [1406]"
00:10.0 "USB Controller [0c03]" "VIA Technologies, Inc. [1106]" "VT82xxxxx UHCI USB 1.1 Controller [3038]" -r81 "ABIT Computer Corp. [147b]" "Unknown device [1406]"
00:10.1 "USB Controller [0c03]" "VIA Technologies, Inc. [1106]" "VT82xxxxx UHCI USB 1.1 Controller [3038]" -r81 "ABIT Computer Corp. [147b]" "Unknown device [1406]"
00:10.2 "USB Controller [0c03]" "VIA Technologies, Inc. [1106]" "VT82xxxxx UHCI USB 1.1 Controller [3038]" -r81 "ABIT Computer Corp. [147b]" "Unknown device [1406]"
00:10.3 "USB Controller [0c03]" "VIA Technologies, Inc. [1106]" "VT82xxxxx UHCI USB 1.1 Controller [3038]" -r81 "ABIT Computer Corp. [147b]" "Unknown device [1406]"
00:10.4 "USB Controller [0c03]" "VIA Technologies, Inc. [1106]" "USB 2.0 [3104]" -r86 -p20 "ABIT Computer Corp. [147b]" "Unknown device [1406]"
00:11.0 "ISA bridge [0601]" "VIA Technologies, Inc. [1106]" "VT8237 ISA bridge [KT600/K8T800/K8T890 South] [3227]" "ABIT Computer Corp. [147b]" "Unknown device [1406]"
00:18.0 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1100]" "" ""
00:18.1 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] Address Map [1101]" "" ""
00:18.2 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] DRAM Controller [1102]" "" ""
00:18.3 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] Miscellaneous Control [1103]" "" ""
01:00.0 "VGA compatible controller [0300]" "nVidia Corporation [10de]" "NV36.2 [GeForce FX 5700] [0342]" -ra1 "" ""

```

---

### Post by Ayuthia on 2008-08-19
I forgot to ask which driver you tried from the no-fluff site.  Did you try step 2f from [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%202f:%20WPC54Gv2%20%20Driver%20Download/Extraction](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%202f:%20WPC54Gv2%20%20Driver%20Download/Extraction)

---

### Post by ShaxxiE on 2008-08-19
> **Ayuthia said:**
> I forgot to ask which driver you tried from the no-fluff site.  Did you try step 2f from [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%202f:%20WPC54Gv2%20%20Driver%20Download/Extraction](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%202f:%20WPC54Gv2%20%20Driver%20Download/Extraction)

Hi again!

Yep i did step 2F, and i do have the Linksys Card.

Ive been looking on ebay for some other cards - ive seen one with the RTL8185L firmware - for about £12/ $24....

I wont give in yet!!

:lolflag:

---

### Post by ShaxxiE on 2008-08-19
Ok i tried to install NDISWrapper again using nofluff guide.

My *'module'* is 'module=ssb' and not 'module=ndiswrapper' and therefore according to fluff i got a problem. :/

```
shaheen@shaheen-desktop:~$ echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
[sudo] password for shaheen: 
blacklist bcm43xx
shaheen@shaheen-desktop:~$ sudo apt-get install ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndiswrapper-utils-1.9 is already the newest version.
The following packages were automatically installed and are no longer required:
  dpatch
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
shaheen@shaheen-desktop:~$ mkdir ~/bcm43xx; cd ~/bcm43xx
shaheen@shaheen-desktop:~/bcm43xx$ wget http://myspamb8.googlepages.com/WPC54Gv2_40826-pruned.zip
--11:38:13--  http://myspamb8.googlepages.com/WPC54Gv2_40826-pruned.zip
           => `WPC54Gv2_40826-pruned.zip'
Resolving myspamb8.googlepages.com... 74.125.47.118
Connecting to myspamb8.googlepages.com|74.125.47.118|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 152,420 (149K) [application/octet-stream]

100%[====================================>] 152,420      209.08K/s             

11:38:14 (208.74 KB/s) - `WPC54Gv2_40826-pruned.zip' saved [152420/152420]

shaheen@shaheen-desktop:~/bcm43xx$ unzip WPC54Gv2_40826-pruned.zip
Archive:  WPC54Gv2_40826-pruned.zip
  inflating: bcmwl5.sys              
  inflating: bcmwl5.inf              
  inflating: lsbcmnds.cat            
shaheen@shaheen-desktop:~/bcm43xx$ sudo ndiswrapper -i bcmwl5.inf
driver bcmwl5 is already installed
shaheen@shaheen-desktop:~/bcm43xx$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: ssb)
shaheen@shaheen-desktop:~/bcm43xx$ sudo depmod -a
shaheen@shaheen-desktop:~/bcm43xx$ sudo modprobe ndiswrapper
shaheen@shaheen-desktop:~/bcm43xx$ sudo cp /etc/network/interfaces /etc/network/interfaces.orig
shaheen@shaheen-desktop:~/bcm43xx$ echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
auto lo
iface lo inet loopback

shaheen@shaheen-desktop:~/bcm43xx$ sudo ndiswrapper -m
module configuration already contains alias directive

shaheen@shaheen-desktop:~/bcm43xx$ echo 'ndiswrapper' | sudo tee -a /etc/modules
ndiswrapper
shaheen@shaheen-desktop:~/bcm43xx$ echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicantENABLED=0
shaheen@shaheen-desktop:~/bcm43xx$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32 **_module=ssb_**
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
  *-network
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:0c:41:13:a6:2b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```

So i now try the **'Trying It Temporarily'** section

```
shaheen@shaheen-desktop:~/bcm43xx$ sudo rmmod b43
ERROR: Module b43 does not exist in /proc/modules
shaheen@shaheen-desktop:~/bcm43xx$ sudo rmmod b44
ERROR: Module b44 does not exist in /proc/modules
shaheen@shaheen-desktop:~/bcm43xx$ sudo rmmod b43legacy #this step added Apr 27 2008
shaheen@shaheen-desktop:~/bcm43xx$ sudo rmmod ssb
shaheen@shaheen-desktop:~/bcm43xx$ sudo rmmod ndiswrapper
shaheen@shaheen-desktop:~/bcm43xx$ sudo modprobe ndiswrapper
shaheen@shaheen-desktop:~/bcm43xx$ sudo modprobe ssb
shaheen@shaheen-desktop:~/bcm43xx$ sudo modprobe b44 #this step added May 1 2008
shaheen@shaheen-desktop:~/bcm43xx$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32 **_module=ssb_**
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
  *-network
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:0c:41:13:a6:2b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
shaheen@shaheen-desktop:~/bcm43xx$ 

```

So 'module=ssb' is still there and it hasnt changed to 'module=ndiswrapper'.

:confused:

---

### Post by Ayuthia on 2008-08-19
> **ShaxxiE said:**
> Ok i tried to install NDISWrapper again using nofluff guide.

My *'module'* is 'module=ssb' and not 'module=ndiswrapper' and therefore according to fluff i got a problem. :/

```
shaheen@shaheen-desktop:~$ echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
[sudo] password for shaheen: 
blacklist bcm43xx
shaheen@shaheen-desktop:~$ sudo apt-get install ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndiswrapper-utils-1.9 is already the newest version.
The following packages were automatically installed and are no longer required:
  dpatch
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
shaheen@shaheen-desktop:~$ mkdir ~/bcm43xx; cd ~/bcm43xx
shaheen@shaheen-desktop:~/bcm43xx$ wget http://myspamb8.googlepages.com/WPC54Gv2_40826-pruned.zip
--11:38:13--  http://myspamb8.googlepages.com/WPC54Gv2_40826-pruned.zip
           => `WPC54Gv2_40826-pruned.zip'
Resolving myspamb8.googlepages.com... 74.125.47.118
Connecting to myspamb8.googlepages.com|74.125.47.118|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 152,420 (149K) [application/octet-stream]

100%[====================================>] 152,420      209.08K/s             

11:38:14 (208.74 KB/s) - `WPC54Gv2_40826-pruned.zip' saved [152420/152420]

shaheen@shaheen-desktop:~/bcm43xx$ unzip WPC54Gv2_40826-pruned.zip
Archive:  WPC54Gv2_40826-pruned.zip
  inflating: bcmwl5.sys              
  inflating: bcmwl5.inf              
  inflating: lsbcmnds.cat            
shaheen@shaheen-desktop:~/bcm43xx$ sudo ndiswrapper -i bcmwl5.inf
driver bcmwl5 is already installed
shaheen@shaheen-desktop:~/bcm43xx$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: ssb)
shaheen@shaheen-desktop:~/bcm43xx$ sudo depmod -a
shaheen@shaheen-desktop:~/bcm43xx$ sudo modprobe ndiswrapper
shaheen@shaheen-desktop:~/bcm43xx$ sudo cp /etc/network/interfaces /etc/network/interfaces.orig
shaheen@shaheen-desktop:~/bcm43xx$ echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
auto lo
iface lo inet loopback

shaheen@shaheen-desktop:~/bcm43xx$ sudo ndiswrapper -m
module configuration already contains alias directive

shaheen@shaheen-desktop:~/bcm43xx$ echo 'ndiswrapper' | sudo tee -a /etc/modules
ndiswrapper
shaheen@shaheen-desktop:~/bcm43xx$ echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicantENABLED=0
shaheen@shaheen-desktop:~/bcm43xx$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32 **_module=ssb_**
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
  *-network
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:0c:41:13:a6:2b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```

So i now try the **'Trying It Temporarily'** section

```
shaheen@shaheen-desktop:~/bcm43xx$ sudo rmmod b43
ERROR: Module b43 does not exist in /proc/modules
shaheen@shaheen-desktop:~/bcm43xx$ sudo rmmod b44
ERROR: Module b44 does not exist in /proc/modules
shaheen@shaheen-desktop:~/bcm43xx$ sudo rmmod b43legacy #this step added Apr 27 2008
shaheen@shaheen-desktop:~/bcm43xx$ sudo rmmod ssb
shaheen@shaheen-desktop:~/bcm43xx$ sudo rmmod ndiswrapper
shaheen@shaheen-desktop:~/bcm43xx$ sudo modprobe ndiswrapper
shaheen@shaheen-desktop:~/bcm43xx$ sudo modprobe ssb
shaheen@shaheen-desktop:~/bcm43xx$ sudo modprobe b44 #this step added May 1 2008
shaheen@shaheen-desktop:~/bcm43xx$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32 **_module=ssb_**
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
  *-network
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:0c:41:13:a6:2b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
shaheen@shaheen-desktop:~/bcm43xx$ 

```

So 'module=ssb' is still there and it hasnt changed to 'module=ndiswrapper'.

:confused:

Of course you do!  I just looked at the file from 2f and found that the pruned file is only for 32-bit.  So when you look at dmesg after you do "sudo modprobe ndiswrapper" you should see a message for ndiswrapper that says something like bad magic using 32 bit drver on 64 bit.

From the NDISwrapper site, there is another driver link that you try:
[http://ftp.us.dell.com/network/R76521na.EXE](http://ftp.us.dell.com/network/R76521na.EXE)

It is around 12 Mb.  I think that you can extract the file by using:
```
unzip R76521na.EXE
```

---

### Post by ShaxxiE on 2008-08-19
> **Ayuthia said:**
> Of course you do!  I just looked at the file from 2f and found that the pruned file is only for 32-bit.  So when you look at dmesg after you do "sudo modprobe ndiswrapper" you should see a message for ndiswrapper that says something like bad magic using 32 bit drver on 64 bit.

From the NDISwrapper site, there is another driver link that you try:
[http://ftp.us.dell.com/network/R76521na.EXE](http://ftp.us.dell.com/network/R76521na.EXE)

It is around 12 Mb.  I think that you can extract the file by using:
```
unzip R76521na.EXE
```

Ok here goes!! :)

here are results from *'sudo modprobe ndiswrapper'*


```
root@shaheen-desktop:~# sudo modprobe ndiswrapper
root@shaheen-desktop:~# 

```

Ok file downloaded and i type but saying file not found... it is on my desktop i can see it!! 

```

root@shaheen-desktop:~# unzip R76521na.EXE
unzip:  cannot find or open R76521na.EXE, R76521na.EXE.zip or R76521na.EXE.ZIP.
root@shaheen-desktop:~# 

```

Ok so in the meantime i got drivers for (my/ a) 64 bit Linksys Card from:

[http://www.savefile.com/projects/1042021]("http://www.savefile.com/projects/1042021") I got this info from a guy called Mr Smith on the Linksys forums.

So i have the file (R76521na.EXE and WMP54Gv4-x64.zip) - but now how do i install it? (remember im not a native Linux user)

I think my Linksys card is V2.... so im not sure if the V4 driver will work... 

ok thanks :)

Shaheen 

here have some popcorn! :popcorn: and a star :KS

---

### Post by ShaxxiE on 2008-08-19
> **ShaxxiE said:**
> Ok here goes!! :)

[http://www.savefile.com/projects/1042021]("http://www.savefile.com/projects/1042021") I got this info from a guy called Mr Smith on the Linksys forums.


The file from the link above (WMP54Gv4-x64.zip) wont work for me because the V4 of the Linksys cards has the RaLink chipset. - Just read the inf file.

:/

[edit] HOWEVER... the WMP54GS-x64.zip may do because that is for linksys adapters with the broadcom firmware..

---

### Post by Ayuthia on 2008-08-19
> **ShaxxiE said:**
> Ok here goes!! :)

here are results from *'sudo modprobe ndiswrapper'*


```
root@shaheen-desktop:~# sudo modprobe ndiswrapper
root@shaheen-desktop:~# 

```

Ok file downloaded and i type but saying file not found... it is on my desktop i can see it!! 

```

root@shaheen-desktop:~# unzip R76521na.EXE
unzip:  cannot find or open R76521na.EXE, R76521na.EXE.zip or R76521na.EXE.ZIP.
root@shaheen-desktop:~# 

```
Sorry, I misled you a little.  Since it is on the desktop, you will need to be in that directory to extract it:
```
cd ~/Desktop
unzip R76521na.EXE
```
It should extract the file into a folder called something like R76521na.  You will need to change into that directory and see if the .inf and .sys files are there:
```
cd R76521na
ls
```
If they are, you will to make sure that you do not have any other drivers loaded:
```
ndiswrapper -l
```
If it returns a driver like bcmwl5, you will need to remove it:
```
sudo ndiswrapper -e bcmwl5
```If that does not remove it try:
```
sudo ndiswrapper -r bcmwl5
```
Once there are no more drivers, you can then install the new one (I am assuming that the file is still bcmwl5.inf:
```
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
```
If ndiswrapper -l shows that the device is present, you can then do the following:
```
sudo ndiswrapper -ma
sudo modprobe -r b43 b43legacy b44 ssb wl ndiswrapper bcm43xx
sudo depmod -ae
sudo modprobe ndiswrapper
```

---

### Post by ShaxxiE on 2008-08-19
> **Ayuthia said:**
> Sorry, I misled you a little.  Since it is on the desktop, you will need to be in that directory to extract it:
```
cd ~/Desktop
unzip R76521na.EXE
```
It should extract the file into a folder called something like R76521na.  You will need to change into that directory and see if the .inf and .sys files are there:
```
cd R76521na
ls
```
If they are, you will to make sure that you do not have any other drivers loaded:
```
ndiswrapper -l
```
If it returns a driver like bcmwl5, you will need to remove it:
```
sudo ndiswrapper -e bcmwl5
```If that does not remove it try:
```
sudo ndiswrapper -r bcmwl5
```
Once there are no more drivers, you can then install the new one (I am assuming that the file is still bcmwl5.inf:
```
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
```
If ndiswrapper -l shows that the device is present, you can then do the following:
```
sudo ndiswrapper -ma
sudo modprobe -r b43 b43legacy b44 ssb wl ndiswrapper bcm43xx
sudo depmod -ae
sudo modprobe ndiswrapper
```

Ok yes the files were there - but i had two sets (as you will see) - One in a folder called AR and another in a folder called IR.

I went with the bcmwl5 whilst in the IR folder.

Now trying out the wireless.... Woops no wireless what-so-ever, i only have the option for the wired network.  Ill re-boot now and try again.

here is the output anyway:

```
shaheen@shaheen-desktop:~$ cd ~/Desktop/R76521na/AR
shaheen@shaheen-desktop:~/Desktop/R76521na/AR$ ls
bcm43xxa.cat  bcm43xx.cat  bcmwl5a.inf  bcmwl5.inf  bcmwl5.sys
shaheen@shaheen-desktop:~/Desktop/R76521na/AR$ cd
shaheen@shaheen-desktop:~$ cd ~/Desktop/R76521na/IR
shaheen@shaheen-desktop:~/Desktop/R76521na/IR$ ls
bcm43xxa.cat  bcm43xx.cat  bcmwl5a.inf  bcmwl5.inf  bcmwl5.sys
shaheen@shaheen-desktop:~/Desktop/R76521na/IR$ ndiswrapper -l
shaheen@shaheen-desktop:~/Desktop/R76521na/IR$ sudo ndiswrapper -e bcmwl5
[sudo] password for shaheen: 
couldn't delete /etc/ndiswrapper/bcmwl5: No such file or directory
shaheen@shaheen-desktop:~/Desktop/R76521na/IR$ sudo ndiswrapper -r bcmwl5
couldn't delete /etc/ndiswrapper/bcmwl5: No such file or directory
shaheen@shaheen-desktop:~/Desktop/R76521na/IR$ sudo ndiswrapper -i bcmwl5.inf
installing bcmwl5 ...
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
shaheen@shaheen-desktop:~/Desktop/R76521na/IR$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: ssb)
shaheen@shaheen-desktop:~/Desktop/R76521na/IR$ sudo ndiswrapper -ma
module configuration information is stored in /etc/modprobe.d/ndiswrapper
shaheen@shaheen-desktop:~/Desktop/R76521na/IR$ sudo modprobe -r b43 b43legacy b44 ssb wl ndiswrapper bcm43xx
shaheen@shaheen-desktop:~/Desktop/R76521na/IR$ sudo depmod -ae
shaheen@shaheen-desktop:~/Desktop/R76521na/IR$ sudo modprobe ndiswrapper

```

---

### Post by ShaxxiE on 2008-08-19
Ok after the re-boot my wireless was back.  But i couldn't connect

I tried the same with the AR folder this time.  Again, after doing so my wireless has completely gone. :(

```
shaheen@shaheen-desktop:~$ cd ~/Desktop/R76521na/AR
shaheen@shaheen-desktop:~/Desktop/R76521na/AR$ ls
bcm43xxa.cat  bcm43xx.cat  bcmwl5a.inf  bcmwl5.inf  bcmwl5.sys
shaheen@shaheen-desktop:~/Desktop/R76521na/AR$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: ssb)
shaheen@shaheen-desktop:~/Desktop/R76521na/AR$ sudo ndiswrapper -e bcmwl5
[sudo] password for shaheen: 
shaheen@shaheen-desktop:~/Desktop/R76521na/AR$ sudo ndiswrapper -r bcmwl5
couldn't delete /etc/ndiswrapper/bcmwl5: No such file or directory
shaheen@shaheen-desktop:~/Desktop/R76521na/AR$ sudo ndiswrapper -i bcmwl5.inf
installing bcmwl5 ...
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
shaheen@shaheen-desktop:~/Desktop/R76521na/AR$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: ssb)
shaheen@shaheen-desktop:~/Desktop/R76521na/AR$ sudo ndiswrapper -ma
module configuration information is stored in /etc/modprobe.d/ndiswrapper
shaheen@shaheen-desktop:~/Desktop/R76521na/AR$ sudo modprobe -r b43 b43legacy b44 ssb wl ndiswrapper bcm43xx
shaheen@shaheen-desktop:~/Desktop/R76521na/AR$ sudo depmod -ae
shaheen@shaheen-desktop:~/Desktop/R76521na/AR$ sudo modprobe ndiswrapper
shaheen@shaheen-desktop:~/Desktop/R76521na/AR$ 


```

---

### Post by ShaxxiE on 2008-08-19
WOW i understand how to use Ndiswrapper!!

:)

I installed the driver from linksys site, and it looks like i get one of the green lights to come on on the wireless icon in the systray.... but it still doesnt connect... but I got a green light! wow development...

```
wmp54gs-x64 : driver installed
	device (14E4:4320) present (alternate driver: ssb)

```

---

### Post by ShaxxiE on 2008-08-19
NOW CONTINUING ON

[http://ubuntuforums.org/showthread.php?p=5625090#post5625090]("http://ubuntuforums.org/showthread.php?p=5625090#post5625090")

I'm about to give up very soon.... If you have followed this thread all the way, sorry there isnt an outcome......

---

