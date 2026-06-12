---
title: "network cant be pinged"
date: 2005-03-28
forum: Networking &amp; Wireless
---

### Post by sveri on 2005-03-28
Hi,

i have linksys network card that is connected to
my laptop.
No matter what i am doing my laptop cant ping my server.

With every other distro there were no problems, but i cant get it
working.

When i ping my laptop i get an error message that a byte
is wrong, but no package was lost on transfer.

Every computer has a static ip.

I wanted to share my dsl connection with my laptop,
maybe somebody can help me.


Thanks in Advance
Sven Richter

---

### Post by alastair on 2005-03-28
You would be much better giving a bit of detail i.e.

ifconfig -a
route -n
cat /etc/network/interfaces

If you are using DHCP, then :

cat /etc/dhcp3/dhclient.conf

(there was a recent DHCP config update issue - see :
[http://ubuntuforums.org/showthread.php?t=22191](http://ubuntuforums.org/showthread.php?t=22191))

If this does not help - show the ping output as well.

---

### Post by mercurus on 2005-03-28
Linksys wireless or a wired card ?
what's the card's chipset ?
are the kernel modules for the card loaded ?
Any output in dmesg or syslog when the card is loaded ?
Can the server ping the laptop ?
any firewall software running on either machine ?

---

### Post by sveri on 2005-03-29
ifconfig -a:
eth0      Protokoll:Ethernet  Hardware Adresse 00:11:D8:6F:F8:BE
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:790 errors:0 dropped:0 overruns:0 frame:0
          TX packets:859 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000
          RX bytes:319915 (312.4 KiB)  TX bytes:137668 (134.4 KiB)
          Interrupt:17 Speicher:fb400000-0

eth1      Protokoll:Ethernet  Hardware Adresse 00:50:BF:A0:3E:B8
          inet Adresse:192.168.0.42  Bcast:192.168.0.255  Maske:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:51 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000
          RX bytes:4348 (4.2 KiB)  TX bytes:882 (882.0 b)
          Interrupt:17 Basisadresse:0x8000

lo        Protokoll:Lokale Schleife
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:839 errors:0 dropped:0 overruns:0 frame:0
          TX packets:839 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0
          RX bytes:74488 (72.7 KiB)  TX bytes:74488 (72.7 KiB)

ppp0      Protokoll:Punkt-zu-Punkt Verbindung
          inet Adresse:217.228.64.233  P-z-P:217.5.98.72  Maske:255.255.255.255
          UP PUNKTZUPUNKT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:778 errors:0 dropped:0 overruns:0 frame:0
          TX packets:845 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:3
          RX bytes:302007 (294.9 KiB)  TX bytes:114725 (112.0 KiB)

route -n:
Kernel IP Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
217.5.98.72     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         217.5.98.72     0.0.0.0         UG    0      0        0 ppp0

cat /etc/network/interfaces
# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth1

iface eth1 inet static
address 192.168.0.42
netmask 255.255.255.0

auto eth1



This is the output from pinging the laptop (192.168.0.44):
PING 192.168.0.44 (192.168.0.44) 56(84) bytes of data.
64 bytes from 192.168.0.44: icmp_seq=1 ttl=64 time=0.154 ms
wrong data byte #30 should be 0x1e but was 0x2b
#16     10 11 12 13 14 15 16 17 18 19 1a 1b 1c 1d 2b 6a c0 a8 2b 6a c0 a8 2b 6a c0 a8 2b 6a c0 a8 1e 1f
#48     20 1d 1e 1f 20 21 1e 1f


It is a wired card, under windoof everything works fine, under fc3 everything worked fine, under ... ;-)
But i like ubuntu very much, and i dont want to use any other distro.


Greetings 
Sven Richter

---

### Post by sveri on 2005-03-29
[QUOTE=sveri]ifconfig -a:
eth0      Protokoll:Ethernet  Hardware Adresse 00:11:D8:6F:F8:BE
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:790 errors:0 dropped:0 overruns:0 frame:0
          TX packets:859 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000
          RX bytes:319915 (312.4 KiB)  TX bytes:137668 (134.4 KiB)
          Interrupt:17 Speicher:fb400000-0

eth1      Protokoll:Ethernet  Hardware Adresse 00:50:BF:A0:3E:B8
          inet Adresse:192.168.0.42  Bcast:192.168.0.255  Maske:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:51 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000
          RX bytes:4348 (4.2 KiB)  TX bytes:882 (882.0 b)
          Interrupt:17 Basisadresse:0x8000

lo        Protokoll:Lokale Schleife
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:839 errors:0 dropped:0 overruns:0 frame:0
          TX packets:839 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0
          RX bytes:74488 (72.7 KiB)  TX bytes:74488 (72.7 KiB)

ppp0      Protokoll:Punkt-zu-Punkt Verbindung
          inet Adresse:217.228.64.233  P-z-P:217.5.98.72  Maske:255.255.255.255
          UP PUNKTZUPUNKT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:778 errors:0 dropped:0 overruns:0 frame:0
          TX packets:845 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:3
          RX bytes:302007 (294.9 KiB)  TX bytes:114725 (112.0 KiB)

route -n:
Kernel IP Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
217.5.98.72     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         217.5.98.72     0.0.0.0         UG    0      0        0 ppp0

cat /etc/network/interfaces
# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth1

iface eth1 inet static
address 192.168.0.42
netmask 255.255.255.0

auto eth1



This is the output from pinging the laptop (192.168.0.44):
PING 192.168.0.44 (192.168.0.44) 56(84) bytes of data.
64 bytes from 192.168.0.44: icmp_seq=1 ttl=64 time=0.154 ms
wrong data byte #30 should be 0x1e but was 0x2b
#16     10 11 12 13 14 15 16 17 18 19 1a 1b 1c 1d 2b 6a c0 a8 2b 6a c0 a8 2b 6a c0 a8 2b 6a c0 a8 1e 1f
#48     20 1d 1e 1f 20 21 1e 1f


It is a wired card, under windoof everything works fine, under fc3 everything worked fine, under ... ;-)
But i like ubuntu very much, and i dont want to use any other distro.


Greetings 
Sven Richter[/QUOTE]
 ok, i solved it,
i bought a new network card in the server with a realtek chipset.

Maybe it was a driver problem.


Greetings
Sven Richter

---

