---
title: "Connect to wireless network, but not internet"
date: 2007-05-09
forum: Networking &amp; Wireless
---

### Post by diceydemon on 2007-05-09
Alright, i just installed ubuntu dapper drake on my laptop, i have connected to my network just fine have a strong signal strength, but i cannot connect to the net or ping any web addresses.


```
ifconfig
inet addr:192.168.2.123 Bcast:192.168.2.255 Mask:255.255.255.0
inet6 addr: fe80::213::2ff::fe81::aeld/64 Scope: Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:859 errors:348 dropped:899 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions: 0 txqueuelen:1000
RX bytes:33787 (32.9 KiB)  TX bytes:4619 (4.5 KiB)
Interrupt:169 Base address:0x6000 Memory:dfdff000-dfdfffff
```

When i ping a url i get ```
Unknown host google
```
When i ping a IP Adress i get ```
Network is unreachable
```

Can you guys help me out please?

---

### Post by Josh1 on 2007-05-09
I had the same problem with dapper but then I upgraded to feisty and it worked out of the box. But in dapper I had to compile my wireless.

---

### Post by diceydemon on 2007-05-09
Can you elaborate on that a little bit for me so i can fix it?

---

### Post by Josh1 on 2007-05-09
Sorry :).

Can you connect to your router via HTTP ([http://10.1.1.1](http://10.1.1.1) or [http://192.168.0.1](http://192.168.0.1) or whatever your router address is)? As far as I can tell, your wireless card is picking up the network and connected (as you said).

---

### Post by diceydemon on 2007-05-09
It's cool man.

Nope, i can't connect to it, and when i ping it in terminal it states that it is unreachable.

---

