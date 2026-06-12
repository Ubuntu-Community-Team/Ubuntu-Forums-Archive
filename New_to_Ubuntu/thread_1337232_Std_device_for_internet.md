---
title: "Std device for internet"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by mbzn on 2009-11-25
Hi

I have a linksys router that i use for my home network (LAN), I use my phone as a modem to connect to the internet, my problem is that when my PC is plugged in to the router it seem to be looking for the internet connection there(times out). as soon as i unplug the Lan cable to the router the iternet works without problems.
Is there a way to tell the pc to use the phone instead while the router is still conected?

Thanx for any advice

---

### Post by ukripper on 2009-11-25
can you plug your lan cable back and post output of the folowing commands:
```
lshw -C network
```

```
ifconfig
```

---

### Post by mbzn on 2009-11-25
sudo lshw -C network
[sudo] password for me: 
  *-network               
       description: Ethernet interface
       product: RTL-8110SC/8169SC Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:03:05.0
       logical name: eth1
       version: 10
       serial: 00:1d:7d:9c:f0:f4
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.101 latency=64 link=yes maxlatency=64 mingnt=32 module=r8169 multicast=yes port=MII speed=100MB/s
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 2e:35:79:08:7a:71
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

ifconfig
eth1      Link encap:Ethernet  HWaddr 00:1d:7d:9c:f0:f4  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:7dff:fe9c:f0f4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2200 (2.2 KB)  TX bytes:9086 (9.0 KB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2418 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2418 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:194946 (194.9 KB)  TX bytes:194946 (194.9 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:41.18.69.0  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:5731 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4904 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:5659019 (5.6 MB)  TX bytes:471181 (471.1 KB)

---

### Post by ukripper on 2009-11-25
according to the output it seems your both networks are  up. So are you using your router just on LAN or are internet sharing among other machines as well?

Can you ping your local gateway while connected

---

### Post by mbzn on 2009-11-25
The router is not connected to the internet. 
So with both pluged in (router and phone)
ping [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)

Then i unpluged the router and...
ping [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (209.85.229.147) 56(84) bytes of data.
64 bytes from ww-in-f147.1e100.net (209.85.229.147): icmp_seq=1 ttl=52 time=289 ms
64 bytes from ww-in-f147.1e100.net (209.85.229.147): icmp_seq=2 ttl=52 time=268 ms
64 bytes from ww-in-f147.1e100.net (209.85.229.147): icmp_seq=3 ttl=52 time=297 ms
64 bytes from ww-in-f147.1e100.net (209.85.229.147): icmp_seq=4 ttl=52 time=255 ms
^C
--- [www.l.google.com](www.l.google.com) ping statistics ---
5 packets transmitted, 4 received, 20% packet loss, time 4004ms
rtt min/avg/max/mdev = 255.893/277.728/297.117/16.399 ms

I believe the lost packet was when i pressed 'Ctrl-c'

---

### Post by mbzn on 2009-11-25
Sorry no internet sharing, just for files at home. I know a switch would have worked perfect but the router was free...

---

### Post by ukripper on 2009-11-25
Can you go in System-->preferences-->Network connections. Select modem/or whatever it is called there and find option there to make modem set to default for internet.

---

### Post by mbzn on 2009-11-25
There is no option for this. Not there any way. Is there another way to do this?

---

### Post by VastOne on 2009-11-25
> **mbzn said:**
> Hi

I have a linksys router that i use for my home network (LAN), I use my phone as a modem to connect to the internet, my problem is that when my PC is plugged in to the router it seem to be looking for the internet connection there(times out). as soon as i unplug the Lan cable to the router the iternet works without problems.
Is there a way to tell the pc to use the phone instead while the router is still conected?

Thanx for any advice

If you disable the DHCP on the router, it becomes a simple switch. It seems to me that the setup of the router is the issue in that it may be trying to acquire an IP from an ISP or elsewhere. I would check the router settings thoroughly.

---

### Post by ukripper on 2009-11-25
through terminal run this:
```
sudo apt-get install gnome-ppp
```

once installed go to Applications-->Internet-->gnome ppp

and then  select setup and options and find there select auto reconnect.

see if that works

---

### Post by QLee on 2009-11-25
[QUOTE=VastOne]If you disable the DHCP on the router, it becomes a simple switch. [/QUOTE]

A correction on this, if you disable DHCP on the router it becomes just a router, that does not turn it into a switch, it turns it into a router without DHCP.

You probably are meaning to use the term "switch" in a more generic manner but I don't want people to misunderstand.

---

### Post by mbzn on 2009-11-25
Hi

As for Gnome-PPP This looks like a work around to getting my phone connected to the internet, i have no problem doing this though...

The router gives me the following options:
Obtain IP auto... (DHCP)- Currently
Static IP
PPPoE
RAS
PPTP
Heart beat signal
L2TP

Static ip does not correct my problem, I just want the PC to connect through my phone rather than trying through the router witch is does currently. ie I want my phone to have priority over the router..

Thanks for the input so far.

---

