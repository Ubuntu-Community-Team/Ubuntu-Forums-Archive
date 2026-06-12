---
title: "ping shows only summary"
date: 2011-05-05
forum: New to Ubuntu
---

### Post by lazier on 2011-05-05
I am executing the following on Ubuntu 11.04:

```
ping -c10 some.domain.name
```Even though there is no -q switch there, only the summary is displayed.
How to see data related to all the 10 requests before the summary?

---

### Post by yetiman64 on 2011-05-05
> **lazier said:**
> I am executing the following on Ubuntu 11.04:

```
ping -c10 some.domain.name
```Even though there is no -q switch there, only the summary is displayed.
How to see data related to all the 10 requests before the summary?

I am on 10.04 so unsure if what I put next will work for you, but I would suggest you try out the verbose switch (-v), eg.

```
ping -c10 -v some.domain.name
``` the default output of ping may be changed with the new release. yetiman64

---

### Post by Grenage on 2011-05-05
I'm seeing the same thing here on 11.04, it must be a bug.

---

### Post by The Cog on 2011-05-05
ping doesn't print anything if no response is received. My guess is that you are pinging something that doesn't respond, or you have a firewall dropping the packets.

---

### Post by alphacrucis2 on 2011-05-05
> **The Cog said:**
> ping doesn't print anything if no response is received. My guess is that you are pinging something that doesn't respond, or you have a firewall dropping the packets.

+1 

Pinging [www.google.com](www.google.com) which does respond to ping is working for me on 11.04 as expected. e.g 


```
alpht@laptopt400:~$ ping -c3 www.google.com
PING www.google.com (72.14.203.99) 56(84) bytes of data.
64 bytes from www.google.com (72.14.203.99): icmp_req=1 ttl=51 time=237 ms
64 bytes from www.google.com (72.14.203.99): icmp_req=2 ttl=51 time=236 ms
64 bytes from www.google.com (72.14.203.99): icmp_req=3 ttl=51 time=236 ms

--- www.google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 236.122/236.724/237.408/0.528 ms
```

Here's what happens with [www.cnn.com](www.cnn.com) which doesn't respond:


```
alpht@laptopt400:~$ ping -c3 [www.cnn.com](www.cnn.com)
PING [www.cnn.com](www.cnn.com) (157.166.224.26) 56(84) bytes of data.

--- [www.cnn.com](www.cnn.com) ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2002ms


```

---

### Post by Grenage on 2011-05-05
Touché indeed, I only checked one.

---

