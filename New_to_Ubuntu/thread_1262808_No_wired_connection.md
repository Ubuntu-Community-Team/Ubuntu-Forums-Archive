---
title: "No wired connection"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by AdeBruijn on 2009-09-10
[FONT=Times New Roman][SIZE=3]I have posted before but I didn't recieve a reply: I just bought a new laptop (Packard Bell EasyNote MZ35-V-080) with a fresh ubuntu 9.04 installation. I can't get (wired) internet access though, even though the cable connection should be active because I connected the cable also to my old laptop or a windows desktop. Ifconfig does not deliver an IP-adress and sudo ifup eth0 delivers “Ignoring unknown interface eth0=eth0”.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3]I found some similar threats, but with one year experience with ubuntu, I dont understand enough of the details. [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Anyone please help, I’m starting to despair.:confused:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3]Arjan[/SIZE][/FONT]

---

### Post by mapes12 on 2009-09-10
Your Ubu machine is not getting itself assigned an IP address. I'm assuming your router uses DHCP. Then this might help: [http://ubuntuforums.org/showpost.php?p=7276275&postcount=8](http://ubuntuforums.org/showpost.php?p=7276275&postcount=8)

If it doesn't work please post back.

BTW keep a copy of your dhclient.conf file as a backup just in case........

---

### Post by AdeBruijn on 2009-09-10
Thanks a lot for your reply.
 
I found the file dhclient.conf in /etc/dhcp3/ whereas the link states that it should be located in /etc. Just to make sure, I tried both outcommenting the line mentioned and copied the file to /etc, hypothesizing that with some update the file may have been relocated and wasn't found where it is expected. 
 
Unfortunately, no luck. eth0 still has no ip-adress assigned. I will try another type of inet connection tonight, but since the other laptop with ubuntu works, I am not too sure whether it will make a difference. I would appreciate any other ideas?
 
Do I need to install some driver for my network card perhaps?
 
cheers 
 
Arjan

---

### Post by mapes12 on 2009-09-10
You could try re installing network manger in Synaptic.

---

