---
title: "Proxy auto-config: Desktop vs. Server configuration"
date: 2014-10-17
forum: Networking &amp; Wireless
---

### Post by Lucas_Ventura on 2014-10-17
Hello,

I've been using Ubuntu Desktop as a headless machine and it had worked "fine"
The Desktop machine is an VMWare in a network behind a proxy, which is configured with a [PAC script]("http://en.wikipedia.org/wiki/Proxy_auto-config"). The script is pretty long, and the best part, is that it checks if the destination can be reached without, so the connection is DIRECT.
In Desktop version, the configuration through GUI is easy as pie (Settings >> Networking >> Proxy settings >> Method >> Authomatic), and works everything: command line, apt, browsers, ....

But now, I wanted to switch to an Ubuntu Server, because I don't need at all the GUI, as all I do in this system is terminal based. Everything I had on Desktop can be ported to Server without no-problem, except, that proxy auto-config.
There is *no source anywere* on the Internet, on how to configure a PAC script on a headless machine.
Is this impossible?
How does Desktop version configure the script "under the hood"? I don't mind to stick to an Ubuntu command.
But I find this lack of feature really annoying.

And I'm not the only one with this need. Some references (all from StackOverflow network ^^)
[http://askubuntu.com/q/527875/305412](http://askubuntu.com/q/527875/305412)
[http://stackoverflow.com/q/25125606/1099452](http://stackoverflow.com/q/25125606/1099452)
[http://unix.stackexchange.com/q/84061](http://unix.stackexchange.com/q/84061)
[http://superuser.com/q/323488](http://superuser.com/q/323488)

Thanks!

---

### Post by TheFu on 2014-10-17
Not sure if this will work or not, but [https://stackoverflow.com/questions/19199424/squid-forward-to-another-proxy-with-authentication-details-for-the-parent-prox](https://stackoverflow.com/questions/19199424/squid-forward-to-another-proxy-with-authentication-details-for-the-parent-prox) says that running squid on the server can connect to other proxies as needed. All the desktops would just point to Squid for their proxy or I suppose you could configure it as a transparent proxy.

Hope this helps. Not sure it will.

---

### Post by Lucas_Ventura on 2014-10-24
Unless I could point to localhost, and squid could "parse" the PAC file, and then do the work, it doesn't fits my problem.
Thanks anyway!

But I think that the "multi-user host" didn't make clear my question.
I have re-did the question, to focus on the main problem ^^

---

### Post by TheFu on 2014-10-24
I've never heard of a proxy server reading input from a PAC, but I'm fairly sheltered.  It shouldn't be too hard to read the existing PAC and make rules for the server, however.

Sorry - got no solution.

---

### Post by Lucas_Ventura on 2014-12-15
Again, misunderstanding:

> **TheFu said:**
> I've never heard of a proxy server reading input from a PAC

The Ubuntu Server I want to build, is a client machine inside a network. So it has to get configured as other machine inside the networkt, connecting to internet through a proxy.
It will not serve as proxy.

The "simple question" is:
> 
Why Ubuntu Desktop version can be configured to use a PAC as proxy (using GUI) and Ubuntu Server doesn't have any way to do it via command?


---

