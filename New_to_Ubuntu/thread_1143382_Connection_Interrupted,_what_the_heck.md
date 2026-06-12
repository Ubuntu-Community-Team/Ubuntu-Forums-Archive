---
title: "Connection Interrupted, what the heck?"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by Entrenched on 2009-04-29
About a third to half of the time when I go to visit a website, any website, I will get the below error message, telling me the connection was interrupted. It is starting to get downright annoying. I will hit the try again button numerous times before the page will actually load. My research says it is an MTU problem, however altering my MTU to a higher rate doesn't seem to do any good. Any thoughts?


Connection Interrupted

The connection to the server was reset while the page was loading.

The network link was interrupted while negotiating a connection. Please try again.

---

### Post by oldsoundguy on 2009-04-29
that could be any of a myriad of issues ranging from a bad card, router, to a bad ISP or ISP connection. (timing out?)

You fail to mention your hardware that is involved.

---

### Post by Dr.Vista on 2009-04-29
> **oldsoundguy said:**
> that could be any of a myriad of issues ranging from a bad card, router, to a bad ISP or ISP connection. (timing out?)

You fail to mention your hardware that is involved.
Something like that was happening to me too.

---

### Post by Entrenched on 2009-04-29
The problem is not hardware, I have used my computer with no problem, and it is new anyhow. It worked fine with Windows XP, the problem is clearly an Ubuntu one. Possibly a bug? Timing out yes, but if so changing the MTU should fix that yes?

The computer is set at a default of 576, that's an absurdly low MTU. However when I change it and restart it is back as it was. Anyone know how to permanently alter the MTU. I don't think this is the problem, since it has the same problem once I change the MTU, but it can't hurt. Thanks.

---

### Post by Dr.Vista on 2009-04-29
> **Entrenched said:**
> The problem is not hardware, I have used my computer with no problem, and it is new anyhow. It worked fine with Windows XP, the problem is clearly an Ubuntu one. Possibly a bug? Timing out yes, but if so changing the MTU should fix that yes?

The computer is set at a default of 576, that's an absurdly low MTU. However when I change it and restart it is back as it was. Anyone know how to permanently alter the MTU. I don't think this is the problem, since it has the same problem once I change the MTU, but it can't hurt. Thanks.
Sometimes I go to a website, lets say google, it says the page is offline but its not possible because I can go to other pages fine. I have to restart my network to make it work.

---

### Post by nandemonai on 2009-04-29
Need some info guys.. What kind of connection would be handy too.. I assume Ethernet?

Start with the output of these commands in terminal:

```
lspci | grep Ethernet
```

```
ifconfig -a
```

```
route
```

```
cat /etc/network/interfaces
```

```
cat /etc/resolv.conf
```

```
ping 91.189.94.156 -c 10
```

```
ping ubuntu.com -c 10
```

[Pastebin]("http://paste.ubuntu.com/") your /var/log/messages log too. That should indicate any problems.

---

### Post by Dr.Vista on 2009-04-29
> **nandemonai said:**
> Need some info guys.. What kind of connection would be handy too.. I assume Ethernet?

Start with the output of these commands in terminal:

```
lspci | grep Ethernet
``````
ifconfig -a
``````
route
``````
cat /etc/network/interfaces
``````
cat /etc/resolv.conf
``````
ping 91.189.94.156 -c 10
``````
ping ubuntu.com -c 10
```[Pastebin]("http://paste.ubuntu.com/") your /var/log/messages log too. That should indicate any problems.
I'm using a wireless connection.
```

Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```

---

### Post by Entrenched on 2009-04-29
Below are the logs the prior poster asked me to post. I hope it indicates any problems, if any. I am thinking it must be a bug of some kind, if anyone can check out the logs and tell me if they see what might be causing this, let me know. Thanks. 


valinor@valinor-desktop:~$ lspci | grep Ethernet
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
valinor@valinor-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0a:eb:81:72:86  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:126296 errors:0 dropped:0 overruns:0 frame:0
          TX packets:116520 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:67625558 (67.6 MB)  TX bytes:11267302 (11.2 MB)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

pan0      Link encap:Ethernet  HWaddr 2e:d7:27:55:48:93  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

valinor@valinor-desktop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
valinor@valinor-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

valinor@valinor-desktop:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 221.232.129.30
nameserver 202.103.44.150
valinor@valinor-desktop:~$ ping 91.189.94.156 -c 10
PING 91.189.94.156 (91.189.94.156) 56(84) bytes of data.
64 bytes from 91.189.94.156: icmp_seq=1 ttl=44 time=447 ms
64 bytes from 91.189.94.156: icmp_seq=3 ttl=44 time=449 ms
64 bytes from 91.189.94.156: icmp_seq=4 ttl=44 time=447 ms
64 bytes from 91.189.94.156: icmp_seq=5 ttl=44 time=447 ms
64 bytes from 91.189.94.156: icmp_seq=6 ttl=44 time=447 ms
64 bytes from 91.189.94.156: icmp_seq=7 ttl=44 time=449 ms
64 bytes from 91.189.94.156: icmp_seq=8 ttl=44 time=447 ms
64 bytes from 91.189.94.156: icmp_seq=10 ttl=44 time=447 ms

