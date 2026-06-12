---
title: "Connection working but no internet in gutsy"
date: 2008-07-03
forum: Networking &amp; Wireless
---

### Post by Emuvente on 2008-07-03
I've been trying to get my ubuntu laptop connected to the internet at my house. The setup here is a wired connection to a comcast cable modem, so no network, just pretty much a straight connection to the internet. I only have problems with this setup and never any where else. Wireless always works fine, and when I connect to the wired network at my school it also works just fine. But with this home setup I can get connected and there are packets transmitting, but when I open a browser the connection times out and when I try to ping anything, I get destination host unreachable. And it's something with my ubuntu laptop, because if I hook up the cable to my XP laptop it works fine (I'm posting this with the XP laptop).
I've searched alot of places to try to get this to work but nothing seems to help. Any help at all would be greatly appreciated.

---

### Post by superprash2003 on 2008-07-03
is your ubuntu machine getting an ip address?? go to the terminal and type ifconfig and post output here..

---

### Post by Emuvente on 2008-07-04
I am getting an ip address you can see it in the ifconfig output:

```
emuvente@ubuntu-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1C:23:F7:ED:BD  
          inet6 addr: fe80::21c:23ff:fef7:edbd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:576 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:38858 (37.9 KB)  TX bytes:7571 (7.3 KB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:1B:77:93:90:8C  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xe000 Memory:fe8ff000-fe8fffff 

eth0:avah Link encap:Ethernet  HWaddr 00:1C:23:F7:ED:BD  
          inet addr:169.254.10.173  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:35 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3205 (3.1 KB)  TX bytes:3205 (3.1 KB)
```

eth0 is the wired connection eth1 is the wireless, I don't know what eth0:avah is.

---

### Post by superprash2003 on 2008-07-04
well you dont seem to be getting an ip with eth0.. go to system->admin->network and go to eth0 properties and set it to DHCP and check again if you get an ip..

---

### Post by Emuvente on 2008-07-04
I already have it set to DHCP. And you can see that eth0 is transmitting packets. The ip address I get is the one in eth0:avah.
When I ping from the terminal, that's the ip that comes up as the sender.

---

### Post by superprash2003 on 2008-07-05
169.x.x.x is an automatic private ip address.. it pops up when your modem isnt able to give you an ip.. try static ip address.. what is your modem's ip address??if it is 192.168.1.1 . then change from DHCP to static ip.. and enter ip as 192.168.1.10 and gateway as 192.168.1.1 .. and then try

---

### Post by Trollslayer on 2008-07-05
Try 'sudo dhclient', theat will try to get an IP address and tell you what is happening as it goes.

---

### Post by Emuvente on 2008-07-06
I have no idea what my modems ip is, and so far any static ips that I tried haven't worked at all.
When I tried dhclient it ran "DHCPDISCOVER" a few times then outputed "No DHCPOFFERS recieved".

---

### Post by Emuvente on 2008-07-08
I had an idea that if I reset the modem once my laptop was connected, then the modem would automatically send a dhcp request and I could get an ip. So I tried that, then I entered sudo dhclient and it found an ip address and I am on the internet now. Thank you guys for all your help.

---

