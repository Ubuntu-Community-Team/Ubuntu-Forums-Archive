---
title: "PXE booted router - iptables issue"
date: 2007-07-28
forum: Networking &amp; Wireless
---

### Post by dannyboy1121 on 2007-07-28
So I thought I would be smart and turn my PXE booted server in to a router (disk NFS mounted on to my NAS) .. 

I got hold of a usb modem .. followed the speedtouch guide and tested it - all working well ..

Went to apply some IPTABLES rules (either directly or using Shorewall) and *pop* I lose sight of the disk.

****.

My guess is that this fundemental to the way iptables works rather than to do with rule sets. 

I would be grateful if anyone with iptables experience could confirm this is expected behaviour.

---

### Post by noob12 on 2007-07-29
If by running the firewall config tool the default rule on the chains gets set to DROP (before the ACCEPT rule for NFS traffic is in place) I'd say yes.
If you set them up manually, you can set it to DROP only after you've got enough ACCEPT rules in place to function.

---

### Post by dannyboy1121 on 2007-07-29
I'll take a look again and see if I can tweak the rule order to stop it from happening .. although I though that my first rule was set to accept lan traffic to the lan interface.

*runs off to power up tuxbox*

---

### Post by noob12 on 2007-07-29
I'm speaking of the default treatment (policy) on the INPUT and OUTPUT chains (which applies while there are no rules, and in general whenever you hit the end of the chain without matching a rule).  In your case, you'd need to force these to ACCEPT  while you build the chain.  At the end, provided you are really accepting everything you need to, you should be able to put them back at a non-permissive policy like DROP.
```

iptables -P INPUT ACCEPT
iptables -P OUTPUT  ACCEPT

```

---

### Post by dannyboy1121 on 2007-07-29
dude .. many thanks for this info. I know bugger all about iptables so your help is appreciated.

---

