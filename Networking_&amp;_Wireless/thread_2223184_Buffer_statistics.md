---
title: "Buffer statistics"
date: 2014-05-09
forum: Networking &amp; Wireless
---

### Post by WWWXXX on 2014-05-09
Hi all:

I am trying to test my network with following cmd:
 tc qdisc "add" dev eth1 parent 10:1 handle 20:bfifo limit "10" kb

I am wondering is there a way to check the buffer statistics like how full it is or some timing info? The I can use kst to visualize them.

Thanks for your help.

---

### Post by WWWXXX on 2014-05-11
Any one can help?

---

### Post by tgalati4 on 2014-05-11
*iperf* will give throughput statistics.  What is it that you are trying to accomplish?

```
man iperf
```

Here's a thread that shows how to use *iperf*:  [http://ubuntuforums.org/showthread.php?t=2143393&highlight=iperf](http://ubuntuforums.org/showthread.php?t=2143393&highlight=iperf)

---

### Post by WWWXXX on 2014-05-12
> **tgalati4 said:**
> *iperf* will give throughput statistics.  What is it that you are trying to accomplish?

```
man iperf
```

Here's a thread that shows how to use *iperf*:  [http://ubuntuforums.org/showthread.php?t=2143393&highlight=iperf](http://ubuntuforums.org/showthread.php?t=2143393&highlight=iperf)

Thanks for your reply!
Actually I would like to see the statistics of the queue.

---

### Post by tgalati4 on 2014-05-12
I don't know of a simple way to pull out network buffer statistics without instrumenting the network stack (and recompiling) to get the data that you want.

This may get you a little closer to what you want:  [http://askubuntu.com/questions/11709/how-can-i-capture-network-traffic-of-a-single-process](http://askubuntu.com/questions/11709/how-can-i-capture-network-traffic-of-a-single-process)

---

