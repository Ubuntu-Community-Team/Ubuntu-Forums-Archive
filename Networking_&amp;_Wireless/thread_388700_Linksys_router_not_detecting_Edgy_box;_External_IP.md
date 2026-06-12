---
title: "Linksys router not detecting Edgy box; External IP woes"
date: 2007-03-19
forum: Networking &amp; Wireless
---

### Post by The Echo on 2007-03-19
I just recently took a full-install plunge of Edgy a few days ago and having been a Windows user all my life, I'm finding it to be a fascinating thing to play with and explore. I have a wired network at home, or rather, 3 Windows boxes wired to a linksys router in order to share a DSL connection. I plugged the Ubuntu box into a spot on the router and had no trouble accessing the internet. The problem is that under the DHCP clients table on my router, it does not list the Ubuntu box at all. All three Windows boxes appear, with their router assigned IPs (192.168.1.100, 192.168.1.101, 192.168.1.102 or along those lines) but the Ubuntu box does not show up. Also, when checking the external IPs of my computer and the Ubuntu, they both come up with the same IP. I have not tried the other two Windows boxes yet. When putting up a ventrilo server (dedicated) on my personal Windows box, I input whatever external IP I got off whatismyip.com most recently, and myself and others can connect to the server via our Ventrilo clients. After figuring out how to get the Ubuntu Ventrilo server up and running, I cannot connect to it from my client. I am assuming it is because of some combination of it not receiving a legitimate IP from my router, and thus being unable to forward the proper ports. I do not, however, know why both computers are getting the same external IP address, and I'm guessing this is also adding to the problem. Any help is appreciated for this Linux newcomer.

---

### Post by The Echo on 2007-03-20
I'm very sorry if I didn't see rules regarding bumping, but it's been over 12 hours and this has sunk quite a bit, before many people got to see it, I'm afraid. Any help is appreciated.

---

### Post by The Echo on 2007-03-20
The router still does not see the ubuntu computer, however this does not seem to affect it's getting and using an IP address. The issue was that I had been forwarding the port for Ventrilo twice, unaware that the router would disregard the second forwarding. It was as simple as disabling the forwarding for my Windows computer and the forwarding worked correctly for the Ubuntu computer.

Case closed, and thanks to the good people in the Ubuntu IRC channel.

---

