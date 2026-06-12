---
title: "Connecting to office VPN"
date: 2007-12-12
forum: Networking &amp; Wireless
---

### Post by acl123 on 2007-12-12
Hi, I'm desperate to get a VPN connection going with my office, but there's very little info out there on how to do this that's understandable without extensive networking knowledge.

The office uses a Netgear FVX538 router, which uses IPsec.

A quote from the netgear forums: "It's not really about support per se. It's the fact that there aren't any VPNC Certified VPN Client software products out there that run on Linux".

Is this correct? I'm not sure what it means, but it doesn't sound good for me.

---

### Post by mmichalik on 2007-12-12
we are using the kVPNc program.

If you download the latest deb package from the website, it has a pretty good GUI setup and is somewhat easy to understand.

[http://home.gna.org/kvpnc/en/index.html](http://home.gna.org/kvpnc/en/index.html)

You will also have to download the openvpn client from the repositories first, then install the deb package.

Hopefully, it will be a simple thing for you.

Good luck!

---

### Post by manthony121 on 2007-12-12
My office has a Smoothwall express firewall.  From my home, I set up a SSH tunnel, forwarding an arbitrary local port to a computer running a vnc server inside the firewall.  Does that sound like what you are trying to do?  If so, I can give you more details.

---

### Post by acl123 on 2007-12-13
Hi guys, thanks
I installed kVPNc and it looks more like what I need. I messed around for a while and couldn't get a connection but I know that you need to be very precise with VPNs. I'll keep working on it.

---

