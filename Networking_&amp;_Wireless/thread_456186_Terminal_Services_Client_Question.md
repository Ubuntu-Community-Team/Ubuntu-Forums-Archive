---
title: "Terminal Services Client Question"
date: 2007-05-27
forum: Networking &amp; Wireless
---

### Post by ed67 on 2007-05-27
I installed Tight VNC Server on my Windows XP machine.  I configured TSC on my Ubuntu laptop to remotely access my XP box.  Works good on my home network.

My question:  How can I access my XP box from my Ubuntu laptop away from home over the internet?  It's fine when I type in the local 192.168.x IP address, but from the internet I would need to type in WHAT exactly?

BTW, I can use LogMeIn but it doesn't work in Firefox on Ubuntu, something with a java problem I haven't been able to fix.  TSC will work fine once I get this part.

Thanks

---

### Post by ed67 on 2007-05-27
Quick clarification after re-reading my post.  My question is how do I access my XP box when I take my laptop away from home, away from my local network, and must access it over the internet.

---

### Post by jonallport on 2007-05-27
Hi Ed,

The theory is simple, the execution may need some tweaking.

You need to forward port 3389 on the external interface of your firewall/router to the internal IP address of your WinXP box.

Things that may hamper this are:

1) Not a permanent connection (dialup) - V. difficult to fix, will revisit later if needed
2) Not a static IP assigned by ISP - need to setup dynamic dns (ISP may already do this, mine does)
3) WinXP box doesn't have fixed IP address - you can assign a specific address from your DHCP config

Otherwise it's simple, most firewalls/NATing routers will let you setup port forwarding (sometimes incorrectly called DMZ server).  Just point external port 3389 to WinXP box port 3389.

To revisit (1), if you need to dial-in then it'll probably have to be Windows RAS on the WinXP box and this is probably the wrong forum to ask about HOW-TOs on Mr Gates's products.

Hope that helps.

---

### Post by ed67 on 2007-05-27
Well.....

I don't have a static IP address for my router, although the computer I want to access does have a static IP address on my home network.

OK, so how do I even see my router on the internet?  How do I find its IP address?  When I type ipconfig /all it tells me what my primary dns and secondary dns is, but isn't that my ISP's address?  Say it is my own IP address, how do I tell Ubuntu's Terminal Service Client what to do?

Thanks again.

---

### Post by jonallport on 2007-05-28
Re. "How do I find its IP address?"

The easiest way is to point your browser at [http://whatsmyip.org](http://whatsmyip.org), the name says it all!

Right...to connect to your router from 'outside', you'll need to some consistent way of finding it.  If your IP address is dynamic then you'll need some dynamic DNS service, all of the Linksys and 3Com routers I've used will handle this (I've just checked the 3Com I'm behind now and it'll sue dyndns.org and tzo.com. I think my old Zoom would do it too)

Hope that advances things.
J

---

### Post by pcmann2004 on 2008-04-03
hello,
ok, i would like to setup where i can acces my linux box from my xp box through mstsc
i can do the other way  xp on linux,  i would like linux on xp
thanks

---

### Post by firedrow on 2008-04-04
ed67,

If your router supports it, register a DynDNS name and setup your router to maintain it.  I know Linksys routers and some D-Link will allow Dynamic DNS.  It doesn't have to be DynDNS.org, check what your router supports and set it up.  This will allow you to connect back to, for example, ed67.noip.org to matter where you are or what your external IP is.  It's pretty nice, especially if you do have a dynamic IP from your ISP.  Once you have the configured you need to port forward 5500 (or what ever port you set in VNC) to your XP machine.  This will allow you to use TSC to connect to the VNC server from outside your home network.

pcmann2004,

Linux doesn't support RDP Server, which is what mstsc (Remote Desktop Connection) connects to.  The business I work for makes extensive use of Terminal Services, and I use a linux laptop, so I am intimately familiar with it.  Your option for connecting back to your linux box from your XP machine is to setup VNC server on your linux box and then download a VNC viewer (tightvnc.com offers a free one) to connect back to it.  You won't be able to use native windows tools to connect like that to linux.  Your other option is connect across SSH and run an X session, but I have never set that up myself so I can't help you there.

---

