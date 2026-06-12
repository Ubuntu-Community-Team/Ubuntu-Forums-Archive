---
title: "ethtool problem"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by gandalf29 on 2007-11-08
Welcome,

I am trying to change offload settings ny typping: ethtool -K lo rx off 
and I get following answer: Cannot set device rx csum settings: Operation not supported

Where is the problem? I am using ethtool version 5.

Best Regards,
Krzysztof Trawinski

---

### Post by Ehtetur on 2007-11-08
> **gandalf29 said:**
> I am trying to change offload settings ny typping: ethtool -K lo rx off

lo is a loopback, not your ethernet card...
Assuming your ethernet card is eth0, the command would be:
ethtool -K eth0 rx off

---

### Post by gandalf29 on 2007-11-08
I have tried this as well. The result is following:

root@kt:~# ethtool -K eth0 rx off
Cannot set device rx csum settings: Operation not supported

---

### Post by Ehtetur on 2007-11-08
I think you're getting that message because your card does not support checksum offloading.

Run this command to see what you can offload:
```
  ethtool -k eth0
```
This is the message I got:
> Offload parameters for eth0:
Cannot get device udp large send offload settings: Operation not supported
rx-checksumming: off
tx-checksumming: on
scatter-gather: on
tcp segmentation offload: off
udp fragmentation offload: off
generic segmentation offload: off

Interestingly enough, after I ran ethtool -K eth0 rx off,   I ran ethtool -K eth0 rx on... thinking it was on before I turned it off... But after I turned it on, I couldn't get on the network.. until I turned it back off.

---

### Post by Lambert on 2007-11-08
There are some drivers/devices not supported by ethtool. Either in whole or part of its features. Maybe why it won't work.

---

### Post by gandalf29 on 2007-11-08
I got following text:

root@kt:~# ethtool -k eth0
Offload parameters for eth0:
Cannot get device rx csum settings: Operation not supported
Cannot get device tx csum settings: Operation not supported
Cannot get device scatter-gather settings: Operation not supported
Cannot get device tcp segmentation offload settings: Operation not supported
Cannot get device udp large send offload settings: Operation not supported
rx-checksumming: off
tx-checksumming: off
scatter-gather: off
tcp segmentation offload: off
udp fragmentation offload: off
generic segmentation offload: off

It seems that offloading is not supported/switched off... Isn't true? 
 Nevertheles when I send packets in loopback (lo) I am getting incorrect checksum, although
 it is calculated correctly ( in raw socekt).
Do you know what may be an issues ?

---

