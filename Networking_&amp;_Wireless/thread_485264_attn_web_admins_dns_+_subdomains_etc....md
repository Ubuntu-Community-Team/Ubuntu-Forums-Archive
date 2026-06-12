---
title: "attn web admins: dns + subdomains etc..."
date: 2007-06-26
forum: Networking &amp; Wireless
---

### Post by scrupul0us on 2007-06-26
I have a question for those web admins out there that use their ubuntu boxes soley to serve to the web (besides a registrar holding their .com name)

right now my .com is with a registrar and is using namespaces freely provided through zoneedit.com

what id like to be able todo is host my own namespaces be able to to essentially get rid of zoneedit all together

i own a handful of .coms that all work off the same server

im also wanting to be able to make my own sub-domains... right now the only way i can do that is to log into zoneedit and set one up to map to a directory on my server... but when u hit the sub-domain it just forwards you to the directory and doesnt keep the sub-domain in the address bar

ive installed bind9 according to this (and just about everything else): [http://howtoforge.com/perfect_setup_ubuntu704_p4](http://howtoforge.com/perfect_setup_ubuntu704_p4)
(scroll down to #11 "dns server")

any help is appreciated

---

### Post by dfreer on 2007-06-26
the howtoforge "perfect ubuntu setup" series is for a fricking ISP server install, with WAY too much unnecessary software. ISPConfig puts all of it's website files in the DocumentRoot for apache, which means you'll have to move or uninstall it, quota isn't needed for most users, and neither is BIND. I highly recommend not using that guide, unless you are using just a portion of it or you really need to do ISP hosting.

Anyways, ignore my little rant. so you have several domain names purchased. Are you planning to serve several websites from the same box, or are you planning to map the domain names to the same site? For example, example.com and gamer.com each have a different page, but they run off "the same server", or do they serve the same exact page?

As for "sub domains", are you refering to the Virtual Hosts feature of apache? For example, [packages.dfreer.org](packages.dfreer.org) is different from [www.dfreer.org](www.dfreer.org)

BIND will be needed if you decide to completely get rid of using other's DNS services. But if you have a static IP address, why not use a free DNS provider? most of them support multiple DNS servers, which is important for reliability. If you have dynamic IP address, you are doing to need to use dynamic DNS site. I pay a reasonable price at dyndns.com for their customDNS option, and it works quite nice.

Of course, I could be completely clueless of what you are trying to accomplish here. Your initial post left a lot to be desired :D

---

### Post by Mr. C. on 2007-06-26
Does zoneedit allow you to create catch all records?

If so, you can just create a * A record that will direct all requests to your site; use virtual hosts in apache.

If you can't create a catch all, then you can setup your own DNS server, and change your NS settings at zoneedit to your server.

MrC

---

