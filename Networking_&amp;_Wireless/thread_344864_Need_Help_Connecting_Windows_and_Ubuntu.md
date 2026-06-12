---
title: "Need Help Connecting Windows and Ubuntu"
date: 2007-01-23
forum: Networking &amp; Wireless
---

### Post by q-ball on 2007-01-23
Hi. I have 2 computers (one running Windows 2000 and the other Ubuntu 6.10). I want to connect them like this:
                                                               Windows <----cable----> Ubuntu
but I can't get SAMBA to work ](*,) . Can someone please post a HowTo or a link to a HowTo?

P.S. I have a PPPoE DSL internet connection through an Alcatel Speedtouch 330 USB modem on my Ubuntu machine...if you could add a little bonus and tell me how to share that connection to my windows machine after (if) I get my network connection running, I would be eternally grateful.

---

### Post by Chiro on 2007-01-23
Maybe this will help 

[http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605)
[http://tldp.org/HOWTO/SMB-HOWTO.html](http://tldp.org/HOWTO/SMB-HOWTO.html)

---

### Post by all4linux on 2007-01-23
> **q-ball said:**
> Hi. I have 2 computers (one running Windows 2000 and the other Ubuntu 6.10). I want to connect them like this:
                                                               Windows <----cable----> Ubuntu
but I can't get SAMBA to work ](*,) . Can someone please post a HowTo or a link to a HowTo?

P.S. I have a PPPoE DSL internet connection through an Alcatel Speedtouch 330 USB modem on my Ubuntu machine...if you could add a little bonus and tell me how to share that connection to my windows machine after (if) I get my network connection running, I would be eternally grateful.

You probably should have stated whether you are using a crossover cable to connect the two computers via the ethernet ports. If not, you can get some information on making a crossover cable at the following site:

[http://yoda.uvi.edu/InfoTech/rj45.htm](http://yoda.uvi.edu/InfoTech/rj45.htm)

Which will give you the wiring for both straight-thru, and crossover ethernet cables. You can also buy one of these at just about any computer store.

I'm too new to ubuntu to help you with the rest of the setup, but I am familiar with the hardware part. 

Dick Berger

---

### Post by q-ball on 2007-01-24
Still no luck :(. I can't get the darn thing working. Every time I try to ping my Windows machine from Ubuntu, I get this message: 'Destination Host Unreachable', and when I try to ping the Ubuntu machine from Windows it says 'Request timed out'. Here's an output of *ifconfig*.

```
eth0      Link encap:Ethernet  HWaddr 00:0A:E6:AF:36:5A
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e6ff:feaf:365a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:129 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:15571 (15.2 KiB)  TX bytes:594 (594.0 b)
          Interrupt:11 Base address:0xe400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:422 errors:0 dropped:0 overruns:0 frame:0
          TX packets:422 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:48797 (47.6 KiB)  TX bytes:48797 (47.6 KiB)

nas0      Link encap:Ethernet  HWaddr 00:0E:50:B4:D4:B0
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:50ff:feb4:d4b0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4989 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6369 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2328696 (2.2 MiB)  TX bytes:3888717 (3.7 MiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:86.34.243.97  P-t-P:89.120.37.254  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:4886 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5868 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:2284800 (2.1 MiB)  TX bytes:3656733 (3.4 MiB)
```
Like I said, I have an USB DSL modem. Could it be that when I got the modem working, I screwed up the other network interfaces? I installed the modem by following the tutorial from [http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html).


> **all4linux said:**
> You probably should have stated whether you are using a crossover cable to connect the two computers via the ethernet ports. If not, you can get some information on making a crossover cable at the following site:

[http://yoda.uvi.edu/InfoTech/rj45.htm](http://yoda.uvi.edu/InfoTech/rj45.htm)

Which will give you the wiring for both straight-thru, and crossover ethernet cables. You can also buy one of these at just about any computer store.

I'm too new to ubuntu to help you with the rest of the setup, but I am familiar with the hardware part. 

Dick Berger

I have a crossover cable. It worked when I had Windows on both machines.

---

