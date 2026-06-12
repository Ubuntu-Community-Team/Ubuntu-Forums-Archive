---
title: "Why do LED lights and special buttons not work?"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by hamofgrey on 2008-12-19
Hi I am a linux newbie and have a quick question. How come LED lights for wireless button do not light up and the button does not work. This is the same for the S1 and AV mode buttons for my Sony Vaio NR330E.

Thanks for any feedback :-)

I am sorry if a duplicate of this post is about here already my internet is playing up!

---

### Post by 73ckn797 on 2008-12-19
> **hamofgrey said:**
> Hi I am a linux newbie and have a quick question. How come LED lights for wireless button do not light up and the button does not work. This is the same for the S1 and AV mode buttons for my Sony Vaio NR330E.

Thanks for any feedback :-)

I am sorry if a duplicate of this post is about here already my internet is playing up!

When did this issue begin? After Ubuntu install or just at a random time? Could be a hardware issue.

---

### Post by ohzopants on 2008-12-19
I imagine you mean the little led that tells you whether or not wireless is enabled on your laptop.  I had a compaq laptop that had a similar led and button; the led never worked but the button did work if you pressed it twice.

This is usually because the driver was written by the community which does not have access to the full hardware specs from sony, so they have to guess some things.

---

### Post by rhcm123 on 2008-12-19
> **hamofgrey said:**
> Hi I am a linux newbie and have a quick question. How come LED lights for wireless button do not light up and the button does not work. This is the same for the S1 and AV mode buttons for my Sony Vaio NR330E.

Thanks for any feedback :-)

I am sorry if a duplicate of this post is about here already my internet is playing up!

Can you see it in network manager or with ndiswrapper? If so, it's irrelevant if the light is off.

---

### Post by hamofgrey on 2008-12-19
Its an Atheros 24420 wireless card, I've had a few problems with the card and getting it to work. I've got to use ath5k to get it to work so that mite be the problem, the wireless button does not turn off at any point as such all it does do however is stopping the laptop connecting to the network. It must not finish sending all the TCP/IP packets to connect to the router and continues to send the beginning of the communication of the necessary data.

If I used ndiswrapper I take it may perhaps work as intended?

I believe the problem maybe as previously stated, that not all the specs were available from sony.

The problem has always occured since installation.

---

### Post by ohzopants on 2008-12-19
Can you currently connect to the internet wirelessly with you laptop?
If so, I would not recommend using ndiswrapper since it will not work better and it will not fix your button/led issue.

---

### Post by rhcm123 on 2008-12-19
> **hamofgrey said:**
> Its an Atheros 24420 wireless card, I've had a few problems with the card and getting it to work. I've got to use ath5k to get it to work so that mite be the problem, the wireless button does not turn off at any point as such all it does do however is stopping the laptop connecting to the network. It must not finish sending all the TCP/IP packets to connect to the router and continues to send the beginning of the communication of the necessary data.


Wait, what? This makes absoloutely no sense.

---

### Post by hamofgrey on 2008-12-19
Sorry my grammar is awful.

When the button is in the off position the card will try to connect to it's favourite available wireless network. It will never fully connect but repeatly try and keep connecting to it. Therefore I believe it is not sending all the necessary packets to finish setting up the connection.

When the button is in the on position the card works perfectly.

It is a shame there appears to be no resolution to fixing the led bug. I googled the problem for a while and it does happen quite often.

---

### Post by rhcm123 on 2008-12-21
> **hamofgrey said:**
> Sorry my grammar is awful.

When the button is in the off position the card will try to connect to it's favourite available wireless network. It will never fully connect but repeatly try and keep connecting to it. Therefore I believe it is not sending all the necessary packets to finish setting up the connection.

When the button is in the on position the card works perfectly.

It is a shame there appears to be no resolution to fixing the led bug. I googled the problem for a while and it does happen quite often.

When it's in the off positon, it is logically enough, off. :) It may seem to the computer that it's sending the packets, but they aren't actually being transmitted. You can check packets with ifconfig. It will output all your interfaces, transmitted/reccived packets, etc.


You should get an output like this:
```
ussr@USSR-LAPTOP:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:d7:eb:6f  
          inet addr:192.168.2.137  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fed7:eb6f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:628 errors:0 dropped:0 overruns:0 frame:0
          TX packets:931 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:53982 (52.7 KB)  TX bytes:983384 (960.3 KB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:15:00:4b:30:85  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:419 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2864968864 (2.6 GB)  TX bytes:2005609085 (1.8 GB)
          Interrupt:22 Base address:0x8000 Memory:b8006000-b8006fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1516 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1516 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:82224 (80.2 KB)  TX bytes:82224 (80.2 KB)

```
eth0 is my ethernet, eth1 is my wifi, lo is the loopback. If you see no packets being transmitted from your wifi interface (i can help you figurout which one is the wifi if you post your info) then you know what is wrong :)

---

