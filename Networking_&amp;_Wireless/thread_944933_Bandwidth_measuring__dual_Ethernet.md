---
title: "Bandwidth measuring / dual Ethernet"
date: 2008-10-11
forum: Networking &amp; Wireless
---

### Post by jtgd on 2008-10-11
Right now I have my Linux box and 2 other Windows machines going to a
switch, then to a Netgear firewall router, then to the cable modem.
Unfortunately for me the other end of the cable is Comcast and I now
need to start metering my bandwidth (I know I'm not the only person in
this situation).  I have no problem doing that for the Linux machine
with darkstat (everything is easier in Linux) but not for the Windows
machines plus what comes through the router via wireless (another
Windows laptop).  If only the Netgear router would total the bandwidth
going out the WAN port, but alas it doesn't, it only gives me packet
counts, not bytes.

So I'm thinking I would like to route everything through the Linux
machine.  I'm thinking I could just get another Ethernet card in the
Linux machine and then have all the other computers go through one 
interface and have the other one connect to
the cable modem directly.  Sadly I would give up the nice firewall
functions of the router (NAT, blocking, port forwarding), but I assume
I can do all that in software in Linux.

I suppose this setup is much like that of having a Linux box be a
stand-alone firewall/router except that it is also my main machine.
Can anyone point me to some good guides to use for setting up this
dual Ethernet thing, or any other advice?  Thanks in advance.

---

### Post by ARhere on 2008-10-11
Since it sounds like you are about to go play, might as well load Ubuntu server on an old box and use that as your firewall, router, whatever.

Once you load Ubuntu server, if you want the GUI just simply do you updates first (*it is faster in command line anyways*) and then load the ubuntu-desktop.

```
sudo apt-get install ubuntu-desktop 
```

-AR

---

### Post by tgalati4 on 2008-10-11
Depending on your router, you can load openwrt firmware on your router and tweak performance that way. Netgear has a new, high-performance wireless router that runs linux: wgr614L. $50 from Frys.com.

---

### Post by jtgd on 2008-10-12
> **ARhere said:**
> Since it sounds like you are about to go play, might as well load Ubuntu server on an old box and use that as your firewall, router, whatever.

Once you load Ubuntu server, if you want the GUI just simply do you updates first (*it is faster in command line anyways*) and then load the ubuntu-desktop.

```
sudo apt-get install ubuntu-desktop 
```

-AR
Thanks, ARhere, but I really need to run this on my current machine.  Can't I run anything I would run on the server on my workstation?

---

### Post by jtgd on 2008-10-12
> **tgalati4 said:**
> Depending on your router, you can load openwrt firmware on your router and tweak performance that way. Netgear has a new, high-performance wireless router that runs linux: wrt614L. $50 from Frys.com.

I just bought a WRT614 from Fry's a few months ago.  I don't recall seeing an "L" model.  I assume that means I can't load software on this one then?  If I had that router would I be able to get bytes counts in/out the WAN?  That may be the more practical solution.

---

### Post by jtgd on 2008-10-12
> **tgalati4 said:**
> Depending on your router, you can load openwrt firmware on your router and tweak performance that way. Netgear has a new, high-performance wireless router that runs linux: wrt614L. $50 from Frys.com.
Can you show me a link to that page?  I can't seem to find it on Frys.com.

---

### Post by tgalati4 on 2008-10-14
My error.  Wrong model number.  Try wgr614l:

[http://shop4.frys.com/product/5643391?site=sr:SEARCH:MAIN_RSLT_PG](http://shop4.frys.com/product/5643391?site=sr:SEARCH:MAIN_RSLT_PG)

You can put openwrt on a lot of different routers, but manufacturers have cut back on memory and processor speed to save cost.  Netgear came out with a router that actually has more memory and a 200 MHz processor.  It's $10 more than the standard wgr614 router-a generally reliable design.

---

### Post by jtgd on 2008-10-30
OK I just got my new Netgear KWGR614 Open Source router.  I haven't fully opened it yet.

Is there any chance it will give me the bandwidth statistics without modification?  Does anyone have this router?

If not and I have to load it, where is this software and how do I load it?

---

