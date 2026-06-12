---
title: "Cannot get wired acces - but I do have wireless"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by AdeBruijn on 2009-09-16
[FONT=Arial]Dear friends[/FONT]
[FONT=Arial] [/FONT]
[FONT=Arial]This is just a new threat to summarize this internet access problem with my laptop and what has been tried before thanks to IZZIERE and MAPES12. Hope it will be more attractive for Ubuntu experts to respond to this summary.:)[/FONT]
[FONT=Arial] [/FONT]
[FONT=Arial]- The problem[/FONT]
[FONT=Arial]I cannot get wired internet acces. I manually installed wicd and now I can have wireless access.  The laptop does not recieve an IP adress[/FONT]
[FONT=Arial] [/FONT]
[FONT=Arial]- System specifications[/FONT]
[FONT=Arial]The laptop is a Packard Bell EasyNote MZ35-V-080[/FONT]
[FONT=Arial]The network card is a Realtek RTL-8139/8139C/8139C+ there are more postings on the net that mention issues with this card. My best guess now is that there is a driver called 8139too, that is assigned the job, but fails.[/FONT]
[FONT=Arial] [/FONT]
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
[FONT=Arial] [/FONT]
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
[FONT=Arial] [/FONT]
[FONT=Arial]I also tried to set an IP manually, even though I don’t know much about how to choose the setting:[/FONT]
[FONT=Arial] [/FONT]
[FONT=Arial]In /etc/networking, add: [/FONT]
[FONT=Arial] [/FONT]
[COLOR=black][FONT=Arial]auto lo
iface lo inet loopback
auto eth0
address 10.75.2.77
netmask 255.255.240.0
network 137.224.252.1
broadcast 137.224.252.11
gateway 10.75.15.254

Or also changing ip adress to 10.75.2.76, but recieved /etc/network/interfaces:5: misplaced option. Also, I have some doubts before after entering ipconfig/all in a DOS screen on a windows machine using the same network, I receive [/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[COLOR=black][FONT=Arial]Dhcp enabled yes
DHCP server 10.110.10.3\[/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[COLOR=black][FONT=Arial]-Tried other kernel settings:[/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[COLOR=black][FONT=Arial]1. add noapic to /boot/grub/menu.lst : kernel "" ro quiet splash becomes ro quiet splash noapic: result: the comp freezes when booting at: [105.537839] ata1.00: revalidation failed (errno=-5)

2. add "acpi=off" to /boot/grub/menu.lst : kernel "" ro quiet splash becomes ro quiet splash "acpi=off": result: the comp freezes when booting at: Starting up...

3. add noisapnp to /boot/grub/menu.lst (...etc) no effect

4. add noisapnp to pnpacpi=off to /boot/grub/menu.lst (...etc) result: the comp freezes when booting during sandwatch[/FONT][/COLOR][FONT=Arial][/FONT]

---

### Post by Elfy on 2009-09-16
Please do not post duplicate threads - this one is still open [http://ubuntuforums.org/showthread.php?t=1262808](http://ubuntuforums.org/showthread.php?t=1262808)

---

