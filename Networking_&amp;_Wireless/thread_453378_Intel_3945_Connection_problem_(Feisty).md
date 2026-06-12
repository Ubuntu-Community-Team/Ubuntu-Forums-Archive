---
title: "Intel 3945 Connection problem (Feisty)"
date: 2007-05-24
forum: Networking &amp; Wireless
---

### Post by alienden on 2007-05-24
Hello. Straight to the point I have XPS1710 laptop with intel 3945ABG wireless card on Ubuntu  v7.04(Feisty). Using KNetworkManager i can see desired AP(Zyxel, funny default name). When I click to connect , it asks for WEP key, and then status indicates "IP configuration started", and it resets back to asking for WEP key. This seem to be an endless loop. Please excuse me for my terrible English, I,m little frustrated with this issue. I,m going to list output from simple  iwconfig, ifconfig and so on. Thank  you for any help in advance.

---

### Post by alienden on 2007-05-24
alienden@alienden-laptop: ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:C5:43:78:3C
          inet addr:192.168.1.35  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe43:783c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11494 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13260 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:7340609 (7.0 MiB)  TX bytes:2203874 (2.1 MiB)
          Interrupt:18

eth1      Link encap:Ethernet  HWaddr 00:18:DE:81:90:D4
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:103 dropped:2030 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:6917 (6.7 KiB)  TX bytes:3458 (3.3 KiB)
          Interrupt:17 Memory:ecfff000-ecffffff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1712 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1712 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:49923 (48.7 KiB)  TX bytes:49923 (48.7 KiB)

alienden@alienden-laptop:$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:16 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:103  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1934   Missed beacon:0

---

### Post by Jonathan Métillon on 2007-05-24
Hi Denis :-P

Maybe you are having an issue with your WEP key, or WEP protocol?

Try without WEP enabled on your AP and tell us what happen.

---

### Post by alienden on 2007-05-24
The very same issue seems to be with WEP protection turned off. I,m also using DHCP for my wireless and LAN in general if this would be of any help.

---

### Post by alienden on 2007-05-24
alienden@alienden-laptop:$ cat /etc/network/interfaces
#auto lo
#iface lo inet loopback

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


iface lo inet loopback

---

