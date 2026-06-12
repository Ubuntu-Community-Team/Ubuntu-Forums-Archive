---
title: "pppoe partially connects"
date: 2006-12-23
forum: Networking &amp; Wireless
---

### Post by admiral_pro on 2006-12-23
So I did a fresh install of Edgy on my computer and the one thing I am having a wicked time connecting on my kubuntu set up. I connect via pppoe and when I run sudo pppoeconf, everything is fine. I verify my name and everything works which I know by running plog. However, nothing loads or nothing connects. I try Konversation and it doesn't connect to the server. One time I was on IRC for a good 30 minutes, but nothing would load in konqueror or when I tried to apt-get updates. ](*,)  There is no firewall, (I know I'm the system admin at my house) and we don't use routers or anything fancy. It is a computer, one ethernet port, one modem, and one pppoe account. I *really* need to get back on my Linux box so I can help more with development. Please help. 

Edit:: I ran ifconfig ppp0 and saw a line that said "UP PEER TO PEER RUNNING NO ARP MUILTICAST" and when I run plog I see this:
ppd[60633] : using interface pp0
ppd[60633] : connect pp0 <--> eth0
ppd[60633] : PAP authentication succeeded
ppd[60633] : peer to calling number 00.10.67.00.D2.Z9 authorized
ppd[60633] : replacing old default route to eth0 [192.1.68.01]
ppd[60633] : Can no determain ethernet address to proxy ARP

Furthermore, I can ping my primary and secondary DNS servers with no packet loss (not sure if that matters).

Thank you in advance.

---

### Post by admiral_pro on 2006-12-25
I fixed it, it's a Christmas miracle. I looked at the box, set it up by entering the modem's IP address and signing in. That was it.

---

