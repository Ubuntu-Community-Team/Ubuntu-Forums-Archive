---
title: "[SOLVED] ethernet doesn't work"
date: 2008-07-06
forum: Networking &amp; Wireless
---

### Post by morty35 on 2008-07-06
I am new to Ubuntu and have a friend who encouraged me to try linux.  I just got a Ubuntu Inspiron 1420 Laptop, and the ethernet internet connection doesn't work.  I plugged it into a socket that I already tested with my main desktop.  The really weird thing is that the ethernet was working at my friend's house.  

   I have a suspicion that the network might be rejecting the laptop, but I don't really know for sure.  I would need to be able to confirm it is a network problem before maintenance at my apartment would do anything.  

How do I check if it is the network that is rejecting my computer verses something wrong with the laptop?  Also, what possible reasons could the network be rejecting a linux computer?

---

### Post by tamoneya on 2008-07-06
can you post the output of running the two following commands in terminal (applications -> accessories -> terminal).  ```
ifconfig
sudo lshw -C network
```

---

### Post by morty35 on 2008-07-06
mortensen@dell-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1E:C9:08:2E:0E  
          inet6 addr: fe80::21e:c9ff:fe08:2e0e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:59 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8044 (7.8 KB)  TX bytes:6479 (6.3 KB)
          Interrupt:17 


eth1      Link encap:Ethernet  HWaddr 00:1F:3C:73:85:CB 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:69 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0x6000 Memory:f9fff000-f9ffffff 

eth0:avah Link encap:Ethernet  HWaddr 00:1E:C9:08:2E:0E  
          inet addr:169.254.2.199  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:264 (264.0 b)  TX bytes:264 (264.0 b)


vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:172.16.66.1  Bcast:172.16.66.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:192.168.85.1  Bcast:192.168.85.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

mortensen@dell-desktop:~$ sudo lshw -C network
[sudo] password for mortensen:
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 02
       serial: 00:1f:3c:73:85:cb
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp firmware=14.2 1:0 () latency=0 link=no module=ipw3945 multicast=yes wireless=unassociated
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:c9:08:2e:0e
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.77 duplex=full latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s

mortensen@dell-desktop:~$

---

### Post by morty35 on 2008-07-06
Update:

At my wife's suggestion, I tried using the internet on the virtual windows I have installed on the laptop, and it worked.  I now know definitely that it is a network issue and not my laptop.  

SOLVED

---

### Post by red_team316 on 2008-07-06
I would try pppoeconf first before considering the problem solved, because your wife's solution is rather pragmatic. When I first started using Ubuntu that was my biggest issue. Now that we have a router, it's not an issue at all.

---

### Post by tamoneya on 2008-07-06
That doesnt exactly appear to be solved to me but if you are satisfied with it thats fine with me.  If you want to work further we should probably look into the dropped packets on eth0:```
RX packets:59 errors:0 dropped:0 overruns:0 frame:0
TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
```
Also can you give us the router model ( or whatever else you are connected to).  I have actually found network hardware that has had trouble with the default kernel and I have had to make some changes to get it to stop dropping connections.

---

### Post by morty35 on 2008-07-09
Sorry, been busy for a few days.  The solution of running the internet in virtual windows does present a lot of problems.  I think I would like to see if I can fix it on the laptop.

I have tried entering the command pppoeconf, and my computer gave the following response:

Please become root before running pppoeconf!

I also don't know how to get the router number.  I am very new to Linux and don't know much about networking in general.

---

### Post by red_team316 on 2008-07-09
anything that asks you for root access, use sudo.

say:
sudo pppoeconf

or sudo apt-get moo

sudo su also works.

Are you locked out?

---

### Post by morty35 on 2008-07-09
I tried the pppoeconf, but it didn't work.  Here is the final message:

                  NOT CONNECTED

Sorry, I scanned 4 interfaces, but the Access Concentrator of your provider did not respond.  Please check your network and modem cables.  Another reason for the scan failure may also be another running pppoe process which controls the modem.


                     <OK>

---

### Post by morty35 on 2008-07-09
I know it isn't the modem or cables, because the internet works on the virtual machine.  What should I try next?

---

### Post by Trollslayer on 2008-07-09
Which network connection is to the internet?
Try 'sudo dhclient' for eth0 and 'sudo dhclient eth1' for eth1, this sohuld request a dynamic IP address from the modem/router.

---

### Post by morty35 on 2008-07-09
Thanks for all the help.  The internet now works for Ubuntu.  


SOLVED

---

