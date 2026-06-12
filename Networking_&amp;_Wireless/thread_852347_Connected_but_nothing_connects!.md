---
title: "Connected but nothing connects!"
date: 2008-07-07
forum: Networking &amp; Wireless
---

### Post by odinbaal on 2008-07-07
Hi all,

Just installed Hardy Heron 8.04.1 on my Toshiba S3000-400 with Realtek RTL 8139 network card.

Setup my internet connection (DSL/PPPOE) with rp-pppoe (needed because of my ISP using a service name), and chose, in "Networks," DHCP.

When I do: sudo pppoe-start, I get an immediate connection, but I can't do anything with browsers or updates or emails. I get an error message saying didn't find server, or connection error, etc. Proxy is setup properly (direct connection to internet), and sudo pppoe -A shows that I'm connected to AC and service name.

ifconfig shows that I have eth0 avahi, lo, and ppp0 as all fine and running.

What am I missing?

Thanks for the help!

---

### Post by odinbaal on 2008-07-08
In addition, when I type netstat -i, I get plenty of errors under RX-ERR and TX-ERR and nothing under RX-OK and TX-OK for interface eth0, meaning (I guess) that interface eth0 (the network card) is attempting to transmit and receive data but cannot.

Any suggestions?

---

### Post by odinbaal on 2008-07-10
OK.

Since no one was bothered to answer a new Ubuntu user, I decided to try again myself.

For the sake of other new Ubuntu users, I am explaining what I did.

As mentioned above, I downloaded rp-pppoe, installed the build essentials from the Ubuntu cd, and built the program with ./go. The graphical interface, ./go-gui, would not build because of unresolved dependencies, and since I had no internet then, I couldn't satisfy them.

rp-pppoe was invoked with pppoe-start, connection was fine, but nothing connected, i.e., I couldn't connect through the internet. Strange indeed.

I did plenty of things gathered from here and from a million other pages, even removing ipv6, with no result.

I was going to give up (I was on my own, and the Ubuntu community was not answering) when I convinced myself to try again with rp-pppoe's graphical interface, tk-pppoe (the ./go-gui). Checked the net (from another machine) and learned that I needed tk8.3 and, before that, tcl8.3. Got the two packages, installed them, and successfully built and installed tk-pppoe.

Now the strangest thing was that after inputting the same info in tk-pppoe that I did in the normal rp-pppoe, not only was I connected, but everything went fine with the internet. I don't know the reason for the discrepancy, but there you go, this is Linux.

Did a full update and was told, by the hardware driver applet, that I could install nvidia's proprietary driver. Ok. Why not. Install, reboot, catastrophe. Garbled screen and all, time to remove this nvidia driver and do more search on my card and maybe post on the forum.

---

