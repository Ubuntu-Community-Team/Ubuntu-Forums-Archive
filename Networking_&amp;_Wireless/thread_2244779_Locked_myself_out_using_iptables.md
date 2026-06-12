---
title: "Locked myself out using iptables"
date: 2014-09-18
forum: Networking &amp; Wireless
---

### Post by chris137 on 2014-09-18
Hi,
so on my vserver I tried to block all ports I don't need using iptables... You know.. just because.
I changed the policy of INPUT to DROP and made a rule for my ssh port and some other ports I needed.
After some time trying, something with a program still did not work so I thought: Whatever, everything back.
So here is what I wanted to do:
iptables -P INPUT DROP
iptables -F

And here is what I did:
iptables -F
..
And there I got kicked off my server because obviously iptables -F does not affect the policy.

Is there a way to get on my server without reinstalling it?
There is nothing too important on there but it will take some time to get it all back if I had to reinstall it.

---

### Post by SeijiSensei on 2014-09-18
When you flush the rules, the machine should revert to accepting everything on all interfaces.  Can you reboot remotely?  Does that help?

---

### Post by chris137 on 2014-09-18
Well..
Fact is I cannot connect via ssh or http and I changed nothing but iptables.
So I guess what it did is deleting all rules but did not set the default policy.
By myself I can't reboot it but if you have no idea I would contact the support anyway.

---

### Post by chris137 on 2014-09-19
Alright so I contacted the support and apparently I got a pretty cool webinterface which I did not know about.
I can do pretty much everything from there e.g. reset the firewall settings.
So I got it solved with this option.

Rebooting did not help btw.

I'm marking this as solved though it might be not helpful for other users.

---

