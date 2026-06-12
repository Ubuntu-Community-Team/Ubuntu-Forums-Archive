---
title: "vpn in windows through virtualbox"
date: 2008-04-13
forum: Networking &amp; Wireless
---

### Post by larsdk on 2008-04-13
Hi,

I have set up Windows XP on a virtual machine using Virtualbox (PUEL ver.) and everything is actually working like a charm. However I now need to use a VPN connection within Windows XP to connect to my work (actually the reason why I started this whole virtualbox thing, since I never got the default linux based VPN clients to work with the combination of my static IP and the MS-based VPN server) and now I can't seem to connect properly - it just says "controlling username and password" for a long time until it quits with an error...

I have setup the netconnection in virtualbox as "attached to: NAT" if that matters...

Any suggestions here?

Lars

---

### Post by Temujin_12 on 2008-04-23
I have the same problem.  Looking at the VPN server logs I'm getting error 721 (see [http://support.microsoft.com/kb/888201](http://support.microsoft.com/kb/888201)).  The suggested resolution from that KB is to make sure GRE can communicate over TCP port 1723.  This doesn't make sense since I don't have this port open on my router but a windows machine on my network can VPN in just fine.  Going ahead and forwarding that port to the Ubuntu machine which is running VirtualBox doesn't make any difference.

I'm not sure what else to try.

---

### Post by bl4k3r on 2008-04-28
Same problem here! Anyone?

---

### Post by Temujin_12 on 2008-04-30
Looking at the [VirtualBox user manual]("http://www.virtualbox.org/download/UserManual.pdf") (warning PDF), there's a section about how to configure virtual networking (which is supposed to make VPN connectivity work).  It is section 6.5 in the user manual (around page 63).  Reading downm there's a section on how to do this for debian/ubuntu distributions.

I haven't walked through this yet, but if/when I do I'll post a condensed version describing how to do it.

If anyone else feels like walking through the instructions from the manual, please post a condensed walk through here.

---

### Post by Chosen320 on 2008-07-21
Thanks... that sorted it out for me. It also explained why I couldn't connect to my work VPN as well as why I couldn't ping anything.

---

