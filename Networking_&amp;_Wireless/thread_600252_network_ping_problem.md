---
title: "network ping problem"
date: 2007-11-02
forum: Networking &amp; Wireless
---

### Post by raghuagarwala on 2007-11-02
HI ,

I just got my eth0 running on ubuntu server 7.10 and now it can ping public IP addresses. But if I want to ping via host name it cannot resolve it. I tested this with 

ping 202.87.41.148
PING 202.87.41.148 (202.87.41.148) 56(84) bytes of data.
64 bytes from 202.87.41.148: icmp_seq=1 ttl=51 time=160 ms

ping [www.hungama.com](www.hungama.com)
ping: unknown host [www.hungama.com](www.hungama.com)

this is when(this is done from another system just to do a cross reference)
PING hungama.com (202.87.41.148): 56 data bytes
64 bytes from 202.87.41.148: icmp_seq=0 ttl=51 time=92.271 ms

I dont know what exactly is the problem.

........

---

### Post by noob12 on 2007-11-02
This suggests a problem resolving hostnames.

Can you post the output of this on the host that is having problems?
```

cat /etc/resolv.conf

```

Check if you see your local router's IP address here.

I have seen a number of problems with Ubuntu and other linux distros being unable to resolve hostnames through router-based DNS proxies.  I think this problem is actually due to bugs in the router-based proxies (not linux).  They work for Windows but not for linux. 

You can workaround this and many related issues by following the first section in the following thread:  [http://ubuntuforums.org/showthread.php?t=543659](http://ubuntuforums.org/showthread.php?t=543659) .   You can use either the OpenDNS servers suggested in that thread or your own ISPs DNS servers directly rather than going through the router-based proxy.

---

