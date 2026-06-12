---
title: "Tcp v6 ?"
date: 2006-10-27
forum: Networking &amp; Wireless
---

### Post by dupa on 2006-10-27
Is this a TCP v6 packet?

```
09:34:02.294214 IP 
(tos 0x0, ttl  64, id 59460, offset 0, flags [DF], proto: TCP (6), length: 60) 
myhost.56587 > tin.virgilio.it.www: S, cksum 0x465a (correct), 4140319698:4140319698(0) win 5840 
<mss 1460,sackOK,timestamp 1354646 0,nop,wscale 2>
```

Does "proto: TCP (6)" mean that is it tcp v6 ?

Thanks

---

### Post by netztier on 2006-10-27
> **dupa said:**
> Is this a TCP v6 packet?

```
09:34:02.294214 IP 
(tos 0x0, ttl  64, id 59460, offset 0, flags [DF], proto: TCP (6), length: 60) 
myhost.56587 > tin.virgilio.it.www: S, cksum 0x465a (correct), 4140319698:4140319698(0) win 5840 
<mss 1460,sackOK,timestamp 1354646 0,nop,wscale 2>
```

Does "proto: TCP (6)" mean that is it tcp v6 ?

Thanks

I'd doubt that. (btw.. what kind of log output is that?)

As it is common, the lower-layer packet header contains a flag that indicates what protocol type will follow in the payload. 

The ethernet header will show "0800" for IP, the IP header shows "6" for TCP, the TCP port number is a hint (not more) for the application protocol.

See also IANA's Web sites:

[Protocol Numbers]("http://www.iana.org/assignments/protocol-numbers")
[Port Numbers]("http://www.iana.org/assignments/port-numbers")

regards

Marc

---

### Post by dupa on 2006-10-27
the log is taken with tcpdump

---

