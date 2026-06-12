---
title: "How to increase buffer size?"
date: 2014-09-24
forum: Networking &amp; Wireless
---

### Post by h.hittini on 2014-09-24
Hi,

I have Ubuntu Server 13.10 running 3.11 kernel
I need to increase the UDP send and receive buffer sizes
How to do that?

Thank you

---

### Post by spjackson on 2014-09-25
Does this help? [http://ask.fclose.com/878/how-to-enlarge-linux-udp-buffer-size](http://ask.fclose.com/878/how-to-enlarge-linux-udp-buffer-size)

---

### Post by h.hittini on 2014-10-01
Thank you spjackson

I was doing some tests on the wireless, the buffer size was enough, I was losing packets due to collisions

I could increase the receiving buffer size on a computer running Ubuntu Server 10.0.04 using the following
```
sudo sysctl -w net.core.rmem_default=26214400
sudo sysctl -w net.ipv4.udp_mem='26214400 26214400 26214400'
sudo sysctl -w net.ipv4.udp_rmem_min=26214400

```

and the transmitting buffer using the following
```
sudo sysctl -w net.core.wmem_default=8388608
sudo sysctl -w net.ipv4.udp_mem='8388608 8388608 8388608'
sudo sysctl -w net.ipv4.udp_wmem_min=8388608

```

I can't confirm the same works in Ubuntu 13.10 because I don't have a channel fast enough to make the current buffer overflow, the current buffer size is sufficient
Of course, I can use the following command to find the current buffer size, but I need something more accurate
```
sysctl -a | grep mem
```

---

