---
title: "resetting iptables"
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by sprouty on 2008-11-24
Hi,

I've got a box set up in a remote location and had privously locked it down access by ip address. Unfortuatly i've only got ssh access into the box and when i run the command iptables -F the box freeze up and i can only regain access by doing a reboot (i do the reboot through a cronned script)

Anyone got any ideas how i can remove the iptables rules through ssh access!

Many Thanks,
Sprouty

---

### Post by s3gfault on 2008-11-24
I'm not sure whats happening, it seems like when you flush the iptables, then a default rule kicks in that denies packets (even though the default after flushing should be accept).  In any case, instead of doing /sbin/iptables -F try doing this:

/sbin/iptables -A INPUT --dport 22 -j ACCEPT

---

### Post by madverb on 2008-11-25
I had the same problem... When you flush all the settings it doesn't change the policies for each chain. The policy would have been set to deny.

---

### Post by sprouty on 2008-11-25
hey ta,

Just to let you know i put all this in a bash script and it worked fine


iptables -F
iptables -A INPUT -j ACCEPT
iptables -A OUTPUT -j ACCEPT
iptables -A FORWARD -j ACCEPT

---

