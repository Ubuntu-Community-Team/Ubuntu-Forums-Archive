---
title: "[SOLVED] basic networking problem or not?"
date: 2008-01-14
forum: Networking &amp; Wireless
---

### Post by Silvain on 2008-01-14
Machine 1 has DHCP server and ppp0 a dial-up modem serving to ethernet , Ethernet cables and hub is ok, My basic problem is no connectivity as  Machine 2 can ping machine 1 and machine 2 gets no reply same situation applys from machine 1 pinging machine 2. Here is my outputs from terminal.
```
 from machine 1
eth1      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:ccff:fe37:b2c6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:173 errors:0 dropped:0 overruns:0 frame:0
          TX packets:199 errors:1 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:18574 (18.1 KB)  TX bytes:21767 (21.2 KB)
          Interrupt:11 Base address:0xc800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:334 errors:0 dropped:0 overruns:0 frame:0
          TX packets:334 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:50392 (49.2 KB)  TX bytes:50392 (49.2 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:xx.xx.xx.xx  P-t-P:204.xx.xx.x  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:548  Metric:1
          RX packets:5312 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5245 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:2562401 (2.4 MB)  TX bytes:436701 (426.4 KB)

silvain@silvain-desktop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
dialup-204.42.1 *               255.255.255.255 UH    0      0        0 ppp0
192.168.0.0     *               255.255.255.0   U     0      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         *               0.0.0.0         U     0      0        0 ppp0
---------------------------------------------------------------------------------
machine 2, a cloned system, with no dial-up and a ethernet adapter

silvain@wet-athlon:~$ ifconfig
eth2      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:192.168.0.229  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::226:54ff:fe13:c157/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:42 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4094 (3.9 KB)  TX bytes:4730 (4.6 KB)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

silvain@wet-athlon:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth2
link-local      *               255.255.0.0     U     1000   0        0 eth2
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth2


```

The basic situation/problem at the moment seems to be that  neither machine will reply to the other when pinged, Cables and hub are ok, the signal is getting thru, am sure of this. Wonder what settings etc, I need to change to fix my lack of communications? Also this might be relevant ,machine 2 is a clone of machine 1, So whatever is keeping machine 1 from replying is probably  what is keeping machine 2 from replying also , this seems logical. Anyone care to give me some ideas about, what to try next?

---

### Post by sqrt2 on 2008-01-14
What's the output of "ping -c 1 <other machine>"? How are those two machines connected? Simply Machine 1 --- Hub --- Machine 2?

---

### Post by Silvain on 2008-01-14
Yes the connection is Machine 1 --- Hub --- Machine 2, When i ping machine 2 from machine one , get no reply ever. And vice versa

---

### Post by Silvain on 2008-01-14
Update: wiping / reloading system 2, just in case, made some wrong changes to it before, then will recheck for ping and then probably repost , ifconfig and routeresults.

---

### Post by Silvain on 2008-01-14
This is the terminal returns from machine 2, after wipe and reload.
```
eth2      Link encap:Ethernet  HWaddr 00:xx:xx:xx:xx:xx  
          inet addr:192.168.0.229  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::226:54ff:fe13:c157/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2716 (2.6 KB)  TX bytes:3274 (3.1 KB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 b)  TX bytes:480 (480.0 b)

silvain@wet-athlon:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth2
link-local      *               255.255.0.0     U     1000   0        0 eth2
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth2


```

When ping Machine2 from Machine1, no reply,
When ping Machine1 from Machine2, no reply..
That is my current situation, Any suggestions?

---

### Post by Silvain on 2008-01-14
More information to post , Plugged in a Windows XP system into my hub and it is able to get internet shared from system 1 and can also ping Machine 1 fine. When try to ping Machine2 from the XP system you then get message "Cannot find host 192.168.0.299". Could this be a routing problem of some kind?

---

### Post by sqrt2 on 2008-01-15
Unless configured very strangely, a system will try to connect machines on the same network by resolving the MAC address via ARP and relying on layer 2 (Ethernet, in this case) to transmit all the packets. There's no routing involved.

