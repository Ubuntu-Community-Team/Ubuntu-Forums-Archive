---
title: "Ethernet connection working at one point; now it's not"
date: 2007-08-23
forum: Networking &amp; Wireless
---

### Post by kyleflan on 2007-08-23
Whenever I first installed Ubuntu on my new machine, the internet connection worked flawlessly. However, I edited /etc/network/interfaces to configure my machine with a static IP since it is going to be a server. I must have done something wrong, because now I can't even ping my router even though going through System>Network shows the correct gateway IP address.

 Does anyone have the default interfaces file so I can replace whatever I have with that to see if that works. And if not, do you guys have any suggestions? I'm not a huge Linux n00b, so, hopefully, I can understand any instructions that might help me out.

Thanks in advance,
Kyle

---

### Post by Wicca on 2007-08-23
Hi,

Can you post your /etc/network/interfaces here?

Also, can you post the output (in terminal) of
```
ifconfig
```

---

### Post by kyleflan on 2007-08-23
/etc/network/interfaces

```
auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.0.4
netmask 255.255.255.0
gateway 192.168.0.1



auto eth0
```

ifconfig

```
eth0     Link encap:Ethernet   HWaddr  00:E0:7D:CF:De:00
UP BROADCAST MULTICAST   MTU:1500   Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0  (0.0 b)    TX bytes:0   (0.0 b)
Interrupt:11 Base address:0x6000

eth0:avah  Link encap:Ethernet HWaddr   00:E0:7D:CF:DE:00
inet addr:169.254.7.192  Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST MULTICAST   MTU:1500 Metric:1
Interrupt:11 Base address:0x6000

lo       encap:Local Loopback
inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr:  ::1/128 Scope:Host
UP LOOPBACK RUNNING   MTU:16436  Metric:1
RX packets:1205  errors:0 dropped:0 overruns:0 frame:0
TX packets 1205  errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:105988 (103.5 KiB)   TX bytes:105988 (103.5 KiB)

```

Sorry if there are any typos. I had to type all of that out from one monitor to another.

Thanks again for the help.

---

### Post by Wicca on 2007-08-23
Hi,
<EDIT>
 Sorry,

I am completely wrong, removed the message.
Have you tried to cold boot your PC, that is, unplug the powercord for about 15 sec?
This helped som people who had similar problems

---

### Post by kyleflan on 2007-08-23
Tried the cold boot. No luck.

I decided to try setting a static IP through the network manager. (I have my router set to assign 192.168.0.4 to the machine.)

Now ifconfig shows this,

```
eth0     Link encap:Ethernet   HWaddr  00:E0:7D:CF:De:00
inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
UP BROADCAST MULTICAST   MTU:1500   Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0  (0.0 b)    TX bytes:0   (0.0 b)
Interrupt:11 Base address:0x6000

lo       encap:Local Loopback
inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr:  ::1/128 Scope:Host
UP LOOPBACK RUNNING   MTU:16436  Metric:1
RX packets:1205  errors:0 dropped:0 overruns:0 frame:0
TX packets 1205  errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:105988 (103.5 KiB)   TX bytes:105988 (103.5 KiB)

```

All the settings seem correct to me (except I'm not sure what Bcast:192.168.0.255 is) but I can neither ping to or from the machine. 

Any other ideas?

Thanks again.

---

### Post by Wicca on 2007-08-23
Hi again,

It might be the avahi deamon giving you an address.

Please restart your network:

```
sudo /etc/init.d/networking restart
```
and do a **ifconfig -a** once again?

---

### Post by kyleflan on 2007-08-23
sudo /etc/init.d/networking restart outputs

```
* Reconfiguring network interfaces...
SIOCDELR: No such process
                                                [OK]
```

ifconfig -a

```

eth0     Link encap:Ethernet   HWaddr  00:E0:7D:CF:DE:00
inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
UP BROADCAST MULTICAST   MTU:1500   Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0  (0.0 b)    TX bytes:0   (0.0 b)
Interrupt:11 Base address:0x6000

lo      Link encap:Local Loopback
inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr:  ::1/128 Scope:Host
UP LOOPBACK RUNNING   MTU:16436  Metric:1
RX packets:1205  errors:0 dropped:0 overruns:0 frame:0
TX packets 1205  errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:105988 (103.5 KiB)   TX bytes:105988 (103.5 KiB)

```

Give you any ideas?

---

### Post by Wicca on 2007-08-23
> Give you any ideas?

Well, not really. I am not an expert on this.

What i do not understand is why there is no traffic going from (and to) eth0, while your network seems to be up. I assume there is a working cable connected to the right interface (sorry for asking , it is not that i underestimate your capabilities ;-))

 What is the output of **route -n** ?

---

### Post by kyleflan on 2007-08-23
Since a static IP wasn't working for me, I went back to DHCP in the Network Manager and I restarted the network. This is what I get:

```
kyle@SERVER:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 6837
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:e0:7d:cf:de:00
Sending on   LPF/eth0/00:e0:7d:cf:de:00
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.1 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:e0:7d:cf:de:00
Sending on   LPF/eth0/00:e0:7d:cf:de:00
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ]
```

Maybe that can give an idea as to what's wrong?

Once again, I appreciate the help.

---

### Post by kyleflan on 2007-08-23
> **Wicca said:**
> Well, not really. I am not an expert on this.

What i do not understand is why there is no traffic going from (and to) eth0, while your network seems to be up. I assume there is a working cable connected to the right interface (sorry for asking , it is not that i underestimate your capabilities ;-))

 What is the output of **route -n** ?

Haha, yes, there is a working cable. Here's route -n

```
Kernel IP routing table
Destination          Gateway          Genmask         Flags  Metric  Ref        Use  Iface
169.254.0.0        0.0.0.0            255.255.0.0    U        0          0           0       eth0
0.0.0.0                0.0.0.0            0.0.0.0            U        1000    0           0       eth0


```

And if these specs matter:

I'm using a 2wire 2701HG-B DSL modem/router (not sure if that's the correct terminology) and the gateway is 192.168.0.1. The other computers on the network work fine, which is how I'm on these forums.

---

### Post by Wicca on 2007-08-23
There it is again, the 169.254.x.x address.

Your problem looks the same as mentioned in this thread:

[http://ubuntuforums.org/showthread.php?t=499361&page=4]("http://ubuntuforums.org/showthread.php?t=499361&page=4")

go check it.

So the solution could be deactivating the avahi-daemon:
```
sudo update-rc.d -f avahi-daemon remove
```
reboot.

I hope that helps.

---

### Post by kyleflan on 2007-08-23
I will try that. I won't be home until tomorrow night, but I'll post then and let you know how it worked out.

Thanks again for your help.

---

### Post by kyleflan on 2007-08-25
I tried your suggestion Wicca, however, when I do ifconfig, I still have an eth0:avah with that 169.254.7.192 IP address. Do you know of anything else that causes this?

---

### Post by kyleflan on 2007-08-26
Wicca, I finally got it to work. I had to restart my router a couple of times, but I got it to work.

Thanks again for your help.

---

### Post by Wicca on 2007-08-26
Hi,

Hmmm.... I wonder what did the trick.

Anyway, it works, and hopefully it will keep doing that.

Enjoy!

---

