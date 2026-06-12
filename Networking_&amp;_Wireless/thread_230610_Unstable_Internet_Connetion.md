---
title: "Unstable Internet Connetion"
date: 2006-08-06
forum: Networking &amp; Wireless
---

### Post by GooOS on 2006-08-06
Till now, this is the only "diffculty" I have in Linux.
Both in Live CD and the installed.

here is a detailed describtion of the problem, I really need this solved or I will freak!

Hardware: ECI B-focus router 312+, Standart Realtek ethernet network card.
Software: Ubuntu Dapper 6.06

Approaching:
I setup the pppoe connection using the "pppoeconf" (I answer the question with the default selection)

the internet connection works and I can surf the internet, so far so good.

The Problem:
When I leave the internet connection idle (no incoming/outgoing data) it disconnects, and the "plog" command displays nothing.
"pon dsl-provider" does not reconnect unless i type "poff -a" first.

messege from plog:
```
Aug  5 17:42:55 gos-desktop pppd[15324]: PAP authentication succeeded
Aug  5 17:42:55 gos-desktop pppd[15324]: peer from calling number 00:02:3B:02:79:D3 authorized
Aug  5 17:42:55 gos-desktop pppd[15324]: replacing old default route to eth0 [10.0.0.138]
Aug  5 17:42:55 gos-desktop pppd[15324]: Cannot determine ethernet address for proxy ARP
Aug  5 17:42:55 gos-desktop pppd[15324]: local  IP address 217.132.169.219
Aug  5 17:42:55 gos-desktop pppd[15324]: remote IP address 212.143.205.245
Aug  5 17:42:55 gos-desktop pppd[15324]: primary   DNS address 194.90.1.5
Aug  5 17:42:55 gos-desktop pppd[15324]: secondary DNS address 212.143.212.143

```

(the internet disconnected 3 times during writing this messege)

/etc/network/interfaces file
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

    pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf

```

please SAVE me

thank you

---

### Post by eXisor on 2006-08-06
Did you select the keepalive option in pppoeconf? Does the modem  manual say anything about keepalive?

Alternatively you can write a script to do a ping and sleep cycle.
See this thread [http://www.ubuntuforums.org/showthread.php?t=10090&highlight=keepalive](http://www.ubuntuforums.org/showthread.php?t=10090&highlight=keepalive)

---

### Post by GooOS on 2006-08-06
OK, how do i do that?

---

### Post by eXisor on 2006-08-08
Ok, follow the link below to a thread which has scripts for the  keepalive issue. Remember you'll have to replace 'fritz' with your own username.

[http://ubuntuforums.org/showthread.php?t=89169&highlight=keepalive](http://ubuntuforums.org/showthread.php?t=89169&highlight=keepalive)

It's by audax321, so all kudos go to him. 

Try it an post back any problems you have.

---

