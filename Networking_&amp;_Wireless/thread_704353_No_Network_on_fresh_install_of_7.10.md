---
title: "No Network on fresh install of 7.10"
date: 2008-02-22
forum: Networking &amp; Wireless
---

### Post by CharlieNixon on 2008-02-22
I have an HP Compaq 6710b. I loaded 7.10 (dual boot w/XP). It seems to work fine so far, except that I can not pull an IP address. I have set the wired connection to dhcp in the network manager in GDM. Here is my **ifconfig** (i masked the HWaddr) 

eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet6 addr: fe80::21c:c4ff:fec6:37de/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:64 (64.0 b)  TX bytes:5906 (5.7 KB)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:14 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0x2000 Memory:e4100000-e4100fff 

eth0:avah Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:169.254.9.41  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:18 



Here is my **lspci**

10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

Any help is appreciated. I'm sure it's something simple I am overlooking.

---

### Post by CharlieNixon on 2008-02-25
Can *anyone* make a suggestion???

---

### Post by dejan.b on 2008-02-25
Well, if you changed your NIC the you should

edit file /etc/iftab and remove the line with MAC address -> reboot!

...assuming that DHCP works OK. Have you tried to set up static IP address?

Cheers,

---

### Post by Iowan on 2008-02-25
Post the contents of **/etc/network/interfaces**.
Also, check System>Administration>Network>Wired connection>Properties and verify you're set for "Automatic configuration (DHCP)" and not "Local Zeroconf network (IPv4 LL)"

---

### Post by CharlieNixon on 2008-02-29
When I set to a static IP my network connection works fine it only malfunctions when I set it to DHCP (I verified this setting). So it works on static but not on DHCP. Should I still post my **/etc/network/interfaces** file?

---

### Post by CharlieNixon on 2008-05-14
I'm not using this system anymore. Thanks for everyone's help.

---

