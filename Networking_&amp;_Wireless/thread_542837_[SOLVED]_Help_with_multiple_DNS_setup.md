---
title: "[SOLVED] Help with multiple DNS setup"
date: 2007-09-04
forum: Networking &amp; Wireless
---

### Post by mkramer on 2007-09-04
I am trying to setup an internal web development server (LAMP + DNS) for a multiuser office.  The LAMP server is running about 15 virtual hosts right now on the domain dg.krm i.e. mkramer.dg.krm.  The idea is to maintain the hosts file on the LAMP server (dg, short for dark-genius) and have the clients use dark-genius as a dns server for any url in the dg.krm domain, and use a different nameserver for top level domains.   

L = Ubuntu 7.04
A = Apache 2
DNS = dnsmasq

I've configured all the *nix clients to do this now with this configuration:
```

###/etc/resolv.conf
search dg.krm krm
nameserver ***.***.***.***  ##my isp's nameservers
nameserver ***.***.***.***

###/etc/resolver/dg.krm
nameserver 192.168.123.100  ##this is the ip of dark-genius

```

This works great if I type in QDN's.  I.E. mkramer.dg.krm resolves using dg.krm's DNS server and google.com resolves using my ISP-provided DNS.

However, the search domains are not working quite right.  If I try "mkramer", something unexpected happens.  I thought that it would append .dg.krm to the search and take me to mkramer.dg.krm.  Instead, it takes me to the page which is being served at the first site available in the virtual hosts list, as if I had just typed the ip of dark-genius.  This is true for any virtual host that I try.  

This puzzling issue highlights a gap in my understanding of name-based virtualization in apache.  How does Apache know that the client has requested mkramer.dg.krm as opposed to dg.krm, if they've all already been resolved to the same ip address by the client's DNS resolver before the request is made? If someone could explain this behavior to me I would really appreciate it, and even better, does anyone know of a way to make this work?

---

### Post by cagey cretin on 2007-09-04
What happens if you remove the ISP's nameserver entry from resolv.conf?

---

### Post by mkramer on 2007-09-04
I figured it out.  In answer to my own question, apache knows the difference between mkramer.dg.krm and dg.krm because of the http Host: header.  

When I type mkramer in the bar, it resolver correctly resolves mkramer.dg.krm to dark-genius's IP address of 192.168.123.100.  However, the HTTP Host: header was specified by Firefox as "mkramer", which was not a valid hostname.  Instead, it dumps me to the default virtual host. In order to fix this, I used the ServerAlias directive and specified "mkramer" as a alias of mkramer.dg.krm.  So now, when apache gets a request on 192.168.123.100:80 and the Host: header specifies "mkramer", it knows where to take me.

---

### Post by mkramer on 2007-09-04
RE: cagey

Everything still works when I do that.  I assume that resolver defaults to using my default gateway as the nameserver.  My default gateway is a router which has an embedded nameserver on it which automatically receives its upstream nameservers from the ISP.  The reason I have them specified is to skip the query on the gateway, which, in all cases, is just going to push the query up the line anyway.  I suppose if the nameservers ever change it will mean that I have to manually change them instead of letting them autoconfigure, but they've been holding steady for years now, so I'm not too worried.

---

### Post by cagey cretin on 2007-09-04
I was asking in case you had multiple hosts running http or smtp, and your querry would be returned to WAN ip...

---

