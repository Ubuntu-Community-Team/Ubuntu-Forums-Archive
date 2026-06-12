---
title: "Redirecting Port 80 Traffic"
date: 2007-02-12
forum: Networking &amp; Wireless
---

### Post by Rootcomputing on 2007-02-12
I am trying to redirect traffic on port 80 to google.com. I am attempting to do this using iptables with the command of --->

iptables -t nat -A PREROUTING -p tcp --dport 80 -j DNAT --to 72.14.207.99:80


I am using ettercap to ARP poison the network in order to have all nodes routed through me. I have ip forwarding enabled, but cant seem to direct the traffic. I do see it coming through me and have verified that the arp table has in fact been compromised, but the traffic continues to flow with no interference. Any suggestions?

---

### Post by kidders on 2007-02-12
Hi there,

This may be a dumb question, but are you sure there are no iptables rules with higher precedence that could be being applied to the packets you want redirected? I've spent a few minutes thinking about this post, and I can't think of another reason the command you posted would fail, at the moment. :-(

Sorry if you've already checked this.

---

### Post by Rootcomputing on 2007-02-12
From what I see the NAT parameters are PREROUTING, POSTROUTING and one to do it locally. Locally it works fine. I saw this website...

[http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/security-guide/s1-firewall-ipt-fwd.html](http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/security-guide/s1-firewall-ipt-fwd.html)

And that has the same exact setup, I tried using the -i switch but it sill made no difference.  As far as I know there are no higher commands. So this should work, just not sure why its not,

---

### Post by kidders on 2007-02-12
> **Rootcomputing said:**
> I tried using the -i switch but it sill made no difference.I would have done that too, just in case.

This is so weird... I've done this type of thing before, and it's always worked. :-( Have you checked to make sure the redirected packets aren't being dropped *after* the redirect? (If that's even possible!) You could try generating lots of data, and using the iptables **-v** switch to keep an eye on DROP policies/rules.

---

### Post by Rootcomputing on 2007-02-13
I am going to mess with it more tonight, but we had ip forwarding on the laptop and it was showing the data running right through us. I think it worked fine when we had the iptables enabled, but I could be wrong and it might have just dropped them all. I am certain it wasn't doing what we wanted though. 

I am going to experiment tonight so Ill keep you informed. Thanks for the help so far.

---

### Post by kidders on 2007-02-14
Hmm... ](*,)

Sorry I've been so little help to you. Let me know what you discover!

---

