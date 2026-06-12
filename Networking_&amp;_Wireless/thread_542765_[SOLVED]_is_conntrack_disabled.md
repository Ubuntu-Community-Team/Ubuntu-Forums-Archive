---
title: "[SOLVED] is conntrack disabled?"
date: 2007-09-04
forum: Networking &amp; Wireless
---

### Post by fusionisthefuture on 2007-09-04
when i turn on this iptables firewall: 

```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     0    --  localhost            localhost 

Chain FORWARD (policy DROP)
target     prot opt source               destination         

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     0    --  localhost            localhost           
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:https 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:bootps 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:domain 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ftp
```

everything works perfectly, except my FTP:

```
Resolving ftp.alsa-project.org... 160.217.9.25
Connecting to ftp.alsa-project.org|160.217.9.25|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/driver ... done.
==> PASV ... 
```

it hangs here, and wont continue, until i change OUTPUT to ACCEPT

my gentoo freind, who knows a bit more about this than i do, was trying to help me troubleshoot, and he looked through the kernel config dealy (i dont know where he was exactly) and somewhere in there it didnt mark conntrack as built in.  is it disabled?  from what i understand, my computer is connecting to port 21 on the server, and logging in just fine, but when the actual transfer is going to start, which requires us both to move to a different port (seems like its always in the 50000 range), it hangs up, which leads me to believe that its not being seen by iptables as a related or established connection, when it in fact is.  

can someone please help me?
thanks in advance
-arne

p.s. this is kernel 2.6.20-16-generic

---

### Post by fusionisthefuture on 2007-09-11
bump?

---

### Post by noob12 on 2007-09-11
The conntrack support is built as modules in the kernel.  They aren't necessarily loaded. 
```

lsmod | grep conntrack

```
If you see zippo, then do this for example to load the ftp conntrack module (and deps).
```

sudo modprobe nf_conntrack_ftp

```
You can see all of the conntrack modules available using, e.g.
```

find /lib/modules -name "*conntrack*"

```

Look for HOWTOs for iptables rules out on the web at large.  I'm not quite sure your rules are adequate to handle PASV FTP even with connection tracking.  Good luck.

---

### Post by fusionisthefuture on 2007-09-11
thanks alot for the reply.  

it seems that the modules are enabled, when i run the first command, i get 
```
nf_conntrack_ipv4      19468  2 
nf_conntrack           62600  2 nf_conntrack_ipv4,xt_state
nfnetlink               7704  2 nf_conntrack_ipv4,nf_conntrack

```

on the iptables howto note, ive looked high and low, and the only ones i can find are for servers, otherwise people always recommend using a ftontend like firestarter, which i cant stand, and ive had problems with.  

thanks,
-arne

---

### Post by fusionisthefuture on 2007-09-11
well i think i got it.  i had to modprobe nf_conntrack_ftp

it seems to work.
thanks,
-arne

---

