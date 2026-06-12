---
title: "traceroute through a proxy"
date: 2007-07-22
forum: Networking &amp; Wireless
---

### Post by TheDeivix on 2007-07-22
Hi everyone, first post :D

When i do a regular traceroute to "foo.com" the request goes through my router first, then through my isp and then through other sites, like this:

```
> traceroute foo.com
1      172.16.0.1
2      my.isp.com
3      ......
4      ......
5      ......
6      foo.com
```

I have a proxy running at 127.0.0.1:8080, how can i make the traceroute go through this proxy first?

Thanx

---

### Post by TheDeivix on 2007-07-22
Bump

Ok, i see no one has answered my question, so i think maybe this is not the right forum to ask this.

Can anyone recommend any other forum or place where this kind of topics are discussed?

Thanx

---

### Post by netztier on 2007-07-23
> **TheDeivix said:**
> Bump

Ok, i see no one has answered my question, so i think maybe this is not the right forum to ask this.

Can anyone recommend any other forum or place where this kind of topics are discussed?

Thanx

<RANT>
[INDENT][COLOR="DarkRed"]When only waiting  5hours for an answer, you don't deserve an answer. Period. :mad: Go find another forum where people just give each other "this cool tool XYZ helps!" answers. First post, eh? 


[SIZE="7"]**Forums are not answer-my-question-machines!**[/SIZE]

*grumble* And bumping after less than two days is lame!
*mumble*[/COLOR][/INDENT]
</RANT>

Try tcptraceroute.

Yet, you basically can't traceroute through a proxy, both traceroute and tcptraceroute rely on an end-to-end communication, be that with ICMP, UDP or TCP. The intermediate routers along the path must reply back to the source that the TTL in the IP header of the packet has expired (using a special ICMP message). 

The replying router is then shown in (tcp)traceroute's output as one hop. To determine the subsequent hop, the TTL in the IP header of the packet is increased by 1, and the packet is sent out again until another router replies that the TTL did expire in transit.

Since a proxy breaks up end-to-end communication into to the segments Client-Proxy and Proxy-Server, you can only traceroute from your source to the proxy, and (if you can login into the proxy) from the proxy to the destination, but not *through* the proxy.

Unless of course, you find or write a feature for a proxy that *emulates* traceroute by intercepting and rewriting the ICMP unreachable messages (plus doing some more weird stuff). I wouldn't know about any software that did this.

regards

Marc

---

