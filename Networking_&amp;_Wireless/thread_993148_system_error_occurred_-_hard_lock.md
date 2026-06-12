---
title: "system error occurred - hard lock"
date: 2008-11-25
forum: Networking &amp; Wireless
---

### Post by loserboy on 2008-11-25
I just did a fresh install of hardy and got most everything ironed out, but I am having some trouble that appears to be network related.

I've just started getting some random hard lockups and I checked my syslog... the only thing that jumps out at me is this:
```

Nov 25 12:18:25 mike-work kernel: [  141.692480] 0000:05:07.0: tulip_stop_rxtx() failed (CSR5 0xfc06c012 CSR6 0xff970111)
```

and there is alot of lines of that followed by many lines of:

```
Nov 25 12:22:24 mike-work kernel: [  383.343214] eth1: (82593) System Error occurred (0)
```

I went to the network settings and disabled eth1 since I use wireless mostly, but I don't know where to go from here

this is what ifconfig says about eth1 - 

```
eth1      Link encap:Ethernet  HWaddr 00:4c:69:6e:75:79  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:12320629 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xa400 
```

and this is what lspci says it is (i think)

```
05:07.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
```

I don't recall feisty ever doing this

any help would be great... freezes arent fun, thanks

---

### Post by loserboy on 2008-11-26
bump...

---

### Post by loserboy on 2008-12-01
hmmm, well can anyone tell me how to blacklist eth1 altogether, upon restart eth1 gets re-enabled.

---

