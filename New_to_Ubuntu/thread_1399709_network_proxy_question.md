---
title: "network proxy question"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by crlang13 on 2010-02-06
hey,

I'm running the Ubuntu 9.10 Netbook remix on my netbook.

I get onto my university's network fine.  At uni, to surf the web, you have to go through the university's proxy, which works either through auto detect in firefox or network proxy program that came with Ubuntu - which I prefer because then the proxy setting are system wide.

What I don't understand how to do is to get the system to automatically not run through the proxy when I'm not using the university wireless.  There is an "ignored hosts" tab, but I'm not terribly sure what to do with it (sorry, total newbie).

I think there's an add on for firefox that will automatically swap the proxy settings based on network, but I was hoping someone out there knew how to do it system wide.

Thanks

---

### Post by rampageoberon on 2010-02-06
Maybe you can consider some sort of iptables rule. Not too sure if it'd work as I can't seem to get the authentication right.

```
/sbin/iptables -t nat -A OUTPUT -p tcp -s <your ip /mask> --dport 80 -j DNAT --to <your proxy for uni>:<proxy port>
```

Something like the above is what I'm thinking about. others in the community may have better suggestions.

Edit: Something I came across that might be useful to read. [http://www.karlrupp.net/en/computer/nat_tutorial](http://www.karlrupp.net/en/computer/nat_tutorial)

---

### Post by crlang13 on 2010-02-06
hmmm,

I'll look into that.  I still have alot to learn about the whole command stuff, but you have to start somewhere I suppose.  Thanks for the link as well, it will be of help.

It'll also be a good way to put off homework...

---

