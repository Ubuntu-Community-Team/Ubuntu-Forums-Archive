---
title: "RT61 - How to work on Ubuntu 7?"
date: 2007-07-12
forum: Networking &amp; Wireless
---

### Post by 3ch0_z3r0 on 2007-07-12
I have an RT61 Wireless Card on Ubuntu 7.
It detects the network, however refuses to connect to it.

The network strength is 4/5 and it is DHCP.

Any help please.
I am Linux newbie, so go easy and guide me if you can.

Thanks guys


Mike :)

---

### Post by sj3fk3 on 2007-07-13
> **3ch0_z3r0 said:**
> I have an RT61 Wireless Card on Ubuntu 7.
It detects the network, however refuses to connect to it.

The network strength is 4/5 and it is DHCP.

Any help please.
I am Linux newbie, so go easy and guide me if you can.

Thanks guys


Mike :)
Is it an open network or does it use encryption? WEP or WPA?
Also show us output from iwconfig and ifconfig (preferably from the wifi adapter only)

---

### Post by wana10 on 2007-07-13
i just went though this exact problem. mine was a wmp54g. to fix mine i had to pull up system>admin>network. go to properties, select ssid, enter wep code, and set to dhcp. then close out and reboot and it all worked.

if you need wpa instead of wep [go here](http://ubuntuforums.org/showthread.php?t=419709)

---

### Post by 3ch0_z3r0 on 2007-07-13
My network is unprotected.
I'll get the results in a bit for those two commands.

---

### Post by jiangweilin on 2007-07-13
I have the same problem

my iwconfig

ra0       RT61 Wireless  ESSID:"joey"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:19:E0:AC:C7:E0   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=87/100  Signal level:-31 dBm  Noise level:-79 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

my ifconfig

ra0       Link encap:Ethernet  HWaddr 00:0E:E8:F8:49:F8  
          inet6 addr: fe80::20e:e8ff:fef8:49f8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20805 errors:0 dropped:0 overruns:0 frame:0
          TX packets:636 errors:7 dropped:7 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2447791 (2.3 MiB)  TX bytes:7736 (7.5 KiB)
          Interrupt:10 

I see the network but can't connect.  I have an unsecured network.

---

### Post by jiangweilin on 2007-07-13
I finally got it to work by manually configuring the interface.  I set it to my network essid, wep with a blank password, and DHCP.  I checked enable and it connected right away.  However, the connection shows with the wired icon instead of the wireless one.  In any case it works, and I don't need roaming mode for a desktop box anyway.

---

### Post by 3ch0_z3r0 on 2007-07-13
Did you manage to configure it successfully with network manager?


Mike

---

### Post by 3ch0_z3r0 on 2007-07-13
ultima@ultima:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra1       RT61 Wireless  ESSID:"NETGEAR"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:4D:13:33:18   
          Bit Rate=24 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=65/100  Signal level:-70 dBm  Noise level:-103 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ultima@ultima:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:6C:CE:B0:3E  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:92 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7104 (6.9 KiB)  TX bytes:7104 (6.9 KiB)

ra1       Link encap:Ethernet  HWaddr 00:80:5A:38:B2:7A  
          inet6 addr: fe80::280:5aff:fe38:b27a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1042 errors:0 dropped:0 overruns:0 frame:0
          TX packets:732 errors:0 dropped:0 overruns:0 carrier:0
          collisions:3 txqueuelen:1000 
          RX bytes:76962 (75.1 KiB)  TX bytes:1360 (1.3 KiB)
          Interrupt:20

---

### Post by 3ch0_z3r0 on 2007-07-13
Anyone?

---

### Post by wana10 on 2007-07-13
pull up a terminal and enter 'sudo gedit /etc/network/interfaces'
at the bottom enter
```
iface ra1 inet dhcp
wireless-essid your_network
wireless-key

auto ra1
```

if you already have a ra1 entry in this file replace it.

then save exit and reboot.

---

### Post by kevdog on 2007-07-13
Id recommend reading this post as its becoming the bible for ra cards.  I know it states its for r73 cards, but it will work for you, as long as everywhere they mention "73" you substitute "61".  It seems like a lot of work, but its not really (the first time through) may be a little tough.  If you have any more questions, please post back

[http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey](http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey)

---

### Post by 3ch0_z3r0 on 2007-07-13
kevdog, I cannot follow the steps as I cannot download the file from Ubuntu (I dont have a Wired connection to do so)

wana10, I try that and I do ifconfig and iwconfig again and get this:

```

ra1       RT61 Wireless  ESSID:"NETGEAR"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:4D:13:33:18   
          Bit Rate=36 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=65/100  Signal level:-68 dBm  Noise level:-103 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ultima@ultima:~$ 


eth0      Link encap:Ethernet  HWaddr 00:01:6C:CE:B0:3E  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0x2000 

ra1       Link encap:Ethernet  HWaddr 00:80:5A:38:B2:7A  
          inet6 addr: fe80::280:5aff:fe38:b27a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:537 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:3 txqueuelen:1000 
          RX bytes:39700 (38.7 KiB)  TX bytes:720 (720.0 b)
          Interrupt:20 


```

---

### Post by kevdog on 2007-07-13
You are going to need another computer to download the file. Transfer to ubuntu via USB stick:

Here is the file you want:
[http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz)

Also to get your computer ready for compiling the sources (all commands typed at command prompt):
#1. Stick in Ubuntu installation CD - wait to become ready (This is while you have Ubuntu already up and running)
#2. sudo apt-cdrom add
#3. sudo aptitude update
#4. sudo aptitude install build-essential

Then once you have the tar.gz file above. This is what I want you to do:
cd ~
mkdir serial_monkey
cd serial_monkey
Put the tar.gz file in this directory ~/serial_monkey

Extract the files:
tar -zxvf rt61-cvs-daily.tar.gz
cd rt61-cvs-daily
make
sudo make install

Then I want you to edit a file by doing this:
gksu gedit /etc/modprobe.d/blacklist

Add the following:
# Blacklist rt73usb, as it is a non-functional beta module which conflicts with the working rt73 module.
blacklist rt73usb
# Blacklist rt2570, as it causes conflicts with rt73
blacklist rt2570
# Other modules that break rt73
blacklist rt2500usb
blacklist rt2x00lib

I then want you to load your compiled module into the kernel
sudo modprobe -v rt61

Then please post the following
modinfo rt61

Reboot
Post back when you get a chance!

---

### Post by wana10 on 2007-07-13
> **3ch0_z3r0 said:**
> kevdog, I cannot follow the steps as I cannot download the file from Ubuntu (I dont have a Wired connection to do so)

wana10, I try that and I do ifconfig and iwconfig again and get this:

```
ra1       Link encap:Ethernet  HWaddr 00:80:5A:38:B2:7A  
          inet6 addr: fe80::280:5aff:fe38:b27a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:537 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:3 txqueuelen:1000 
          RX bytes:39700 (38.7 KiB)  TX bytes:720 (720.0 b)
          Interrupt:20 
```

ok i pulled up my ifconfig and here it is.
```
ra1       Link encap:Ethernet  HWaddr 00:1A:70:A5:35:89  
          inet addr:192.168.1.107  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:70ff:fea5:3589/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:562093 errors:0 dropped:0 overruns:0 frame:0
          TX packets:125461 errors:3 dropped:3 overruns:0 carrier:0
          collisions:46992 txqueuelen:1000 
          RX bytes:221436347 (211.1 MiB)  TX bytes:22414497 (21.3 MiB)
          Interrupt:20 
```

the difference between ours is that you have no inet address. your router is not assigning an ip address through dhcp. find your broadcast ranges and try to manually assign yourself an ip address
if that doesn't work reset to dhcp and enter the following in terminal
```
sudo ifdown ra1
sudo ifup ra1
sudo dhclient ra1
```

if still nothing on a reboot enter grub, press e to edit boot options and add 'acpi=off' to your boot options.

---

### Post by aewestenbarger on 2007-08-21
Thank you kevdog.  I've been having the same issues with this card as the original poster, and your solution worked for  me.

Here's the output of my modinfo rt61 file:

```
filename:       /lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00-legacy/rt61/rt61.ko 
license:        GPL 
description:    Ralink RT61 802.11abg WLAN Driver 1.1.0 CVS CVS 
author:         http://rt2x00.serialmonkey.com 
srcversion:     180F8980D3385B365E8F654 
alias:          pci:v00001814d00000401sv*sd*bc*sc*i* 
alias:          pci:v00001814d00000302sv*sd*bc*sc*i* 
alias:          pci:v00001814d00000301sv*sd*bc*sc*i* 
depends:        
vermagic:       2.6.20-16-generic SMP mod_unload 586 
parm:           debug:Enable level: accepted values: 1 to switch debug on, 0 to switch debug off. (int) 
parm:           ifname:Network device name (default ra%d) (charp) 
```

Thanks for helping out a newbie.  :)

