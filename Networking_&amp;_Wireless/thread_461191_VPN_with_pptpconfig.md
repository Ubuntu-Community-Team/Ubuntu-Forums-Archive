---
title: "VPN with pptpconfig"
date: 2007-06-01
forum: Networking &amp; Wireless
---

### Post by incasa on 2007-06-01
Hi all,

I am new to Ubuntu, though not new to Linux.

For work, I need a VPN connection, Windows pptp. I installed pptpconfig from the  ttp://quozl.netrek.org/pptp/pptpconfig/ repos.

I launch it as root and have configured it correctly, but I get an error "Cannot determine ethernet address for proxy ARP" and the connection hangs. 

With MEPIS, the same procedure works OK, so I am a bit lost as to why it doesn't work with Ubuntu.

Any ideas or hints? Is there another way to setup a VPN maybe?

---

### Post by jamesjtucker on 2007-06-01
What vpn solution do you use? We use cisco here, and i can say that the cisco client is a PITA to get working. vpnc is a great vpn client for me, and i can show you how to get that running, but im not sure what your vpn is.

---

### Post by incasa on 2007-06-01
Hi,

the VPN is a windows pptp vpn. My company allows me to use Linux, but their servers are still windows based. So basically, a pptp vpn client

---

### Post by incasa on 2007-06-02
ehm, BUMP

---

### Post by incasa on 2007-06-04
FWIW,

I found a site where someone explained I had to install network-manager-pptp. This works, albeit with the nasty habit of routing ALL traffic through the VPN tunnel instead of only the IP addresses I tell it to....

We keep on working on it

---

### Post by joe84maiden on 2007-06-06
I just got the same error message. The only way I could find round it was to install network-manager and network-manager-gnome. From there you can sudo nm-applet which gives you your vpn network connection program. This works without the error. Unfortunately there are many more dependencies for this but if you can apt-get these from the internet then there isn't a problem.

---

### Post by AlexDudko on 2007-06-12
Well, I had the same problem: "Cannot determine ethernet address for proxy ARP". It happened, when everything was installed from the precompiled packages (.deb). When I compiled it myself from the source, everything worked just fine. So the problem is somewhere in the precompiled packages.

---

