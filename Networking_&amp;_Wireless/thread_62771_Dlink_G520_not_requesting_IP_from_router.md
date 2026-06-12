---
title: "Dlink G520 not requesting IP from router"
date: 2005-09-05
forum: Networking &amp; Wireless
---

### Post by mwalle on 2005-09-05
hello;
I've been switching all my computers to wireless to get rid of this tripping hazard that snakes around my house, but i've had troubles with Ubuntu detection of my dlink DWL-520. i setup madwifi and my system now detects that i have a wireless card, but i'm not being assigned an IP despite setting the WEP key, ESSID, access point, and i set the Mode as master (not sure if that affects being assigned an IP from my router); the router is also set up to assign an IP to this card, so it's not a problem with that (it should be assigned as 192.168.0.102).
In the networking panel in gnome it is says "the interface ath0 is active", but of course, as soon as i deactivate eth1, their is no more connection :(.
I'm confused why i will not be assigned an ip, can't think of what else to do.
it's listed in lspci, so that's good:
```
0000:00:07.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
```

and here's my iwconfig:
```
root@ubuntu:/home/mark # iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

ath0      IEEE 802.11b  ESSID:"maceo"
          Mode:Master  Frequency:2.412 GHz  Access Point: 00:11:95:D4:35:2E
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:6865-6C6C-6F   Security mode:restricted
          Power Management:off
          Link Quality=21/94  Signal level=-74 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:22  Invalid misc:22   Missed beacon:0

sit0      no wireless extensions.
```

here's my ifconfig comparing eth1 and ath0, should it be of any use:
```
ath0      Link encap:Ethernet  HWaddr 00:11:95:D4:35:2E
          inet6 addr: fe80::211:95ff:fed4:352e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:89548 dropped:0 overruns:0 frame:89548
          TX packets:2570 errors:22 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:0 (0.0 b)  TX bytes:877852 (857.2 KiB)
          Interrupt:18 Memory:f0ac0000-f0ad0000

eth1      Link encap:Ethernet  HWaddr 00:50:FC:23:F9:82
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::250:fcff:fe23:f982/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:80592 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6954 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:29386108 (28.0 MiB)  TX bytes:1164894 (1.1 MiB)
          Interrupt:17 Base address:0xec00
```

and i edited my /etc/network/interfaces file to try and force it to work, to no avail:

```
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

#wireless
iface ath0 inet dhcp
wireless-essid maceo
wireless-key 68656c6c6f
wireless-mode master

auto ath0

auto eth1
```

if you need anything else to help me solve this problem, please ask.

Thanks for your help!

---

