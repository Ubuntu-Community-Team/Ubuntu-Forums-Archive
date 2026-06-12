---
title: "No network connection with Realtek 8111/8168 and Gutsy Gibbon"
date: 2008-01-20
forum: Networking &amp; Wireless
---

### Post by jio23 on 2008-01-20
Hi,

I have run into network problems while installing Gutsy Gibbon on a new server (not a dual boot).  Basically, i can see the card, all the lights are on on the NIC and router, but there is no network.  I have spent the past 4 hours looking through forums but with no results - similar problems, but no solution for me.

The network card is an on board realtek 8111/8168 NIC. I have a sound card and video card also installed, but no drivers for these yet - i can not get online to download them :)  The server is a intel dual core.

john@mediacentre:~$ uname -a
Linux mediacentre 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

below are some details of the system config.  This is untouched after the install (the 3rd install with a freshly downloaded version of GG).  Hopefully there is plenty of info here.

The router is set up for DHCP and it works jsut fine - it is what i am using to connect right now.

Any suggestions to get my new server on the net will be greatly appreciated.  All I can think of is to rip out the realtek and put in a new PCI NIC card.

Thanks,
John

=======

john@mediacentre:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev ff)
04:00.0 Multimedia audio controller: Creative Labs SB Audigy LS
04:01.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)

john@mediacentre:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1D:7D:35:2E:54  
          inet6 addr: fe80::21d:7dff:fe35:2e54/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:4294967270 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xa000 

eth0:avah Link encap:Ethernet  HWaddr 00:1D:7D:35:2E:54  
          inet addr:169.254.4.19  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2416 (2.3 KB)  TX bytes:2416 (2.3 KB)

john@mediacentre:~$ ethtool -i eth0
driver: r8169
version: 2.2LK
firmware-version: 
bus-info: 0000:03:00.0

john@mediacentre:~$ more /etc/hosts
127.0.0.1       localhost
127.0.1.1       mediacentre

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

john@mediacentre:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0

john@mediacentre:~$ more /etc/network/interfaces
auto lo
iface lo inet loopback
iface eth0 inet dhcp
auto eth0

==========

---

### Post by jio23 on 2008-01-20
I forgot to mention that i get the same result from the install CD and the server bootup.  I have never successfully accessed the network with this server as it is new and had no other OS on it.  John.

---

### Post by deanfred on 2008-01-20
John,
I don't have an answer, but I wanted to make you aware of my post, which is the same problem.  Please let me know if you get an answer, and I'll do likewise.  Best I can determine, Ubuntu is selecting the wrong driver for the 8111/8168 chip family.  It's picking the R8169 driver, not the r8168 driver (for which Realtec's web site as a recent driver update.)  If I knew how to properly replace the driver in Gutsy, I would do that but I am a newbie and don't know the accepted way to do this.

I don't want to buy another NIC card.  I spent a DAY selecting this motherboard for its feature/pricepoint/durability/power consumption.  I'm trying to build a low power file server for my home network and don't want it consume more power than needed by adding cards for functions which are already on my motherboard.  By the way, XP has *NO PROBLEM* with the motherboard NIC.  The board is a GA-G31M-S2L.

Good luck!  
Dean

Oops...here's the link
[http://ubuntuforums.org/showthread.php?t=671614](http://ubuntuforums.org/showthread.php?t=671614)

---

### Post by jio23 on 2008-01-20
Hi again,

I have tried to install a new driver for this NIC, folloing instructions posted on the following urls:

[http://www.linuxquestions.org/questions/linux-newbie-8/help-with-internet-connection-592616/](http://www.linuxquestions.org/questions/linux-newbie-8/help-with-internet-connection-592616/)
[http://www.linuxquestions.org/questions/linux-newbie-8/asrock-conroe945g-dvi-motherboard-538845/?highlight=realtek+8111](http://www.linuxquestions.org/questions/linux-newbie-8/asrock-conroe945g-dvi-motherboard-538845/?highlight=realtek+8111)

I managed to build and install the driver r8186-8.004.00, others i tried were not compilable or were older versions than recommended.

However, I still get the same result.  No network connection and no aparent changes to the configuration, even after reboot.  It still seems to think that the card is an r8169!  Even after rebooting and retrying the build and install.  Here's the output from ethtool:

john@mediacentre:/usr/src/r8168-8.004.00$ sudo ethtool eth0
Settings for eth0:
        Supported ports: [ FIBRE ]
        Supported link modes:   1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  Not reported
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: FIBRE
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: pumbg
        Current message level: 0x00000033 (51)
        Link detected: yes
john@mediacentre:/usr/src/r8168-8.004.00$ sudo ethtool -i eth0
driver: r8169
version: 2.2LK
firmware-version: 
bus-info: 0000:03:00.0
john@mediacentre:/usr/src/r8168-8.004.00$ 

Any help or direction would be great.  I have run out of ideas and certainly at the ragged end of my linux knowledge.

Thanks,
John

---

### Post by jio23 on 2008-01-21
Hi,

I have made progress on this and moved to another forum.  Details can be found at the following url: [http://www.linuxquestions.org/questions/linux-networking-3/no-network-detected-realtek-81118168-issue-615047/#post3029998](http://www.linuxquestions.org/questions/linux-networking-3/no-network-detected-realtek-81118168-issue-615047/#post3029998)

Cheers,
John

---

