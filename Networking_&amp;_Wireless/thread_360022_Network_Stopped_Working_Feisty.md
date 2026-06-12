---
title: "Network Stopped Working: Feisty"
date: 2007-02-12
forum: Networking &amp; Wireless
---

### Post by MrKeith on 2007-02-12
Everything was working just fine with Feisty Fawn running under VMWare until a few days ago. I was happy as a clam. DHCP networking was fine, even Samba worked. 

Today when I booted up Feisty I had no network connection through VMware back to my Windows host machine. I have tried several different things but nothing works. Any help would be appreciated. I am fairly novice as far as Linux goes.  Here is some diagnostic info:

eth0    Link encap:Ethernet  HWaddr 00:0C:29:B8:D2:CD  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:256 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3997 (3.9 KiB)  TX bytes:29499 (28.8 KiB)
          Interrupt:17 Base address:0x1400 

eth0:avah Link encap:Ethernet  HWaddr 00:0C:29:B8:D2:CD  
          inet addr:169.254.9.208  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0x1400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4448 (4.3 KiB)  TX bytes:4448 (4.3 KiB)


Network Manager shows:
eth0
driver pcnet32 
speed unknown
ip address: 0.0.0.0

UPDATE:
I issued these commands and now I can access the Internet through my host machine. However, I need this to work as DHCP rather than static, as I want to run the Feisty virtual machine on different host computers.

sudo ifconfig eth0 192.168.1.9 netmask 255.255.255.0
sudo route add default gw 192.168.1.2

---

### Post by spd106 on 2007-02-12
As you've probably guessed you're not picking up an IP address through dhcp. Since you're on feisty this could be any one of many issues. I suggest you look through the /var/log/syslog file for some Network Manager related information.

---

### Post by MrKeith on 2007-02-13
Update2: 

Problem solved. I changed the guest Ethernet type in VMWare from "bridged" to "NAT" and was able to connect in Feisty using DHCP. About the same time I noticed that I could not get a DHCP address from my router for another computer on my network. I rebooted my router, changed the VMWare ethernet back to "bridged", booted Feisty, and everthing is working properly now. Normally my router is very rock-solid, arghhhhh.

---

