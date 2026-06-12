---
title: "ADSL connection problem!"
date: 2008-09-16
forum: Networking &amp; Wireless
---

### Post by cunelastavica on 2008-09-16
I have ADSL modem connected over ethernet cable to PC and after running pppoe-setup, setting all parameters, I started pppoe-start and it said that I've been connected but I wasn't able to ping any address or to load it with browser.
Here is the listing of ifconfig, after which is ping to ADLS modem:
```

root[vuja]# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:6e:41:78:7d 
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:813 errors:0 dropped:0 overruns:0 frame:0
          TX packets:777 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:58554 (57.1 KiB)  TX bytes:59617 (58.2 KiB)
          Interrupt:22

lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:43 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4000 (3.9 KiB)  TX bytes:4000 (3.9 KiB)

ppp0      Link encap:Point-to-Point Protocol 
          inet addr:89.111.*.*  P-t-P:89.111.*.*  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:3092 (3.0 KiB)  TX bytes:824 (824.0 B)


root[vuja]# ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=254 time=0.554 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=254 time=0.704 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=254 time=0.729 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=254 time=0.541 ms
^C
--- 192.168.1.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2999ms
rtt min/avg/max/mdev = 0.541/0.632/0.729/0.085 ms

```

I have no idea what could possibly be wrong.

---

### Post by ianhaycox on 2008-09-16
To eliminate a DNS problem. Have you tried pinging  64.233.167.99  (google.com) or connecting via the browser with [http://209.85.129.104/](http://209.85.129.104/) ([www.google.com](www.google.com))

---

### Post by cunelastavica on 2008-09-16
I tried that. No result.

```
root[vuja]# ping 64.233.167.99
PING 64.233.167.99 (64.233.167.99) 56(84) bytes of data.
From 192.168.1.1 icmp_seq=1 Destination Host Unreachable
From 192.168.1.1 icmp_seq=2 Destination Host Unreachable
From 192.168.1.1 icmp_seq=3 Destination Host Unreachable
From 192.168.1.1 icmp_seq=4 Destination Host Unreachable
^C
--- 64.233.167.99 ping statistics ---
4 packets transmitted, 0 received, +4 errors, 100% packet loss, time 3001ms

root[vuja]# ping google.com
ping: unknown host google.com
```

---

### Post by timcredible on 2008-09-16
doesn't your dsl modem have all the ppoe settings?  you don't need them on your pc, just on the dsl modem.  you probably access the modem by opening firefox and going to [http://192.168.1.1](http://192.168.1.1)

---

### Post by ianhaycox on 2008-09-16
Looks like your modem isn't syncronized. As the previous reply says, go to [http://192.168.1.1](http://192.168.1.1) log in and check the status page to see if there is an internet connection.

Dumb question, but is the modem plugged into the phone socket correctly with filters on all the sockets.

---

### Post by cunelastavica on 2008-09-16
> **timcredible said:**
> doesn't your dsl modem have all the ppoe settings?  you don't need them on your pc, just on the dsl modem.  you probably access the modem by opening firefox and going to [http://192.168.1.1](http://192.168.1.1)

I don't have automatic connection when os starts. I need to connect through username and password(I do it like this under windows on the same pc).
 Yes, I accessed modem through firefox and [http://192.168.1.1](http://192.168.1.1).

---

### Post by caljohnsmith on 2008-09-16
This is just an idea, but for most ADSL modems, you can configure them so they use "PPPoE on modem" as opposed to "PPPoE is on the computer", which is what you have set up. If you use PPPoE on the modem, you put your user/password there (instead of on your computer setup), and then you can connect with your computer to the modem with simple DHCP, which is Ubuntu's defualt. If your modem has that functionality, which I would guess it does, I think that would be alot easier than trying to set up PPPoE on your computer.

---

### Post by cunelastavica on 2008-09-16
> **caljohnsmith said:**
> This is just an idea, but for most ADSL modems, you can configure them so they use "PPPoE on modem" as opposed to "PPPoE is on the computer", which is what you have set up. If you use PPPoE on the modem, you put your user/password there (instead of on your computer setup), and then you can connect with your computer to the modem with simple DHCP, which is Ubuntu's defualt. If your modem has that functionality, which I would guess it does, I think that would be alot easier than trying to set up PPPoE on your computer.

I did just that and it worked! Thanks!
I would liked I had option of connecting when I want and not automaticly on start up, but this is fine too.
Thanks again everyone, for ofering your help.

---

