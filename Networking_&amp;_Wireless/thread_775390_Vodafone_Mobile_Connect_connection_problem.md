---
title: "Vodafone Mobile Connect connection problem"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by zweistein on 2008-04-30
I have a Vodafone Mobile Connect card, and was thrilled to finally see that Linux users got a nice graphical interface with the Betavine drivers as well. However, I just can't seem to make them function properly.

When I install and run the drivers (I tried versions 1.99.17 and 2.0beta1), and I manage to get them to respond to me clicking on "Connect" and actually connect to my ISP, I can't do anything with the connection. The most unusual problem is with pinging - even when I try to ping my gateway, I get the following error: *ping: sendmsg: Operation not permitted*. The only thing I **can** ping is my own IP address.

I also tried running comgt and connecting manually, but with the same results. I am sure I was able to connect with comgt and these wvdial settings in some of the previous versions of Ubuntu.

Here is my /etc/ppp/peers/wvdial. I am pretty much sure these are correct, because I've seen some other people using these exact settings to connect to my ISP normally:
```
debug
noauth
name wvdial
replacedefaultroute
noipdefault
nomagic
usepeerdns
ipcp-accept-local
ipcp-accept-remote
nomp
noccp
nopredictor1
novj
novjccomp
nobsdcomp
refuse-chap
refuse-mschap
refuse-mschap-v2
refuse-eap

```

And here is my /etc/wvdial.conf:
```
[Dialer Defaults]
Modem = /dev/noz0
Baud = 460800
SetVolume = 0
Dial Command = ATDT
FlowControl = NOFLOW
Init1 = ATZ
Init2 = ATM0

[Dialer network]
Init4 = AT+COPS?;+CSQ

[Dialer internet]
Username = xxxx
Password = xxxx
Phone = *99***1#
Stupid Mode = 1
Init5 = AT+CGDCONT=1,"IP","carnet.vip.hr"
Dial Attempts = 2

```

Another (strange?) thing I noticed is that I get a bunch of these lines in my /var/log/messages when connected:
```
Unknown OutputIN= OUT=ppp0 SRC=193.198.84.36 DST=193.198.184.130 LEN=85 TOS=0x00 PREC=0x00 TTL=64 ID=63821 DF PROTO=UDP SPT=32822 DPT=53 LEN=65
```

The IP address under DST is my gateway IP.

I tried my luck with Google, and I found that the ping error could be the result of a firewall running. I don't have any firewall software running, and I even tried to flush my iptables entries entirely, but to no avail.

I have an Option Globetrotter 3G+ PCMCIA card, and I'm running Ubuntu 7.10.

Thank you VERY much for your time and help. If any more information is needed, I would be glad to post it.

Sincerely,
Nikola

---

### Post by jolly79 on 2008-04-30
Hi

dont know if it helps but here is what i done:
First i installede the gui program and i made i connect..

Then i follewede this guide:
[http://tlab.org/index.php?page=huawei-e620-3g-pcmcia-data-card-with-telia-in-ubuntu-linux](http://tlab.org/index.php?page=huawei-e620-3g-pcmcia-data-card-with-telia-in-ubuntu-linux)

I have already removed the pin, so i didnt follow that part.

Here is a copy of my /etc/wvdial.conf

[Dialer 3g]
Phone = *99***1#
Username = irrelevant
Password = irrelevant
Stupid Mode = 1
Dial Command = ATDT
Modem = /dev/ttyUSB0
Baud = 750800
Init2 = ATZ
Init3 = ATE0V1&D2&C1S0=0+IFC=2,2
ISDN = 0
Modem Type = Analog Modem
Init5 =AT+CGDCONT=1,"IP","bredband.tre.dk";

I can execute this in a command line whem my card starts blinking blue:
wvdial 3g

Then i connects...

This is much better than the gui program.

But for sonme reason this program needs to be installede on my x40 to work.

Hope i helps :-)

---

### Post by jolly79 on 2008-04-30
maybe try changing the wvdial conf to:

[Dialer internet]
Phone = *99***1#
Username = irrelevant
Password = irrelevant
Stupid Mode = 1
Dial Command = ATDT
Modem = /dev/ttyUSB0
Baud = 750800
Init2 = ATZ
Init3 = ATE0V1&D2&C1S0=0+IFC=2,2
ISDN = 0
Modem Type = Analog Modem
Init5 =AT+CGDCONT=1,"IP","carnet.vip.hr"


and execute wvdial internet...

Se if it works,,,

No harm in giving it a go... good luck with the modem

Sorry for my poor english

---

### Post by zweistein on 2008-04-30
Thank you for your help! I tried with your wvdial configuration files, but I couldn't manage to get it to work (the ping - operation not permitted thing again). I don't believe the problem is in my connection strings, because the card connects just fine (I can see it in my ISP logs, I get an IP / DNS address etc.).

There seems to be a routing problem somewhere, but I just can't figure out where. I tried *route add default gw [my gw IP address]*, but that didn't help.

---

