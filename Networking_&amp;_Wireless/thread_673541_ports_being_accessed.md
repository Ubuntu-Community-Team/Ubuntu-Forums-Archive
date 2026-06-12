---
title: "ports being accessed"
date: 2008-01-20
forum: Networking &amp; Wireless
---

### Post by FlashOmega on 2008-01-20
I am wondering if there is a single command to show all the ports currently being accessed (like a shell command) ... does 'nstat' do that?... or does it just list the listening ports? and not all ports being accessed.

If I am not being clear please let me know:D

Thanks

---

### Post by compiledkernel on 2008-01-20
its netstat and yes, it does indeed show an active list of running stuff. 

if your running iptables on your machine, you can also install iptstate (which is a top like application in the terminal that show you active states on your machine as well). 

for the netstat command just run 

netstat -a  (for all port) 
netstat -l (for stuff that just listening).

---

### Post by FlashOmega on 2008-01-20
Thank you very much for the clarification AND extra info.

:D

---

