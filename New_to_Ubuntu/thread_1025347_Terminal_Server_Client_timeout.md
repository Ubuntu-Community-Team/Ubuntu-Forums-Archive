---
title: "Terminal Server Client timeout"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by kscarroll54 on 2008-12-30
Brand new Inspiron mini with Ubuntu (lpia). Have to RDP to XP workstation at my office. Can't seem to connect. The only error I get is that it's timing out. Is there a log somewhere that would offer more information? I've tried adding it to /etc/hosts, using the :<port number>, verified that the firewall has a hole punched for the appropriate port. RDP works fine from my husband's Vista laptop.

Help?:confused:

---

### Post by scorp123 on 2008-12-30
> **kscarroll54 said:**
> Have to RDP to XP workstation at my office. Can't seem to connect. The only error I get is that it's timing out. And how are you trying to access that machine in the office? If your office uses private range addresses + NAT then they'd have to properly configure port-forwarding on their firewall or else you will not be able to get through to that office PC. Or maybe you're supposed to use some VPN solution?

Something else that confused me was what you wrote about your **/etc/hosts** ... this file resolves hosts which might not have a DNS entry and it helps your own machine to resolve itself when there is no DNS available. Port numbers or anything like that have no business being in that file, you're only supposed to enter hostnames and their IP addresses into that file, nothing else.

---

### Post by stephanvaningen on 2008-12-30
Does the Vista-computer connect to the company with IPSec/VPN-software first?

Can you ping the target computer on both laptops via IP address? What's the result on both?

---

### Post by kscarroll54 on 2008-12-30
First, let me apologize for not being clear. I tried adding :<port> to the rdp address.

My office does not use vpn, they do not use nat routing, they do not use private addresses. My husband's vista machine just uses standard rdp protocaol.

And yes, I can ping that machine from ubuntu.

Thanks in advance for your assistance! I'm thoroughly enjoying learning this! (except for the part where I really need to get into my work machine and do some work today!) :)

---