--- 91.189.94.156 ping statistics ---
10 packets transmitted, 8 received, 20% packet loss, time 9007ms
rtt min/avg/max/mdev = 447.083/448.001/449.564/0.782 ms
valinor@valinor-desktop:~$ ping ubuntu.com -c 10
PING ubuntu.com (91.189.94.156) 56(84) bytes of data.
64 bytes from vostok.canonical.com (91.189.94.156): icmp_seq=1 ttl=44 time=1329 ms
64 bytes from vostok.canonical.com (91.189.94.156): icmp_seq=2 ttl=44 time=1196 ms
64 bytes from vostok.canonical.com (91.189.94.156): icmp_seq=3 ttl=44 time=1439 ms
64 bytes from vostok.canonical.com (91.189.94.156): icmp_seq=4 ttl=44 time=484 ms
64 bytes from vostok.canonical.com (91.189.94.156): icmp_seq=5 ttl=44 time=688 ms
64 bytes from vostok.canonical.com (91.189.94.156): icmp_seq=6 ttl=44 time=983 ms
64 bytes from vostok.canonical.com (91.189.94.156): icmp_seq=7 ttl=44 time=949 ms
64 bytes from vostok.canonical.com (91.189.94.156): icmp_seq=8 ttl=44 time=1211 ms
64 bytes from vostok.canonical.com (91.189.94.156): icmp_seq=9 ttl=44 time=1090 ms

--- ubuntu.com ping statistics ---
10 packets transmitted, 9 received, 10% packet loss, time 11481ms
rtt min/avg/max/mdev = 484.114/1041.484/1439.836/287.561 ms, pipe 2
valinor@valinor-desktop:~$

---

### Post by nandemonai on 2009-04-30
> **Dr.Vista said:**
> I'm using a wireless connection.
```

Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```

Likely an issue with wireless itself. If you don't think this is the case perhaps do some searches here on the forums and google in relation to your particular card.

---

### Post by nandemonai on 2009-04-30
> **Entrenched said:**
> Below are the logs the prior poster asked me to post. I hope it indicates any problems, if any. I am thinking it must be a bug of some kind, if anyone can check out the logs and tell me if they see what might be causing this, let me know. Thanks. 


valinor@valinor-desktop:~$ lspci | grep Ethernet
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
valinor@valinor-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0a:eb:81:72:86  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:126296 errors:0 dropped:0 overruns:0 frame:0
          TX packets:116520 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:67625558 (67.6 MB)  TX bytes:11267302 (11.2 MB)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

pan0      Link encap:Ethernet  HWaddr 2e:d7:27:55:48:93  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

valinor@valinor-desktop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
valinor@valinor-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

valinor@valinor-desktop:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 221.232.129.30
nameserver 202.103.44.150
valinor@valinor-desktop:~$ ping 91.189.94.156 -c 10
PING 91.189.94.156 (91.189.94.156) 56(84) bytes of data.
64 bytes from 91.189.94.156: icmp_seq=1 ttl=44 time=447 ms
64 bytes from 91.189.94.156: icmp_seq=3 ttl=44 time=449 ms
64 bytes from 91.189.94.156: icmp_seq=4 ttl=44 time=447 ms
64 bytes from 91.189.94.156: icmp_seq=5 ttl=44 time=447 ms
64 bytes from 91.189.94.156: icmp_seq=6 ttl=44 time=447 ms
64 bytes from 91.189.94.156: icmp_seq=7 ttl=44 time=449 ms
64 bytes from 91.189.94.156: icmp_seq=8 ttl=44 time=447 ms
64 bytes from 91.189.94.156: icmp_seq=10 ttl=44 time=447 ms

--- 91.189.94.156 ping statistics ---
10 packets transmitted, 8 received, 20% packet loss, time 9007ms
rtt min/avg/max/mdev = 447.083/448.001/449.564/0.782 ms
valinor@valinor-desktop:~$ ping ubuntu.com -c 10
PING ubuntu.com (91.189.94.156) 56(84) bytes of data.
64 bytes from vostok.canonical.com (91.189.94.156): icmp_seq=1 ttl=44 time=1329 ms
64 bytes from vostok.canonical.com (91.189.94.156): icmp_seq=2 ttl=44 time=1196 ms
64 bytes from vostok.canonical.com (91.189.94.156): icmp_seq=3 ttl=44 time=1439 ms
64 bytes from vostok.canonical.com (91.189.94.156): icmp_seq=4 ttl=44 time=484 ms
64 bytes from vostok.canonical.com (91.189.94.156): icmp_seq=5 ttl=44 time=688 ms
64 bytes from vostok.canonical.com (91.189.94.156): icmp_seq=6 ttl=44 time=983 ms
64 bytes from vostok.canonical.com (91.189.94.156): icmp_seq=7 ttl=44 time=949 ms
64 bytes from vostok.canonical.com (91.189.94.156): icmp_seq=8 ttl=44 time=1211 ms
64 bytes from vostok.canonical.com (91.189.94.156): icmp_seq=9 ttl=44 time=1090 ms

