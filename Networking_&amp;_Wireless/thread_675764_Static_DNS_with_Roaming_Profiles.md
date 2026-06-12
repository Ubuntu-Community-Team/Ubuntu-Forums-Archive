---
title: "Static DNS with Roaming Profiles"
date: 2008-01-23
forum: Networking &amp; Wireless
---

### Post by jpyper on 2008-01-23
Hello all,

I'm currently running Ubuntu Gutsy on my laptop. It works great for just about everything I've thrown at it.

I've recently setup pdnsd (aptitude show pdnsd) on this laptop to use as a caching DNS server, since I'm constantly bouncing around between wireless networks on my job and tend to run into areas that have really slow DNS server.

My biggest issue is, each time I connect to a different network, NetworkManager changes the /etc/resolv.conf to the DNS server(s) provided by the DHCP server on the wireless network.  I don't want that.  I use OpenDNS ([http://opendns.com/](http://opendns.com/)) for all my DNS queries and pdnsd caches the replies locally for 3 days for faster access to sites.

The only other thought that I've had about preventing NetworkManager from changing the nameserver line in /etc/resolv.conf would be to chmod 444 or 400 to that file.  It doesn't seem logical though. There has to be a way to stop NetworkManager's madness that's driving me mad here.

Any ideas is surely appreciated.  Thanks in advance.


   John

---

### Post by wieman01 on 2008-01-23
Would this help?

[http://ubuntuforums.org/showthread.php?t=28203]("http://ubuntuforums.org/showthread.php?t=28203")

Editing '/etc/resolv.conf' is indeed the only thing you can do right now, as NM cannot handle static IP addresses which also includes DNS servers. Please read the tutorial above as it will provide some insight.

---

### Post by fhteagle on 2008-02-16
[http://edeleonjr.blogspot.com/2008/01/static-dns-with-dhcp-in-ubuntu.html](http://edeleonjr.blogspot.com/2008/01/static-dns-with-dhcp-in-ubuntu.html)

Worked like a champ for me across wifi DHCP and usb-rndis-lite connection to my phone...

---