### Post by AdeBruijn on 2009-09-14
Tried lots of things: I reinstalled ubuntu 9.04 or tried 8.04, downloaded and installed wicd, nothing...:(
 
There are quite a number of links associated with my network card: 
RTL-8139/8139C/8139C+, just google for the term with (and ubuntu). Some of the suggestions I tried:
 
1. add noapic to /boot/grub/menu.lst : kernel "" ro quiet splash becomes ro quiet splash noapic: result: the comp freezes when booting at: [105.537839] ata1.00: revalidation failed (errno=-5)
 
2. add "acpi=off" to /boot/grub/menu.lst : kernel "" ro quiet splash becomes ro quiet splash "acpi=off": result: the comp freezes when booting at: Starting up...
 
3. add noisapnp to /boot/grub/menu.lst (...etc) no effect
 
4. add noisapnp to pnpacpi=off to /boot/grub/menu.lst (...etc)  result: the comp freezes when booting during sandwatch
 
I would greatly appreciate any more ideas. Meanwhile, I'm trying to register at [https://bugs.launchpad.net](https://bugs.launchpad.net) to see what happened with [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/22575](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/22575)
 
 
Arjan

---

### Post by izziere on 2009-09-14
Sorry. but this is not a DHCP problem.  Your OS does not recognise your ethernet port - ie it has not properly supported the hardware so it goes nowhere near the DHCP server.  Please post the output of

```
dmesg | grep eth0
```

this should show a message about whether the hardware has been detected and, if so, what software services tried to be loaded.

Also please show the output of

```
sudo lspci
```

---

### Post by AdeBruijn on 2009-09-14
Thanks a lot for your immediate reply:
 
arjan@arjan-laptop:~$ dmesg | grep eth0
[ 3.812165] eth0: RealTek RTL8139 at 0xa000, 00:1b:24:3b:a9:02, IRQ 21
[ 3.812168] eth0: Identified 8139 chip type 'RTL-8100B/8139D'
[ 25.648323] eth0: link down
[ 25.648454] ADDRCONF(NETDEV_UP): eth0: link is not ready
 
 
arjan@arjan-laptop:~$ sudo lspci
00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
09:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
09:04.0 Network controller: RaLink RT2561/RT61 rev B 802.11g
 
 
cheers,
 
arjan

---

### Post by izziere on 2009-09-14
Aha.  So it has located and put in place the network card.  It is the network settings.  Post the output of ```
sudo nano /etc/network/interfaces
```

and also ```
ifconfig -a
```

and also try ```
sudo ifup eth0
```

The latter may bring up the network interface

---

### Post by AdeBruijn on 2009-09-14
ifconfig:
 
eth0 Link encap:Ethernet HWaddr 00:1b:24:3b:a9:02 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:21 Base address:0xa000 
 
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:44 errors:0 dropped:0 overruns:0 frame:0
TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:3424 (3.4 KB) TX bytes:3424 (3.4 KB)
 
pan0 Link encap:Ethernet HWaddr e2:94:eb:e7:f0:ca 
BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
wlan0 Link encap:Ethernet HWaddr 00:0d:f0:3b:ca:96 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
 
wmaster0 Link encap:UNSPEC HWaddr 00-0D-F0-3B-CA-96-00-00-00-00-00-00-00-00-00-00 
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
 
sudo ifup eth0
Ignoring unknown interface eth0=eth0.
 
/etc/network/interfaces
auto lo
iface lo inet loopback
 
cheers

---

### Post by izziere on 2009-09-14
Try adding the following line to the interfaces file:

```

auto eth0
iface eth0 inet dhcp
```

you then need to 

```

sudo /etc/init.d/networking restart
```

and see what happens. Keep fingers crossed

---

### Post by izziere on 2009-09-14
Sorry, I assumed your router was DHCP rather than static IP.  If your router requires a static IP follow the instructions [here]("http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html")

---

### Post by AdeBruijn on 2009-09-14
nop...  I already found this suggestion in another discussion, keeping fingers crossed was new though :P
 
arjan@arjan-laptop:~$ sudo gedit /etc/network/interfaces
arjan@arjan-laptop:~$ sudo /etc/init.d/networking restart
* Reconfiguring network interfaces... 
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:1b:24:3b:a9:02
Sending on LPF/eth0/00:1b:24:3b:a9:02
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
grep: /etc/resolv.conf: No such file or directory

---

### Post by AdeBruijn on 2009-09-14
crossed your latest post, wait a sec

---

### Post by AdeBruijn on 2009-09-14
nothing...
 
The network file now became:
 
auto lo
iface lo inet loopback
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.254
 
arjan@arjan-laptop:~$ sudo /etc/init.d/networking restart
* Reconfiguring network interfaces... 
SIOCDELRT: No such process

---

### Post by izziere on 2009-09-14
A couple of suggestion before I head off for the night:

1) There is no "auto eth0" in your interfaces file.  It needs it.
2) While you copied the different IP addresses from the post I directed you to, are they the same as on your router?  I don't know your system, but most home networks have a gateway on 192.168.1.1 or 192.168.0.1.  Sorry for not making that clearer earlier.
3) Check there is no conflict between the static IP address you have just assigned and the IP addresses in /etc/hosts.  If you have assigned a private IP address in hosts, make sure it is the same as in interfaces
4) Check your router settings.  Confirm whether or not the DHCP server is on, what ranges are accepted for IP addresses, what the gateway IP address is, whether there is MAC filtering, etc.

---

### Post by AdeBruijn on 2009-09-15
Nothing still. The server however, definately uses a DHCP protocol, the output of ipconfig/all using my windows desktop delivers:

Dhcp enabled yes
DHCP server 10.110.10.3
 
ip adress 10.75.2.77
subnet mask 255.255.240.0
default gateway 10.75.15.254
 
there is no assignment to resemble 
network or
broadcast.
 
I have tried following parameters in interfaces file:
 