What does "arp -n" say after trying to ping machine 1 from machine 2?

---

### Post by Silvain on 2008-01-15
Hi Sqrt2, 
Have managed to undo most of the stuff like :
1, go back to old dhcp setting from before the one system was made into dhcp server.
2. Stopped/ removed masquerade script routine.
3. Took out line in dhcp3 server configs that made server listen.
4. Flushed ip tables
5. Removed dnsmasqe via synaptic package manager.
6. Next change /etc/dhcp3/dhclient.conf comment out # prepend domain-name-servers 127.0.0.1
7. Took the ether net card out of roaming mode, and put it into DHCP config, and then I was able to ping. 

It should have worked in the roaming mode , right ?

Did that arp command got this:

```
silvain@wet-athlon:~$ arp -n
Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.0.1              ether   00:xx:xx:xx:xx:xx   C                     eth2
```

---

### Post by sqrt2 on 2008-01-15
Wait, you have masquerading running on the first machine? That's a very different sitiuation, you *must* mention something like that in detail in your first post.

Also, "roaming mode" is an expression associated with wireless networking, all you have mentioned are ethernet cables. What comes close to it would be "promiscuous mode" but there should have been mention of that in your ifconfig output. So what do you mean by "roaming mode"?

The fact that arp knows the hardware address of the first machine means that the machines can see each other. When you use masquerading this means that you do some kind of packet filtering/mangling, so the output of "iptables -t -nal -vnL" and "iptables -t filter -vnL" is important.

---

### Post by Silvain on 2008-01-16
> **sqrt2 said:**
> Wait, you have masquerading running on the first machine? That's a very different sitiuation, you *must* mention something like that in detail in your first post.
.
Hm, my bad maybe?  I did mention that my Machine1 is a server, my thoughts are  that  there is nothing else workable, really ?  Firestarter never worked for me at all for sharing internet off this Machine 1, And from all my reading here, couldn't find anything to use other than masquerading on my setup . See this post:
[http://ubuntuforums.org/showthread.php?t=660557]("http://ubuntuforums.org/showthread.php?t=660557") to know more about my Machine1 setup.

Roaming mode is that little box you "tic" . Heres how to get there, "System">"Administration">"Network Settings">click "Wired connection". See the little box in upper left top corner now ? You should if this is followable, hope it is. Alternately you can click an icon,"looks like two monitors next to speaker icon" on what might be the top bar on your desktop , providing you have not moved it and get there also.

Ok will try running those other commands in a while on both machines and post back later.

---

### Post by Silvain on 2008-01-17
This is from my Machine1:
```
silvain@silvain-desktop:~$ sudo iptables -t -nal -vnL
[sudo] password for silvain:
iptables v1.3.6: can't initialize iptables table `-nal': Table does not exist (do you need to insmod?)
Perhaps iptables or your kernel needs to be upgraded.

```

I spent about a solid week and a half to two downloading updates on this system at least once, and minor updated at least once since then. Updating is a a very slow annoying process here. Given the speed rate my weak land line gives. The unknown rate is fairly common, then sometimes you get 500byte to 1.1K bytes a second, what a joy !

---

### Post by sqrt2 on 2008-01-17
Should be "nat", not "nal", sorry. Anyway, what is it that's not working right now? You mentioned that pinging already works.

---

### Post by Silvain on 2008-01-17
It is working now since I turned the roaming mode off on the network setup for the ethernet connection. And changed it to DHCP setup on Machine2.

Still its a bit odd that it couldn't ping machine 1 until that was changed. Oh tried that command. ```
silvain@silvain-desktop:~$ sudo iptables -t -nat -vnL
iptables v1.3.6: can't initialize iptables table `-nat': Table does not exist (do you need to insmod?)
Perhaps iptables or your kernel needs to be upgraded.
silvain@silvain-desktop:~$ 

```

Guess I should mark this thread as solved now.

---

