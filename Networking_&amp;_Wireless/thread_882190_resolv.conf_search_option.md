---
title: "resolv.conf search option"
date: 2008-08-06
forum: Networking &amp; Wireless
---

### Post by victorbrca on 2008-08-06
Just wanted to double check something. 

My ISP hijacked the search results page, it brings to their page instead of the default page on my browser (Google). I want to bypass this and I found that changing the DNS was not enough, I had to also change my search option. 

Would my assumption be correct if I said that the "nameserver" option is for DNS (address translation) and the "search" for searching unmatched URLs? 

Also, I did some reading and found that resolv.conf usually gets overwritten by the DHCP server. My DHCP server does not have an option for "search". Should I guess that it will overwrite the search part on my resolv.conf? 

[Screenshot of DHCP server menu]("http://www.smoothwall.org/images/promos/3.0/services-dhcp-proxy.png").


Thanks,

Vic.

---

### Post by superprash2003 on 2008-08-07
you could do that by editing your dhclient.conf file.. 
For reference :[http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)  Opendns servers used here

---