---

### Post by Pegasus_from_UA on 2007-09-07
I  installed rt61 driver and got 2 error

```
buzdack@buzdack-desktop:~/Documents/Wi-Fi_Dlink/RT61_Linux_STA_Drv1.1.0.0/Module$ cp Makefile.6 Makefile
buzdack@buzdack-desktop:~/Documents/Wi-Fi_Dlink/RT61_Linux_STA_Drv1.1.0.0/Module$ sudo make all
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/buzdack/Documents/Wi-Fi_Dlink/RT61_Linux_STA_Drv1.1.0.0/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/buzdack/Documents/Wi-Fi_Dlink/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.o
/home/buzdack/Documents/Wi-Fi_Dlink/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c: &#1042; &#1092;&#1091;&#1085;&#1082;&#1094;&#1080;&#1080; ‘RT61_probe’
/home/buzdack/Documents/Wi-Fi_Dlink/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:197: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: ‘struct net_device’ has no member named ‘get_wireless_stats’
/home/buzdack/Documents/Wi-Fi_Dlink/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c: &#1042; &#1092;&#1091;&#1085;&#1082;&#1094;&#1080;&#1080; ‘RT61_open’
/home/buzdack/Documents/Wi-Fi_Dlink/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:326: &#1087;&#1088;&#1077;&#1076;&#1091;&#1087;&#1088;&#1077;&#1078;&#1076;&#1077;&#1085;&#1080;&#1077;: passing argument 2 of ‘request_irq’ from incompatible pointer type
make[2]: *** [/home/buzdack/Documents/Wi-Fi_Dlink/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.o] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 1
make[1]: *** [_module_/home/buzdack/Documents/Wi-Fi_Dlink/RT61_Linux_STA_Drv1.1.0.0/Module] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [all] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 2
```


