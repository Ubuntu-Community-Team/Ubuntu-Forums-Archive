---
title: "network connection stopped working"
date: 2005-09-16
forum: Networking &amp; Wireless
---

### Post by detochka on 2005-09-16
](*,)  hello

it's the weirdest thing in the world. my internet just stopped working out of a sudden.

[SIZE=4]_ifconfig: _[/SIZE]
*eth0*

Link encap:Ethernet HWaddr 00:06:29:F7:3C:7B
inet6 addr: fe80::206:29ff:fef7:3c7b/64 Scope:Link
UP BROADCASTRUNNING MULTICAST MTU:1500 Metric:1
RX packets:46 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:5343 (5.2 Kib) TX bytes:0 (0.0 b)

*lo*
Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:11523 errors:0 dropped:0 overruns:0 frame:0
TX packets:11523 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes: 3195438 (3.0 MiB) TX bytes:3195438 (3.0 MiB)


I tried plugging the same cable into other machines, and it works fine, so i have no clue what to do.

Please help

---

### Post by KingBahamut on 2005-09-16
Did you configure it for IPv6? 

Thats what im seeing or maybe my glasses arent thick enough. =)

---

### Post by detochka on 2005-09-16
>>Did you configure it for IPv6?

If I knew what you're talking about, it could answer you. I just know that it worked perfectly fine for a long long time, and then it stopped.  :???:

---

### Post by KingBahamut on 2005-09-16
> [b]eth0

Link encap:Ethernet HWaddr 00:06:29:F7:3C:7B
inet6 addr: fe80::206:29ff:fef7:3c7b/64 Scope:Link
UP BROADCASTRUNNING MULTICAST MTU:1500 Metric:1
RX packets:46 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:5343 (5.2 Kib) TX bytes:0 (0.0 b)[/b]


This is what bothers me, your address is **inet6 addr: fe80::206:29ff:fef7:3c7b/64** 

Have you made any network changes recently? has your network changed at all where you are that you know of?

---

### Post by mlomker on 2005-09-16
I assume you're using DHCP since there's no address.

```

sudo dhclient eth0

```

What does that give you?

---

### Post by detochka on 2005-09-16
<>Have you made any network changes recently? has your network changed at all <>where you are that you know of?


There were no network changes at all. I didnt change anything AT ALL...

---

### Post by detochka on 2005-09-16
[SIZE=4]sudo dhclient eth0[/SIZE]



sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:06:29:f7:3c:7b
Sending on LPF/eth0/00:06:29:f7:3c:7b
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6

---

### Post by mlomker on 2005-09-16
> DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6

The end of that is what I needed to see, not the beginning.  Did it give up or get an address?

---

### Post by detochka on 2005-09-16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
 DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
 DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
 DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
 DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
 DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
 DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1

No DHCPOFFERS recieved
No working leases in persistent database - sleeping

---

### Post by mlomker on 2005-09-16
Have you run an **apt-get upgrade** recently?  I worked with a guy for hours yesterday on a similar problem and he had to reinstall...must have deleted an important file somewhere.

In any case, why don't you post your /etc/network/interfaces file and we'll see if there's anything unusual in there.  Do you know what kind of card it is?  **dmesg | grep eth0** might tell us something.

---

### Post by detochka on 2005-09-16
[SIZE=4]dmesg | grep eth0[/SIZE]

el100: eth0:e100_probe: add 0xfeaff000, irq 22, MAC addr 00:06:29:F7:3C:7B
el100: eth0:e100_watchdog: link up, 100Mbps, full-duplex
etho: no IPv6 routes present
NETDEV WATCHDOG: eth0: transmit timed out
el100: eth0:e100_watchdog: link up, 100Mbps, full-duplex
NETDEV WATCHDOG: eth0: transmit timed out
el100: eth0:e100_watchdog: link up, 100Mbps, full-duplex
NETDEV WATCHDOG: eth0: transmit timed out
el100: eth0:e100_watchdog: link up, 100Mbps, full-duplex

---

### Post by detochka on 2005-09-16
1. I havent run [SIZE=4]upgrade [/SIZE]at all

2. [SIZE=4]/etc/network/interfaces[/SIZE]
# The loopback network interface
auto lo
iface lo inet loopback

# List of hotpluggable network interfaces
mapping hotplug
               script grep
               map eth0

# The promary network interface
iface eth0 inet dhcp

auto eth0

---

### Post by mlomker on 2005-09-16
The config looks fine...not modified at all.  The dmesg output looks like you've just plugged and unplugged it a few times...nothing interesting there.

This should manually restart everything related to the card.  Beyond that I'd try booting to a livecd (Knoppix perhaps) and seeing if things work okay.  If so then the problem may be too difficult to find and reinstalling would be the way to go.

```

su
rmmod el100
modprobe el100
ifconfig eth0 up
dhclient eth0

```

---

### Post by detochka on 2005-09-16
su
[SIZE=4]rmmod el100[/SIZE]
ERROR: Module el100 doesnot exist in /proc/modules


[SIZE=4]modprobe el100[/SIZE]
FATAL:  Module el100 not found


That's a good idea, though to try booting from a live CD... I'll defintiely give it a try ;-)

---

### Post by mlomker on 2005-09-16
[QUOTE=detochka]su
[SIZE=4]rmmod el100[/SIZE]
ERROR: Module el100 doesnot exist in /proc/modules
[/quote]

Maybe it should have been **e100**.  **lsmod | grep 100** should tell us.

---

### Post by detochka on 2005-09-17
](*,)  any other suggestions?

---

### Post by mlomker on 2005-09-17
[QUOTE=detochka]](*,)  any other suggestions?[/QUOTE]

If past experience is any indication...you will need to reinstall at this point.  We've tried everything that is rational.

---

### Post by detochka on 2005-09-18
My friend told me that i can re-install some modules that might be bad. Im not quite sure what he's talking about, so if someone could help me with that, if you think that's legitimate... = )

---

### Post by mlomker on 2005-09-18
[QUOTE=detochka]My friend told me that i can re-install some modules that might be bad. Im not quite sure what he's talking about, so if someone could help me with that, if you think that's legitimate... = )[/QUOTE]

Sure, if you can figure out which ones to replace and a safe way to replace them.  The diagnostics that we did give no indication of where the problem is.

Perhaps you should invite your friend over to take a look?  ;)

---

