---
title: "[SOLVED] fwbuilder - problem activating rule in firewall"
date: 2008-06-26
forum: Networking &amp; Wireless
---

### Post by hmspower on 2008-06-26
really need help here.
i have 2 pc both installed with ubuntu desktop.
1 is meant for firewall and 1 for management installed with fwbuilder.
in the firewall, i set the "firewall.fw" to be installed in "/etc/firewall". i have no problem if i install the policy directly on the firewall itself (as root).

however, when i tried to install using the management pc (as root),   the "firewall.fw" can be copied to "/etc/firewall", but it failed to install. below is some of the log..

```
Logged in 
SSH session terminated, exit status: 0 
Activating new policy 
root@xxx.xxx.xxx.xxx's password: 
--**--**-- 
Logged in 
Activating firewall script generated Tue Jun 24 17:03:23 2008 by admin
/etc/firewall/firewall.fw: 186: /usr/sbin/iptables: not found 
/etc/firewall/firewall.fw: 187: /usr/sbin/iptables: not found 
/etc/firewall/firewall.fw: 188: /usr/sbin/iptables: not found 
/etc/firewall/firewall.fw: 206: /usr/sbin/iptables: not found 
/etc/firewall/firewall.fw: 206: /usr/sbin/iptables: not found 
/etc/firewall/firewall.fw: 209: /usr/sbin/iptables: not found 
/etc/firewall/firewall.fw: 210: /usr/sbin/iptables: not found 
/etc/firewall/firewall.fw: 211: /usr/sbin/iptables: not found 
Rule 0 (lo) 
/etc/firewall/firewall.fw: 220: /usr/sbin/iptables: not found 
/etc/firewall/firewall.fw: 221: /usr/sbin/iptables: not found 
Rule 1 (global) 
/etc/firewall/firewall.fw: 229: /usr/sbin/iptables: not found 
/etc/firewall/firewall.fw: 230: /usr/sbin/iptables: not found 
/etc/firewall/firewall.fw: 231: /usr/sbin/iptables: not found 
/etc/firewall/firewall.fw: 232: /usr/sbin/iptables: not found 
/etc/firewall/firewall.fw: 233: /usr/sbin/iptables: not found 
/etc/firewall/firewall.fw: 234: /usr/sbin/iptables: not found 
Rule 2 (global) 
/etc/firewall/firewall.fw: 242: /usr/sbin/iptables: not found 
/etc/firewall/firewall.fw: 243: /usr/sbin/iptables: not found 
/etc/firewall/firewall.fw: 244: /usr/sbin/iptables: not found 
/etc/firewall/firewall.fw: 245: /usr/sbin/iptables: not found 
/etc/firewall/firewall.fw: 246: /usr/sbin/iptables: not found 
/etc/firewall/firewall.fw: 247: /usr/sbin/iptables: not found 
Rule 4 (global) 
/etc/firewall/firewall.fw: 255: /usr/sbin/iptables: not found 
/etc/firewall/firewall.fw: 256: /usr/sbin/iptables: not found 
/etc/firewall/firewall.fw: 257: /usr/sbin/iptables: not found 
/etc/firewall/firewall.fw: 258: /usr/sbin/iptables: not found 
/etc/firewall/firewall.fw: 259: /usr/sbin/iptables: not found 
/etc/firewall/firewall.fw: 260: /usr/sbin/iptables: not found 
Rule 5 (global) 
/etc/firewall/firewall.fw: 268: /usr/sbin/iptables: not found 
/etc/firewall/firewall.fw: 269: /usr/sbin/iptables: not found 
/etc/firewall/firewall.fw: 270: /usr/sbin/iptables: not found 
Rule 6 (global) 
/etc/firewall/firewall.fw: 278: /usr/sbin/iptables: not found 
/etc/firewall/firewall.fw: 279: /usr/sbin/iptables: not found 
/etc/firewall/firewall.fw: 280: /usr/sbin/iptables: not found 
/etc/firewall/firewall.fw: 281: /usr/sbin/iptables: not found 
/etc/firewall/firewall.fw: 282: /usr/sbin/iptables: not found 
/etc/firewall/firewall.fw: 283: /usr/sbin/iptables: not found 
Policy activated 
Connection to xxx.xxx.xxx.xxx closed. 
SSH session terminated, exit status: 0 
Done 

```

i tried using fwbuilder for windows version in windows pc, and rules can be installed just fine in the firewall. fyi, same "firewall.fwb" is used for all 3 pcs.

i am in a really blurry situation rite now, hope all the gurus and sifus here can help... thanks in advance..

---

### Post by kevdog on 2008-06-26
Why dont you create a symbolic link -- since the iptables executable is really in /sbin rather than /usr/sbin

sudo ln -s /sbin/iptables /usr/sbin/iptables

---

### Post by hmspower on 2008-06-26
where do i insert the command, in managament or firewall?

edit: update.. i just specify the "/sbin/iptables" in "Host OS Settings" > "Path" tab > "iptables" space.. problem solved.. Thanks kev!

---

### Post by majedaly on 2010-10-19
> **hmspower said:**
> where do i insert the command, in managament or firewall?

edit: update.. i just specify the "/sbin/iptables" in "Host OS Settings" > "Path" tab > "iptables" space.. problem solved.. Thanks kev!
Thanks, that did the trick for me as well. Editing the firewall , then choosing "Host OS Settings" > "Path" tab > "iptables"

---

