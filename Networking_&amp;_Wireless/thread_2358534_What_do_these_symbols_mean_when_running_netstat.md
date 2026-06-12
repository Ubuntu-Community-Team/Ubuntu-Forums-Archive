---
title: "What do these symbols mean when running netstat?"
date: 2017-04-14
forum: Networking &amp; Wireless
---

### Post by KenUBF on 2017-04-14
Hi all, 

I just had a quick question. What do these symbols mean when running netstat? 
```

[::]:*    *:* 

```

  I've searched online but have never been able to find any information. Thanks!

---

### Post by Doug S on 2017-04-14
Could you show us a context where you get those outputs? They look like IPV6 and IPV4 versions of any address and any port, but I'm not sure, and used to seeing it (IPV4) as "0.0.0.0:*"

---

### Post by KenUBF on 2017-04-15
> **Doug S said:**
> Could you show us a context where you get those outputs? They look like IPV6 and IPV4 versions of any address and any port, but I'm not sure, and used to seeing it (IPV4) as "0.0.0.0:*"


Hi Doug, thanks for the reply. Here is the complete netstat output.

```

$ netstat -a
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 mate:domain             *:*                     LISTEN
tcp        0      0 localhost:55212         localhost:9150          TIME_WAIT
tcp        0      0 localhost:9151          localhost:55118         TIME_WAIT
tcp        0      0 localhost:55228         localhost:9150          TIME_WAIT
tcp        0      0 localhost:55240         localhost:9150          TIME_WAIT
tcp        0      0 localhost:55236         localhost:9150          TIME_WAIT
tcp        0      0 localhost:55206         localhost:9150          TIME_WAIT
tcp        0      0 192.X.X.XXXXXXXXX     140.90.101.207:https    ESTABLISHED
tcp        0      0 localhost:55224         localhost:9150          TIME_WAIT
tcp        0      0 192.X.X.XXXXXXX     customer-217-69-14:9001 TIME_WAIT
tcp        0      0 localhost:55110         localhost:9151          TIME_WAIT
tcp        0      0 localhost:55256         localhost:9150          TIME_WAIT
tcp        0      0 192.XXX.X.XXX:XXXXX     customer.worldstr:https TIME_WAIT
tcp        0      0 localhost:55108         localhost:9151          TIME_WAIT
tcp        0      0 localhost:9150          localhost:55252         TIME_WAIT
tcp        0      0 localhost:55218         localhost:9150          TIME_WAIT
udp        0      0 mate:domain             *:*
udp        0      0 *:bootpc                *:*
udp        0      0 192.XXXXXXXXX:ntp       *:*
udp        0      0 localhost:ntp           *:*
udp        0      0 *:ntp                   *:*
udp        0      0 *:ipp                   *:*
udp        0      0 *:mdns                  *:*
udp        0      0 *:41764                 *:*
udp        0      0 *:45649                 *:*
udp6       0      0 [::]:52128              [::]:*
udp6       0      0 [::]:57809              [::]:*
udp6       0      0 2600:XXXXXXXXXXXXXX:ntp [::]:*
udp6       0      0 fe80:XXXXXXXXXXXXXX:ntp [::]:*
udp6       0      0 2600:XXXXXXXXXXXXXX:ntp [::]:*
udp6       0      0 2600:XXXXXXXXXXXXXX:ntp [::]:*
udp6       0      0 ip6-localhost:ntp       [::]:*
udp6       0      0 [::]:ntp                [::]:*
udp6       0      0 [::]:mdns               [::]:*
raw6       0      0 [::]:ipv6-icmp          [::]:*                  7             

```

---

### Post by Doug S on 2017-04-16
It looks like it means "any address : any port" to me.

---

### Post by KenUBF on 2017-04-27
Thanks for the info!

---

