---
title: "guarddog firewall and network printer"
date: 2006-11-19
forum: Networking &amp; Wireless
---

### Post by jynyl on 2006-11-19
Using Kubuntu Edgy with Guarddog to configure the firewall.
The printer is a network printer, running on our home LAN.  In printer configuration, it uses port 9100 on a static IP address.
With Guarddog running, I can't access the printer for printing or scanning.  With Guarddog off, both functions work fine.

There doesn't seem to be any feature in Guarddog to enable this.  I tried making a new protocol in Guarddog at port 9100, tried both udp and tcp, but it still didn't work.

Any tips on getting the firewall to enable traffic to the printer?

TIA

Peter

---

### Post by jynyl on 2006-11-21
From first impressions, it looks like firestarter makes a better firewall front end.

---

### Post by takakia on 2007-12-14
To make a Windows shared printer (samba shared printer) work you need to enable Microsoft SMB over TCP and Windows Networking (NETBIOS) in Internet  Zone  (enabling in Local had no effect in my case) in Guarddog configuration. 

This worked on Debian Lenny KDE.

---

