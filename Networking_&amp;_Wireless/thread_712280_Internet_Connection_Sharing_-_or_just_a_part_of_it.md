---
title: "Internet Connection Sharing - or just a part of it?"
date: 2008-03-01
forum: Networking &amp; Wireless
---

### Post by Prism on 2008-03-01
Hi there,

I have an Ubuntu machine which is a gateway to a Windows machine. The internet connection sharing was fine until lately. Somehow, the Windows machine can't surf now to the Windows Update site, which is a major concern. Further examination discovered that microsoft.com site wasn't reachable as well.

The most surprising thing is that the linux machine can view these MS sites, so it's not their fault. However, pinging microsoft.com usually looks like this:

```

$ ping www.microsoft.com
PING lb1.www.ms.akadns.net (207.46.192.254) 56(84) bytes of data.

--- lb1.www.ms.akadns.net ping statistics ---
10 packets transmitted, 0 received, 100% packet loss, time 9008ms

```

I'm using the iptables script for internet sharing found here: [http://www.debuntu.org/iptables-how-to-share-your-internet-connection](http://www.debuntu.org/iptables-how-to-share-your-internet-connection) , but I've also tried a known-to-work configuration of shorewall.

I don't know when this problem started, nor what changes were made to any of the machines, I noticed it yesterday.

So, what might be the problem?

Thanks in advance!

---

### Post by dmizer on 2008-03-02
i think the ping thing is normal.  i CAN visit [www.microsoft.com](www.microsoft.com), but i cannot ping it:
```
$ ping www.microsoft.com
PING lb1.www.ms.akadns.net (207.46.19.254) 56(84) bytes of data.

--- lb1.www.ms.akadns.net ping statistics ---
14 packets transmitted, 0 received, 100% packet loss, time 13012ms
```
is windows update the only site you're having problems with?

i suggest you look at windows as your problem on this one:
[http://www.jsifaq.com/SF/Tips/Tip.aspx?id=7903](http://www.jsifaq.com/SF/Tips/Tip.aspx?id=7903)

---

### Post by Prism on 2008-03-02
MSN Messenger and Windows Messenger can't connect as well in the windows machine, so I think it's not windows in that case (I'd really like it if it is, though ;) ).

---

### Post by Prism on 2008-03-08
Problem still exists. Anyone, please? Currently it seems to me like the Ubuntu machine is blocking any connections which has the word "Microsoft" in it. :(

---

