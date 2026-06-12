---
title: "Help me setup my network for my kids!"
date: 2008-01-12
forum: Networking &amp; Wireless
---

### Post by Statik on 2008-01-12
Hi all,

I am using Gutsy and I want to setup a proxy/firewall for my kids computers. Here is the setup:

```

Cable Modem -> Wireless Router -+-> My Computer -> Switch -+-> Kid 1
                                                       +-> Wife's Laptop                  +-> Kid 2

```

What I want is to have the kids get their IPs from my computer (DHCP), have their connections firewalled (firestarter?) and only have access to websites I whitelist (squid?)

I think I've found the proper how-to's on DHCP and firestarter so that I can achieve this, but not squid. How do I setup squid to only, but firmly, filter the computers on eth1 (anything connected to the switch), but leave my computer alone?

If there is something other than squid I should use, let me know.

Any help appreciated.

Statik

---

### Post by enuf on 2008-01-17
Install Webmin - GUI for a lot of stuff within linux - 

[http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html]("http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html")

including squid as a transparent proxy - 
[http://linuxgazette.net/141/lazar.html]("http://linuxgazette.net/141/lazar.html")

---

### Post by Statik on 2008-01-24
Those look to be exactly what I'm looking for. I'll keep you informed of my progress.

Statik

---

