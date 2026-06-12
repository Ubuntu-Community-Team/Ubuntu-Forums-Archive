---
title: "my WIRED internet says it is connected but no pages load"
date: 2007-11-20
forum: Networking &amp; Wireless
---

### Post by cmlewin on 2007-11-20
I have a dual boot XP/Ubuntu machine running as I just installed Feisty using Wubi (to make it safe since its a friends comp)...

I've gone through so many threads, disabling ipv6, checking off and unchecking every option I can think of, manually entering the IP/Subnet/Gateway addresses, and still no connection.  I really can't think of what else to do... It works perfectly in Windows and I just am out of ideas... I need someone that REALLY knows linux and ubuntu... Hell I'd let someone remote desktop this if they were a mod here or something.  Just help as I'm super duper frustrated.

Thanks.

C

---

### Post by MrFSL on 2007-11-20
Alright let's suppose that you have everything setup correctly. What is the output of:
```
ifconfig
```

Also what is the output of:
```
sudo cat /etc/resolv.conf
```

Also what is the result of:
```
ping www.google.com
```

---

### Post by cmlewin on 2007-11-20
> **MrFSL said:**
> Alright let's suppose that you have everything setup correctly. What is the output of:
```
ifconfig
```
[b]eth0      Link encap:Ethernet  HWaddr 00:16:EC:B4:74:67   
          inet6 addr: fe80::216:ecff:feb4:7467/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:20 Base address:0xac00  
 
eth0:avah Link encap:Ethernet  HWaddr 00:16:EC:B4:74:67   
          inet addr:169.254.7.222  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          Interrupt:20 Base address:0xac00  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:112 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:112 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:9400 (9.1 KiB)  TX bytes:9400 (9.1 KiB) [/b]

Also what is the output of:
```
sudo cat /etc/resolv.conf
```
[b]nameserver 68.87.73.242 
nameserver 68.87.71.226 [/b]

Also what is the result of:
```
ping www.google.com
```
**ping: unknown host [www.google.com](www.google.com)**


i'm sure things aren't set up correctly, otherwise it'd be working no? :)

also another note, when i unplug the modem to reboot it, the icon on the panel does not change to indicate anything has been unplugged... i'm not sure if that makes a difference

big thanks for any help.

---

### Post by dmizer on 2007-11-20
try disabling ipv6.

howto here: [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?)

---

### Post by cmlewin on 2007-11-20
> **dmizer said:**
> try disabling ipv6.

howto here: [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?)

disabled it properly but still no difference.

should i manually enter the IP address? have it auto-detect? enter any other information? i'm completely clueless as to what i need to do or not do... i really need a step-by-step process to try every option at this point i suppose.

LEET USERS PLZ HELP! :) thx

---

### Post by dmizer on 2007-11-20
try this:
```
sudo dhclient eth0
```
then post the output (if any), as well as repost the output of:
```
ifconfig
```

i am SO not leet, but we'll get you online.

---

### Post by cmlewin on 2007-11-20
> **dmizer said:**
> try this:
```
sudo dhclient eth0
```
then post the output (if any), as well as repost the output of:
```
ifconfig
```

i am SO not leet, but we'll get you online.

well you know more than i do... this is like chinese to me... and i'm not chinese.

thanks for the promised dedication! :)

...

[b]jdf252@ubuntu:~$ sudo dhclient eth0 
Password: [/b]
Internet Systems Consortium DHCP Client V3.0.4 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 
 
Listening on LPF/eth0/00:16:ec:b4:74:67 
Sending on   LPF/eth0/00:16:ec:b4:74:67 
Sending on   Socket/fallback 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2 
No DHCPOFFERS received. 
No working leases in persistent database – sleeping. 

**jdf252@ubuntu:~$ ifconfig **
eth0      Link encap:Ethernet  HWaddr 00:16:EC:B4:74:67   
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:20 Base address:0x8c00  
 
eth0:avah Link encap:Ethernet  HWaddr 00:16:EC:B4:74:67   
          inet addr:169.254.7.222  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          Interrupt:20 Base address:0x8c00  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:1024 (1024.0 b)  TX bytes:1024 (1024.0 b)

---

### Post by dmizer on 2007-11-20
let's take a look at what kind of ethernet card you have.  post the output of:
```
lspci
```

also post the contents of this file:
/etc/network/interfaces

also ... are you using ubuntu, kubuntu, or xubuntu?

---

### Post by cmlewin on 2007-11-20
> **dmizer said:**
> let's take a look at what kind of ethernet card you have.  post the output of:
```
lspci
```

also post the contents of this file:
/etc/network/interfaces

