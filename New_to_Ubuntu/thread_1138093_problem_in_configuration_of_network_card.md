---
title: "problem in configuration of network card"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by adel87 on 2009-04-26
hello
by using tool networks and by selecting int eth
when I click on configuring I have this message

```

the interface does not exist 
Check that it is correctly seized and that it is correctly taken charges some by your system

```here the result of the order ifconfig

```



eth0 Link encap: Ethernet HWaddr 00: e0: 4c: 90: 87: c0  
          inet adr: 192.168.0.101 Bcast: 192.168.0.255 Masks: 255.255.255.0
          adr inet6: fe80:: 2e0: 4cff: fe90: 87c0/64 Scope: Bond
          UP BROADCAST RUNNING MULTICAST MTU: 1500 Metric: 1
          Packets received: 5489 errors: 0: 0 overruns: 0 frame: 0
          TX packets: 5521 errors: 0 dropped: 0 overruns: 0 carrier: 0
          collisions: 0 lg file transmission: 1000 
          Received bytes: 5418878 (5.1 MB) transmitted Bytes: 697634 (681.2 KB)
          Interruption: 11 basic Address: 0xc000 

lo Link encap: Local loop  
          inet adr: 127.0.0.1 Masks: 255.0.0.0
          adr inet6: :: 1/128 Scope: Host
          UP LOOPBACK RUNNING MTU: 16436 Metric: 1
          Packets received: 912 errors: 0: 0 overruns: 0 frame: 0
          TX packets: 912 errors: 0 dropped: 0 overruns: 0 carrier: 0
          collisions: 0 lg file transmission: 0

```thank

---

### Post by spikoley on 2009-04-26
Post card's details from the command below.

```
lspci
```

---

