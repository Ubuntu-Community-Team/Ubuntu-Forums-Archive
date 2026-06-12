---
title: "Setting NIC to full duplex"
date: 2006-10-03
forum: Networking &amp; Wireless
---

### Post by lseabra on 2006-10-03
Hi,

I'm using Ubuntu 6.06.1 and want to force my NIC to 100 Mb / Full duplex.
When I try to do this using "sudo mii-tool -F 100baseTx-FD eth0" I don't get any reply. And when I check it with "mii-tool -w etho" I get "eth0: no autonegotiation, 100baseTx-HD, link ok".
Am I doing something wrong?

Thanks for you time,
Luis

---

### Post by bswilson on 2006-10-03
I believe that you have to bring the interface down **before** you change the media interface duplex settings.  Try bringing eth0 down, *then* run your mii-tool command, and thing bring eth0 back up.

```
$ sudo ifdown eth0
$ sudo mii-tool -F 100baseTx-FD eth0
$ sudo ifup eth0
```

Give that a shot...

---

### Post by lseabra on 2006-10-04
Hi,

Thanks. I just tried out what you suggested but I still get the same results: no full duplex at all.
What puzzles me the most is that I can't see any errors on the logs or when I run the mii-tool command.
I don't have a clue what to do next... any suggestions?

Thanks,
Luis

---

### Post by lseabra on 2006-10-04
Hi,

I don't undersand why mii-tool didn't work, by I got the NIC on full duplex now with "ethtool -s eth0 speed 100 duplex full autoneg off".

Luis

---

### Post by dannyboy79 on 2006-10-04
what is the advantage of having it full duplex? how do i know if my card is set to that etc etc,

---

### Post by lseabra on 2006-10-04
If your NIC is on full duplex you'll have communications going both ways at the same time. If it's on half duplex you send and receive one step at a time.
If you run the command "sudo mii-tool -w eth0" for your eth0 NIC you'll get something like 100baseTx-FD for full duplex and 100baseTx-HD for half duplex.

Luis

---

### Post by dannyboy79 on 2006-10-05
thank you very much, i did that and it says that my eth0 is FD which you said is Full Duplex!. thanks agauin

---

### Post by netztier on 2006-10-05
> **lseabra said:**
> If your NIC is on full duplex you'll have communications going both ways at the same time. If it's on half duplex you send and receive one step at a time.


What did you do to the other end of the cable (i.e. your switch or hub port)?

There is no point in fixing a NIC to FullDuplex if the other end of the cable does not do the same thing. Most low-cost, unmanaged switches offer no means to configure a port's settings. A classical ethernet hub only offers half duplex, anyway.

Fixing the speed and duplex parameters of most NICs disables the autonegotiation feature, and therefore it won't advertise it's settings to it's peer.

The peer (here: your switch port) detecting a link, but unable to learn the duplex settings from it's counterpart will then have to fall back to half duplex by default. This leads to a [COLOR="Red"]**duplex mismatch**[/COLOR], which is bad to have in a network, and even strongly painful to detect with unmanaged switches. **[COLOR="Red"]Your network will suffer severe performance degration on a duplex-mismatched link[/COLOR]**.

If you're lucky and your NIC continues to advertise it's settings despite being in fixed-configuration for fullduplex, you won't have this problem. But of the >2000 NICs we have connected to our network @my.job.com, I wouldn't know of any single one that would show this behaviour.

Therefore I repeat, as already more than once in these forums:

[COLOR="red"][SIZE="4"]leave your NIC's HDX/FDX settings on "auto", unless you know exactly what you are doing![/SIZE][/COLOR]

FDX/HDX negotiation has become reliable and is working well with modern NICs, switches and drivers; there's no benefit from not using it.


kind regards

Marc

---

### Post by bob rohde on 2006-11-15
What file does one edit to turn off autonegotiation and lock the speed and mode capabilities of the NIC? And what values would one use to turn off autonegotiation, lock the speed to 100 and the duplex to full?

---

