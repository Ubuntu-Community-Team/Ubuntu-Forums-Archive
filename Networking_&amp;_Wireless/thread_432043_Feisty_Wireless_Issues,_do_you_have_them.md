---
title: "Feisty Wireless Issues, do you have them?"
date: 2007-05-03
forum: Networking &amp; Wireless
---

### Post by Whiffle on 2007-05-03
Okay I've been searching around here for a bit because I'm having wireless issues with feisty.  I noticed I'm not the only one, and I thought I'd see if I could get some more information about who is having what problems.  That is what this thread is for, in theory.

Here is what I've got:
IBM thinkpad T43
Intel Pro Wireless ipw2200 driver 
network-manager Version: 0.7.0-cvs20061010 (need this for LEAP)


Up until last week sometime, it was going swimmingly, i was even connecting to LEAP.  But, I don't know what changed but here is what is going on:

I can connect to an open wireless network no problem, everything works.  When I connect to the LEAP network at school (which works under windows), I put in my login info, and it connects.  I get an IP address, I have DNS servers, everything.  Everything I know to check says that it should be working, but it doesn't.  If I ping my router, I get this:
```

ping: sendmsg: Operation not permitted

```

Websites get an "unknown host"

If I watch network manager's console output, I see similar messages sprinkled throughout.  

Anybody having similar experiences?

---

### Post by Whiffle on 2007-05-05
Ok so, I might have figured this out...it seems to be an iptables issue and not a network manager issue.  If I reboot, everything behaves as above (except for some reason I can't even do an open network now), but if I run these commands (with sudo or as root of course)

```

iptables -F
iptables -A INPUT -j ACCEPT
iptables -A FORWARD -j ACCEPT
iptables -A OUTPUT -j ACCEPT

```

It works.  I havn't gotten to try it on an encrypted network yet, but I intend to do that this afternoon.

---

### Post by Whiffle on 2007-05-05
Woo hoo.  It is working with LEAP here at school as well.

---

