---
title: "another &quot;No Internet Connection&quot; thread"
date: 2008-03-11
forum: Networking &amp; Wireless
---

### Post by JakobMonrad on 2008-03-11
I'm having some problems my the Znote 6515wd.  I simply can't get connection to the internet.
My wifi connection finds and connect to a network (not mine BTW) but my wired connection just refuses to find anything.  
I'll prefer to use the wired connection, as I don't have a wireless network of my own.
I can't get any connections through firefox at all, even if I disconnect one or the other connections.

I've tried KevDogs [guide]("http://ubuntuforums.org/showthread.php?t=574501") to networking, but no help for me there.  Couldn't even get the wireless moved from eth1 to wlan0 or Ndiswrapper installed 
(think I need to start a package manager first, but how ?)

I'm running  dual boot Ubuntu 7.10 / WinXP installation, and under WinXP, my internet works normaly.
I've tried an old live version of Ubuntu 5.1 to check if the internet worked there, but sadly no.

Hope somebody can help me out here, because I'm really over ny head here (new n00b to ubuntu - 2 days totlal, so i'm still strugling to understand it all :))

lspci
```
monrad@Znote-6515WD:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce Go 6600] (rev a2)
06:04.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
06:06.0 **Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05)**
06:07.0 **Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)**
06:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
```

ifconfig
```
monrad@Znote-6515WD:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:A0:D1:C1:27:46  
          inet6 addr: fe80::2a0:d1ff:fec1:2746/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:92 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2388 (2.3 KB)  TX bytes:0 (0.0 b)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:13:CE:69:7C:D0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Memory:b000b000-b000bfff 

eth0:avah Link encap:Ethernet  HWaddr 00:A0:D1:C1:27:46  
          inet addr:169.254.6.128  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1144 (1.1 KB)  TX bytes:1144 (1.1 KB)
```

lshw -C network
```
monrad@Znote-6515WD:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: PRO/Wireless 2915ABG Network Connection
       vendor: Intel Corporation
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth1
       version: 05
       serial: 00:13:ce:69:7c:d0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.0kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=128 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=unassociated
  *-network:1
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:06:07.0
       logical name: eth0
       version: 10
       serial: 00:a0:d1:c1:27:46
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=64 maxlatency=64 mingnt=32 module=r8169 multicast=yes
```

---

### Post by SpaceTeddy on 2008-03-11
can please also supply the output of 
```
cat /etc/network/interfaces
cat /etc/resolv.conf
route -n
```

thanks

---

### Post by JakobMonrad on 2008-03-11
Hey Space Teddy

Sure I can (and thanks for your time):

CAT /etc/network/Interfaces
```
monrad@Znote-6515WD:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
```

CAT /etc/resolv.conf
```
monrad@Znote-6515WD:~$ cat /etc/resolv.conf
nameserver 192.168.0.1
```

Route -n
```
monrad@Znote-6515WD:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 eth1
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0
```

---

### Post by SpaceTeddy on 2008-03-11
are you using ubuntu with network manager ? if so, your /etc/network/interfaces should only contain an entry for the loopback device - anything else is entirely managed by network -manager

try to changeing your /etc/network/interfaces to the following content
```
auto lo
iface lo inet loopback
```

this should give network manager full control over the network devices

also, these two lines 
```
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 eth1
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0
```
suggest that something is very wrong with your network configuration. the 0.0.0.0 entry should only be in there once, and it should never ever have a gatway of 0.0.0.0 itself

maybe this can be fixed by just correcting the /etc/network/interfaces - if not, i'll have to think some more. 

also, make sure you have a backup of your original file - just in case i am wrong :)

---

### Post by JakobMonrad on 2008-03-11
Hi again :)

Well it didn't work, but it did do something; it no longer lists eth1 (wireless) in route -n.  
But that secondary, as i dont have my own wireless yet :)

I tried to switch between roaming and dhcp in the network manager (the icon top right on the bar), but as it didn't help either, I reset it to roaming position.

It appers that eth0 stubbornly hold on to its 0.0.0.0 gateway.

(Oh, and the reason for the time between posts, is that I have to rebbot to switch to Ubuntu to try the solutions and then switch back to Win to post).

```
**monrad@Znote-6515WD:~$ cat /etc/network/interfaces**
auto lo
iface lo inet loopback

**monrad@Znote-6515WD:~$ cat /etc/resolv.conf**
nameserver 192.168.0.1


**monrad@Znote-6515WD:~$ route -n**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0


**monrad@Znote-6515WD:~$ lshw -C network**
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: PRO/Wireless 2915ABG Network Connection
       vendor: Intel Corporation
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth1
       version: 05
       serial: 00:13:ce:69:7c:d0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.0kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=128 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=unassociated
  *-network:1
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:06:07.0
       logical name: eth0
       version: 10
       serial: 00:a0:d1:c1:27:46
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=64 maxlatency=64 mingnt=32 module=r8169 multicast=yes

```

