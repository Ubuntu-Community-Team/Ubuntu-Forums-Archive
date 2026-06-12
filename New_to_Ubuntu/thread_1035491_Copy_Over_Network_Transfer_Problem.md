---
title: "Copy Over Network Transfer Problem?"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by cfree220 on 2009-01-09
Hi all,

I recently set up a Samba server on an old dell desktop. Ultimately, I pla to use something like Unison to keep the hard drive in the Dell synced with my laptop HDD, but for the meantime I'm copying over the network.

All was going well. I was only getting about a 5 mb/s (peak) transfer and was transferring about 147 GB over the network. About half way through, the transfer rate started to slow, and the ETA disappeared. It indicates that files are still being moved (in bunches of about ten)... but does that mean that they are actually being moved? The task manager is indicating that I'm only using about 5% of my connection bandwidth, whereas before it showed 99%

---

### Post by blueridgedog on 2009-01-10
Is the volume on the destination server full?  You can check with:

```
df
```

How about the task manager on the server?  Is it heavily loaded?

Or in a terminal:

```
top
```

Alternatively, are there errors on the network?  You can check by using:

```
ifconfig
```

In a terminal and look for errors such as:

```
eth0      Link encap:Ethernet  HWaddr   
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:d8ff:fecf:bf40/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
[COLOR="Red"]          RX packets:37748 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34970 errors:0 dropped:0 overruns:0 carrier:0[/COLOR]
          collisions:0 txqueuelen:1000 
          RX bytes:35271205 (35.2 MB)  TX bytes:6949940 (6.9 MB)
          Interrupt:23 Base address:0x2000 
```

---

