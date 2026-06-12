---
title: "Dual WAN / LAN in ubuntu - force some protocols to use certain network"
date: 2007-05-22
forum: Networking &amp; Wireless
---

### Post by Vaevictus on 2007-05-22
Hello all,

I have a wireless connection provided by my university, which has great bandwidth for downloading / uploading using azureus. This connection however has very high latency.

I also have a wired ethernet network using an ADSL router which has very low latency but is only 1mbit.

What I want to do is configure ubuntu to:

1) Use wireless network (eth1) for all torrent data
2) use wired network (eth0) for all gaming data. (unreal tournament)
3) use wired network (eth0) for all HTTP traffic (the wireless lan is unsecured and I am more comfortable browsing net using ADSL)
4)Both network interfaces must be up at the same time so i can download very fast and still play games.

I am aware that I will need to use IPTABLES to accomplish this, and it looks very complicated.

Is there a GUI for generating the relevant IPTABLES script (select protocol to use on each interface) or will I have to make this manually?

If I have to make the script manually, which i feel is beyond my capabilities at the moment, could anyone get me off to a start?

Many Thanks,
Vae

---

### Post by pacobernal on 2008-06-09
I am not 100% sure that this is what you are looking for but, take a look at ebox, i remember seeing interface, firewall and port redirection on the webgui.

---