--- ubuntu.com ping statistics ---
10 packets transmitted, 9 received, 10% packet loss, time 11481ms
rtt min/avg/max/mdev = 484.114/1041.484/1439.836/287.561 ms, pipe 2
valinor@valinor-desktop:~$

First thing I notice, as you mentioned above is that your MTU is not set correctly for an Ethernet connection. I'm no expert on MTU but I assume it's auto configured hence that could indicate an issue with your interface.

You can manually set MTU by adding a line underneath eth0 in /etc/network/interfaces (ie mtu 1492 or 1500). That being said I'm assuming you're using network manager to setup your connection hence there being no entry in your /etc/network/interfaces file. In that case you should just be able to change the MTU in your connection settings under network manager.

What version are you using btw? 8.04 / 8.10 / 9.04? And is this a static or DHCP setup?

If you're using 8.10 you may need to delete the auto connection and recreate one to get around a bug in Network Manager in Intrepid.

Everything else looks ok but your ping results are a little odd..

Fair bit of packet loss on your IP ping and a much higher latency on your DNS ping yet lower packet loss..

I'm actually thinking, based on those pings that you could have a DNS issue ISP side.

One other thing to check would be the output from ethtool. You may need to install it first though as I'm not sure it's default.

```
sudo apt-get install ethtool
```

```
sudo ethtool eth0
```

---

### Post by Dr.Vista on 2009-04-30
> **nandemonai said:**
> Likely an issue with wireless itself. If you don't think this is the case perhaps do some searches here on the forums and google in relation to your particular card.
Seems the problem is fixed for now. I don't know what was going on.

---

### Post by nandemonai on 2009-04-30
> **Dr.Vista said:**
> Seems the problem is fixed for now. I don't know what was going on.

With WiFi there are numerous variables to consider. Signal strength, interference and so on.

Was most likely something along those lines.

---

### Post by Skrynesaver on 2009-04-30
Hi, increasing the MTU(**M**aximum **T**ransfer **U**nit) is rarely the solution, it determines the packet size, and if the packet size is too large you end up with split packets being reformed by the network code.

However decreasing the MTU can often improve throughput, depending on the network topologies between you and the outside world.
```

   16 Mbps Token Ring       17914
   4 Mbps Token Ring         4464
   FDDI                             4352
   Ethernet                        1500
   IEEE 802.3/802.2           1492
   PPPoE (WAN Miniport)    1480
   X.25                              576

```

---

### Post by nandemonai on 2009-04-30
> **Skrynesaver said:**
> Hi, increasing the MTU(**M**aximum **T**ransfer **U**nit) is rarely the solution, it determines the packet size, and if the packet size is too large you end up with split packets being reformed by the network code.

However decreasing the MTU can often improve throughput, depending on the network topologies between you and the outside world.
```

   16 Mbps Token Ring       17914
   4 Mbps Token Ring         4464
   FDDI                             4352
   Ethernet                        1500
   IEEE 802.3/802.2           1492
   PPPoE (WAN Miniport)    1480
   X.25                              576

```

True, but it's odd that his MTU is being set at 576 no? ala X.25?

---

### Post by Entrenched on 2009-04-30
Well I fixed the problem. It turns out the problem is the MTU. I went into network manager and changed it to 1492, and now the problem has disappeared. Now the only problem is, for some reason, when I turn of the computer and re boot, the MTU reverts back in network manager, and I have to manually change it again. Anyone know how to make the change permanent? I thought changing it in Network manager would do just that.

A for the eth tool, the commands provide for use in terminal services did not work, as it keeps saying the download directory is locked, or some such. Shame, I was hoping to get the ethtool in case of future problems.

---

### Post by nandemonai on 2009-04-30
> **Entrenched said:**
> Well I fixed the problem. It turns out the problem is the MTU. I went into network manager and changed it to 1492, and now the problem has disappeared. Now the only problem is, for some reason, when I turn of the computer and re boot, the MTU reverts back in network manager, and I have to manually change it again. Anyone know how to make the change permanent? I thought changing it in Network manager would do just that.

A for the eth tool, the commands provide for use in terminal services did not work, as it keeps saying the download directory is locked, or some such. Shame, I was hoping to get the ethtool in case of future problems.

If you're using Intrepid as I suspect then refer to my previous post.

"If you're using 8.10 you may need to delete the auto connection and recreate one to get around a bug in Network Manager in Intrepid."

If you had synaptic or something else open that uses apt (such as add/remove) while trying to install ethtool you'll get a lock issue. Make sure Synaptic / Add/Remove / Update Manager is not open when using apt-get in terminal.

Alternativly you could just install ethtool via Synaptic.

---

