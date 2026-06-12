---
title: "SSH works with dial-up, not with ADSL"
date: 2006-10-21
forum: Networking &amp; Wireless
---

### Post by cheesecake on 2006-10-21
I want to SSH my computer at work from home.

This works fine if I use a dial-up connection.

When I try to SSH using ADSL the connection times out.

I have a Belkin G wireless router, with a firewall. I cannot connect when the firewall is disabled. I have no firewall on Ubuntu.

I suspect that I need to do something with the router, or there is an issue with the ISP. A lot has been written on accessing an SSH server through a firewall or router, but I think this is a slightly different problem. 

If anyone has any ideas, they would be appreciated.

---

### Post by cheesecake on 2006-10-27
Problem resolved now.

My machine is at a University, and my dial-up was to the University, so of course I could SSH it through the dial-up! I needed to request to have port 22 opened on the machine at work to SSH when not already on the network.

A few useful things I found out during this process:

* Use nmap to see if the machine you are trying to access has port 22 (or any other) open by, e.g.

nmap -P0 -p 22 [ip address of machine]

* If you can VPN the network your machine is on, then you may get around opening port issues.

* If you want your home machine, with a router, to be SSHable, then, as many other sites say, forward port 22 on the router. For my Belkin router there is an idiots how to, with pictures, here:

[http://www.portforward.com/english/routers/port_forwarding/Belkin/F5D7632-4/SSH.htm](http://www.portforward.com/english/routers/port_forwarding/Belkin/F5D7632-4/SSH.htm)

---

