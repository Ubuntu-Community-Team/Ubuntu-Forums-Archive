---
title: "[SOLVED] no internet with correct settings"
date: 2008-03-03
forum: Networking &amp; Wireless
---

### Post by Anonimoes on 2008-03-03
Lately I have been running into a strange networking problem: Until summer 2007 I was using Ubuntu happily (versions 6.06 - 7.04). During the summer holidays I ordered a new pc and installed Vista on it which works fine. Then after some time I decided to try ubuntu on mij new pc and installed version 6.10. I filled out the appropriate boxes for my network configuration that had always worked flawlessly on the older versions of ubuntu. (IP, subnetmask, gateway, DNS1, DNS2) Despite the fact that all configuration seems allright I have no internet connection. When I issue an ifconfig I get eth0 with only an inet6 address and no ipv-4 address. I can set the IPV-4 address manually and set the gateway using ifconfig eth0 tunnel IP-gateway. I then can ping the gateway but when I try to reacht the DNS servers I get an "no rout to host" error. 

After this I returned to Vista since this was still working fine and forgot about the network problems. Last week though I dicided to have another go at it, sadly to no avail. I even tried alpha5 of version 8.04 and although the internet connection in this version works for a while it disconnects and then never reconnects again. (I even managed to download all updates and installed them) At this point I get the exact same behaviour I described for version 6.10. A possible explanation might be that the updates broke my internet connection but after a fresh install I was able to use the internet for less than a minute before it blacked out...

Can anyone give me a clou as to where the problem might be situated? If you need more info please ask for it and I will post it here.

PS: I am required to use a static IP addres with a gateway.

---

### Post by Iowan on 2008-03-03
Post results of **ifconfig** and the contents of **/etc/network/interfaces.**  Also, check System>Administration>Network>Wired Connection>Properties to verify you have a configuration of **Static IP address**.

---

### Post by Anonimoes on 2008-03-04
ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:1A:4D:49:2B:38  
          inet addr:195.169.226.81  Bcast:195.169.226.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1659 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:198232 (193.5 KB)  TX bytes:2207 (2.1 KB)
          Interrupt:17 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```
Aparently ifconfig sets the correct values now, still no connection though...

ping commands:
```

simon@vhe-le16c202:~$ ping 131.174.60.21
connect: Network is unreachable
simon@vhe-le16c202:~$ ping www.google.com
ping: unknown host www.google.com
simon@vhe-le16c202:~$ 
```
The IP I'm pinging is one of my DNS Servers.

/etc/network/interfaces
```
auto lo
iface lo inet loopback


iface eth0 inet static
address 195.169.226.81
netmask 225.255.255.0
gateway 195.169.226.254

auto eth0

```

System>Administration>Network>Wired Connection>Properties is set to static IP address (as it always was).

---

### Post by The Cog on 2008-03-04
The only difference in my interfaces file is that 
**auto eth0**
appears before (above) the 
**iface eth0**
and confguration lines. I don't know if that's important. It might be your problem.

It looks like you are still missing the default route. What does 
**route -n**
say?

---

### Post by Anonimoes on 2008-03-04
Yeah, looks like it, this is te route -n output:
```
simon@vhe-le16c202:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
195.169.226.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0

 
```

Switching the line you recommended didn't help by the way.

This is all on ubuntu 7.10, so not on the (probably buggy) 8.04 alpha 5.

[edit] Well your remark about there being no route set led me to search for the proper way to set the gateway, This turned out to be route add default gw [IP addr]. After executing this command i 'suddenly' had a connection :) So thanks a lot for getting me started on this one! I guess I will just put this command in a bootscript to set the gateway each time ubuntu boots.

---

### Post by The Cog on 2008-03-05
> I guess I will just put this command in a bootscript to set the gateway each time ubuntu boots.
That shouldn't be necessary. That's what the gateway clause in /etc/interfaces is for. Try moving the auto eth1 up above the rest of the stanza (I don't know if that will fix it but its' worth a try).

---

### Post by Anonimoes on 2008-03-05
I've already tried that but it didn't work... (You suggested it in you other post as well)

Well, of course the method with a bootscript is not very nice but rather "quick and dirty", this is fine by me however since it works like a charm now.

---

