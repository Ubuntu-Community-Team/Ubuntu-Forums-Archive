---
title: "Gutsy networking is Slowing my pc"
date: 2007-11-04
forum: Networking &amp; Wireless
---

### Post by WinterWeaver on 2007-11-04
Hey guys,

I'm having a problem with the networking in Gutsy.

No-Problem >> I can connect to the internet without problems.

Is Problem >> The network slows my PC drastically! When I have the network cable plugged in, and I try open the terminal or gedit or any other app... it takes 20 seconds plus O.o....

when I unplug the network cable, all apps launches under 2 seconds.

What can this be??

oh.. and btw, I believe this might be tied with my router, cause I went to visit a buddy of mine, and on his network (also router), everything was super fast.

any ideas?

Here is some terminal commands, in case you need them:

Route:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
link-local      *               255.255.0.0     U     1000   0        0 eth0
10.0.0.0        *               255.0.0.0       U     0      0        0 eth0
default         10.0.0.2        0.0.0.0         UG    0      0        0 eth0

```

Route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
10.0.0.0        0.0.0.0         255.0.0.0       U     0      0        0 eth0
0.0.0.0         10.0.0.2        0.0.0.0         UG    0      0        0 eth0

```

sudo ifdown -v eth0
```
ifdown: interface eth0 not configured
```

sudo ifup -v eth0
```
Ignoring unknown interface eth0=eth0.
```

ifconfig
> eth0      Link encap:Ethernet  HWaddr 00:13:8F:32:C9:97  
          inet addr:10.0.0.7  Bcast:255.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::213:8fff:fe32:c997/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2081 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1820 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2026994 (1.9 MB)  TX bytes:322712 (315.1 KB)
          Interrupt:22 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5248 (5.1 KB)  TX bytes:5248 (5.1 KB)


Thanks in advance,

WW

---

### Post by WinterWeaver on 2007-11-04
I just had a thought.

I tried to disable networking (via Network Manager) and I opened gedit >> 1 or 2 secs

I enabled networking again, opened gedit again >> 15 - 20 secs

??

---

### Post by Computer Guru on 2007-11-04
dude, stop spamming!

---

### Post by WinterWeaver on 2007-11-04
> **Computer Guru said:**
> dude, stop spamming!

errrr... lol.... I wasn't spamming.... and if you don't have anything constructive to actually help with a request, then please don't post.

---

### Post by Computer Guru on 2007-11-04
lol, 3 or 4 different posts on the same topic in different threads looks like spamming to me :)

keeping the board clutter-free is pretty constructive, don't you think?

anyway, disable ipv6.

---

### Post by WinterWeaver on 2007-11-04
The topics are not related... apparently you didn't even try read them.

The other topic is even a couple of days old... and I merely replied on someone elses post... Whilst at the same time creating a new post on a different problem.

So please read threads first, before assuming that I just spam the forum.

ps: have already tried disabling ipv6 with no joy.

---

### Post by Computer Guru on 2007-11-04
Did you restart your PC after disabling?

Restarting the networking service is not enough.

You also have to remove all IPv6 entries from your hosts list.

---

### Post by WinterWeaver on 2007-11-04
yes, I did restart, but no, I didn't know I should disable it in the hosts also.

where is the file located that I should edit?

EDIT: nvm... found it via search

---

