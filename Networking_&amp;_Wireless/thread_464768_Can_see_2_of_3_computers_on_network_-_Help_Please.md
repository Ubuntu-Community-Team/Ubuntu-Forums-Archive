---
title: "Can see 2 of 3 computers on network - Help Please"
date: 2007-06-05
forum: Networking &amp; Wireless
---

### Post by jba6511 on 2007-06-05
As the title explains, I can see my windows xp computer as well as the shares on my laptop when I go to the network from places. I can not see my desktop however. My desktop is running ubuntu fiesty and so is my laptop. On my desktop I can see the shares I have selected to share on the desktop, but I do not see the windows xp computer or the laptop. So in summary:

From laptop:
shares on windows xp (ubuntu) 192.168.1.111
shares on laptop itself                 192.168.1.100
can NOT see desktop (ubuntu)

From desktop:                                192.168.1.1
shares on desktop itself
can NOT see laptop or windows xp

I set up samba exactly the same and all computers are on the same workgroup (which I called network). All computers are also set to use static ip addresses (see scheme above) with the same DNS and gateway. Any ideas why I can not see the other computers from my laptop?

---

### Post by dmizer on 2007-06-05
my guess is because you have a firewall blocking access.  windows firewall?  zone alarm ... something like that.

also ... it's possible that your network card has file and printer sharing disabled.  check network connections > tcpip properties.

edit:
wait ... i'm confused.

you have three computers.  two ubuntu (desktop and laptop) and one xp?
the ubuntu desktop cannot see the ubuntu laptop or windows xp?

if that's the case ... have you configured firestarer to have your desktop act as a dhcp server for internet connection sharing (which would explain why the desktop has a 1.1 address while your other machines have a 1.100 address).

---

### Post by jba6511 on 2007-06-05
sorry desktop is 192.168.1.101. That is correct two ubuntu and one xp and the ubuntu desktop can not see the others. I have not enabled any firewalls in ubuntu and the only one enabled in windows is the default windows xp firewall. I do not think it is a firewall issue as my laptop can see the xp machine just fine.

---

### Post by dmizer on 2007-06-05
on the ubuntu desktop ... what is the output of this command:
```
smbtree
```
and ... what are you doing to try to mount the shares from xp and the laptop?

---

### Post by jba6511 on 2007-06-05
nevermind guys, I was my fault. I checked the network connections again and I have 2 eth interfaces, 1 that is built into the motherboard and one I added in myself. I am using the one I added in and had it set to auto dhcp. I changed it to static and now I can see everyhthing. Sorry for the confusion - should have checked this first. Thanks for the help though

---

### Post by dmizer on 2007-06-05
heh ... sometimes it's the simple things that get overlooked. ;)  glad you got it fixed though!

---

