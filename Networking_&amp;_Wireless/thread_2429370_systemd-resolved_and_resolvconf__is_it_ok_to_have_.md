---
title: "systemd-resolved and resolvconf : is it ok to have both installed?"
date: 2019-10-17
forum: Networking &amp; Wireless
---

### Post by birdman1 on 2019-10-17
Systemd-resolved is present by default in Ubuntu 18.04. Resolvconf pkg is not.


  From reading around, systemd-resolved provides name resolution while  resolvconf provides multi-client access to update the configuration of  name resolution.


  The question is: do they both happily co-exist? Does resolvconf know  about systemd-resolved and update its configuration? Or instead, does  systemd-resolved somehow learn about updates to name resolution files  that resolvconf has done?


  I get suspicious when I see that resolvconf symlinks to  /run/resolvconf/resolv.conf whereas systemd-resolved symlinks to  /run/systemd/resolve/resolv.conf. Seems conflicting to me.

---

### Post by SeijiSensei on 2019-10-17
I'd stick with systemd-resolved at this point. I don't see Ubuntu going back to resolvconf. And, no, I wouldn't try to use them both.

---

### Post by birdman1 on 2019-10-18
Ok. So if I only use systemd-resolved and don't use resolvconf, does systemd-resolved now provide the function that resolvconf used to provide i.e. synchronised updates to resolv.conf from multiple clients? 
Sorry for continuing to ask but the picture is not fitting together for me. (Ubuntu 18.04.2 x86).

---

### Post by birdman1 on 2019-10-22
Can anyone in the Ubuntu community explain the situation with these name  resolution software packages?? Surely this was well understood before a  distro was released??

---

### Post by SeijiSensei on 2019-10-22
I'm not sure what you mean by "synchronized updates to resolv.conf."  That file never changes. It simply points to the location of one or more nameservers. 

Name resolution mechanisms have been something of a moving target with Ubuntu over the past couple of years. Some releases used dnsmasq, then later resolvconf. Since systemd is now the preferred mechanism for all system-level functions, using systemd-resolved makes the most sense and will likely be the standard for some time to come.

In most cases systemd-resolved will use the nameservers provided by your DHCP server during boot unless you manually override them in /etc/systemd/resolved.conf. See the manual pages for [systemd-resolved]("https://manpages.ubuntu.com/manpages/bionic/man8/systemd-resolved.service.8.html") and [resolved.conf]("https://manpages.ubuntu.com/manpages/bionic/en/man5/resolved.conf.5.html").

---

