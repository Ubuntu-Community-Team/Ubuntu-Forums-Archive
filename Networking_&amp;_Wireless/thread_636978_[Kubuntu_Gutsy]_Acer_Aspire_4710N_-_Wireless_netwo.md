---
title: "[Kubuntu Gutsy] Acer Aspire 4710N - Wireless networking  problems"
date: 2007-12-10
forum: Networking &amp; Wireless
---

### Post by ddrake on 2007-12-10
Hello

 I have installed Kubuntu Gutsy 7.10 on a new Acer Aspire 4710N (Intel Core 2 duo with 
builtin Intel Pro 3945 wireless support).

 I have tried several suggestions of handling a non-working intel ipw3945 wireless system.
None have worked fully. This includes blacklisting ipw3945 and adding iwl3945 into /etc/modules (to be loaded into the booting kernel).This resulted in the wireless
device not working at the hardware level (The wireless LED went dead).

Here are some results:
> 
root@ananda:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:D3:EC:B8:9B
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d3ff:feec:b89b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:2054 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2397 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1865719 (1.7 MB)  TX bytes:307045 (299.8 KB)
          Interrupt:17

eth1      Link encap:Ethernet  HWaddr 00:1B:77:E1:97:8D
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:9 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0xa000 Memory:d8000000-d8000fff

eth1:avah Link encap:Ethernet  HWaddr 00:1B:77:E1:97:8D
          inet addr:169.254.8.202  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Base address:0xa000 Memory:d8000000-d8000fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:47 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4194 (4.0 KB)  TX bytes:4194 (4.0 KB)


root@ananda:~# dmesg| grep ipw3945
[   14.292000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.2mp.ubuntu1
[   14.292000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   14.292000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   16.180000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
[ 1072.964000] ipw3945: Radio Frequency Kill Switch is On:


root@ananda:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:16 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0

root@ananda:~# iwconfig eth1 essid <****id masked******>
root@ananda:~# dhclient eth1
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:1b:77:e1:97:8d
Sending on   LPF/eth1/00:1b:77:e1:97:8d
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.



What am I missing out?  Kindly share your successful experiences
with this kind of hardware.

Thanks a lot in advance
DD

PS: I  followed the thread - [http://ubuntuforums.org/showthread.php?t=297659](http://ubuntuforums.org/showthread.php?t=297659)  -- but could not progress much! 
I understand that some ipw3945 intel pro card *work* and some *don't* (as reported in someother post) however, has anyone
decisively solved this ipw3945 problem for kubuntu gutsy?

---

