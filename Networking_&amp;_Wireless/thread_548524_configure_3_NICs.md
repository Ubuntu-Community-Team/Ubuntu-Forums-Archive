---
title: "configure 3 NICs"
date: 2007-09-11
forum: Networking &amp; Wireless
---

### Post by fadoul on 2007-09-11
Hi i

'am configuring a gateway with the last distribution (704 server) with 2 gigabits nics  DGE-530T and one 100 mb  3c905C. I don't understand what happen, i have correctly configured my /etc/network/interfaces file , all nics are powered (i can see them at the start) and when i open a session, only 2 of them are up. and one of mt dlink is working and not the other one (powered off avec boot)

# The loopback network interface
auto lo eth0 eth1 eth2
iface lo inet loopback
/etc/network/interfaces
# The primary network interface : LAN DLINK gigabit
iface eth0 inet static
address 192.168.1.254
netmask 255.255.255.0
network 192.168.0.0
gateway 192.168.1.251

# The second network interface : DMZ DLINK gigabit
iface eth1 inet static
address 192.168.33.1
netmask 255.255.255.0

# The third network interface : public  DLINK gigabit
iface eth2 inet static
address 194.224.246.33
netmask 255.255.255.224

root@octave:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:17:9A:05:7A:1B
          inet addr:192.168.1.254  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1759 errors:0 dropped:0 overruns:0 frame:0
          TX packets:307 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:175599 (171.4 KiB)  TX bytes:51570 (50.3 KiB)
          Interrupt:9

eth1      Link encap:Ethernet  HWaddr 00:B0:D0:64:4F:BA
          inet addr:192.168.33.1  Bcast:192.168.33.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 Base address:0x8c00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:680 (680.0 b)  TX bytes:680 (680.0 b)



can somebody help ? 
Thks
Fadoul


root@octave:~# lspci -v|grep -i ethernet
01:08.0 Ethernet controller: D-Link System Inc DGE-530T Gigabit Ethernet Adapter (rev 11) (rev 11)
        Subsystem: D-Link System Inc DGE-530T Gigabit Ethernet Adapter (rev 11)
01:0b.0 Ethernet controller: D-Link System Inc DGE-530T Gigabit Ethernet Adapter (rev 11) (rev 11)
        Subsystem: D-Link System Inc DGE-530T Gigabit Ethernet Adapter (rev 11)
01:0c.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)

---

### Post by fadoul on 2007-09-11
it was an IRQ problem

sorry..

---

