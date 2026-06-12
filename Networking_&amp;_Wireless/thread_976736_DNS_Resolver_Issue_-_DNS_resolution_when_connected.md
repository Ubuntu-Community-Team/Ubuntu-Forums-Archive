---
title: "DNS Resolver Issue - DNS resolution when connected to 2 networks"
date: 2008-11-09
forum: Networking &amp; Wireless
---

### Post by Zanx on 2008-11-09
Hi,

I am a long time Linux (server) user but have only recently got to the point where I can run all of my core apps (or a suitable replacement app)  under linux. I chose Ubuntu as my distribution. 

I am a Network Engineer I work at many different locations and rely on the at&t network client to connect me to my corporate network (mail, corporate im, etc) while still allowing me access to the local (customer or my home) network.

The issue I have is with the DNS resolver. The at&t client correctly modifies the resolv.conf and places my corporate nameservers at the top of the file. As my corporate name server is always available and knows nothing about the 'customer.local' DNS domain I am unable to resolve any local names. 

If I modified the resolv.conf (manually or with a script) to put the local DNS servers first then I can resolve locally but not the internal addresses of my corporate network.

Using a local DNS server with forwarders isn't really an option as it too static given the number of sites I visit.

This issue has already been discussed in the following closed thread, however there does not appear to be a resolution.   

[http://ubuntuforums.org/showthread.php?t=528098&](http://ubuntuforums.org/showthread.php?t=528098&)

This has worked fine under Windows for the past 4 years (and I really don't want to have to migrate back) so I'm really hopeful for some ideas that might lead to a solution.

Thanks,
Sam

---

