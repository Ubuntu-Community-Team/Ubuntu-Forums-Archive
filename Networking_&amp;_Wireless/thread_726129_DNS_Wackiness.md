---
title: "DNS Wackiness"
date: 2008-03-16
forum: Networking &amp; Wireless
---

### Post by thalin on 2008-03-16
So this problem is easily one of the strangest I've come across in my several years running Linux.  I'm runnning 7.10.  Here's the deal:  Azureus, Firefox, and Opera (possibly other apps as well) can't seem to look up DNS entries.  However, on the command line I can use host, nslookup, ping, ssh, tracepath and links and do DNS lookups perfectly well.  Pidgin can use DNS to look up it's server names.  MPD can play streams still.  VMs on the machine can use DNS flawlessly.  The only applications I've found which **can't** do DNS lookups are the three I listed above, Azureus, Firefox and Opera.

This problem started happening after I switched my DNS servers to OpenDNS.  I changed my router settings (other machines on my network seem to work fine -- including other Gutsy boxes).  I decided for some reason to also change my machine settings.  I followed the instructions on the OpenDNS website, which consisted of changing the entries in Network Manager, creating an /etc/resolv.conf.auto, and adding a prepend domain-name-servers line in /etc/dhcp3/dhclient.conf.  Once I did that and restarted my interface, DNS stopped working on Firefox.

So to try to fix and eventually just try to figure out what's going on, here's what I've done.  First, I undid all of the changes I had done on my machine.  removed the DNS servers from Network Manager, I removed the /etc/resolv.conf.auto, and I nuked the line from /etc/dhcp3/dhclient.conf and restarted the interface.  That didn't help me any.  I rebooted.  I set network.dns.disableIPv6 = true in about:config in firefox.  I moved my .mozilla directory to make sure it wasn't anything wrong in my profile.  I removed and reinstalled firefox.  Then I installed opera in hopes I could just use it -- no luck.  Then I noticed that Azureus wasn't connecting to the tracker anymore.

Next I made a SOCKS-via-ssh proxy to VPS I have on the internets (ssh -D) and set my network settings on Firefox to use the proxy. No go.  I tried looking up a new address, hoping it was just some strange DNS cache that was failing.  Nope.  Tried doing host google.com and using the IP address -- it works!  Firefox can actually talk to the network.  Finally, I totally removed (apt-get remove) and reinstalled Firefox (by the way, this also removes ubuntu-desktop and a bunch of other stuff).

Anyway, nothing I've done has made any difference.  I can't figure this out.  I am totally at a loss on this one, and nobody I've talked to has been able to help me in any way.  Are you up to the challenge?!

---

