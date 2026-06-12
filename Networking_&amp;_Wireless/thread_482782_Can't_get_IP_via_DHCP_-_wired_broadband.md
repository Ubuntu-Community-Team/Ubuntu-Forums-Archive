---
title: "Can't get IP via DHCP - wired broadband"
date: 2007-06-24
forum: Networking &amp; Wireless
---

### Post by pseudonym on 2007-06-24
I installed Ubuntu Feisty in "lite" mode using the [Minimal CD]("https://help.ubuntu.com/community/Installation/MinimalCD") method, on a machine with the following specs - ```
IBM PC 300PL
550MHz Pentium III
256MB PC100 RAM
Intel 440BX Chipset
80GB Seagate HDD
Sony CD-RW drive
32MB Nvidia TNT2 AGP video card
3Com 3c509B ISA network card
Intel Etherexpress Pro Onboard LAN
Silicon Image 680 PCI IDE controller card
Ensoniq AudioPCI sound card
PCI USB2.0 card
```
I temporarily disabled the Intel LAN and did the installation using the 3Com ISA card. Everything went fine and I set the system up how I want it.

My trouble started when I began to try out different network configurations. I re-enabled the onboard LAN, and tested out a couple of other network cards, as well as trying to plug in my cable modem via USB. I settled on the ISA card as the internet interface (eth0) and the onboard LAN as the internal one (eth1). But when I started up Ubuntu again with this setup, I found I could no longer get an IP via DHCP from my cable modem.

Here is some relevant terminal output - ```
ifconfig (with just the 3Com card enabled)

eth0    Protokoll:Ethernet  Hardware Adresse <Ethernet MAC Address appears here>  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15117 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:907870 (886.5 KiB)  TX bytes:3762 (3.6 KiB)
          Interrupt:3 Basisadresse:0x220 

lo        Protokoll:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```
```
sudo dhclient

Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

```
cat /etc/network/interfaces

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
```

The card itself is working properly because I can connect without problems from a live CD (eg. [Puppy Linux]("http://www.puppyos.com/"), from where I'm writing this now).

I've tried the following -

1. Restarting the cable modem, with the computer powered off.
2. Specifying the network card's MAC address in /etc/iftab
3. Specifying the MAC address in /etc/dhcp3/dhclient.conf
4. Specifying the MAC address in /etc/network/interfaces
5. 2, 3, & 4 all together
6. Reconfiguring/re-installing dhcp3-client
7. Re-installing Ubuntu from a partition image, from what I thought was a working configuration.

I'm almost at the point of re-installing from scratch, but before doing that I want to see if anybody can shed any light on this issue.

Thanks.

---

### Post by pseudonym on 2007-06-24
bump

---

### Post by aonegodman on 2008-06-05
Having same problem and "bump" doesn't seem to help!  :(

---

