---
title: "Can't see windows shares over secured wireless network"
date: 2008-05-13
forum: Networking &amp; Wireless
---

### Post by t2hause on 2008-05-13
I'm having an issue with Ubuntu 8.04 and I can't seem to find anyone with the same problem or a solution.  I connect to two wireless networks: one at home and one at work.  The one at home is WEP secured and the one at work is unsecured.  I can browse network shares at work but not at home.  Any ideas?

---

### Post by bluefrog on 2008-05-13
any firewall on your windows at home?

in nautilus, type in the address bar

smb://your-windows-IP/c$

should give you something, if not, your windows is certainly the problem.

---

### Post by t2hause on 2008-05-13
Thanks, I will try when I get home.  Also on the home network is a Maxtor Harddrive that networks to the router directly and I cannot access it either.  As far as I know it doesn't have a firewall.  What could be the issue there?

---

### Post by bluefrog on 2008-05-13
can you ping everything from all boxes?

---

### Post by t2hause on 2008-05-13
The only computer that responds to a ping is the ubuntu box.  However, when I type "smb://windows-ip/c$" and enter a password the share mounts and I can access it no problem.  I just can't browse the shares or ping any windows computers.

---

### Post by t2hause on 2008-05-14
now i'm on the network at work and tried to ping the windows boxes and they wouldn't respond either.  yet, i can browse and access their shares no problem.  could it somehow be because this network is unsecured but my home network uses shared WEP key?

---

