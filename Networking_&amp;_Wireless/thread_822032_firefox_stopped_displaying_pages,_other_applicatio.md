---
title: "firefox stopped displaying pages, other applications work fine"
date: 2008-06-07
forum: Networking &amp; Wireless
---

### Post by jardeeq on 2008-06-07
I`m experiencing some strange error in all Gecko-based browsers. Firefox refuses to display any page - it says "Address Not Found" (with advice to check spelling, DNS or proxy settings and so on... you know). But everything in network connection settings seems to be OK, all other applications work (Pidgin, Evolution... I`m writing this post in Opera 9.5beta).

I use ubuntu 8.04 amd64 on my laptop (Lenovo ThinkPad R61, recently upgraded from 7.10). Firefox version number is 3beta5 from ubuntu repository, 2.0.0.9 and 3rc2 from firefox site)  I work on-line mainly in two network environments, using GNOME Network Manager applet:
[LIST]
[*]home wireless network with WEP security, ASUS WL500g wireless router, DHCP-enabled IP address management
[*]wired company network, also with DHCP, mostly windows machines.
[/LIST]

I`ve never had any such network-related issue. But few days ago there were some problems in company network, which caused I didn`t recieve IP address from DHCP server and therefore stayed about two hours offline. After the network had been fixed everything started to work except Firefox.

After some searching all around (google :-)) I have tried the following steps (according mainly to [http://kb.mozillazine.org/Error_loading_any_website):](http://kb.mozillazine.org/Error_loading_any_website):)

[LIST]
[*]Disable IPv6 support (it`s completely disabled in my system due to VMWare Server 2.0 beta - following this short tutorial: [http://ubuntu-tutorials.com/2007/11/18/how-to-disable-ipv6-on-ubuntu-710-gutsy-gibbon/](http://ubuntu-tutorials.com/2007/11/18/how-to-disable-ipv6-on-ubuntu-710-gutsy-gibbon/))
[*]Disable DNS caching in Firefox (reference: [http://blog.taragana.com/index.php/archive/simple-firefox-hacks-to-boost-performance/](http://blog.taragana.com/index.php/archive/simple-firefox-hacks-to-boost-performance/) - both cache expiration and cache entries set to zero)
[*]Disable all extensions, uninstall firefox-gnome support
[*]Create new fresh profile
[*]Create even new fresh user account in ubuntu
[*]Alter DNS settings in /etc/resolv.conf - using servers from [http://opendns.com](http://opendns.com) temporarily fixed problem - Firefox started working, but it was in company network... when I came home, Firefox stopped working again and "trick" with changing DNS settings didn`t help anymore.
[*]Download Firefox from it`s official website (version 3rc2), unpack and start with fresh profile
[*]**[update]** Manual network configuration ([http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)) Shouldn`t I completely uninstall Network Manager?
[/LIST]

So any of mentioned steps doesn`t lead to solution. There shouldn`t be running any firewall which could block firefox from accessing internet.

I also tried to boot from Hardy Heron LiveCD. It worked fine, including Firefox, so I think reinstalation of whole system will solve my problem. But I won`t have time to do this in next one or two weeks and it isn`t wery good solution (remember never-ending Windows 9x reinstalations many years ago ;-))

I`m not sure whether it is Ubuntu-specific or general Firefox issue, but I think it`s some missconfiguration in Network Manager applet or some other error in my Ubuntu... but configuration accessible through GUI seems to be correct.

Thank you for any ideas.

---

