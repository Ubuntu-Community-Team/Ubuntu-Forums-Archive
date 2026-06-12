---
title: "firewall or not with router"
date: 2008-06-25
forum: Networking &amp; Wireless
---

### Post by Revvion on 2008-06-25
Oke, i got a router with a build in firewall so my question is do i need to configure iptables(firewall) as well or will this not add anything to security?

---

### Post by netztier on 2008-06-25
> **Revvion said:**
> Oke, i got a router with a build in firewall so my question is do i need to configure iptables(firewall) as well or will this not add anything to security?

In most cases, the NAT/PAT function in your router will shield your LAN off from almost anything that comes from the outside - but not from what comes inside the things you let in: Malicious Mail or Web content that could profit from security flaws in your mail program or browser won't be stopped by neither a firewall, nor iptables, nor a NAT/PAT router (however a content scanning proxy might be able to).

If you want to restrict or control what is going *out* to the internet from your PC, you could indeed use iptables on the PC itself.

In general, I recommend this: no firewall on the PCs if they're behind a router, but keep an eye on which network enabled services you run on your PC - activating a service such as SSH, Apache or Samba always lead to a port being opened and being put into LISTENING state for incoming connections - can't avoid that, this has to be like this.

Without appropriate port-forwardings, a router will shield off connection attempts to these services from the Internet, so in sum, you're still pretty safe, even without iptables. If all ports are closed, there's nothing to protect and nothing for iptables to filter - so why run in in the first place?


regards

Marc

---

### Post by Revvion on 2008-06-26
oke thanks

---

