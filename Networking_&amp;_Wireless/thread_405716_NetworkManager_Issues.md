---
title: "NetworkManager Issues"
date: 2007-04-10
forum: Networking &amp; Wireless
---

### Post by era86 on 2007-04-10
My wpa wireless, no matter where I go, no longer works. It used to work before, but now it will not connect to any wpa network. I was wondering that maybe I tampered with the config files and such. If this is the case, can someone tell me where the config files are? Or if anyone has any ideas, please let me know. It would really make life easier! Thanks so much.

---

### Post by ubukool on 2007-04-10
More information will be required to help.   What version of Ubuntu are you using?  What happens when you left click the Network Manager icon - does it show any wireless networks at all?

can you go into terminal and post the results of typing  'iwconfig'  and then 'ifconfig' 

Thanks!

---

### Post by era86 on 2007-04-10
I am using 6.06 and when I click the icon, it shows all connections. The problem is, when I try to connect, it prompts me for my passcode, and then takes awhile, but does not connect. Here are my outputs:

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:""
          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:3  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

sit0      no wireless extensions.

~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0B:5D:7F:B6:A4
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:5dff:fe7f:b6a4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31704 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53400 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:10757159 (10.2 MiB)  TX bytes:5183993 (4.9 MiB)
          Interrupt:11

eth1      Link encap:Ethernet  HWaddr 00:0E:35:C3:05:C5
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:348726 errors:48 dropped:48 overruns:0 frame:0
          TX packets:22500 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:16879 (16.4 KiB)  TX bytes:3688 (3.6 KiB)
          Interrupt:11 Base address:0x2000 Memory:d0206000-d0206fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01
          inet addr:172.16.53.1  Bcast:172.16.53.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08
          inet addr:172.16.120.1  Bcast:172.16.120.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

Hope that helps! Thank you so much!

---

### Post by spd106 on 2007-04-10
Try looking in the /var/log/syslog file for any errors.

---

### Post by era86 on 2007-04-10
There is a message that continues to pop up saying:

skip - SSID mismatch 

Could this be the problem?

I also get

No keys have been configured - skip key clearing

Any thoughts? Maybe you could tell me what type of errors specifically? Thanks!

---

