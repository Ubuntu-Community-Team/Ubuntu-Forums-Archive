---
title: "Internet connection problem"
date: 2005-09-16
forum: Networking &amp; Wireless
---

### Post by IanArc on 2005-09-16
hi,
Im using the Hoary 5.04
using a P4 2.4 mhz pc
with two Ethernet cards

one connected to a pppoe which is connected to an antenna for a Wi-Fi connetion [eth0]
while the other one is conneted to my C-NET swich [eth1]

with **dmesg | grep eth0**
eth0: Davicom DM9102/DM9102A rev 64 at 0001a800, 00:08:A1:1B:58:94, IRQ 17.
eth0: no IPv6 routers present

with **dmesg | grep eth1**
eth1: Davicom DM9102/DM9102A rev 64 at 0001a400, 00:08:A1:8D:DF:B8, IRQ 18.
eth1: Setting full-duplex based on MII#1 link partner capability of 45el.
eth1: no IPv6 routers present

i tried **ifconfig**
eth0     Lin encap:Etherne HWaddr 00:08:A1:1B:58:94
            inet6 addr: fe80::208:a1ff:a1ff:fe1b:5894/64 Scope:Link
            UP BROADCAST RUNNING MULTICAST     MTU:1500     Metric:1
            RX packets:192 errors:0 dropped:0 overruns:0 frame:0
            TX packets:17 errors:185 dropped:0 overruns:0 carrier:186
            collisions:0 txqueuelen:1000
            RX bytes:14262 (13.9KiB) TX bytes:4482 (4.3 KiB)
            Interrupt:17  Base address:0xa800

eth1    Link encap:Ethernet    HWaddr 00:08:A1:8D:DF:BB
            inet6 addr: fe80::208:a1ff:fe8d:dfb8/64 Scope:Link
            UP BROADCAST MULTICAST     MTU:1500     Metric:1
            RX packets:983 errors:1693 dropped:0 overruns:0 frame:0
            TX packets:80 errors:0 dropped:0 overruns:0 carrier:186
            collisions:0 txqueuelen:1000
            RX bytes:83764 (81.8 KiB) TX bytes:26028 (25.4 KiB)
            Interrupt:18  Base address:0xa400

as you have notice i have no IP address eventhough i set eth0 and eth1 to DHCP using the  System > Administration > Networking
eth0 -Properties - configuration  DHCP [Activated]
eth1 -Properties - configuration  DHCP [Activated]

in the /etc/network/interfaces file.

iface eth0 inet dhcp
auto eth0

iface eth1 inet dhcp
auto eth1

so because i dont have an ip address most probably i wont be conected to the web. Now someone suggested to me to use **netconfig** command but when i tried it linux prompted me an error saying "command not found"

and also with **dhclient eth0**

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:08:a1:1b:58:94
Sending on LPF/eth0/00:08:a1:1b:58:94
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS recieved
No working leases in persistent database - sleeping

noow here's my concern:
   - first how can i get the **netconfig** command for ubuntu; can it really help me?
   - is there other way to solve this? or is there something wrong with the ISP
   - and how can i share my internet connection incase my pc gets connected to the web.
   - and why isnt the server giving me any IP address eventhough i selected for a DHCP setting

by the way when i was using win xp and set eth0 [to obtian ip automatically]
and eth1 [192.168.0.1] {for inet sharing} all was fine i was able connect to internet and share it with no problems. ;(

---

### Post by IanArc on 2005-09-18
*bump*

---

### Post by cwaldbieser on 2005-09-18
> **IanArc]hi,
Im using the Hoary 5.04
using a P4 2.4 mhz pc
with two Ethernet cards

one connected to a pppoe which is connected to an antenna for a Wi-Fi connetion [eth0]
while the other one is conneted to my C-NET swich [eth1]

with **dmesg | grep eth0**
eth0: Davicom DM9102/DM9102A rev 64 at 0001a800, 00:08:A1:1B:58:94, IRQ 17.
eth0: no IPv6 routers present

with **dmesg | grep eth1**
eth1: Davicom DM9102/DM9102A rev 64 at 0001a400, 00:08:A1:8D:DF:B8, IRQ 18.
eth1: Setting full-duplex based on MII#1 link partner capability of 45el.
eth1: no IPv6 routers present

i tried **ifconfig**
eth0     Lin encap:Etherne HWaddr 00:08:A1:1B:58:94
            inet6 addr: fe80::208:a1ff:a1ff:fe1b:5894/64 Scope:Link
            UP BROADCAST RUNNING MULTICAST     MTU:1500     Metric:1
            RX packets:192 errors:0 dropped:0 overruns:0 frame:0
            TX packets:17 errors:185 dropped:0 overruns:0 carrier:186
            collisions:0 txqueuelen:1000
            RX bytes:14262 (13.9KiB) TX bytes:4482 (4.3 KiB)
            Interrupt:17  Base address:0xa800

eth1    Link encap:Ethernet    HWaddr 00:08:A1:8D:DF:BB
            inet6 addr: fe80::208:a1ff:fe8d:dfb8/64 Scope:Link
            UP BROADCAST MULTICAST     MTU:1500     Metric:1
            RX packets:983 errors:1693 dropped:0 overruns:0 frame:0
            TX packets:80 errors:0 dropped:0 overruns:0 carrier:186
            collisions:0 txqueuelen:1000
            RX bytes:83764 (81.8 KiB) TX bytes:26028 (25.4 KiB)
            Interrupt:18  Base address:0xa400

as you have notice i have no IP address eventhough i set eth0 and eth1 to DHCP using the  System > Administration > Networking
eth0 -Properties - configuration  DHCP [Activated]
eth1 -Properties - configuration  DHCP [Activated]

in the /etc/network/interfaces file.

iface eth0 inet dhcp
auto eth0

iface eth1 inet dhcp
auto eth1

so because i dont have an ip address most probably i wont be conected to the web. Now someone suggested to me to use **netconfig** command but when i tried it linux prompted me an error saying "command not found"

and also with **dhclient eth0**

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:08:a1:1b:58:94
Sending on LPF/eth0/00:08:a1:1b:58:94
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS recieved
No working leases in persistent database - sleeping

noow here's my concern:
   - first how can i get the **netconfig** command for ubuntu said:**
> 
and eth1 [192.168.0.1] {for inet sharing} all was fine i was able connect to internet and share it with no problems. ;(
You have diagnosed the problem correctly-- for some reason you do not seem to be picking up any IP addresses via dhcp.  Maybe something in your /etc/dhcp3/dhclient.conf is not configured as it needs to be?  If you post it, we can take a look.

It is worth noting that there are two DHCP clients for use on GNU/Linux systems.  Ubuntu comes standard with dhclient, but you could try to get dhcpcd and try that to see if it works any better.

If you have a Live CD that actually auto-detects and gets the network working correctly (Knoppix, etc), it you can just try copying parts of the configuration from that, too.

I am not familiar with netconfig, but Googling seems to indicate that it is a script or program that tries to automatically configure your network settings.

---

