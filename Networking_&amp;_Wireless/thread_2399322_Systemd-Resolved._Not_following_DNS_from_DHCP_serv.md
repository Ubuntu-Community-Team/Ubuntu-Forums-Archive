---
title: "Systemd-Resolved. Not following DNS from DHCP server?"
date: 2018-08-23
forum: Networking &amp; Wireless
---

### Post by Tadaen_Sylvermane on 2018-08-23
I got my server fully up and running on Ubuntu 18.04 LTS today. My pxe boot machines are running fine. Had some network difficulties. I finally found that it was a DNS issue, moved the /etc/resolv.conf symlink to /etc/resolv.conf.orig and made a static file with the proper dns server (my main server) and everything is working wonderfully. 

Obviously this is a hack though. How can I get systemd-resolved to respect the dns assigned via dhcp? I'm sure it can be done, I just haven't found it yet.

---

