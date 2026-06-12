---
title: "resolvconf won't store DNS server information using DHCP"
date: 2007-02-28
forum: Networking &amp; Wireless
---

### Post by Snapper187 on 2007-02-28
Hi folks,

I've got some problem with using resolvconf in conjunction with a DHCP client, namely dhcp3-client (dhclient) which seems to be installed by default on Ubuntu.

Whenever I try to configure my machine using DHCP and thus retrieve IP address and DNS server information from any network, the DNS server information will not be put into /etc/resolv.conf (which, due to resolvconf, is a link to somewhere in /etc/resolvconf/). As soon as I remove the resolvconf package, however, things work just perfectly using DHCP. I'm in need of resolvconf though since I'm regularly switching between networks where the DNS information will be supplied by DHCP and where this is not the case and I have to use resolvconf's *dns-nameservers* directive from /etc/network/interfaces.

Notice that this affects *nameserver* entries from /etc/resolv.conf only: Using resolvconf and dhcp3-client, the *search* directive will be provided every time.

What I've tried so far is switching over to dhcpcd and see if things work out differently. Apparantly, they not only didn't, but I cannot even manage get resolv.conf filled without resolvconf installed using this alternative DHCP client. I'm kind of preferring dhcp3-client anyway so I'd like to concentrate on Ubuntu's default DHCP client.

By the way: I'm affected by this problem in multiple, different DHCP environments, even different countries.

By the way: I haven't been able to get any useful debugging data out of dhclient. (it doesn't seem to come with any debug switches.) And using dhclient <interface> as opposed to ifup isn't much of a help either.

I'm glad for any help.

Some version info (using Edgy):

dpkg -l resolvconf dhcp3-client
[...]
ii  dhcp3-client   3.0.4-6ubuntu6 DHCP Client
rc  resolvconf     1.36ubuntu1    nameserver information handler

Of course, resolvconf is removed right now so I can get on the 'Net and post this.

---