also ... are you using ubuntu, kubuntu, or xubuntu?

ubuntu..

**jdf252@ubuntu:~$ lspci **
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01) 
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge 
00:11.0 IDE interface: ATI Technologies Inc ATI 437A Serial ATA Controller (rev 80) 
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80) 
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) 
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) 
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) 
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81) 
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80) 
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01) 
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80) 
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) 
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200] 
02:02.0 Communication controller: Conexant HSF 56k Data/Fax Modem 
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) 
02:06.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0) 

**jdf252@ubuntu:~$ gedit /etc/network/interfaces **
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback



iface eth0 inet dhcp

auto eth0

---

### Post by dmizer on 2007-11-20
let's try stopping network-manager:
```
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sudo /etc/dbus-1/event.d/25NetworkManager stop
```

restart networking:
```
sudo /etc/init.d/networking restart
```
and post the output.

---

### Post by cmlewin on 2007-11-20
> **dmizer said:**
> let's try stopping network-manager:
```
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sudo /etc/dbus-1/event.d/25NetworkManager stop
```

restart networking:
```
sudo /etc/init.d/networking restart
```
and post the output.

uh oh... i did your sudo aptitude remove command you originally posted... dumb move? here's the output of that... let me know if i should still run the command to stop it........

[b]jdf252@ubuntu:~$ sudo aptitude remove network-manager network-manager-gnome
Password:[/b]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
The following packages will be REMOVED:
  network-manager network-manager-gnome 
0 packages upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 2335kB will be freed.
Writing extended state information... Done
(Reading database ... 86970 files and directories currently installed.)
Removing network-manager-gnome ...
Removing network-manager ...
 * Stopping network connection manager NetworkManager                    [ OK ] 
 * Stopping network events dispatcher NetworkManagerDispatcher           [ OK ] 

**jdf252@ubuntu:~$ sudo /etc/init.d/networking restart**
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 5893
removed stale PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:16:ec:b4:74:67
Sending on   LPF/eth0/00:16:ec:b4:74:67
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:16:ec:b4:74:67
Sending on   LPF/eth0/00:16:ec:b4:74:67
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ]


thanks thanks

---

### Post by dmizer on 2007-11-20
well ... it actually doesn't appear to matter if you uninstalled it or if you simply disabled it.  i thought you might have to uninstall the gnome desktop meta-package to uninstall network-manager, but apparently not.

so no, it doesn't matter if you uninstalled or if you followed my edit.

you're still not getting connected though.

check cable connections, and try rebooting the router (modem?).  is this a laptop or desktop?  is there a light on the card which indicates there is a connection?  try a different cable if you have one handy.

edit for two more questions:
1) are you directly connected to your modem (no router)?
2) are you dual booting with windows?

---

### Post by Michaelmeee on 2007-11-20
I beleive you may have the same problem as I have. [http://www.uluga.ubuntuforums.org/showthread.php?p=3794636#post3794636](http://www.uluga.ubuntuforums.org/showthread.php?p=3794636#post3794636) Try looking through there and using some of the commands they gave me.

---

### Post by dmizer on 2007-11-20
> **Michaelmeee said:**
> I beleive you may have the same problem as I have. [http://www.uluga.ubuntuforums.org/showthread.php?p=3794636#post3794636](http://www.uluga.ubuntuforums.org/showthread.php?p=3794636#post3794636) Try looking through there and using some of the commands they gave me.

your problem was quite different.  you had an ip address from your provider but cmlewin is not getting any ip address at all.

symptoms are the same, but the cause is not.

---

### Post by Michaelmeee on 2007-11-20
Alright, heh, just sounded a bit similar so I thought I'd see if any of that would help him. :)

---

### Post by cmlewin on 2007-11-20
thanks for the concern michaelmeee....

dmizer, changing the ethernet cable and resetting do nothing. i dunno what to dooo

---

### Post by dmizer on 2007-11-20
> **cmlewin said:**
> thanks for the concern michaelmeee....

dmizer, changing the ethernet cable and resetting do nothing. i dunno what to dooo

ahh ... just woke up from a fantastic night sleep.  little cold though.

are you dual booting with windows?  if so, please turn off the computer, and unplug the power for 10 seconds.  then reboot into linux and see if the card works.

---

### Post by cmlewin on 2007-11-27
> **dmizer said:**
> ahh ... just woke up from a fantastic night sleep.  little cold though.

are you dual booting with windows?  if so, please turn off the computer, and unplug the power for 10 seconds.  then reboot into linux and see if the card works.

sorry for the late reply as i've been out of town and haven't had the chance to try this. mark as solved for me!

posting this response on gutsy!

dmizer es teh 1337

---