---

### Post by SpaceTeddy on 2008-03-11
mhm... can you check your logs to see if your have any evidence that your computer acctually got a dhcp lease ? (i assume you have a dhcp server since your windows works)

also, what happens if you forcefully try to get a dhcp-lease from your router ? do this with
```
sudo dhclient eth0
```

do you acctually get any response there ?

---

### Post by JakobMonrad on 2008-03-11
Back again

The Sudo dhckient eth0 gave me:

```
**monrad@Znote-6515WD:~$ sudo dhclient eth0**
[sudo] password for monrad:
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:a0:d1:c1:27:46
Sending on   LPF/eth0/00:a0:d1:c1:27:46
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 10.0.0.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
monrad@Znote-6515WD:~$ 

```

The last line makes me wonder if im doing something wrong here...

---

### Post by SpaceTeddy on 2008-03-11
> DHCPOFFER from 10.0.0.1
this makes no sense, since you seem to have your network configured to be on the 192.168.0.0 subnet (or am i mistaking that here). nonetheless - you got an offer, but for some reason there was no reaction to it... the main problem with that is, i don't know why this happens either :(

but - just to see IF it would work (i am still thinking something is wrong with the dhcp lease), i would suggest you manually set your IP address - just temporarily.

first off - you need to disable network manager for that - rightclick on it, then uncheck the button manage network (or something like it)

then you can give your computer an IP address in your subnet (don't know what it is, but just use the IP of your router and add one to the last digit). you can also check your network configuration in windows. basicially, you set the ip with
> sudo ifconfig eth0 **IP** where ip gets replaced by, lets say 10.0.0.2

furthermore i am assuming that your router would have the 10.0.0.1 (since that is where the offer came from) - so edit the file /ect/resolv.conf with this command
> gksu gedit /etc/resolv.conf
and put this line in:
> nameserver 10.0.0.1
remove all others (if there are any... the settings in resilf.conf are usually temoprarily unless you have a static configuration - which you don't, according to your interfaces

lastly, you need to set your default route - first check if there is no route with for the subnet 0.0.0.0 - if there is, delete it. delete them all (the 0.0.0.0 ones)

once they're all gone, add a default route with this command (again, the 10.0.0.1 is your router)
```
sudo route add default gw 10.0.0.1
```

and check if your internet works then. if it does, it is some weird problem with the dhcp leases... but what i most likely do not know

---

### Post by JakobMonrad on 2008-03-11
Hmm - Still no luck

The only thing in resolv.conf, before I edited it was:
```
nameserver 192.168.0.1
```

Could it be a problem that the connection goes through a hub, before reaching my DSL-modem ??

---

### Post by SpaceTeddy on 2008-03-11
hang on - you do not have a router inbetween you and the modem ?

oh man... if that is the case, i've been beating the wrong horse all the time :(
i thought you had a router... due to the ipaddresses in your first post - silly me, i should have asked.

no, the hub is not the problem (tho such a setup is not really... nice), it should work.
if the dsl-modem is directly attached to your computer (and it is not a router), you do not need to configure your network cards - you need to configure pppoe.

this can be done via pppoeconf. 

so, if (when you are in windows) you choose a dial-up and then choose connect (not just plug the network cable in and it works), then you need to setup pppoe

run this command to set it up
```
sudo pppoeconf
```

and follow the on screen instructions. once that is completed, you should be connected... hopefully :)

---

### Post by JakobMonrad on 2008-03-11
Wait - I think im confussing both of us here.  The set is as follows:

line-in (wall) -->
 DSL-Router (Zyxel Prestige 660R-61) -->
 hub (3 connection) -->
1)| --> Zepto Znote 6515wd                                                                                                                          
2)|--> Work PC (turned off)
3)|--> Spare connection

Or was that what you meant ???

---

### Post by SpaceTeddy on 2008-03-11
ok, so you are not directly connected to the internet - you have an internal network - the dsl modem got me all confused :) forget the sidetrip to the pppoe configuration :)

could you please, while you are in windows, supply the output of the following command. i am courious what your network configuration looks like in windows.
```
ipconfig /all
route print
```

But to be honest, i am slowly running out of ideas...

---

### Post by JakobMonrad on 2008-03-11
Well - don't worry.  I ran out of idea's long ago :)
Im just happy somebody has the time to try helpng me out.

