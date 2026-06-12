---
title: "Remote Access via HTTP, SSH; Dis-connectivity"
date: 2007-03-07
forum: Networking &amp; Wireless
---

### Post by moon2js on 2007-03-07
I'm trying to do daily work remotely (from office, coffeeshop, etc) on an Ubuntu box setup at home. I frequently can't access it and I'm wondering if someone could point out some troubleshooting methods.

Remote access will work for five minutes and then be down for the next five minutes. Yesterday (after replacing the ethernet cable) it worked flawlessly for hours, but today it's back to sometime up, sometimes down. And by up, I mean http/ssh works great (for five to fifteen minutes), and by down, connection timeouts across the board.

My setup is Edgy running ssh/http servers without firewall, ports forwarded via router, and myusername.homeip.net provided by dyndns.com. My ISP is Verizon DSL (so I access http via 8080).

Does Edgy have software issues I can fix or does anyone know some good Google search terms I can try?

Config files posted upon request, that is if I can get to it within five minutes.

**UPDATE: This was resolved by updating the firmware on the router. The manufacturer released an update addressing dyna dns a couple days after I originally posted this. 'Buntu not to blame.**

---

### Post by Mr. C. on 2007-03-07
As root, show output from:

ifconfig -a
netsatat -s
ethtool -S eth0

MrC

---

### Post by moon2js on 2007-03-07
```
me@werewolf:~$ sudo **ifconfig -a**
Password:
eth0      Link encap:Ethernet  HWaddr 00:12:34:56:78:9a
          inet addr:192.168.1.97  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:daff:fe12:b885/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3261 errors:0 dropped:0 overruns:1 frame:0
          TX packets:457 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:955454 (933.0 KiB)  TX bytes:68210 (66.6 KiB)
          Interrupt:9 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

me@werewolf:~$ sudo **netstat -s**
Ip:
    3314 total packets received
    0 forwarded
    0 incoming packets discarded
    597 incoming packets delivered
    488 requests sent out
Icmp:
    0 ICMP messages received
    0 input ICMP message failed.
    ICMP input histogram:
    0 ICMP messages sent
    0 ICMP messages failed
    ICMP output histogram:
Tcp:
    0 active connections openings
    7 passive connection openings
    0 failed connection attempts
    0 connection resets received
    5 connections established
    580 segments received
    471 segments send out
    0 segments retransmited
    0 bad segments received.
    0 resets sent
Udp:
    17 packets received
    0 packets to unknown port received.
    0 packet receive errors
    17 packets sent
TcpExt:
    2 TCP sockets finished time wait in fast timer
    20 delayed acks sent
    5 packets directly queued to recvmsg prequeue.
    5 of bytes directly received from prequeue
    118 packet headers predicted
    193 acknowledgments not containing data received
    0 TCP data loss events
me@werewolf:~$ sudo **ethtool -S eth0**
NIC statistics:
     tx_deferred: 0
     tx_max_collisions: 0
     tx_multiple_collisions: 0
     tx_single_collisions: 0
     rx_bad_ssd: 0
me@werewolf:~$
[...and time out!]
```

Come to think of it, this machine timed out downloading a few updates on synaptic -- had to retry -- when I first set her up.

---

### Post by Mr. C. on 2007-03-07
What brand of ethernet hardware is this?  00:41:CB is not in any vendor databases that I find.

lshw -class network

---

### Post by moon2js on 2007-03-07
oops. Here 'tis:

```
me@werewolf:~$ sudo **lshw -class network**
Password:
  *-network
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 10
       bus info: pci@00:10.0
       logical name: eth0
       version: 6c
       serial: 00:12:34:56:78:9a
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=3c59x duplex=full ip=192.168.1.97 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:1400-147f iomemory:e8020000-e802007f irq:9
```

Is it possible I just have a crap/old NIC? I can try swapping it with one that's in another machine someday. But it did work flawlessly yesterday and yesterday only (not before or since). I'll try from within the LAN soon.

Thanks for looking at this, btw.

---

### Post by Mr. C. on 2007-03-07
The 3Com tornado NIC (3c905) is recent enough, and is a very good NIC.

Your system has detected and is using correct driver (3c59x).  

The 00-50-DA is 3Com's vendor ID (mac address: 00:50:da:12:b8:85)

But your ifconfig data shows: 00:41:CB:21:C7:74.  This address is not a registered address.

Are you running in nsidwrapper mode?

That card runs fine with the native 3c59x module.

MrC

---

### Post by moon2js on 2007-03-08
Well, it isn't new. The NIC came with the system, which was bought in 1999. I had to remove failing RAM when I was preping the system for Ubuntu.

But ssh/http is working great now while I'm accessing it from within the LAN. No problems yet, knock on wood. I don't know why this seems so random, though.

I guess that means it's either the router or the ISP? Today, while remoting in, it was especially bad; a live session ssh only lasted two minutes tops before timing out. Weird.

Edit: Oh, the ipconfig Mac address is a mistake -- the second one is right and consistent. I haven't touched any of the network settings since Ubuntu install save the static IP address.

---

### Post by Mr. C. on 2007-03-08
Oh, yes, I recall now.  The 3c905 is old!  Later models were the 3c905b, c, 3c980 and 3c985.  Oh, how easy it is to forget these mundane, esoteric details.

I suppose there must be something going on with your external connection; if its stable internally, you know the card / driver pair is fine.

MrC

---

### Post by moon2js on 2007-03-08
Well, I'm remoting in flawlessly today from outside the LAN. But I assume this is another "on" day.

I don't understand why it works one day and then the next it's uber-flakey.

I wanna blame the router but I have no evidence other than it Not Being Linksys.

---

### Post by Mr. C. on 2007-03-08
Good to hear.

Check the firmware for the router; many a problems are solved with a simple firmware update.  If the firmware is newer, and has release notes, perhaps something in there will show itself as the likely culprit.

MrC

---

