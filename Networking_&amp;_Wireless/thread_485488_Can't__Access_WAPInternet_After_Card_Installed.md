---
title: "Can't  Access WAP/Internet After Card Installed"
date: 2007-06-26
forum: Networking &amp; Wireless
---

### Post by sjrlaw on 2007-06-26
Hi folks!  Ubuntu noob here!  I have 6.10 installed with a Linksys WMP55G wireless NIC.  Ubuntu recognized the card, and I was able to configure it, but I cannot see the Windows machines on the network and cannot access the Internet.  This seems to be a common problem from my perusal of these pages, but help!!

---

### Post by 65 mustang on 2007-06-26
what wireless network are you trying to connect to?

could you open a terminal and post the results of:
```

ifconfig
iwconfig

```

---

### Post by sjrlaw on 2007-06-27
I ran ifconfig and iwconfig, and th outcome is below:

steve@Steves-Linux-Box:~$ ifconfig

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)


steve@Steves-Linux-Box:~$ iwconfig

lo        no wireless extensions.eth1
          IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid
          RTS thr: off   Fragment thr: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0eth0
          no wireless extensions.sit0
          no wireless extensions.


Help!

---

