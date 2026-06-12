---
title: "Linux Killing Internet Connection"
date: 2008-03-11
forum: Networking &amp; Wireless
---

### Post by biosonik on 2008-03-11
I have Ubuntu 8.04 (tried Ubuntu 7.10, Kubuntu 7.10, Kubuntu 8.04) and WinXP on my computer. My connection is routed through a Buffalo (DD-WRT Firmware) router then a Surfboard 5100i modem.

When using WinXp my connection is fine, in-fact, its perfect. Everything operates as it should although it is a completely different story when using Linux --

When using linux, if my connection peaks or continues for a long period of time, it cuts out and a "*Unrecognized PID*" error is logged on the Surfboard Modem meaning a significant drop in signal power. Like I said, this does not happen in Windows XP.

I've tried several different versions of (k)ubuntu with the same result. I've even (for a minute) thought it was my routers fault and upgraded the firmware on it...no success.

Does anyone know how to fix this?

Thanks
-Vince

P.S. the internet does not slow down before cutting, it just cuts

---

### Post by arpad9 on 2008-03-11
Well, I'm sure one of the first things you are going to be told is that 8.04 is not a stable release and you shouldn't be using it.  I'm not going to tell you that though...

You need to attack the problem methodically.

First, the thing connecting to the Internet for all intents and purposes is your router.  Period.  That then is routing all of your internal LAN traffic to the WAN (Internet).  By this logic, the OS on your LAN shouldn't make a difference at all.  Maybe there's something else going on?

But let's say that there isn't.  What is the traffic like between your computer and the router?  You might install the System Monitor panel app into your panel and watch to see if there are any weird things going on.

If that doesn't reveal anything, you could analyze the traffic with something like wireshark (or tcpdump) to get a closer look.

Also, what does your local connection look like:
ifconfig -a
netstat -nr

What is the local IP for your router?

One last thing (though this shouldn't make a difference in OS), do you have your router cloning your computer's MAC?  Maybe there's some ISP weirdness happening that, by chance, just happens to only exhibit itself when you're in Linux.

---

### Post by biosonik on 2008-03-11
At one point yes, my router did clone my computers MAC code although this has been recently changed with no change to the currently problem.

ifconfig result --
```

eth0  Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:192.168.1.140  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18070 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13793 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20095183 (19.1 MB)  TX bytes:1118797 (1.0 MB)
          Interrupt:20 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:104 errors:0 dropped:0 overruns:0 frame:0
          TX packets:104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5200 (5.0 KB)  TX bytes:5200 (5.0 KB)

```

netstat results --
```

Kernel IP routeing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0

```

Previously I have disabled router support of IPv6 and IPv6 on my computer.

System Monitor didn't show anything different BUT WireShark did show something rather strange...

Before a cut the following messages are brought up - 
```

9197	15.550034	192.168.1.1	224.0.0.1	IGMP	V2 Membership Query
9198	16.238080	192.168.1.140	224.0.0.251 IGMP V2 Membership Report
9203	73.264134	192.168.1.140	91.189.89.5	TCP	54402 > http [RST] Seq=1 Win=0 Len=0
9204	78.233130	Buffalo_2e:ee:18		ARP	Who has 192.168.1.140?  Tell 192.168.1.1
9205	78.233149	AsustekC_ae:48:9b		ARP	192.168.1.140 is at XX:XX:XX:XX:XX:XX

```

There are also a number of TCP out of order, Dup ACK and non-http errors

---

### Post by biosonik on 2008-03-11
I installed firestarter (firewall) and although I can't confirm this, it seems fixed. The problem in a way is to do with Ubuntu, but it is not a flaw. More the lack of a firewall which allows everything and anything to enter and exit the computer whereas on Windows, the buildin firewall blocks minor ID requests.

long story short, I remember seeing random blocks on Norton firewall in windows and thought nothing of them, hence why this problem only exists in Linux and not in Windows. 

The problem is - my ISP attempting to block my internet connection - first they identify my computer, check their records and notice i'm going faster than i'm ment to (shh don't tell them) then cut the cord and (guessing) because my router is the primary connection, it reconnects.

Thanks arpad9, I wouldn't have fixed this if you didn't mention the MAC cloning ;)

---

### Post by handydan918 on 2008-03-11
> I installed firestarter (firewall) and although I can't confirm this, it seems fixed. The problem in a way is to do with Ubuntu, but it is not a flaw. More the lack of a firewall which allows everything and anything to enter and exit the computer whereas on Windows, the buildin firewall blocks minor ID requests.
Glad you got it fixed! 
Just wanted to clarify this common misunderstanding about firewals in Linux. The firewalling is done at the kernel level (iptables) and it's there whether of not you have a gui tool like firestarter or(my favorite) guarddog installed.All those gui frontends do is make it possible for us mere mortals to configure iptables.

---

