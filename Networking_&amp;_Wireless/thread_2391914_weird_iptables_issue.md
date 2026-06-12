---
title: "weird iptables issue"
date: 2018-05-14
forum: Networking &amp; Wireless
---

### Post by sniper8752 on 2018-05-14
I noticed my iptables has been weird recently.  I could not figure out how http/s traffic was getting through, so long story short, I ran sudo iptables -I INPUT -j DROP.  It kicked my ssh session.  I am not able to get in via ssh now.  But for some reason, I can still browse the web, and the content is not cached either. I've also dropped OUTPUT traffic, and everything still works on my client.  I can ping and browse the web on the client, but on my server,  I can not ping or use wget.  How is this traffic getting through, and some not?

Edit:
I figured out why this is happening.  My forward chain is allowing all of these connections.  My two rules I have are:
```
-A FORWARD -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A FORWARD -s ip -i eth0 -o eth1 -m conntrack --ctstate NEW -j ACCEPT
```

Is there any way to limit the type of connections?  This seems to be a wildcard, allowing all kinds of traffic.  And how is traffic allowed in and out, when the default policies are set to explicitly drop traffic?

---

### Post by SeijiSensei on 2018-05-15
Do you just want to block browsing or everything?  If you just want to block outbound HTTPS requests add
```

/sbin/iptables -A INPUT -p tcp -i eth0 --dport 443 -j REJECT

```
assuming eth0 points to your internal LAN.  If you block all RELATED,ESTABLISHED traffic you won't be able to use any services.

You don't say where these rules are stored.  If they're on the client, I'd dump that approach and just apply rules to whatever routes traffic out to the Internet.  The "server" perhaps?

---

