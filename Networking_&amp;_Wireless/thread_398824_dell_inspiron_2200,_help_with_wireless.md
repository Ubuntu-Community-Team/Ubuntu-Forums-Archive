---
title: "dell inspiron 2200, help with wireless"
date: 2007-04-01
forum: Networking &amp; Wireless
---

### Post by rice on 2007-04-01
hi guys, ok i may sound stupid but i cant seem to figure out how to make the wireless work on my laptop... i have a dell inspiron 2200 and i dled ubuntu 6.10 last nite, i have no idea how to make it work cause i dont know much about ubuntu...can someone plzzzzz help?!?!?! thanks guys

---

### Post by rice on 2007-04-01
anybody???

---

### Post by dbott67 on 2007-04-01
It depends on the type of wireless card you have installed.  Can you post the output of the following 2 commands:
```
dbott@dapper:~$[COLOR=Red]** lspci**[/COLOR]

0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Graphics Port (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
0000:00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
0000:00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 7145
0000:03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0000:03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd: Unknown device 0832
0000:03:01.1 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
0000:03:01.2 System peripheral: Ricoh Co Ltd: Unknown device 0843 (rev 01)
0000:03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
0000:03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
[COLOR="Red"]0000:0b:00.0 Network controller: Broadcom Corporation: Unknown device 4311 (rev 01)
[/COLOR]
```
and
```
dbott@dapper:~$ [COLOR=Red]**sudo lshw -C network**[/COLOR]
Password:
  *-network
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0b:00.0
       logical name: wlan0
       version: 01
       serial: 00:16:ce:31:88:6f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.25 firmware=Broadcom,11/02/2005, 4.10.40.0 ip=192.168.1.105 link=yes multicast=yes wireless=IEEE 802.11b
       resources: iomemory:dfcfc000-dfcfffff irq:169
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:0c:ad:05
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=b44 driverversion=0.97 duplex=half link=no multicast=yes port=twisted pair speed=10MB/s
       resources: iomemory:df9fe000-df9fffff irq:217

```

If you've got Broadcom wireless (4311 or 4318, etc.) you can follow my instructions here:
[http://www.ubuntuforums.org/showthread.php?t=274915](http://www.ubuntuforums.org/showthread.php?t=274915)

Read the section on **Broadcom 4311 Wireless.**

-Dave

---

### Post by rice on 2007-04-01
when i ran the first search this is what i 

rice@rice-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)

---

### Post by rice on 2007-04-01
and for the other search i got:

rice@rice-laptop:~$ sudo lshw -C network
Password:
  *-network:0 DISABLED    
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@02:03.0
       logical name: eth1
       version: 02
       serial: 00:90:4b:e5:ab:a9
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.17-11-generic ip=192.168.0.9 link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:dfdfe000-dfdfffff irq:193
  *-network:1
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth0
       version: 03
       serial: 00:12:3f:ee:72:d5
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.5.10-k2-NAPI duplex=full firmware=N/A ip=192.168.0.9 link=yes multicast=yes port=MII speed=100MB/s
       resources: iomemory:dfdfd000-dfdfdfff ioport:df40-df7f irq:201

i'll try the link u sent...thank you

---

### Post by dbott67 on 2007-04-02
Hi Rice,

Your laptop is using the Broadcom 4318 wireless card:

```
 rice@rice-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
02:03.0 [COLOR=Red]Network controller: Broadcom Corporation **BCM4318** [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)[/COLOR]
02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)
``````
 rice@rice-laptop:~$ sudo lshw -C network
Password:
  *-network:0 DISABLED    
       description: [COLOR=Red]Wireless interface[/COLOR]
       product: [COLOR=Red]BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller[/COLOR]
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@02:03.0
       logical name: eth1
       version: 02
       serial: 00:90:4b:e5:ab:a9
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
configuration: broadcast=yes [COLOR=Red]driver=bcm43xx[/COLOR] driverversion=2.6.17-11-generic ip=192.168.0.9 link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:dfdfe000-dfdfffff irq:193
  *-network:1
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth0
       version: 03
       serial: 00:12:3f:ee:72:d5
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.5.10-k2-NAPI duplex=full firmware=N/A ip=192.168.0.9 link=yes multicast=yes port=MII speed=100MB/s
       resources: iomemory:dfdfd000-dfdfdfff ioport:df40-df7f irq:201
```It's also using the [COLOR=Red]bcm43xx[/COLOR] driver (which I have not had success with).  

