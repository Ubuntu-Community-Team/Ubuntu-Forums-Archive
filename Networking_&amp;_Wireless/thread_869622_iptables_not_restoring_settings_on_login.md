---
title: "iptables not restoring settings on login?"
date: 2008-07-25
forum: Networking &amp; Wireless
---

### Post by AVT- on 2008-07-25
Ever since latest updates, iptables hasn't been restoring settings on login.

I have this in my /etc/network/interfaces:

```
auto eth0
iface eth0 inet dhcp
pre-up iptables-restore < /etc/iptables.rules
post-down iptables-restore < /etc/iptables.rules
```

Yet, for some reason it isn't working, since at login, I have to run iptables-restore < /etc/iptables.rules to get my settings to restore correctly.

Has something changed?

(I should note, when I say latest updates, I'm talking everything since June 22, which is the last time I was working with the system in question)

---

### Post by SpaceTeddy on 2008-07-27
long shot - i remember an update to ufw a few day back. The only reason i noticed it was because i never, ever use any programm to configure iptables. I always do it myself. So i was wondering why i had this even installed and why it was updateing. 

Maybe it has something to do with that...

just an idea... not a real solution...

---

### Post by kevdog on 2008-07-27
Wouldn't this statement:

post-down iptables-restore < /etc/iptables.rules

in actuality be:

post-down iptables-save > /etc/iptables.rules

Isn't that want you want to do?? Actually save the ruleset into a file when the interface is taken down?

---

