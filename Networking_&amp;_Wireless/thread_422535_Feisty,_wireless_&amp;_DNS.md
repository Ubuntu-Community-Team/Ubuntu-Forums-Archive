---
title: "Feisty, wireless &amp; DNS"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by johnaaronrose on 2007-04-25
I successfully used (with the Swiftfox web browser & the Evolution email client) the OpenDNS servers by including their IP addresses on the prepend line in /etc/dhcp3/dhclient.conf (using Ubuntu Feisty newly released version) on a Dell Inspiron 1501 laptop linked to a wired router. The wired router I have doesn't allow setting of DNS into it.   

As the Broadcom wireless card on the laptop doesn't work with the Ubuntu supplied driver, I installed it using ndiswrapper (downloaded from sourceforge and compiled) and the R140747.EXE driver (downloaded from Dell). The wireless card then works OK to nearby wireless networks. However, Swiftfox cannot load web pages due to the OpenDNS IP adddresses disappearing, checked by using the Network Manager. Even if I then disable the wireless connection and reboot, the DNS IP addresses do not return. I can key these IP addresses manually into Network Manager, but it's a pain to do after every bootup.

Any ideas please?

---

### Post by sdide on 2007-04-25
edit /etc/resolv.conf  (as root)
and add the lines

nameserver <OpenDNS server 1 ipaddress>
nameserver <OpenDNS server 2 ipaddress>

---

