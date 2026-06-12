---
title: "Ubuntu blocks MS sites and services?"
date: 2008-03-08
forum: Networking &amp; Wireless
---

### Post by Prism on 2008-03-08
Hi there,

I'd like to start a new thread about it because it seems like the old one doesn't get attention. Also, it will be shown in the unanswered posts section.

I have a home network where my Ubuntu machine is connecting to the internet and serves as a getway to a Windows machine.

Everything is fine in the ubuntu machine, but when I try to surf from the windows machine to microsoft.com, windows update site or connect to Windows Messenger/Live Messenger I don't get any connection.

I'm using static IP connection in the home network and PPPOE to connect to the internet.
My iptables -L output looks like that:

```

Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            
ACCEPT     0    --  anywhere             anywhere            
Badflags   tcp  --  anywhere             anywhere            tcp flags:FIN,ACK/FIN 
Badflags   tcp  --  anywhere             anywhere            tcp flags:PSH,ACK/PSH 
Badflags   tcp  --  anywhere             anywhere            tcp flags:ACK,URG/URG 
Badflags   tcp  --  anywhere             anywhere            tcp flags:FIN,RST/FIN,RST 
Badflags   tcp  --  anywhere             anywhere            tcp flags:FIN,SYN/FIN,SYN 
Badflags   tcp  --  anywhere             anywhere            tcp flags:SYN,RST/SYN,RST 
Badflags   tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,PSH,ACK,URG/FIN,SYN,RST,PSH,ACK,URG 
Badflags   tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,PSH,ACK,URG/NONE 
Badflags   tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,PSH,ACK,URG/FIN,PSH,URG 
Badflags   tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,PSH,ACK,URG/FIN,SYN,PSH,URG 
Badflags   tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,PSH,ACK,URG/FIN,SYN,RST,ACK,URG 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-reply 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 
Firewall   icmp --  anywhere             anywhere            
ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:22054 
DROP       udp  --  anywhere             anywhere            udp spt:netbios-ns dpt:netbios-ns 
Rejectwall  0    --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain Badflags (11 references)
target     prot opt source               destination         
LOG        0    --  anywhere             anywhere            limit: avg 10/min burst 5 LOG level warning prefix `Badflags: ' 
DROP       0    --  anywhere             anywhere            

Chain Firewall (1 references)
target     prot opt source               destination         
LOG        0    --  anywhere             anywhere            limit: avg 10/min burst 5 LOG level warning prefix `Firewall: ' 
DROP       0    --  anywhere             anywhere            

Chain Rejectwall (1 references)
target     prot opt source               destination         
LOG        0    --  anywhere             anywhere            limit: avg 10/min burst 5 LOG level warning prefix `Rejectwall: ' 
REJECT     0    --  anywhere             anywhere            reject-with icmp-port-unreachable

```

The windows machine doesn't have a firewall for now.

What can I do about it?

Thanks. :)

---

### Post by handydan918 on 2008-03-08
Caveat: I am far from being an iptables guru.

However.

This line:

```
DROP       udp  --  anywhere             anywhere            udp spt:netbios-ns dpt:netbios-ns 
```

is suspicious to me, because some of the protocols listed are very likely in use by the M/S site. 
40.00 usd for a NAT router might be a good investment...unless you just enjoy this sort of hackery...

:)

---

### Post by Prism on 2008-04-05
I'm sorry about the late response, I've been quite busy until now.

Disabling this line (or actually any other DROP line in iptables) doesn't work. Ubuntu still blocks Windows Update, Microsoft site and Windows Live Messenger.

I've been looking everywhere today, yet I couldn't find the answer. I hope it will be fixed soon because it's really annoying - and it gives my brother an opportunity to claim that windows is better than ubuntu. :)

---

### Post by superprash2003 on 2008-04-05
i have a similar setup like yours , but it works fine here.are you using firestarter by any chance?

---

### Post by Prism on 2008-04-05
No.

Are you using plain iptables script or a more advanced program? Could you describe me how you configured your network?

---

