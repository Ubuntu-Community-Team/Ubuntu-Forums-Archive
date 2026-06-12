---
title: "RapidSVN + proxy"
date: 2008-10-03
forum: Networking &amp; Wireless
---

### Post by terrordrone on 2008-10-03
Hi,

Im under a proxy.

When i try to update/commit in RapidSVN i get the following error :

Error: Error while performing action: PROPFIND request failed on '...'
PROPFIND of '...': Could not resolve hostname `osl.iiitb.ac.in': No address associated with hostname (...)

---

### Post by minis on 2008-10-14
Hi terrordrone, 
RapidSVN uses the configuration files of the commandline client: so if you configure the servers file in $HOME/.subversion, adding the proxy configuration, it should work.
Working with: Ubuntu 8.04, subversion 1.4.2, RapidSVN 0.9.4.

See [http://rapidsvn.tigris.org/servlets/ReadMsg?list=users&&msgNo=325]("http://rapidsvn.tigris.org/servlets/ReadMsg?list=users&&msgNo=325") for the original post.

Bye,
m.

---

