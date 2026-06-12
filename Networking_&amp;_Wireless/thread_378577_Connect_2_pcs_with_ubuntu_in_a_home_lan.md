---
title: "Connect 2 pcs with ubuntu in a home lan"
date: 2007-03-07
forum: Networking &amp; Wireless
---

### Post by rogorido on 2007-03-07
Hi,

I need your help because I'm getting mad. I fail to configure a small home network. It's incredible. 

I do following steps:

1) PC1
ifconfig eth0 192.168.1.1 netmask 255.255.255.0 up

/etc/hosts
127.0.0.1 localhost.localdomain localhost
 192.168.1.1 igoriano.midominio.com igoriano
 192.168.1.2 laptop.midominio.com laptop

2) pc2:
 ifconfig eth0 192.168.1.2 netmask 255.255.255.0 up

/etc/hosts
127.0.0.1 localhost.localdomain localhost
 192.168.1.2 laptop.midominio.com laptop
 192.168.1.1 igoriano.midominio.com igoriano

With this configuration pc1 does not see pc2 and pc1 says:
PING laptop.midominio.com (192.168.1.2) from 192.168.1.1 eth0: 56(84) bytes of data.
 ping: sendmsg: Operation not permitted

Thanx

---

### Post by codered867 on 2007-03-07
So I take it that you are not using a switch or router? Are you plugging an Ethernet cable from one directly to the other? If so is it a crossover cable?

---

### Post by chili555 on 2007-03-07
Do you connect to a router or...? Usually, the IP address of the router is 192.168.1.1, not one of the clients. Please tell us a bit more about your setup. You might include the output of route -n. Thanks.

---

### Post by rogorido on 2007-03-07
> **codered867 said:**
> So I take it that you are not using a switch or router? Are you plugging an Ethernet cable from one directly to the other? If so is it a crossover cable?


thanx for you answers.
yes it is a crossover cable.
It's really strange.

I don't think its a hardware problem, but i'm really desperate with this.

On the pc1 

root@igoriano:/home/igor# ethtool eth0
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 10Mb/s
        Duplex: Half
        Port: MII
        PHYAD: 32
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: d
        Current message level: 0x00000007 (7)
        Link detected: yes

NOTE: link detected yes

But on pc2: the same but link detected NO

---

### Post by Mr. C. on 2007-03-07
Two Ethernet devices must establish link with each other.  They are almost always set to auto-negotiate their speed and duplex settings, however, many older pieces of hardware had all sorts of compatibility issues, and this was especially noticeable in direct cable situations.

Your system reports:

Advertised auto-negotiation: Yes
Speed: 10Mb/s
Duplex: Half

It told the other system it can auto-negotiate the speed and duplex; however, there is no guarantee the other system can, or did properly.  You need to be sure the speed/duplex matches in this case.  10Mb/half is correct for a cross-over cable situation.

Get a switch, and you will get reliable 100Mb/full duplex.

Otherwise, force the speed/duplex of the second system to 10/half no-auto.

MrC

---

### Post by rogorido on 2007-03-07
> **Mr. C. said:**
> 
It told the other system it can auto-negotiate the speed and duplex; however, there is no guarantee the other system can, or did properly.  You need to be sure the speed/duplex matches in this case.  10Mb/half is correct for a cross-over cable situation.

Get a switch, and you will get reliable 100Mb/full duplex.

Otherwise, force the speed/duplex of the second system to 10/half no-auto.

MrC

Thanx for your help.

It's incredible that such a simple thing can be so complicated. I'm using linux for 6 or 7 years and never found such a complicated (and absurd) situation...

I changed with ethtool the parameters and it looks like:
pc1
[the same]
pc2
       Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Advertised auto-negotiation: No
        Speed: 10Mb/s
        Duplex: Half
        Port: MII
        PHYAD: 32
        Transceiver: internal
        Auto-negotiation: off
        Supports Wake-on: pumbg
        Wake-on: d
        Current message level: 0x00000007 (7)
        Link detected: no


And it does NOT work.
But maybe it's another problem... Maybe it's the network (hosts, etc.) not well configured...

---

### Post by rogorido on 2007-03-07
maybe I should be more complete (although I think that should not be the problem...)

PC1 is connected to the internet over a usb modem. That creates the following ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:40:F4:92:97:A1
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:f4ff:fe92:97a1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:468 (468.0 b)
          Interrupt:177 Base address:0xec00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

