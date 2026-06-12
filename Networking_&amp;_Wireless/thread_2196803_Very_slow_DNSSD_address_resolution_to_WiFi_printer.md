---
title: "Very slow DNSSD address resolution to WiFi printer"
date: 2013-12-31
forum: Networking &amp; Wireless
---

### Post by RickPJ on 2013-12-31
I have a very strange problem with a new Epson WiFi printer (XP-412). I have two machines running almost identical Kubuntu setups, version 13.10, one a 64-bit desktop with wired Ethernet, the other a 32-bit netbook with WiFi.

The printer is installed and configured fine, connects to the WiFi network (set up via the printer panel), and talks to the cloud with Google CloudPrint, Epson remote print/scan etc. so no problem there.

But when configuring the printer device in Kubuntu, the desktop works 100% but not the netbook.

The printer advertises two interfaces via self-discovery, one the classic lpd, the other dnssd. But the netbook doesn't appear to see the dnssd device, only the lpd one. Avahi-utils sees the advertised interface, but it isn't offered in printer setup, either via KDE or CUPS web config.

Because the setup should be identical on both machines, I copied the CUPS printers.conf file from the desktop to the netbook. That allowed me to queue a print job, but initially the job didn't print, saying the printer was not found. But after a few minutes, it suddenly printed out! This behaviour is consistent - very slow to make initial contact with the printer, just from this machine.

My conclusion is that when the netbook tries to resolve the dnssd address of the printer, it takes 2 -3 minutes of re-trying before it gets a result. Once it's there, prints run OK, the throughput is fine. The delay is why it doesn't show in setup, because it won't wait that long.

I've checked nsswitch on both machines, and both are the same.

So why should DNSSD resolution be horribly slow from one machine, and instant from the other? I'd love to know if anyone's got any ideas!

Cheers, and Happy New Year to all!

---

