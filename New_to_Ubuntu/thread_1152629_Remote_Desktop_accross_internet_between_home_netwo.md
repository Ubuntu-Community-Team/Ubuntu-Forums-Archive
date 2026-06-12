---
title: "Remote Desktop accross internet between home networks with no domain or server"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by rainierjamie on 2009-05-08
I am looking for a way to remote (full OS control, not just command line) between home networked computers (no servers, no domains) in order to connect to other Ubuntu systems across the internet to do tech support on systems that I sell.  
I read about tunneling VNC thru ssh, but I understand that it requires and IP address and or a domain.  Home networking has neither in any useful fassion, in that the IP would be something like 192.168.1.5 or 10.0.0.3 behind a router, and no way to associate it with the WAN IP address given by the ISP to the router.  And I would be coming from behind a router as well.  Sometimes my clients are using 56k modems as well.  There are not static IP's available either.
Is there something where you can send and encrypted key via email or anything of the sort?  Or some other method?  
I could do this remote in from a Windows system or an Ubuntu system.

---

### Post by bawilson2 on 2009-05-08
You could try doing something like DynDNS to setup a domain name.  You can running something like ddclient to automatically update their ip address with the server.  You'd then have to configure each of their routers to forward the vnc request to the correct machine but it should work.  I don't have dial up but I've done a similar thing to connect to my home machine.

---

