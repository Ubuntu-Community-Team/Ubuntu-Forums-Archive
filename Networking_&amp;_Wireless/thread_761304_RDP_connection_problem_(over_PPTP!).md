---
title: "RDP connection problem (over PPTP!)"
date: 2008-04-21
forum: Networking &amp; Wireless
---

### Post by lucaspr on 2008-04-21
First of all.. 

The PPTP - VPN connection is working fine.. I'm able to ping the Windows 2003 server!
So that is working.

I can make a RPD connection using the administrator account, But when I log in as a user the system gives me the following error:
 (First in dutch than my translation in English.. Maybe there are dutch forum user/readers who can translate this sentence better than me :) )

In dutch: U moet beheerdersrechten hebben als u zich op deze computer wilt aanmelden

my translation: You need to have administrator rights when u log on to this computer.

But when I use a Windows XP computer over here, set up a VPN connection and use mstsc and log on as the same user, no problem.. I can log on fine, read mail do what I can do as the user..

How can this be? What did I forget? Does it has something to do with DNS resolution? Then how can I solve this?

---

### Post by lucaspr on 2008-04-21
Solved it..

rdesktop in combination with -0 (zero) was the problem! 

I replaced 
rdesktop -u XXX -f -N -z -0 ip.of.terminal-server
with
rdesktop -u XXX -f -N -z ip.of.terminal-server

Then it works great! :popcorn:

---

