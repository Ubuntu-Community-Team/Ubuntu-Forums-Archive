---
title: "Help please"
date: 2005-08-24
forum: Networking &amp; Wireless
---

### Post by bgolden12345 on 2005-08-24
I have an hp/compaq nx5000 this laptop has a Intel Pro/2100b wireless card.  The light for the radio comes on during the hardware detection process, but does not seem to be functioning properly.  This is the rest of the inforation that I have, I would appreciate any help with this.  Thanks in advance, by the way, I am very new to linux.

eth0      Link encap:Ethernet  HWaddr 00:04:23:90:45:34
          inet6 addr: fe80::204:23ff:fe90:4534/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Base address:0x6000 Memory:90100000-90100fff

eth1      Link encap:Ethernet  HWaddr 00:08:02:DF:D4:57
          inet addr:10.6.18.200  Bcast:10.6.18.255  Mask:255.255.255.0
          inet6 addr: fe80::208:2ff:fedf:d457/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:773 errors:0 dropped:0 overruns:0 frame:0
          TX packets:893 errors:0 dropped:0 overruns:0 carrier:0
          collisions:33 txqueuelen:1000
          RX bytes:519178 (507.0 KiB)  TX bytes:126004 (123.0 KiB)
          Interrupt:20

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:300 (300.0 b)  TX bytes:300 (300.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

billy@goldenpc:~$ iwconfig
lo        no wireless extensions.

eth0      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power:off
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1      no wireless extensions.

sit0      no wireless extensions.

billy@goldenpc:~$ sudo cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth1

# The primary network interface
iface eth1 inet dhcp

auto eth1

iface eth0 inet dhcp

auto eth0

---