Before you go too far, can you post the output of the following commands:
```
dbott@dapper:~$ [COLOR=Red]cat/etc/network/interfaces[/COLOR]
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid bott
wireless-key s:mysecretwepkey
```and 

```
dbott@dapper:~$ [COLOR=Red]ifconfig -a[/COLOR]
eth0      Link encap:Ethernet  HWaddr 00:15:C5:0C:AD:XX
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:438044459 errors:0 dropped:0 overruns:0 frame:0
          TX packets:438044459 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1712747473 (1.5 GiB)  TX bytes:1712747473 (1.5 GiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:16:CE:31:88:XX
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:ceff:fe31:886f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:738503 errors:0 dropped:0 overruns:0 frame:0
          TX packets:500344 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:658372626 (627.8 MiB)  TX bytes:64530804 (61.5 MiB)
          Interrupt:169 Memory:dfcfc000-dfd00000
```

and
```
dbott@dapper:~$ [COLOR=Red]iwlist scanning[/COLOR]

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :

Cell 01 - Address: 00:40:05:B2:AF:YY
              ESSID:"bott"
              Mode:Master
              Frequency:2.437 GHz (Channel 6)
              Quality=34/100  Signal level=39/100  Noise level=11/100
              Encryption key:on
              Bit Rate:22 Mb/s

Cell 02 - Address: 00:05:5D:FA:B2:XX
              ESSID:"soni"
              Mode:Master
              Frequency:2.437 GHz (Channel 6)
              Quality=24/100  Signal level=27/100  Noise level=12/100
              Encryption key:on
              Bit Rate:54 Mb/s

sit0      Interface doesn't support scanning.
```-Dave

---

### Post by rice on 2007-04-03
hi dave,
srry for the late reply but this is what the following comandes gave me:

rice@rice-laptop:~$ cat/etc/network/interfaces
bash: cat/etc/network/interfaces: No such file or directory
rice@rice-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:12:3F:EE:72:D5  
          inet addr:172.17.35.95  Bcast:172.17.35.255  Mask:255.255.252.0
          inet6 addr: fe80::212:3fff:feee:72d5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2080 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1594 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1690431 (1.6 MiB)  TX bytes:224370 (219.1 KiB)

eth1      Link encap:Ethernet  HWaddr 00:90:4B:E5:AB:A9  
          inet addr:192.168.0.9  Bcast:192.168.0.255  Mask:255.255.255.0
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:1 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

rice@rice-laptop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth1      No scan results
eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

rice@rice-laptop:~$ 

thanks

---

### Post by dbott67 on 2007-04-03
Hi Rice,

The first command should have a space between [COLOR=Red]cat[/COLOR] and [COLOR=Red]/etc/network/interfaces.

