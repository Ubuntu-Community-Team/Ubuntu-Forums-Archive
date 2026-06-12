---
title: "TCP and UDP port forwarding problem"
date: 2017-10-23
forum: Networking &amp; Wireless
---

### Post by goemonburo on 2017-10-23
I am trying to ssh into my server when it's VPNed, but it's not working.  My VPN provider has set up a port, let's call it 12345, that's supposedly "open" both in TCP and UDP.

I have set up sshd to listen on TCP port 12345, which I've tested by successfully sshing into my machine without the VPN running.  I can also ssh normally, using port 22.  

But when the VPN is up, all I get is "Connection refused."

I have repeatedly tried to convince the VPN that this is an issue at their side, as my nmap scan of the VPNed system shows the port 12345 UDP as "open" but the TCP as "open|filtered."

They say it's a problem with my firewall, but I don't believe I'm RUNNING a firewall.  Isn't ufw disabled from the start?

I'm behind a router, and have opened port 12345 successfully there (or otherwise I couldn't ssh using -p 12345 when I'm NOT using the VPN).

My biggest problem is that I don't have the knowledge to properly understand how to check things.  I thought the fact that I can SSH fine without the VPN to port 12345 but when it's up I can't access it would mean that it's a problem with the VPN, but could there be some other problem at my side that's causing errors?  Are there IPtable rules I need to modify to allow the port to connect when it's on the VPN?  

Any help would be very much appreciated.  Thank you!

---

### Post by SeijiSensei on 2017-10-23
Are you using the machine's VPN address, or are you trying to connect to its external address?  The latter probably won't work with the VPN running because of the routing required to make the VPN tunnel your default gateway to the Internet.  Try using the server's VPN address instead.

---

### Post by goemonburo on 2017-10-23
> **SeijiSensei said:**
> Are you using the machine's VPN address, or are you trying to connect to its external address?  The latter probably won't work with the VPN running because of the routing required to make the VPN tunnel your default gateway to the Internet.  Try using the server's VPN address instead.

Can you give me an example.  I've used several different syntax:

ssh [email]me@VPN.IP.ADR.ESS[/email]
ssh -p 12345 [email]me@vpns.external.addres[/email]s
ssh -p 12345 [email]me@my.own.dynamicdns.name[/email]

In the case of this VPN, they say to connect by adding an "x" to the server name.  So if it's a server 123.myvpnsdomain.com, the correct domain would be 123x.myvpnsdomain.com.

What I really want to do is figure out how this works PERFECTLY on my side, but fails with the VPN, if it's not their fault.  :-)  Because I can fix errors on MY side.  They seem unwilling or unable to fix anything on theirs.  They assure me it's working, though, and everything on their side is fine.

Is it some other setting?

---

### Post by SeijiSensei on 2017-10-25
Did you try "ssh -p 12345 [email]me@VPN.IP.ADR.ESS[/email]"?  Was there a reason you omitted the port from the command?

---

