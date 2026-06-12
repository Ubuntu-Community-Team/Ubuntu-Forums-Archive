---
title: "Fixing resolv.conf and resolvconf to remove ISP dns names"
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by mike310z on 2008-11-05
This is bewildering, apparently in the past you could just set the DNS names you wanted in resolv.conf, and now a script resolvconf does it by magic.  
Unfortunately the magic it uses is to connect me to Comacasts DNS servers.

Using dig and nslookup I can quickly establish that Comcasts dns takes over two seconds to do what openDNS  or many other dns servers can do in tens of milliseconds.

I though it would be easy to fix this, but its NOT!

First I set the DNS names in the three spots in the router by hand  - reboot - no luck, Comcasts dns names are on top.

Next I noticed that resolv.conf has Comcasts name in the search section, so  I gave the router a domain name etc so that it appears in resolv.confs search list - reboot - no luck Comast still top of the list.

Next I played with all the secret sauce in the /etc/resolvconf/.. directories, and did sudo resolvconf -u - no luck with anything that would survive a reboot.

I am stuck, if I sudo vi /etc/resolv.conf and delete Comcasts dns names from the top of the list, all my network access become massively faster and the web comes alive again, its a staggering improvement for removing two lines of text.

Can anyone tell me how to get this and its interaction with the  NetworkManager  to to do the right thing ?

Thanks Mike

---

### Post by eyemou on 2009-06-29
This was bothering me... I had installed VPNC, in order to connect to a client's Cisco VPN. However, when I was not connected, I noticed that my web browsing, etc. was s-l-o-w. As it turns out, their DNS servers, which  were unreachable, were listed in /etc/resolv.conf, and before my ISP's DNS, slowing everything down as DNS queries were sent to their DNS servers, and had to time out.

After having to manually edit my /etc/resolv.conf file after every boot, I looked into how resolv.conf was constructed, and ran across this:

/etc/resolvconf/run/interface

There was a file in there for my connection (in my case, called "eth0.inet"), and one for the vpn (called "tun0"). "sudo rm"'d the "tun0" connection, and I'm all set.

Perhaps that will help...

---

