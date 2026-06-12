---
title: "/etc/nsswitch.conf"
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by sulekha on 2008-11-05
Hi all,
 
 the following line  is taken from my /etc/nsswitch.conf file
 
** hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4**
 
 
 can any one explain me what is meant by mdns4_minimal ,[NOTFOUND=return], and mdns4

---

### Post by spd106 on 2008-11-05
Hello,

It's the recommended settings for Avahi (the mdns daemon). 

See this page at the project website for more information.
[http://avahi.org/wiki/AvahiAndUnicastDotLocal](http://avahi.org/wiki/AvahiAndUnicastDotLocal)

---

### Post by joeldbenson on 2013-04-05
The hosts: line specifies the order in which various name resolution services will be tried. The default is to:

 1. Begin by checking the /etc/Hosts file. If that file provides an IP address for the host name in question, it is used.

2. Otherwise try mdns4_minimal, which will attempt to resolve the name via  multicast DNS only if it ends with .local. If it does but no such mDNS  host is located, mdns4_minimal will return NOTFOUND. The default  name service switch response to NOTFOUND would be to try the next listed service,  but the [NOTFOUND=return] entry overrides that and stops the search with  the name unresolved.

3. Then try the specified DNS servers. This will happen more-or-less  immediately if the name does not end in .local, or not at all if it  does. If you remove the [NOTFOUND=return] entry, nsswitch would try to  locate unresolved .local hosts via unicast DNS. This would generally be a bad thing , as it would send many such requests to Internet DNS servers that would never resolve them. Apparently, that happens a lot.

4. The final mdns4  entry indicates mDNS will be tried for names that don't end in .local if your specified DNS servers aren't able to resolve them. I thought this was meant  to catch mDNS hosts when you don't specifiy the .local TLD, but I just  tried it and it doesn't work. Guess I will look into it.

Further information on nss-mdns can be found at [http://0pointer.de/lennart/projects/nss-mdns/](http://0pointer.de/lennart/projects/nss-mdns/)

---