ipconfig /all
```
Microsoft Windows XP [version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\Monrad>ipconfig /all

Windows IP-konfiguration

      Værtsnavn. . . . . . . . . . . . . . . . . . : znote-6515wd
      Primært DNS-suffiks. . . . . . . . . . . . . :
      Nodetype . . . . . . . . . . . . . . . . . . : Ukendt
      IP-routing aktiveret . . . . . . . . . . . . : Nej
      WINS-proxy aktiveret . . . . . . . . . . . . : Nej

Ethernet-netværkskort Local Area Connection 3:

      Forbindelsesspecifikt DNS-suffiks. . . . . . :
      Beskrivelse. . . . . . . . . . . . . . . . . : Realtek RTL8169/8110 Family
 Gigabit Ethernet NIC
      Fysisk adresse . . . . . . . . . . . . . . . : 00-A0-D1-C1-27-46
      Dhcp aktiveret . . . . . . . . . . . . . . . : Ja
      Automatisk konfiguration aktiveret . . . . . : Ja
      IP-adresse . . . . . . . . . . . . . . . . . : 10.0.0.4
      Undernetmaske. . . . . . . . . . . . . . . . : 255.255.255.0
      Standardgateway. . . . . . . . . . . . . . . : 10.0.0.1
      DHCP-server. . . . . . . . . . . . . . . . . : 10.0.0.1
      DNS-servere. . . . . . . . . . . . . . . . . : 212.242.40.3
                                                     212.242.40.51
      Rettigheden opnået . . . . . . . . . . . . . : 11. marts 2008 18:05:53
      Rettigheden udløber. . . . . . . . . . . . . : 14. marts 2008 18:05:53

C:\Documents and Settings\Monrad>
```

Route Print:
```
Windows IP-konfiguration

      Værtsnavn. . . . . . . . . . . . . . . . . . : znote-6515wd
      Primært DNS-suffiks. . . . . . . . . . . . . :
      Nodetype . . . . . . . . . . . . . . . . . . : Ukendt
      IP-routing aktiveret . . . . . . . . . . . . : Nej
      WINS-proxy aktiveret . . . . . . . . . . . . : Nej

Ethernet-netværkskort Local Area Connection 3:

      Forbindelsesspecifikt DNS-suffiks. . . . . . :
      Beskrivelse. . . . . . . . . . . . . . . . . : Realtek RTL8169/8110 Family
 Gigabit Ethernet NIC
      Fysisk adresse . . . . . . . . . . . . . . . : 00-A0-D1-C1-27-46
      Dhcp aktiveret . . . . . . . . . . . . . . . : Ja
      Automatisk konfiguration aktiveret . . . . . : Ja
      IP-adresse . . . . . . . . . . . . . . . . . : 10.0.0.4
      Undernetmaske. . . . . . . . . . . . . . . . : 255.255.255.0
      Standardgateway. . . . . . . . . . . . . . . : 10.0.0.1
      DHCP-server. . . . . . . . . . . . . . . . . : 10.0.0.1
      DNS-servere. . . . . . . . . . . . . . . . . : 212.242.40.3
                                                     212.242.40.51
      Rettigheden opnået . . . . . . . . . . . . . : 11. marts 2008 18:05:53
      Rettigheden udløber. . . . . . . . . . . . . : 14. marts 2008 18:05:53

C:\Documents and Settings\Monrad>route print
===========================================================================
Liste over grænseflader
0x1 ........................... MS TCP Loopback interface
0x2 ...00 a0 d1 c1 27 46 ...... Realtek RTL8169/8110 Family Gigabit Ethernet NIC
 - Packet Scheduler Miniport
===========================================================================
===========================================================================
Aktive ruter:
Netværksdestination        Netmaske          Gateway       Grænseflade  Metrikvæ
rdi
          0.0.0.0          0.0.0.0         10.0.0.1        10.0.0.4       20
         10.0.0.0    255.255.255.0         10.0.0.4        10.0.0.4       20
         10.0.0.4  255.255.255.255        127.0.0.1       127.0.0.1       20
   10.255.255.255  255.255.255.255         10.0.0.4        10.0.0.4       20
        127.0.0.0        255.0.0.0        127.0.0.1       127.0.0.1       1
        224.0.0.0        240.0.0.0         10.0.0.4        10.0.0.4       20
  255.255.255.255  255.255.255.255         10.0.0.4        10.0.0.4       1
Standardgateway:          10.0.0.1
===========================================================================
Vedvarende ruter:
  Ingen

C:\Documents and Settings\Monrad>
```

---

