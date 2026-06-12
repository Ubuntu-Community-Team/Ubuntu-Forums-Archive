---
title: "I can't connect to internet! d-link 302t"
date: 2008-06-27
forum: Networking &amp; Wireless
---

### Post by lord_nerevar on 2008-06-27
Hi everyone,
I have a D-Link 302T ADSL modem, connected via ethernet to my PC.
I want to use the modem to go in internet with Ubuntu LiveCD 8.04.
I use "sudo pppoeconf" to configure my modem and it's all ok, but then i cannot navigate the net.
Doing "plog" few seconds after pppoeconf it seems to be ok, but i cannot navigate, then if i try newly plog it says "modem hangup".
I've also tried to use "pon dsl-provider" and "poff dsl-provider" to turn on and off the connection but this doesn't help.
The modem is ok (it works well on windows) and the ADSL LED is on, but the Ethernet LED doesn't switch on. ..


I've tried to configure manually the net, too, by system->administration->net

I've put 192.168.1.2 as static IP, 255.255.255.0 as subnet mask and 192.168.1.1 as gateway, but i can't connect to internet anyway.

I've tried to ping myself on 192.168.1.1, and the output is:
connect: network is unreachable. The problem seems to be that the net card haven't got an address. but i am not expert, so if you needs some outputs of some commands, ask me.. 

Please HELP!!

---

### Post by ASellors on 2008-06-27
I had a similar problem a while back and after a bit of searching I came across a reasonably simple solution. It seems as though Windows turns off the ethernet device on shutdown, so.....

- Boot up Windows
- Right click on My Computer
- Click on Properties -> Hardware -> Device Manager
- Expand your network card section and double click on your network card
- Set "Wake-on-lan after shutdown" to enabled

A quick re-boot into Ubuntu and your internet should burst into life :-)

Can't guarantee that it'll work for you, but it's worth a try!

---

### Post by lord_nerevar on 2008-06-28
> **ASellors said:**
> I had a similar problem a while back and after a bit of searching I came across a reasonably simple solution. It seems as though Windows turns off the ethernet device on shutdown, so.....

- Boot up Windows
- Right click on My Computer
- Click on Properties -> Hardware -> Device Manager
- Expand your network card section and double click on your network card
- Set "Wake-on-lan after shutdown" to enabled

A quick re-boot into Ubuntu and your internet should burst into life :-)

Can't guarantee that it'll work for you, but it's worth a try!

Nothing to do, the command ifconfig ppp0 give the same output: device not found, and the ethernet led on my modem continue to be off.

---

