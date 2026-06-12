---
title: "How does a firewall work?"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by wlraider70 on 2009-06-24
Ok I have a few basic questions about how a hardware firewall works. 

My setup is like this. 

ISP -> firewall -> 24 port switch-> server and users. 

So the firewall blocks packets from the wan (Internet) to the LAN right?
Does the firewall block hardwired packets from one user to another?
Also should I have software firewalls disabled on LAN systems?

---

### Post by nandemonai on 2009-06-24
> **wlraider70 said:**
> Ok I have a few basic questions about how a hardware firewall works. 

My setup is like this. 

ISP -> firewall -> 24 port switch-> server and users. 

So the firewall blocks packets from the wan (Internet) to the LAN right?
Does the firewall block hardwired packets from one user to another?
Also should I have software firewalls disabled on LAN systems?

In that setup the firewall will only allow or deny packets from going to the Internet/WAN or coming from the Internet/WAN. It will not block anything on the LAN. For that you would need either a gateway / proxy machine to act as a overall LAN firewall or software firewalls on the machine(s) you want to protect internally.

Running software firewalls behind a hard firewall is fine if that's what you need. Generally the only reason you would discourage it would be lack of need if you have a general 'external' firewall protecting you from the Internet and trust local users to do the right thing OR to prevent configuration headaches down the line.

---

### Post by wlraider70 on 2009-06-24
so i got an internal to internal port error, that would NOT be from my firewall?

---

### Post by The Cog on 2009-06-24
The firewall can only block packets going to/from the internet in your setup - it can't interfere with conversations between machines internally. Strictly speaking, the firewall selectively drops packets coming from the internet unless they are in response to connections initiated from your LAN.

You may want to also install firewalls on your internal PCs to prevent them from connecting to each other - it depends on your level of paranoia really. It might make life difficult sometimes, but also might just prevent the spread of a virus if it gets into one of your PCs.

---

