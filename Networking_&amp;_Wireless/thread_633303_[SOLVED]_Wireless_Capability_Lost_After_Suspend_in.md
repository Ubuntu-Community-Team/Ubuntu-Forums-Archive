---
title: "[SOLVED] Wireless Capability Lost After Suspend in 7.10"
date: 2007-12-06
forum: Networking &amp; Wireless
---

### Post by jhstuckey on 2007-12-06
I've tried researching networking in Ubuntu 7.10 but I've been unable to remedy this particular problem; I've seen lots of people who have had various wireless networking problems in 7.10, but I've yet to come across any discussion that has been of any help.

Here's the situation:
Whenever the computer is put into suspend mode, and then out of suspend mode, it is then rendered unable to connect to the internet via wireless. However, on the menu bar, the wireless connection still shows up as connected. If the computer is taken away from the router, the computer still displays the list of networks (and the network it was connected to) before it was removed; it simply shows 0% connectivity.  If the computer is restarted, everything works fine. So in short, my problem is that I have to restart the computer every time I move the laptop to a different internet source.

Here's an interesting correlation that I noticed upon running 'ifconfig' in the terminal: 

Fg1. The output of 'ifconfig' after restarting the computer, and before suspending it (i.e., the wireless internet connection works perfectly): 
```
ifstuckey@stuckey-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr [removed]
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr [removed]
          inet addr:[removed]  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:77ff:fe29:9f0a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:0 dropped:14 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1506 (1.4 KB)  TX bytes:5248 (5.1 KB)
          Interrupt:17 Base address:0x6000 Memory:d0000000-d0000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

Fg2. The output of 'ifconfig' immediately after suspending the computer and restoring it (no wireless): 
```
stuckey@stuckey-laptop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

F3. The output of 'ifconfig' a few minutes after suspending the computer and restoring it (no wireless): 
```
stuckey@stuckey-laptop:~$ ifconfig
eth1      Link encap:Ethernet  Hwaddr [removed]
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:31 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0x2000 Memory:d0000000-d0000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

During the process of writing this post, I discovered the solution to the problem. The computer now has no problems reconnecting to wireless networks after being placed in suspend mode. Since I suspect others may be having the same trouble, the solution I used is below: 

Step1: In the terminal type:
```
 sudo gedit /etc/default/acpi-support
```
Near the bottom of *acpi-support (/etc/default) you will see:
```
# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES=""
```

Step2: Change the above to:
```
# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES="networking"
```

---

