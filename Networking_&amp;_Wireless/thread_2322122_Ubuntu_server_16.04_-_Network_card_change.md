---
title: "Ubuntu server 16.04 - Network card change"
date: 2016-04-26
forum: Networking &amp; Wireless
---

### Post by chrismyers on 2016-04-26
Hi Guys,

I need to work out how to get the new network card working in 16.04 server.

It used to be in [COLOR=#000000][FONT=Ubuntu Mono]/etc/udev/rules.d/70-persistent-net.rules but that file no longer exists.

How do I do this in the new version? I have tried searching, but I'm unsure what to search for.

Regards,

Chris.[/FONT][/COLOR]

---

### Post by chrismyers on 2016-04-26
Additional:

I've tried searching for [COLOR=#000000][FONT=Tahoma]enp8s0 as it appears to be the new name instead of eth0.

Getting little to nothing useful to work with.


[/FONT][/COLOR]

---

### Post by Jason_Hunter on 2016-04-26
Can you describe a little more what's you problem?

You're talking about getting a new card working and then you're talking about udev rules?

---

### Post by Bashing-om on 2016-04-26
chrismyers; Hello;

I do not have access presently to 16.04 .. But I am unaware that there is a change in networking in 16.04. 
In 14.04 - as my reference - it is the file /etc/network/interfaces that controls the active interface for the server application.
My example:
```

sysop@1404mini:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
##changed eth0 to eth1 26feb2014##
auto eth1
iface eth1 inet dhcp
sysop@1404mini:~$ 

```
Where my active interface is now 'eth1' and my router hands out the IPs ( dhcp ) .

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by chrismyers on 2016-04-27
Thanks guys for your responses.


Yes, it look like I am talking about the udev rules, but in 16.04, the udev directory is empty!

I'm fully aware of the config file [COLOR=#000000][FONT=Ubuntu Mono]/etc/network/interfaces but this is not the problem. The card isn't active, so it can't be configured.

I'm still searching for a fix. If I find a fix before someone helps, I'll post it.

Cheers.


[/FONT][/COLOR]

---

### Post by chrismyers on 2016-04-27
Hi Guys,

I found the fix. I just needed to discover the new label for the new interface.

[FONT=arial]I ran:

ip link

This showed the new interface label. I then modified the label to match in:

[COLOR=#000000]/etc/network/interfaces

I hope this helps future users.[/COLOR][/FONT]

---

### Post by chaitanyaarige on 2017-02-14
I tried with ip link:

> 1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00

2: enp8s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP mode DEFAULT group default qlen 1000
    link/ether 30:xx:xx:x8:bx:ax brd ff:ff:ff:ff:ff:ff

3: wlp9s0f0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN mode DORMANT group default qlen 1000
    link/ether 40:xx:xa:19:xe:xf brd ff:ff:ff:ff:ff:ff



What am I supposed to change?

---