auto lo
iface lo inet loopback
auto eth0
address 10.75.2.77
netmask 255.255.240.0
network 137.224.252.1
broadcast 137.224.252.11
gateway 10.75.15.254
 
Or also changing ip adress to 10.75.2.76, but recieved /etc/network/interfaces:5: misplaced option
 
Even when I do have a dhcp connection, there could still be some use trying to set the ip manually, some posts suggested that this would solve the issue. However, I still don't know what settings to use?
 
Cheers,
 
Arjan

---

### Post by AdeBruijn on 2009-09-20
[FONT=Arial]Being new to the forum, I started a new thread to summarise the issue with my network card, whereas of course, I should have 'bumped' this one. Please consider this a genuine BUMP :(:):P.[/FONT]

[FONT=Arial]- The problem[/FONT]
[FONT=Arial]I cannot get wired internet acces. I manually installed wicd and now I can have wireless access, but even though I do have wifi in some locations, it's still annoying to depend on it. Problem is that the laptop does not recieve an IP adress[/FONT]

[FONT=Arial]- System specifications[/FONT]
[FONT=Arial]The laptop is a Packard Bell EasyNote MZ35-V-080[/FONT]
[FONT=Arial]The network card is a Realtek RTL-8139/8139C/8139C+ there are more postings on the net that mention issues with this card. My best guess now is that there is a driver called 8139too, that is assigned the job, but fails.[/FONT]

[FONT=Arial]- Tried before:[/FONT]
[FONT=Arial]ifconfig delivers

eth0 Link encap:Ethernet HWaddr 00:1b:24:3b:a9:02 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:21 Base address:0xa000 
[/FONT]
[FONT=Arial]sudo ifup eth0:
Ignoring unknown interface eth0=eth0.

sudo gedit /etc/network/interfaces:
auto lo
iface lo inet loopback

Tried adding the following line to the interfaces file:[/FONT]
[FONT=Arial]auto eth0[/FONT]
[FONT=Arial]iface eth0 inet dhcp[/FONT]

[FONT=Arial]sudo /etc/init.d/networking restart[/FONT]
[FONT=Arial]arjan@arjan-laptop:~$ sudo gedit /etc/network/interfaces
arjan@arjan-laptop:~$ sudo /etc/init.d/networking restart
* Reconfiguring network interfaces... 
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:1b:24:3b:a9:02
Sending on LPF/eth0/00:1b:24:3b:a9:02
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.[/FONT]

[FONT=Arial]I also tried to set an IP manually, even though I don’t know much about how to choose the setting:[/FONT]

[FONT=Arial]In /etc/networking, add: [/FONT]

[COLOR=black][FONT=Arial]auto lo
iface lo inet loopback
auto eth0
address 10.75.2.77
netmask 255.255.240.0
network 137.224.252.1
broadcast 137.224.252.11
gateway 10.75.15.254

Or also changing ip adress to 10.75.2.76, but recieved /etc/network/interfaces:5: misplaced option. Also, I have some doubts before after entering ipconfig/all in a DOS screen on a windows machine using the same network, I receive [/FONT][/COLOR]

[COLOR=black][FONT=Arial]Dhcp enabled yes
DHCP server 10.110.10.3\[/FONT][/COLOR]

[COLOR=black][FONT=Arial]-Tried other kernel settings:[/FONT][/COLOR]

[COLOR=black][FONT=Arial]1. add noapic to /boot/grub/menu.lst : kernel "" ro quiet splash becomes ro quiet splash noapic: result: the comp freezes when booting at: [105.537839] ata1.00: revalidation failed (errno=-5)

2. add "acpi=off" to /boot/grub/menu.lst : kernel "" ro quiet splash becomes ro quiet splash "acpi=off": result: the comp freezes when booting at: Starting up...

3. add noisapnp to /boot/grub/menu.lst (...etc) no effect

4. add noisapnp to pnpacpi=off to /boot/grub/menu.lst (...etc) result: the comp freezes when booting during sandwatch[/FONT][/COLOR]

