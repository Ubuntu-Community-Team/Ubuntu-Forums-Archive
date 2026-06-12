---
title: "Unable to access from outside network...."
date: 2014-07-23
forum: Networking &amp; Wireless
---

### Post by Cory_Henderson on 2014-07-23
Hello there,

I have for a while now been running a gameserver, mysql, apache server on my ubuntu server.
It has been working wonderfully for the past year now.

Yet all of a sudden today, no one can access it from the outside. I can access it through lan or wan (locally)
And this includes all ports (game server runs on a different port) none can be accessed now.

Running Ubuntu Server (64 bit) 12.04.4


Static IP and ports are forwarded (it was working fine).

tcpdump (using with open port checker which times out)
```


    107.20.89.142.57571 > 192.168.-.---.80: Flags [S], cksum 0xfac6 (correct), seq 1426883260, win 14600, options [mss 1460,sackOK,TS val 3877498108 ecr 0,nop,wscale 5], length 0



```

I really need this fixed ASAP, thanks for everyone who tried to help

---