nas0      Link encap:Ethernet  HWaddr 00:0E:50:D5:94:7F
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:50ff:fed5:947f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12651 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11614 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:12253360 (11.6 MiB)  TX bytes:1591652 (1.5 MiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:88.19.99.157  P-t-P:192.168.153.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:12372 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11330 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:12143935 (11.5 MiB)  TX bytes:1216694 (1.1 MiB)

---

### Post by Mr. C. on 2007-03-07
> **rogorido said:**
> 
It's incredible that such a simple thing can be so complicated. I'm using linux for 6 or 7 years and never found such a complicated (and absurd) situation...


Really the problem is that you are trying to do something that is know to be problematic.  These cards are not designed to work in this fashion optimally.  Often one can get things to work just fine; but because users don't understand how this stuff works, it causes endless frustration.

> **rogorido said:**
> 
        Link detected: no

And it does NOT work.
But maybe it's another problem... Maybe it's the network (hosts, etc.) not well configured...

Your problem (now) is that you have NO LINK.  This means either a) wrong cable type, b) card is disabled, c) cable is unplugged, d) broken cable.

Examine the link lights on the back of the cards (if your cards have such).   The will tell you when there is a link connection.

> **rogorido said:**
> 
But maybe it's another problem... Maybe it's the network (hosts, etc.) not well configured...


This has absolutly nothing to do with hosts, or any other higher level networking.  You don't have link.

MrC

---

### Post by rogorido on 2007-03-07
> **Mr. C. said:**
> 
Examine the link lights on the back of the cards (if your cards have such).   The will tell you when there is a link connection.



This has absolutly nothing to do with hosts, or any other higher level networking.  You don't have link.

MrC

That's the problem: 
PC1 tells me: 
 Link detected: yes

PC2:
 Link detected: no

???

---

### Post by Mr. C. on 2007-03-07
Obviously one of them is reporting incorrect information.

This is a hardware problem; seek solutions from those I gave you previously.

MrC

---

### Post by rogorido on 2007-03-07
> **Mr. C. said:**
> Obviously one of them is reporting incorrect information.

This is a hardware problem; seek solutions from those I gave you previously.

MrC

maybe you're right...

anyway: 
1) thanx for your help

2) I want to do sth as easy as:
I have 2 pcs with ubuntu. PC1 is connected to internet with a stupid speedtouch modem (not easy to configure in linux; is a usb modem). I want to have have also in PC2 internet connection (through PC1? that was the original idea...). What is the best solution? A switch? Have you maybe a link where I can find information?

thanks in advance,

---

### Post by Mr. C. on 2007-03-07
If your SpeedTouch does not provide routing/nat service, you need a setup like this:

[http://i.dslr.net/sharing/share_linksys.gif](http://i.dslr.net/sharing/share_linksys.gif)

If you want to learn to, and configure your PC1 as a router, you should still get a switch to place between PC1 and PC2 :

[http://i.dslr.net/sharing/share_natmodem.gif](http://i.dslr.net/sharing/share_natmodem.gif)

Learn about routing in general. See Week 6 notes at: [http://cis68c2.mikecappella.com/calendar.php](http://cis68c2.mikecappella.com/calendar.php)

Here are all sorts of pictures and explanations:

[http://www.dslreports.com/pictures#8](http://www.dslreports.com/pictures#8)

The easiest is the hardare Firewall/NAT/Router appliance, typically just called "routers".  They are cheap, and easy to setup, and most all today don't care what cable type (straight or crossover) you use.

MrC

---

### Post by rogorido on 2007-03-07
> **Mr. C. said:**
> If your SpeedTouch does not provide routing/nat service, you need a setup like this:

[http://i.dslr.net/sharing/share_linksys.gif](http://i.dslr.net/sharing/share_linksys.gif)

If you want to learn to, and configure your PC1 as a router, you should still get a switch to place between PC1 and PC2 :

[http://i.dslr.net/sharing/share_natmodem.gif](http://i.dslr.net/sharing/share_natmodem.gif)

Learn about routing in general. See Week 6 notes at: [http://cis68c2.mikecappella.com/calendar.php](http://cis68c2.mikecappella.com/calendar.php)

Here are all sorts of pictures and explanations:

[http://www.dslreports.com/pictures#8](http://www.dslreports.com/pictures#8)

The easiest is the hardare Firewall/NAT/Router appliance, typically just called "routers".  They are cheap, and easy to setup, and most all today don't care what cable type (straight or crossover) you use.

MrC

thanks a lot!!

---

