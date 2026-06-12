---
title: "Another SSH problem, have already tried a lot of things"
date: 2007-03-04
forum: Networking &amp; Wireless
---

### Post by Subterranean on 2007-03-04
Just from searching these forums and google I realise this is a common problem, but I'm getting the "ssh: connect to host XXX.XXX.XX.XX port XXXXX: Connection refused" message all the time when i try to connect to my system using my *external* IP address. If I use my internal one (192.168.x.x) or "localhost" it connects fine, leading me to believe that sshd is running fine. Here are some of the things I've done:
[LIST]
[*]Made sure port 22 was forwarded to my computer through my router
[*]Changed the port used to a different 5 digit one. Changed this in the SSHD and SSH and also made sure I was forwarding this new port. Online tests show it to be forwarded to me correctly.
[*]Tried running telnet using "telnet <my External IP>" which told me it had connected fine, although I'm not sure which user/pass you use to log onto it, so i exited. Obviously I would like to use the more secure ssh though.
[*]Typing " sudo iptables -vL" gives the expected output
[*]I have not yet been able to test this on another computer connected to the internet, though I dont see why my current computer would not be able to connect if others could.
[/LIST]

Can anyone come up with any other possible reason this would not be working?

EDIT- I should also mention I can connect to another external machine using ssh with no problem, just not my own computer.

---

### Post by gradedcheese on 2007-03-04
This always worked fine for me... are you sure your NAT is set up correctly?  Can you SSH into some external computer (not on your LAN) and then, from that session, try to SSH in to your PC via the external IP? ;)  Perhaps going out and back in via the router is the problem, due to some configuration there.

---

### Post by Mr. C. on 2007-03-04
> **Subterranean said:**
> "ssh: connect to host XXX.XXX.XX.XX port XXXXX: Connection refused" 

"Connection refused" means that that no socket bind occurred; hence either there's nothing listening, or a firewall blocked the request.

Are you saying you're trying to connect from your LAN using your WAN ip address?

MrC

---

