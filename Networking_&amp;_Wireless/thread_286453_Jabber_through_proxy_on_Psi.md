---
title: "Jabber through proxy on Psi"
date: 2006-10-27
forum: Networking &amp; Wireless
---

### Post by PriceChild on 2006-10-27
Ok so here's the deal...

I'm behind a proxy[LIST]
[*]Auto-configuration script - [http://www.york.ac.uk/proxy.config](http://www.york.ac.uk/proxy.config)
[*]Proxy address: wwwcache.sns.york.ac.uk - Port number: 8080[/LIST]Gaim connects to my gmail jabber perfectly first time (not qunu.com though...)

I'm trying to use Psi to get msn transport in with the gaim client.

However, i can't get Psi to connect.

Starting off by just trying to register a new jabber.org account through it, (will mess with gmail later)

When using gaim, in firestarter i can see a connection on 5222 Xmpp-client.

Whenever i set up the proxy in Psi, it tries to access through 8080 not 5222 obviously... However it won't even think about appearing in firestarter if i don't set the proxy.

I'm tired and haven't got a clue...

---

### Post by kOoLiNuS on 2006-11-15
I've got Psi 0.10 and want to use it with googletalk and/or my jabber account.
I'm behind an authenticated proxy, so i went to the program interface and set up it properly. My problem is that i can't connect no matter what type of proxy i choose (HTTP "connect", socks). Any idea / tips to get it through ?

---

### Post by PriceChild on 2006-11-16
I've gotten around it using a different method.

I'm using ssh tunneling.

If you've got one, then:```
ssh -L 7779:talk.google.com:5222 <<sshserveraddress>> -l <<sshserverloginname>>
```Then tell the jabber client to connect to localhost on port 7779 :D

---

