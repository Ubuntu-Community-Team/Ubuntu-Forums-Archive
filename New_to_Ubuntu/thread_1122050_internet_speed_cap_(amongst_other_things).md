---
title: "internet speed cap (amongst other things)"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by GreTTin on 2009-04-10
hey all,

I've been trying to sort this out for ages but have gotten stuck/lost and don't know what to try next.

I have a marvell/yukon ethernet port on my asus motherboard it uses sky2 as it's driver I've tried using sk98lin but couldn't get it to stick long enough to check if it's even any better.

my internet seems capped at 1.5mps on speedtest.net but other computers in the house get 6 as normal (one windows, one puppy linux) and it also drops out all the time. so annoying.

Any info you need don't hesitate to ask. I just hope someone can help me.

Thanks in advance
Paul

---

### Post by lfaraone on 2009-04-11
Are you using wifi?

---

### Post by cariboo on 2009-04-11
Could you paste the output of:

```
sudo ethtool eth0
```

in your next post. You will have to open an Applications-->Accesories-->Terminal to enter the above command.

You could also try iperf to see what your network speed between computers is. Iperf is in the repositories. Install on two computers, and run one as a server:

```
iperf -s
```

and on the other computer:

```
iperf -c <servername or ip address>
```

You should get results that look something like this:

On the server:

```
iperf -s
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  4] local 192.168.1.200 port 5001 connected with 192.168.1.100 port 36772
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-10.2 sec    114 MBytes  94.0 Mbits/sec
```

and on the host:

```
iperf -c willy
------------------------------------------------------------
Client connecting to willy, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.1.100 port 36772 connected with 192.168.1.200 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec    114 MBytes  95.6 Mbits/sec
```

I'm going to have to update to 1Gb switches and routers soon.

Jim

---

### Post by GreTTin on 2009-04-11
Hi thank you for the response.

No I'm not using wifi it's through a homeplug device. They work fine on the other computers and I've swapped them around to verify they work.

here is the output of that command

```
paul@main:~$ sudo ethtool eth0
[sudo] password for paul: 
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pg
	Wake-on: d
	Current message level: 0x000000ff (255)
	Link detected: yes

```

I'm not sure how to do the other command exactly? can I use iperf from a windows machine or is there a .pet for puppy? I'm not great at installing things from source.

Thank you for your help.

Paul

---

### Post by GreTTin on 2009-04-13
Does that code mean anything to any one?

Hope you can help.

---

