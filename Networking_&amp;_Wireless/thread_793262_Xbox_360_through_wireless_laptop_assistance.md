---
title: "Xbox 360 through wireless laptop assistance"
date: 2008-05-13
forum: Networking &amp; Wireless
---

### Post by ParanoidArtemus on 2008-05-13
As the usual situation with these threads, I'm attempting at connecting my 360 to the internet through my ethernet port. I've searched through the forums but I only wind up losing my internet connection and retrying.

Here is my current ifconfig status. I am connected to my router wirelessly and nothing is plugged into the eth port.  
```
michael@michael-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:38:1b:ac:51  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1528 errors:0 dropped:0 overruns:0 frame:0
          TX packets:132 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:125596 (122.6 KB)  TX bytes:20191 (19.7 KB)
          Interrupt:219 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2221 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2221 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:108335 (105.7 KB)  TX bytes:108335 (105.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:13:e8:54:6d:7f  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:e8ff:fe54:6d7f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:46177 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41680 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:58952248 (56.2 MB)  TX bytes:5309438 (5.0 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-E8-54-6D-7F-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

I'm willing to start from scratch and any information would be helpful.

Btw. running a linksys WRT54G in case that matters.

---

### Post by SpaceTeddy on 2008-05-14
mhm - looks like a classic internet sharing problem to me. 

three things need to be done (i will only do the quick and dirty here - for the full information, please refer to [[COLOR="Blue"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=713874") thread i have written for this cause)

1.) make sure that the xbox and the computer can ping each other. This may involve setting a static IP on both side (your laptop and the xbox) or (if your xbox only aquired ips through dhcp) you will need to setup a dhcp-server. Both are explained in the thread mentioned.
The important thing is that you need to be able to ping the xbox, and the xbox needs to be able to ping the laptop. Without basic network connectivity, this cannot work.
Also make sure that you set the DNS server for the xbox to your WRT54G, and the gateway for the xbox is the IP of the **wired** ethernet card.

2.) enable IP-Forwarding on the ubuntu box.
```
sudo sysctl -w net.ipv4.ip_forward=1
```

3.)enable masuerading on your ubuntu so the pakets can find their way back to the xbox.
```
sudo iptables -A --table nat -o wlan0 -j MASQUERADE
```

that should be all. for more info, check the mentioned thread.
If any specific questions arise, just ask :)

hope it helps :)

---

