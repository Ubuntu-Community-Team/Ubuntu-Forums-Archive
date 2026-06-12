---
title: "Unable to access webmin - server firewall problem?"
date: 2013-12-08
forum: Networking &amp; Wireless
---

### Post by Indian Summer on 2013-12-08
Hi,

I have a Ubuntu 12.04 server where I've at one point installed webmin on port 10000, but now I can't access it from outside any more. (My browser says "Connection refused".) If I ssh to the server, I can access it from the command line though.

So I thought it would have to be a firewall issue. Well, I temporarily did "ufw disable", but I still couldn't access it. 

It's not a problem on my laptop as I can't access it from elsewhere either.

What could be the problem here? Where should I be looking to figure this out?

---

### Post by SeijiSensei on 2013-12-08
If by "outside" you mean from somewhere on the Internet outside your network, you need to check your router.  It must have port 10000 open and forwarded back to the same port on your server.  However I'd suggest that you forward some other arbitrary high port (1024-65535) back to port 10000 to thwart simple port scanners trying to find breakable webmin installations.  "Security through obscurity" won't stop dedicated attackers but will limit automated scanners.

---

### Post by Indian Summer on 2013-12-08
Thank you for the input, SeijiSensei.

The server is actually a VPS - in fact hosted by Linode. (I see you have a link to their admin docs in your signature.) 

It seems I may have misunderstood the relationship between ufw and iptables. I thought ufw was the easy-to-use front-end to iptables, but it seems I was wrong. I ran some commands to [disable my iptables rules]("http://www.cyberciti.biz/faq/turn-on-turn-off-firewall-in-linux/"), and then I was finally able to connect to webmin again. 

```
iptables -F
iptables -X
iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT
```

I may not know exactly what I'm doing here ... Would someone care to try and explain?

---

### Post by SeijiSensei on 2013-12-09
Yes, you just tore down your firewall and exposed the machine to the Internet frontier.  Most of those commands clear any existing rules.  The last three set the default "policies" (-P) for INPUT, OUTPUT, and FORWARDing across interfaces to ACCEPT all traffic.

Until you know what you want to do, I *strongly* recommend restoring whatever firewall you had running before, then spend some time learning about iptables rules.  After you have restored the firewall, run this command:

```
sudo iptables -L -nv
```

to list all the rules currently in effect.  You'll probably see some rules with "--dport" fields that permit particular services; e.g., "--dport 22" is designed to enable access to SSH.  You want to modify the default rules by adding one similar to the SSH rule but uses "--dport 10000" as well.  I write firewalls by hand so I don't know how to modify UFW for this purpose.

I believe you can configure Webmin to use a different port for access; I recommend doing so.

---

### Post by Indian Summer on 2013-12-09
> **SeijiSensei said:**
> Yes, you just tore down your firewall and exposed the machine to the Internet frontier.  Most of those commands clear any existing rules. The last three set the default "policies" (-P) for INPUT, OUTPUT, and FORWARDing across interfaces to ACCEPT all traffic.
Exactly - that is what I wanted to do, as apparently ufw wasn't working properly (or as I expected) with these rules.

> Until you know what you want to do, I *strongly* recommend restoring whatever firewall you had running before, then spend some time learning about iptables rules.  After you have restored the firewall, run this command:

```
sudo iptables -L -nv
```

to list all the rules currently in effect.  You'll probably see some rules with "--dport" fields that permit particular services; e.g., "--dport 22" is designed to enable access to SSH.  You want to modify the default rules by adding one similar to the SSH rule but uses "--dport 10000" as well.  I write firewalls by hand so I don't know how to modify UFW for this purpose.
Thank you for the concern, but I personally now much prefer just using ufw :) After I disabled the iptables rules, I enabled ufw again, and the default ufw rules were apparently quite strict. (I think all ports were blocked, actually. Luckily I had already configured it to allow webmin.) So I opened up the ports I needed there: http on port 80, a couple for the email server, webmin and of course ssh.  
> I believe you can configure Webmin to use a different port for access; I recommend doing so.
Yes, that is a good point. I will find a different port here. "Security through obscurity" has some appeal with me, to be honest, just as long as it doesn't make my own life unnecessarily complicated.

---

### Post by SeijiSensei on 2013-12-11
I would hope that all ports are blocked by default.  The security model for Ubuntu is to have nothing running that requires an open port.  (In comparison, RedHat-flavored systems come with SSH enabled by default.)

---

