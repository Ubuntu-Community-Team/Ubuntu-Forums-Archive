---
title: "DNS address obtained via DHCP to be overruled"
date: 2008-02-26
forum: Networking &amp; Wireless
---

### Post by wally.the.guzzler on 2008-02-26
Scenario:

I use wireless connection at office and home. At both places, I get network parameters via DHCP. Everything works fine at home.

In office, my DHCP server gives me a wrong "nameserver" entry, which I want to overrule. I edited /etc/dhcp3/dhclient.conf and used "prepend domain-name-servers" variable to put correct DNS IP, which I expect from office DHCP server. However, this modification annoys me when I connect to home network. Is there a way to stop DHCLIENT stop writing /etc/resolv.conf based on parameters obtained from DHCP servers and use 2 versions of resolv.conf that I define? Or, can there be any other option.

PS: The DHCP server in office gives correct DNS IP to users using Windows/Mac!

Thanks.
Wally.

---

### Post by stream303 on 2008-02-26
If the server is the typical soho router, you may want to put your ISP's primary and backup nameservers *into the router's setup page*, which will then get properly passed to all your machines.

If you don't know them a good alternative is to look at [www.opendns.org](www.opendns.org) and see the nameserver addresses at the bottom right of the page.  You might be able to use these addresses for everything!

---

