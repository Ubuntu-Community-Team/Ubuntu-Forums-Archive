---
title: "Wifi working erradically after upgrade to 16.04 LTS (bcm4318)"
date: 2017-04-12
forum: Networking &amp; Wireless
---

### Post by dumazdamaz on 2017-04-12
I had an old laptop on 14.04 LTS and the wifi worked without problems. This is BCM4318 and it's installed with b43 and fwcutter. When I upgrade tot 16.04 LTS it still sometimes works, but at other times it just does not load a page from the internet nor does it allow apt update, for example. When the connection is not working I can nevertheless ping any ip or site that I want on LAN or internet and I have an IP from the dhcp server. There appears to be no name resolution problem either. I have noticed that the version of firmware-b43-installer has changed between the two versions and that the changelog says "NEw upstream and   * remove patches + merge with upstream".

So, I am left wondering whether this could be the reason and if it could possibly work to revert back to 1:018-2, or is it likely that there is some other reason?

Is there some best practice and safe way of doing this? Or should one just purge the current package and download a .deb and manually install that? Probably it needs to be pinned to that version at least.

---

