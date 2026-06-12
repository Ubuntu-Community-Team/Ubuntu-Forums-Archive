---
title: "[SOLVED] DNS Server (djbdns, bind)"
date: 2007-08-09
forum: Networking &amp; Wireless
---

### Post by Sargon on 2007-08-09
Hi

I used to run djbdns under a Gentoo box and now switched to Ubuntu. My requirements are:

(1) DNS cache for internal servers
(2) DNS server for internal servers
(3) DNS server for the rest of the world

djbdns was pretty easy to setup and meets all my requirements nicely.

Since djbdns doesn't seem to be nicely packaged for Ubuntu, I'm considering to give bind a try. The bind tutorials I've found so far don't really cover my requirements though.

I found the HowTo here ([http://ubuntuforums.org/showthread.php?t=236093&highlight=bind9+dns+howto](http://ubuntuforums.org/showthread.php?t=236093&highlight=bind9+dns+howto)) but this seems to cover requirement (2) and that's it. Any ideas and/or pointers to other HowTos/tutorials?

Sargon

---

### Post by Sargon on 2007-08-09
Just gave djbdns a try and... it was a disaster.

When following the home page of djbdns ([http://cr.yp.to/djbdns.html](http://cr.yp.to/djbdns.html)), not even daemontools compile out of the box. When following the directions of [http://www.djbdnsrocks.org/](http://www.djbdnsrocks.org/), daemontools fail too (with a different error) Finally using the Ubuntu package 'djbdns-installer' fails miserably as well. (there's no /etc/inittab anymore...) I even had trouble removing the package. Oh well... so djbdns is - at least for me - a no go under Ubuntu. Very sad to see...

That leaves me with bind... great! ;)

Sargon

---

### Post by Sargon on 2007-08-12
I've installed and configured Bind9 now.

Unfortunately, the webmin module didn't work as expected. (it doesn't show created views). But the explanations found [here]("http://www.openaddict.com/bind9_views_for_dns_zones.html") were straightforward and easy to understand. Just what I was looking for! :)

Sargon

---

### Post by MarilenCorciovei on 2008-01-08
I managed to install djbdns without any major problem and is working as expected: [http://www.len.ro/work/tools/gutsy-on-a-ubuntu-server/dhcp-and-djbdns/view]("http://www.len.ro/work/tools/gutsy-on-a-ubuntu-server/dhcp-and-djbdns/view")

---

### Post by zazuge on 2008-04-19
thanks god you did find some way to run djbdns
because if what did say daniel burnestein was right , then BIND have serious  sercurity flaws (like DNS poisoning attacks)

---