### Post by SpaceTeddy on 2008-03-11
ok, this is makeing less and less sense to me :( But back to ubuntu now.

your configuration seems to be right (in ubuntu), and the temporary setting i suggest should have worked... ok...mhm... 

try running these commands in ubuntu (almost same as before, but this time i know the IP's - you can just copy and paste)

```
sudo ifconfig eth0 10.0.0.4
sudo route add default gw 10.0.0.1
```

and remove anything from this file
```
gksu gedit /etc/resolv.conf
```

and then place these two lines in:
> nameserver 212.242.40.3
nameserver 212.242.40.51

now, for the testing. once the commands up there are in, please supply the output of 
```
ifconfig eth0
route -n
ping -c4 www.google.de
```

PS: nice language you got on your computer - it looks funny :)

---

### Post by JakobMonrad on 2008-03-11
No luck there either :(

If this fail o work, I might try another linux distribution to see f there any difference there.
(if it works there, I'll try to hijack the config files).
Or I'l try to dig out a old PC from somewhere and try that one instead.


hehe - the language in the code box look funny because it's in danish,  the writing outside the code
box looks funny because I'm a bad speller AND danish :)


```
**monrad@Znote-6515WD:~$ ifconfig eth0**
eth0      Link encap:Ethernet  HWaddr 00:A0:D1:C1:27:46  
          inet addr:10.0.0.4  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::2a0:d1ff:fec1:2746/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:135 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:217 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9536 (9.3 KB)  TX bytes:0 (0.0 b)
          Interrupt:11 

**monrad@Znote-6515WD:~$ route -n**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        0.0.0.0         255.0.0.0       U     0      0        0 eth0
0.0.0.0         10.0.0.1        0.0.0.0         UG    0      0        0 eth0


**monrad@Znote-6515WD:~$ ping -c4 www.google.de**
ping: unknown host www.google.de

```

---

### Post by SpaceTeddy on 2008-03-11
silly silly me... again :)
the subnet mask is wrong - if you do not supply it when seting the ip, it will assume one. you are not in the same network as your router (well, you are, but i do not know how picky the pakets filters are)

anyway - the ifconfig command should be
```
sudo ifconfig eth0 10.0.0.4 netmask 255.255.255.0
```
to force the correct subnet mask (which your windows has)...

if you're game, lets give it another shot

PS: danish look cool, tho i would have thought it was swedish (don't worry, mine is all in german :) )

---

### Post by JakobMonrad on 2008-03-11
Damn - still no luck :(

Here what i get:
```
monrad@Znote-6515WD:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:A0:D1:C1:27:46  
          inet addr:10.0.0.4  Bcast:10.0.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:111 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1506 (1.4 KB)  TX bytes:0 (0.0 b)
          Interrupt:11 

monrad@Znote-6515WD:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 eth0



```

PS - Danish or swedish, the difference isn't that big.  It's mostly the spelling and a few different words :-)

---

### Post by SpaceTeddy on 2008-03-11
in that try, the subnet was correct, but the default gateway was not set properly (as you can see in your route command)

again, here are the two commands that need to be run
```
sudo ifconfig eth0 10.0.0.4 netmask 255.255.255.0 
sudo route add default gw 10.0.0.1
```

and make sure you have the proper nameserver set in your resolv.conf :)

---

### Post by JakobMonrad on 2008-03-11
Nope - still not there


```
monrad@Znote-6515WD:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         10.0.0.1        0.0.0.0         UG    0      0        0 eth0

Resolv.conf
nameserver 212.242.40.3
nameserver 212.242.40.51


```

I accidently got network manager turned on (or does it do that on boot?) and it promply cleared everything.  Had to do it over.

But should the nameserers be changed back to 10.0.0.1 ??

---

### Post by SpaceTeddy on 2008-03-11
your configuration looks fine now... and i am out of ideas too. network manager does not really matter, it will only overwrite your configuration from time to time when you are doing manual config like this.

i am all out of ideas... sorry :(

if anyone else got some - now is the time !

--- EDIT ---

maybe you want to try again with the nameserver, but i do not think it makes a difference.

---

### Post by JakobMonrad on 2008-03-11
Tried the nameserver again - no luck


But thanks alot for all your time :KS

I'll keep trying and maybe see if another distribution can get through and the see what kindt of setup it uses.

---

### Post by handydan918 on 2008-03-11
This is a real reach, but some cards fail to initialize in a dual-boot environment. The only work-around I know of is to do a full shutdown with a 10 count and then boot Linux again. 


Like I said, it's a real reach...

---

### Post by SpaceTeddy on 2008-03-11
since we're at long shots - i might have another one aswell. I am pretty certain that it will not make a difference...

try changeing your local subnet from 10.0.0.0/8 to something like 192.168.0.0/24 - that is something that needs to be done in the router tho - and can possibly render everything in your network useless. just tought i'd warn you :(

---