[COLOR=Black]The output of ifconfig -a shows the current configuration settings for the various interfaces (the wired interface, eth0 and the wireless interface, eth1, as well as the local loopback, lo).  All of these look normal:
```
[/COLOR][/COLOR] rice@rice-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:12:3F:EE:72:grin:5  
          i**net addr:172.17.35.95**  Bcast:172.17.35.255  Mask:255.255.252.0
          inet6 addr: fe80::212:3fff:feee:72d5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2080 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1594 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1690431 (1.6 MiB)  TX bytes:224370 (219.1 KiB)

eth1      Link encap:Ethernet  HWaddr 00:90:4B:E5:AB:A9  
**           inet addr:192.168.0.9**  Bcast:192.168.0.255  Mask:255.255.255.0
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:1 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

It appears as though your eth1 (wireless) has an IP address assigned to it (192.168.0.9).  The output of [COLOR=Red]cat /etc/network/interfaces[/COLOR] will indicate whether it's a static or DHCP assigned address.

The last command (iwlist scanning) indicates that eth1cannot detect any wireless APs.

My guess is that you will need to blacklist the bcmxx driver and follow my link above to install ndiswrapper.  It *looks* daunting, but it's not that hard.  Really!

-Dave

---

### Post by rice on 2007-04-03
srry about that, heres the output for the first one again

rice@rice-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet dhcp
address 192.168.0.9
netmask 255.255.255.0


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface eth1 inet dhcp
wireless-essid MacConnect
address 192.168.0.9
netmask 255.255.255.0


auto eth0

auto eth1

do u know the driver which i'll have to install by any chance?

---

### Post by rice on 2007-04-03
all the drivers shown in the link that u gave me dont go with my laptop (dell inspiron 2200), im not sure which driver to install, if u could help me out that would be great, thanks again

---

### Post by dbott67 on 2007-04-03
You can get the 2 required files from here:
[http://biginoz.free.fr/linux/bcmwl5a.inf](http://biginoz.free.fr/linux/bcmwl5a.inf) - bcmwl5a.inf
[http://biginoz.free.fr/linux/bcmwl5.sys](http://biginoz.free.fr/linux/bcmwl5.sys) - bcmwl5.sys

Save them in your home folder in Ubuntu.

[COLOR=Blue][I]The above information is from:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B)

Item # 2 (Card Name: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02))

[/I][COLOR=Black]Then, follow the instructions here to compile and install.  Be sure to read the instructions very carefully, as missing a simple step can lead to problems.

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

If you run into problems, post back here... I'll keep my eyes open.

-Dave[/COLOR]
[/COLOR]

---

### Post by dbott67 on 2007-04-03
> **rice said:**
> srry about that, heres the output for the first one again

rice@rice-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet dhcp
address 192.168.0.9
netmask 255.255.255.0


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface eth1 inet dhcp
wireless-essid MacConnect
address 192.168.0.9
netmask 255.255.255.0


auto eth0

auto eth1

do u know the driver which i'll have to install by any chance?

The[COLOR=Blue] **/etc/network/interfaces** [/COLOR]file also needs to be fixed up.

It should look like this:
```

rice@rice-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

*[COLOR=Red]# This is your wired interface.  Set to obtain IP address automatically.[/COLOR]*
auto eth0
iface eth0 inet dhcp

[COLOR=Red]*# This is your wireless interface.*[/COLOR]*[COLOR=Red]  Set to obtain IP address automatically.[/COLOR]*
 auto eth1
 iface eth1 inet dhcp
wireless-essid "your-essid"
wireless-key s:your_ascii_wep_key

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

After you install ndiswrapper and are able to scan, we'll need to make sure any encryption is set properly.

-Dave

---

### Post by rice on 2007-04-03
ok...2 problems one .inf didn't dl, when i clicked on it link a pg with a bunch of code opened up, but when i clicked on the .sys file i was able to dl it. and the second thing is the card i have 

Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

i don't c the driver which i need for my laptop, there are a lot of drivers for BCM4318 but none which say dell inspiron 2200, can i dl any dell one or does it have to be specific to mine?

---

### Post by dbott67 on 2007-04-03
> **rice said:**
> ok...2 problems one .inf didn't dl, when i clicked on it link a pg with a bunch of code opened up, but when i clicked on the .sys file i was able to dl it. and the second thing is the card i have 

Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

i don't c the driver which i need for my laptop, there are a lot of drivers for BCM4318 but none which say dell inspiron 2200, can i dl any dell one or does it have to be specific to mine?

For the .inf file, just right-click the file & select "Save Link As... "