---

### Post by mapes12 on 2009-09-20
> **AdeBruijn said:**
> [FONT=Arial]Being new to the forum, I started a new thread to summarise the issue with my network card, whereas of course, I should have 'bumped' this one. Please consider this a genuine BUMP :(:):P.[/FONT]

[FONT=Arial]- The problem[/FONT]
[FONT=Arial]I cannot get wired internet acces. I manually installed wicd and now I can have wireless access, but even though I do have wifi in some locations, it's still annoying to depend on it. Problem is that the laptop does not recieve an IP adress[/FONT]

[FONT=Arial]- System specifications[/FONT]
[FONT=Arial]The laptop is a Packard Bell EasyNote MZ35-V-080[/FONT]
[FONT=Arial]The network card is a Realtek RTL-8139/8139C/8139C+ there are more postings on the net that mention issues with this card. My best guess now is that there is a driver called 8139too, that is assigned the job, but fails.[/FONT]

[FONT=Arial]- Tried before:[/FONT]
[FONT=Arial]ifconfig delivers

eth0 Link encap:Ethernet HWaddr 00:1b:24:3b:a9:02 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:21 Base address:0xa000 
[/FONT]
[FONT=Arial]sudo ifup eth0:
Ignoring unknown interface eth0=eth0.

sudo gedit /etc/network/interfaces:
auto lo
iface lo inet loopback

Tried adding the following line to the interfaces file:[/FONT]
[FONT=Arial]auto eth0[/FONT]
[FONT=Arial]iface eth0 inet dhcp[/FONT]

[FONT=Arial]sudo /etc/init.d/networking restart[/FONT]
[FONT=Arial]arjan@arjan-laptop:~$ sudo gedit /etc/network/interfaces
arjan@arjan-laptop:~$ sudo /etc/init.d/networking restart
* Reconfiguring network interfaces... 
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:1b:24:3b:a9:02
Sending on LPF/eth0/00:1b:24:3b:a9:02
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.[/FONT]

[FONT=Arial]I also tried to set an IP manually, even though I don&#8217;t know much about how to choose the setting:[/FONT]

[FONT=Arial]In /etc/networking, add: [/FONT]

[COLOR=black][FONT=Arial]auto lo
iface lo inet loopback
auto eth0
address 10.75.2.77
netmask 255.255.240.0
network 137.224.252.1
broadcast 137.224.252.11
gateway 10.75.15.254

Or also changing ip adress to 10.75.2.76, but recieved /etc/network/interfaces:5: misplaced option. Also, I have some doubts before after entering ipconfig/all in a DOS screen on a windows machine using the same network, I receive [/FONT][/COLOR]

[COLOR=black][FONT=Arial]Dhcp enabled yes
DHCP server 10.110.10.3\[/FONT][/COLOR]

[COLOR=black][FONT=Arial]-Tried other kernel settings:[/FONT][/COLOR]

[COLOR=black][FONT=Arial]1. add noapic to /boot/grub/menu.lst : kernel "" ro quiet splash becomes ro quiet splash noapic: result: the comp freezes when booting at: [105.537839] ata1.00: revalidation failed (errno=-5)

2. add "acpi=off" to /boot/grub/menu.lst : kernel "" ro quiet splash becomes ro quiet splash "acpi=off": result: the comp freezes when booting at: Starting up...

3. add noisapnp to /boot/grub/menu.lst (...etc) no effect

4. add noisapnp to pnpacpi=off to /boot/grub/menu.lst (...etc) result: the comp freezes when booting during sandwatch[/FONT][/COLOR]

A LAN that uses class A private address routing (10.0.0.1 through to 10.255.255.254) uses a subnet mask of 255.0.0.0 

Yours doesn't. 

Most routers assign IP's through class C addresses (192.168.0.1 through to 192.168.255.254) with a subnet mask of 255.255.255.0. Why have you gone for class A assignment with your router DHCP server?

Your subnet mask does not appear to a standard address.

---

