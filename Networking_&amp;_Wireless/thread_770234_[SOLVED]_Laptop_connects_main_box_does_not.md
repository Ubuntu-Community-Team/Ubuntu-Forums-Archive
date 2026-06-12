---
title: "[SOLVED] Laptop connects main box does not"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by satipera on 2008-04-27
Hello, after upgrading to hardy my laptop connects wirelessly no problem at all. But the main PC will not connect via a wired connection after upgrade and even after a clean install, i have tried messing around with network manager and i can't get it to work any ideas anyone? thanks  :(   I have done another clean install and it is presently completely at install out of the box settings.

---

### Post by superprash2003 on 2008-04-27
please type ifconfig in the terminal and post results here

---

### Post by satipera on 2008-04-27
here it is ty


To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ian@ian-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:92:d5:8c:ba  
          inet6 addr: fe80::21a:92ff:fed5:8cba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:4983 (4.8 KB)
          Interrupt:245 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:1a:92:d5:8e:5b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:246 Base address:0x6000 

eth0:avahi Link encap:Ethernet  HWaddr 00:1a:92:d5:8c:ba  
          inet addr:169.254.9.144  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:245 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1756 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1756 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:87992 (85.9 KB)  TX bytes:87992 (85.9 KB)

ian@ian-desktop:~$ 
ian@ian-desktop:~$

---

### Post by superprash2003 on 2008-04-27
is DHCP enabled in your router? if so enable it in the network manager also.. WHat is your router's ip address?

---

### Post by satipera on 2008-04-27
yes dhcp is supported if therouter is the default gateway or default route then it is 192.168.1.254 i have tried what you suggested before but will do so again onthe wirless laptop the roaming box is ticked and that is it




i have unticked roaming applied dhcp and put 192.168.1.254 in dns no joy

---

### Post by satipera on 2008-04-28
Forgive me for "bumping" this thread but i have new information, the os appears to recognize both ethernet 0 and 1 (in network manager) but refuses to connect to the net, however when i remove the ethernet connector and instead use the usb connector on the router then it connects at once.  Any ideas what the problem is? does this help? (nothing wrong with cables it connects under m$)

---