As for the specific driver, the one I linked to above appears to be the correct one (Dell is only the laptop vendor, but Broadcom is the wireless card manufacturer.  As long as we use the correct driver for the NIC, it wouldn't matter whether you had a Dell, HP, Gateway or Compaq computer.

So, to answer your question: no, the driver does not have to be specific for Dell; only for the network card.

-Dave

---

### Post by dbott67 on 2007-04-03
By the way, the reason I picked the 2nd Broadcom 4318 driver was because of the output from your computer (from [COLOR=Teal]lspci[/COLOR]):
```
[COLOR=Red] 02:03.0 [/COLOR]Network controller: Broadcom Corporation [COLOR=Blue]BCM4318[/COLOR] [AirForce One 54g] 802.11g Wireless LAN Controller[COLOR=Red] (rev 02)[/COLOR]
```

Your lspci output matches the list information from the webpage:
> Card Name: Broadcom Corporation [COLOR=Blue]BCM4318[/COLOR] [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) [LIST]
[*]Ndiswrapper version: 1.1-4
[*]Chipset name: Broadcom BCM4318
[*][COLOR=Red]PCIID: 02:03.0 (rev 02)[/COLOR]
[*]Windows driver location: [[40]]("http://biginoz.free.fr/linux/bcmwl5a.inf"). Also need .sys file [[41]]("http://biginoz.free.fr/linux/bcmwl5.sys")
[*]Using Ubuntu 5.10 on Dell Inspiron 1300[/LIST]-Dave

---

### Post by rice on 2007-04-04
thanks alot dave...im at school rite now and i wont get a chance to compile and install it, till later on but i'll let u know how it goes

---

### Post by rice on 2007-04-04
ok so i got the drivers and everything installed and it works, but now its saying that i dont have wireless network ??? not sure what happened any idea?

---

### Post by dbott67 on 2007-04-04
I'm not sure I understand.  What works?

What does the iwlist scanning display?  Can you post it here?

If iwlist reports that it detects any APs, then the wireless card is working.  We just need to connect it to your AP.

There is a great wireless manager called NetworkManager that you an install to easily connect that supports WEP & WPA:
```
sudo apt-get install network-manager-gnome
```

-Dave

---

### Post by rice on 2007-04-04
hey dave, this is the output for iwlist...and yes i already dled the network manager that was one of the first things i did cause i thought it would help lol. the problem is when i go to systems->admin->networking it only shows the wired connection and moden, it doesn't show the wireless at all and im not sure why

rice@rice-laptop:~$ su
Password: 
root@rice-laptop:/home/rice# iwlist
Usage: iwlist [interface] scanning
              [interface] frequency
              [interface] channel
              [interface] bitrate
              [interface] rate
              [interface] encryption
              [interface] key
              [interface] power
              [interface] txpower
              [interface] retry
              [interface] ap
              [interface] accesspoints
              [interface] peers
              [interface] event

---

### Post by dbott67 on 2007-04-05
Hi rice,

You need to add 'scanning' to the end of iwlist:
```
dbott@dapper:~$ iwlist scanning

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :

Cell 01 - Address: 00:40:05:B2:AF:YY
              ESSID:"bott"
              Mode:Master
              Frequency:2.437 GHz (Channel 6)
              Quality=34/100  Signal level=39/100  Noise level=11/100
              Encryption key:on
              Bit Rate:22 Mb/s

Cell 02 - Address: 00:05:5D:FA:B2:XX
              ESSID:"soni"
              Mode:Master
              Frequency:2.437 GHz (Channel 6)
              Quality=24/100  Signal level=27/100  Noise level=12/100
              Encryption key:on
              Bit Rate:54 Mb/s

sit0      Interface doesn't support scanning.
```

Also, can you post the output of 'cat /etc/iftab':
```
dbott@thedrake:~$ cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:50:ba:c0:a7:55 arp 1

```

-Dave

---

### Post by rice on 2007-04-05
oo srry about that

root@rice-laptop:/home/rice# iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

root@rice-laptop:/home/rice# cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:12:3f:ee:72:d5 arp 1
eth1 mac 00:90:4b:e5:ab:a9 arp 1


here are the outputs

---

### Post by dbott67 on 2007-04-05
Okay, for whatever reason your eth1 is not activated.  eth1 is your wireless card.  Let's try to activate it manually.  Run the command below and post the output here:
```
sudo ifup eth1
```and then run:
```
iwlist scanning
```If you don't see any results, can you post the output of the following commands *[COLOR=Blue](scroll down the list to see the ndiswrapper loaded on my computer)[/COLOR]*:
```
dbott@edgy:~$ lsmod
Module                  Size  Used by
binfmt_misc            13448  1
rfcomm                 42260  0
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
ipv6                  272288  16
fglrx                 406988  22
speedstep_centrino      9760  1
cpufreq_userspace       5408  0
cpufreq_stats           7744  0
freq_table              6048  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       2944  0
cpufreq_ondemand        8876  2
cpufreq_conservative     8712  0
video                  17540  0
tc1100_wmi              8324  0
sbs                    16804  0
sony_acpi               6412  0
pcc_acpi               14080  0
i2c_ec                  6272  1 sbs
i2c_core               23424  1 i2c_ec
hotkey                 11556  0
dev_acpi               12292  0
button                  7952  0
battery                11652  0
container               5632  0
ac                      6788  0
asus_acpi              17688  0
nls_utf8                3200  5
ntfs                  112116  4
nls_iso8859_1           5248  1
nls_cp437               6912  2
vfat                   14720  2
fat                    56348  1 vfat
af_packet              24584  8
[COLOR=Red] ndiswrapper[/COLOR]           204436  0
sbp2                   24584  0
parport_pc             37796  0
lp                     12964  0
parport                39496  2 parport_pc,lp
joydev                 11200  0
sg                     37404  0
tsdev                   9152  0
sr_mod                 18212  0
cdrom                  38944  1 sr_mod
sdhci                  20108  0
b44                    26764  0
mii                     6912  1 b44
mmc_core               32136  3 sdhci
usbhid                 45152  0
snd_hda_intel          20116  1
snd_hda_codec         164608  1 snd_hda_intel
snd_pcm_oss            47360  0
snd_mixer_oss          19584  1 snd_pcm_oss
pcspkr                  4352  0
snd_pcm                84612  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
snd                    58372  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
intel_agp              26012  1
agpgart                34888  2 fglrx,intel_agp
hw_random               7320  0
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
serio_raw               8452  0
shpchp                 42144  0
pci_hotplug            32828  1 shpchp
psmouse                41352  0
evdev                  11392  2
ext3                  142856  1
jbd                    62228  1 ext3
ohci1394               37040  0
ieee1394              306104  2 sbp2,ohci1394
uhci_hcd               24968  0
ehci_hcd               34696  0
usbcore               134912  5 [COLOR=Red]**ndiswrapper**[/COLOR],usbhid,uhci_hcd,ehci_hcd
ide_generic             2432  0
sd_mod                 22656  8
generic                 6276  0
ata_piix               11780  7
libata                 74892  1 ata_piix
scsi_mod              144648  5 sbp2,sg,sr_mod,sd_mod,libata
thermal                15624  0
processor              31560  2 speedstep_centrino,thermal
fan                     6020  0
fbcon                  41504  0
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0
capability              5896  0
commoncap               8704  1 capability
dbott@edgy:~$

```We're looking for ndiswrapper.  We also _**do not**_ want to see [COLOR=Red]**bcmxx.**

[COLOR=Black]I'd also like to see the output of 'sudo lshw -C network' again:
```
dbott@edgy:~$ sudo lshw -C network
Password:
  *-network
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0b:00.0
       logical name: wlan0
       version: 01
       serial: 00:16:ce:31:88:6f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes [COLOR=Red]driver=ndiswrapper[/COLOR] driverversion=1.37 firmware=Broadcom,11/02/2005, 4.10.40.0 ip=192.168.1.105 link=yes multicast=yes wireless=IEEE 802.11b
       resources: iomemory:dfcfc000-dfcfffff irq:169
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:0c:ad:05
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=b44 driverversion=1.00 duplex=half link=no multicast=yes port=twisted pair speed=10MB/s
       resources: iomemory:df9fe000-df9fffff irq:217

```-Dave
[/COLOR][/COLOR]

---

### Post by rice on 2007-04-05
hey dave, here are the results which i get..

rice@rice-laptop:~$ sudo ifup eth1
Password:
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth1 ; No such device.
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.

rice@rice-laptop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

rice@rice-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
i915                   21632  3 
drm                    74644  4 i915
speedstep_centrino      9760  1 
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  1 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sbs                    16804  0 
sony_acpi               6412  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
i2c_core               23424  1 i2c_ec
hotkey                 11556  0 
dev_acpi               12292  0 
button                  7952  0 
battery                11652  0 
container               5632  0 
ac                      6788  0 
asus_acpi              17688  0 
ipv6                  272288  10 
af_packet              24584  2 
parport_pc             37796  0 
lp                     12964  0 
parport                39496  2 parport_pc,lp
joydev                 11200  0 
tsdev                   9152  0 
pcmcia                 40380  0 
snd_intel8x0           34844  1 
snd_ac97_codec         97696  1 snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
usbhid                 45152  0 
snd_pcm                84612  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
e100                   38020  0 
mii                     6912  1 e100
snd                    58372  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
pcspkr                  4352  0 
yenta_socket           28812  1 
rsrc_nonstatic         15360  1 yenta_socket
pcmcia_core            43924  3 pcmcia,yenta_socket,rsrc_nonstatic
evdev                  11392  2 
intel_agp              26012  1 
agpgart                34888  3 drm,intel_agp
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
psmouse                41352  0 
serio_raw               8452  0 
ext3                  142856  1 
jbd                    62228  1 ext3
ehci_hcd               34696  0 
uhci_hcd               24968  0 
usbcore               134912  4 usbhid,ehci_hcd,uhci_hcd
ide_generic             2432  0 
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
ide_disk               18560  3 
piix                   11780  1 
generic                 6276  0 
thermal                15624  0 
processor              31560  2 speedstep_centrino,thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability

rice@rice-laptop:~$ sudo lshw -C network
  *-network:0 UNCLAIMED   
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       resources: iomemory:dfdfe000-dfdfffff irq:1
  *-network:1
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth0
       version: 03
       serial: 00:12:3f:ee:72:d5
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.5.10-k2-NAPI duplex=full firmware=N/A ip=192.168.0.3 link=yes multicast=yes port=MII speed=100MB/s
       resources: iomemory:dfdfd000-dfdfdfff ioport:df40-df7f irq:201

i really dont get why eth1 just stopped working :S

---

### Post by dbott67 on 2007-04-05
The ndiswrapper is not loaded.

Can you post the output of the following:
```
dbott@edgy:~$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: bcm43xx)

```



If you don't see anything similar to what I've got, then run this command from the directory where you saved the drivers :
```
sudo ndiswrapper -i bcmwl5a.inf
```

Run the 'ndiswrapper -l' command again:
```
dbott@edgy:~$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: bcm43xx)

```

Next, run:
```
sudo depmod -a
```
Then:
```
sudo modprobe ndiswrapper
```
Finally, run iwlist scanning again and post the results here.

-Dave

---

### Post by H.E. Pennypacker on 2007-05-06
rice, we have the same laptop.  Here's how to get wireless working:

1.  Install ndiswrapper.
2.  Install bcmwl5.inf (the driver) using ndiswrapper.
3.  Blacklist bcm43xx (the open source driver), so that it does not interfere with bcmwl5.inf.
4.  Add ndiswrapper to startup.

Admittedly, these steps are not very helpful for a new user, but that's the gist of how to get wireless working.

We have the same wireless card (BCM4318).  Do a forum search on BCM4318, and you'll get quite a few results.

If you don't want to waste your time, and want something that will save you a lot of time, consider buying a more Linux friendly wireless card.  BCM4318 is one of the LEAST Linux friendly cards available.

---

