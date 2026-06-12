---
title: "LAN with mixed dhcp and static IP ?"
date: 2008-07-25
forum: Networking &amp; Wireless
---

### Post by bricedebrignaisplage on 2008-07-25
My LAN topology is showed on attached fig.
basically there are 3 computers on a mobile robot and some others for development. All GNU/Linux (Ubuntu 6.06, 7.10 and 8.04). They are connected with some ethernet switches and a router.

The 3 computers on the robot need a static IP so that they can communicate together when the robot is not attached to that LAN.
For the development computers it's convenient if they receive their IP through DHCP...

So for the 3 on the robot I configured their /etc/network/interface to get a static IP 172.16.0.[1,2,3] and netmask 255.255.255.0
The router is configured as a DHCP server, it assigns IP 172.16.0.[1,2,3] to the 3 computers on the robot based on their MAC address (there is a table for that in the router config page). The development computers just get an IP via normal DHCP.

All of those computers can communicate together using SSH, we can access files remotely with FISH, and access the internet. All fine!

BUT!!!
The weird part is that large data packets sent through UDP are lost. Small packet (<= 1468 bytes to be precise) get through. However, if the robot is configured with DHCP they no longer get lost. (it's part of our application: the robot sends data to external computer for graphical display)

So how can I fix that? Here are some of my ideas, but I don't know how to implement them:
[LIST]
[*]Configure the router properly to allow static IP and DHCP assigned IP to coexist. I am using a Linksys WRT54GC.
[*]Configure the robot's computers to try to get a DHCP address and if it fails, fall back to a static IP.
[*]Create an IP alias eth0:1 that would get its IP through DHCP, while eth0 would have a static IP.
[/LIST]

In the past we only had ethernet switches and static IPs and everything was fine, except that we had no internet connection.


Any help would be much appreciated.

---

### Post by bab1 on 2008-07-25
There is no reason to have the robots in the address pool for dhcp.  Static and dynamic addresses can coexist in the network.

Your UDP packet loss is due to the MTU settings being slightly off.  Wireless routers sometimes allow slightly larger packets than the ethernet standard to be passed.  I would manually set the MTU on all interfaces to 1500 MTU.  This is set by```
sudo ifconfig [COLOR="Blue"]mtu 1500[/COLOR] eth0
```

If you still have problems, you can set it lower with no harm, say 1200.

---

### Post by caljohnsmith on 2008-07-25
> **bab1 said:**
> I would manually set the MTU on all interfaces to 1500 MTU.
Just as a small note, if you are using ADSL with PPPoE or similar, the MTU will be limited to 1492 since the PPPoE protocol adds 8 additional bytes to the IP header. This applies to most DSL customers.

An easy way to figure out what your MTU should be is to use ping where you specify the payload size:
```
ping -s 1464 google.com
```
Note though that the total IP packet size will be 1464+28=1492 since there is 28 bytes of header info. Thus if the packet gets fragmented for payload above 1464, then you should set your MTU=1492. Ping will let you know when it becomes fragmented with something like the following:
```

john@TECH5321:/etc/default$ ping -s 1464 google.com
PING google.com (64.233.167.99) 1464(1492) bytes of data.
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=1 ttl=237 (truncated)
...

john@TECH5321:/etc/default$ ping -s 1465 google.com
PING google.com (64.233.167.99) 1465(1493) bytes of data.
From adsl-71-154-211-87.dsl.sndg02.sbcglobal.net (71.154.211.87) icmp_seq=1 Frag needed and DF set (mtu = 1492)
...

```
Note in the first case, the packet was transmitted fine, but in the second case ping complains "Frag needed".

---

### Post by bab1 on 2008-07-25
I have noticed that.  I normally don't mess with MTU settings.  That's good info to have. :-)

---

### Post by bricedebrignaisplage on 2008-07-29
my router sets the MTU to 1492 and could not find a way to change that. It's a linksys wrt54gc. There is a MTU parameter that I can set to auto or manual with a value, but it just refuses to accept manual 1500.
My university's DHCP server sets the MTU to 1492, so maybe the router detects that and decides that setting it manually to 1500 would not be appropriate.

Anyway, "ping -s 1464 google.com" doesn't work. For some reason my pings don't come back... Although I have no problem with accessing google from my browser...
```

$ ping -w 5 -s 1464 google.com
PING google.com (72.14.207.99) 1464(1492) bytes of data.

--- google.com ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4010ms

```

So shall I set the static IP computers with a MTU of 1492? Then all computers would have the same MTU.
How does the MTU affects networking anyway? Is it just a matter of having the same MTU and everything is fine?

---

### Post by bab1 on 2008-07-29
Did we cure your robot prob?

You really don't need to be to picky with your MTU settings if everything is working.  You can set them to 1500 -28 = 1472 (read caljohnsmith's great tutorial [[COLOR="Magenta"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=872346"))

As long as the packets will pass you are ok.

If you try```
ping -s 1472 google.com
```
and it doesn't pass try 1464 or what is recommended by caljohnsmith.

Don't mess with the router.  Concentrate on the computer.  The router is fine as is.

---

### Post by caljohnsmith on 2008-07-29
bricedebrignaisplage, I think you are misunderstanding a little bit about MTU (the Maximum Transmission Unit for a TCP packet). The MTU is limited by your physical connection and can not be arbitrarily set. For instance, a standard ethernet connection is limited to an MTU of 1500 bytes. Now if you use PPPoE (Point-to-Point Protocol over Ethernet), which is common for a DSL connection and probably the type of connection you have with your University, PPPoE requires an additional 8 bytes of header information be added to each packet; that then limits your MTU to 1500-8=1492. 

So when your computer communicates with Google for example, the TCP packets sent back and forth will be limited by the *smallest* MTU anywhere in the path between you and Google. So even though Google has an ultra-awesome network that can handle large MTUs, you will still be limited by your local connection's MTU of 1492. And to clarify, if your connection truly has an MTU of 1492, ideally you would set your computer's MTU to 1492, but there is nothing that prevents you from setting the MTU to a smaller value (you just can't set it to a larger value). But obviously you want to use the largest MTU possible to optimize your connection.

About pinging Google, try first just a normal ping with its default small packet size, and this time ping their web servers:
```
ping www.google.com
```
If that doesn't work, then it might be possible that your University blocks outgoing ping requests to prevent DOS (denial of service) attacks. Can you ping anyone else? :) If the above works, then you can play with different packet sizes, starting low and working up until you get packet fragmentation. Then you will be able to find your true MTU.

---

