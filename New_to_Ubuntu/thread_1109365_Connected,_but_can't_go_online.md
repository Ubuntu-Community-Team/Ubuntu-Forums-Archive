---
title: "Connected, but can't go online"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by littlejeep84 on 2009-03-28
Hello.... I am very new to Linux so this is probably something simple but...

I installed Linux on an old pc, and while it shows eth1 as being connected with IP address, subnet mask and all that, it will not go online.  I can even log into my router and make changes to that, but cannot go online.  I am using a DSL connection/modem through a Linksys wireless router.  This PC is connected to the router via a network cable.

Any help would be very appreciated.  If additional info is needed, please let me know.

---

### Post by halavin on 2009-03-28
can you give us your: 

sudo ifconfig ?

---

### Post by littlejeep84 on 2009-03-28
> **halavin said:**
> sudo ifconfig ?

eth1      Link encap:Ethernet  HWaddr 00:e0:18:36:27:4d  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:18ff:fe36:274d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:767 errors:0 dropped:0 overruns:0 frame:0
          TX packets:826 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:318072 (318.0 KB)  TX bytes:93208 (93.2 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:90 errors:0 dropped:0 overruns:0 frame:0
          TX packets:90 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4636 (4.6 KB)  TX bytes:4636 (4.6 KB)

pan0      Link encap:Ethernet  HWaddr 7e:c5:78:16:47:ed  
          inet6 addr: fe80::7cc5:78ff:fe16:47ed/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:636 (636.0 B)

---

### Post by fly-by-night on 2009-03-28
Go to Main Menu/System/Preferences/Network Configuration

Under the Wired section you will have to manually configure your router settings.  If no connections show, click on "Add" and specify your setting to connect to router.

Under IPv4 Settings, you will have to specify the DNS Servers as 208.67.222.222, 208.67.220.220 (OpenDNS as an example, use other if so choose)

That should do.

Edit:  Changed wireless to wired after re-read

---

### Post by littlejeep84 on 2009-03-28
I went to the wired connection and IPv4 tab.... connection appeared.  I edited the settings with my IP, netmask, gateway, and DNS server.  Still no internet connection.  I can still ping and log into my router.

---

