---
title: "Problems accessing wired connection"
date: 2014-11-26
forum: Networking &amp; Wireless
---

### Post by Philip_Dean on 2014-11-26
Hi there, 

I am using Ubuntu 14.04.1 LTS. Kernel 3.16.0.23-generic

Upon loading, there are no connections. The ethernet previously worked, but has now stopped. 

I have checked the ethernet port and wire is working correctly. The light is on and flashing in the back of the computer when the ethernet is plugged in. 

It appears there is no eth0, and when queried, no ethernet card is found. The driver for the card is e1000e i believe, and does exist in lsmod.

I tried reinstalling completely from a disc image of 14.04.1 LTS, but the problem persists. the version of e1000e is 2.3.2-k. 

I have no internet access of any kind on this computer, so any fix would have to bear this in mind. 

Here are some details of the problem:

ifconfig -a
lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3280 (3.2 KB)  TX bytes:3280 (3.2 KB)

sudo lshw -class network
  *-network UNCLAIMED    
       description: Ethernet controller
       product: 82579LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi cap_list
       configuration: latency=0
       resources: memory:e1500000-e151ffff memory:e1580000-e1580fff ioport:4040(size=32)

Thanks for the help, and let me know of any more details needed. 

Phil Dean

---

### Post by Bashing-om on 2014-11-26
Philip_Dean; Hi !

Let's start at the start for trouble shooting:
What links are identified, and what assignments are made:
```

ip link ls

```

Now, who/what controls the networking :
```

cat /etc/network/interfaces

```

Once these are known there is a direction to work toward.

[INDENT][INDENT]a failure to communicate
[INDENT][INDENT][INDENT][INDENT]somewhere
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

