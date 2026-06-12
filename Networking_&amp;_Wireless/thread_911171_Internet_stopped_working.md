---
title: "Internet stopped working"
date: 2008-09-05
forum: Networking &amp; Wireless
---

### Post by MrNatewood on 2008-09-05
I can't figure out why this is happening.
My wired internet connection just stopped working in ubuntu.
I didn't touch the network settings before it happened.
I also have a windows partition on the very same computer and the internet there is working just fine.

It's a standard ADSL modem connected with DHCP. set as DHCP vpth on the windows and the ubuntu partitions but for some reason stopped working with ubuntu.

this is the output of ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:0e:a6:91:f2:dd  
          inet6 addr: fe80::20e:a6ff:fe91:f2dd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:318 errors:0 dropped:0 overruns:0 frame:0
          TX packets:180 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:84876 (82.8 KB)  TX bytes:13016 (12.7 KB)
          Interrupt:21 

eth2      Link encap:Ethernet  HWaddr 00:90:27:13:05:f5  
          inet6 addr: fe80::290:27ff:fe13:5f5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2608 (2.5 KB)  TX bytes:468 (468.0 B)

eth0:avahi Link encap:Ethernet  HWaddr 00:0e:a6:91:f2:dd  
          inet addr:169.254.11.39  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4728 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4728 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:248458 (242.6 KB)  TX bytes:248458 (242.6 KB)

```

and this is the ipconfig in windows if it matters(same computer):
```

Windows IP Configuration


Ethernet adapter Local Area Connection 2:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 192.168.0.1
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . :

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 85.64.210.195
        Subnet Mask . . . . . . . . . . . : 255.255.255.128
        Default Gateway . . . . . . . . . : 85.64.210.129
```

Any ideas on how to fix this?

---

### Post by c2olen on 2008-09-05
You seem to have your APIPA address active in Ubuntu, meaning you did not get a valid IP address during the DHCP request phase.
Have you rebooted your laptop, or have you restarted your networking?
Have you restarted your ADSL modem?

Can you post some screenprints of your network-manager settings regarding the wired settings? Otherwise, the syslog.log (in /var/log) could help.

Probably yes to all questions, right?

---

