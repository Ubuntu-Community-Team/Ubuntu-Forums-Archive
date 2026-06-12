---
title: "[SOLVED] Access to LAN hostnames broken in gutsy?"
date: 2007-11-10
forum: Networking &amp; Wireless
---

### Post by gexcko on 2007-11-10
I recently installed a Gutsy server running DHCP/DNS/Apache on my LAN. The DHCP works perfectly for all machines on the network, as does apache (with 3 virtual servers running), however the DNS is presenting issues.

I've got BIND9 installed and configured to lookup anything not hosted local through  the root servers (which works on every machine - all internet access is ok) and I'm hosting a local zone as well. 

Anything under the local zone (there's 7 entries) works perfectly for all machines running windows or macos, but the one I have running ubuntu (gutsy desktop) refuses to access the LAN computers by hostname, it accepts ips perfectly.

I've checked the connection settings in the desktop, and all the numbers look right (DNS is set to my internal machine).

If I run nslookup on a local hostname (forums.villa.local for example)  I get the proper ip, if I ping that ip it works fine, but if I ping the hostname I get a 'host not found' error.

I can also access the website running at forums.villa.local by ip, but not hostname in firefox.

I've attached a screenshot of the terminal I ran ...

Any ideas?

---

### Post by gexcko on 2007-11-10
Heh - I stumbled across the solution .. when I noticed the livecd for backtrack2 worked with the local hostnames just fine ... I compared all the networking files and noticed that the *hosts* line in */etc/nsswitch.conf* had other entries besides the simple *files dns* that backtrack used ... I changed the file, restarted networking, and all is well.

---