but when i done i have next by command #iwconfig
          ```
ra1       RT61 Wireless  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-121 dBm  Noise level:-111 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
is my wireless conection are working ???
I can't connect my laptop =(
Ubuntu 7.04 on desktop , Windows XP on laptop.
P.S. sorry for poor English

---

### Post by regomodo on 2007-09-12
[http://ubuntuforums.org/showthread.php?t=490217](http://ubuntuforums.org/showthread.php?t=490217)

look at step 1

also from [http://ubuntuforums.org/showthread.php?t=419709&highlight=rt61+feisty&page=5](http://ubuntuforums.org/showthread.php?t=419709&highlight=rt61+feisty&page=5)

I thought i'd post my method. It combines a few peoples' guides here

1. Download the driver from -

[http://prdownloads.sourceforge.net/r...ar.gz?download](http://prdownloads.sourceforge.net/r...ar.gz?download)

2. Extract the driver using full paths to wherever you want

3. Open terminal and "cd" (change directory) to the "./Module" folder of the driver

4. Install the driver

$ sudo make
$ sudo make install

5. copy needed files

$mkdir /etc/Wireless/RT61STA
$cp *.bin from rt61 driver ¨Modules¨ folder to /etc/Wireless/RT61STA

6. edit interfaces file

$ sudo gedit /etc/network/interfaces

add at the bottom [editing the correct bits]

Quote:
auto ra0
iface ra0 inet dhcp
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwconfig ra0 essid my_essid
pre-up iwpriv ra0 set WPAPSK="my_pass_key"
[For me i had to replace ra0 with ra1. Do an "ifconfig" to see what your install sees the card as.]

7. Reboot computer [yes you can do an ifup/ifdown but i found this more reliable]

$ sudo reboot -n

8. Sort out the routes [Sometimes i didn't have to do this. Sometimes i do. No idea why.]

$ sudo route del default
$ sudo route add default gw 192.168.1.1 [varies with router]

9. All done! Hopefully.

Then once you've done that, comment out all the changes you made in /etc/network/interfaces and install (from source) rutilt

---

