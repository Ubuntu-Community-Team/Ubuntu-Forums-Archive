---
title: "post-up script and networkmanager"
date: 2008-09-11
forum: Networking &amp; Wireless
---

### Post by Internux on 2008-09-11
Hello,

I'm trying to put a post-up script, which should be launch once any interface is up (eth0, wlan0, wifi0, eth1.... any but lo).

In some doc, I found that we just have to put some config in
/etc/network/interfaces
So did I, it worked nicely.
BUT.... networkmanager does NOT manage interfaces which are described in "interfaces" file.....

So, how can I do to make understand NM that I want him to run one script as soon as he catches an IP on an interface ?

Thanks in advance

C.

---

