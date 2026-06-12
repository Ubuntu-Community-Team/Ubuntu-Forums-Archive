---
title: "Wifi problems. Intel Pro/Wireless 3945"
date: 2008-07-18
forum: Networking &amp; Wireless
---

### Post by buntu_con_crema on 2008-07-18
Hello All,

This is my first post in the forum and I'm a relative newcomer to Linux so I hope I don't scare anyone off.:)
I have been using a distro of Ubuntu Studio 7.10 for the past year up until recently when I tried to update to 8.04 through the Update Manager, long story short, it didn't work and wouldn't boot in normal mode. Tried tried and tried again with no joy. 
So, I'm back on 7.10(nothing lost since backed up before the upgrade:-D). However My wireless is now not working :( . I've searched the forums and tried a few things but no joy.
If anyone could point me in the direction of some info on how to get it going from the beginning of the process or maybe guide me through it hear I would be very grateful.
Also having trouble with configuring my Synaptics pointing device but maybe I should put that in another thread.

Here is the results of some of my probing around.

Thanks in advance.

```
thomas@Headache:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:98:A3:EC  
          inet addr:192.168.1.21  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe98:a3ec/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8352 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6878 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9705622 (9.2 MB)  TX bytes:949648 (927.3 KB)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:18:DE:72:0B:AC  
          inet6 addr: fe80::218:deff:fe72:bac/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:345 errors:345 dropped:351 overruns:0 frame:0
          TX packets:118 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:77961 (76.1 KB)  TX bytes:36628 (35.7 KB)
          Interrupt:17 Base address:0xc000 Memory:d6000000-d6000fff 

eth1:avah Link encap:Ethernet  HWaddr 00:18:DE:72:0B:AC  
          inet addr:169.254.6.179  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0xc000 Memory:d6000000-d6000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

```
thomas@Headache:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"NEUF_E74C"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:17:33:5E:E7:4D   
          Bit Rate:54 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=95/100  Signal level=-32 dBm  Noise level=-33 dBm
          Rx invalid nwid:0  Rx invalid crypt:213  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:6   Missed beacon:0
```

---

