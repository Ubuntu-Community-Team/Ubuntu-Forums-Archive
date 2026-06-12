---
title: "Static DNS with Network Manager"
date: 2006-10-13
forum: Networking &amp; Wireless
---

### Post by rbrugman on 2006-10-13
Is there any way to get network manager to use static dns (in my case, OpenDNS) instead of the dhcp-provided dns servers?  I have my home network set up to use OpenDNS, but at school I am forced to use their servers, which really suck and slow down my connection.  I figured out how to do it on my mac and under Windows, but I can't get linux set up.

Thanks,
Robert

---

### Post by darrenm on 2006-10-13
edit /etc/dhcp3/dhclient.conf and you will see everything you need to know

---

### Post by rbrugman on 2006-10-13
supersede domain-name-servers 208.67.222.222, 208.67.220.220; did the trick for OpenDNS.  Thanks a bunch for pointing me to the file.

---

