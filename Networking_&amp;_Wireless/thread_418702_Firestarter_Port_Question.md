---
title: "Firestarter Port Question"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by jcws6 on 2007-04-22
Sorry for the amateur question, but this one should be pretty easy.  I'm trying to only allow 1 incoming port from the INTERNET, but open all ports from my LOCAL NETWORK.  Is this possible via Firestarter?

More info:  I'm setting up a file server & I want to access it via an unprotected SAMBA share when I'm in my network, but I'll be accessing the share via OpenVPN (thru the 1 open port) when I'm at a PC outside of my network.

---

### Post by jcws6 on 2007-04-22
Nevermind, got it.  Man, that was easy.

I enabled SMB (137-138 445) & VPN (5900) for "192.168.1.100/255.255.255.248", and VPN (1194) for "everyone."  Theoretically, this should allow anything on my network (192.168.1.100 - 192.168.1.107) direct access to network shares & VNC (this works), and anything outside of my network can only access the VPN port (haven't tested this yet).

I'm looking for an expert opinion on this setup.  Does this sound secure?

---

