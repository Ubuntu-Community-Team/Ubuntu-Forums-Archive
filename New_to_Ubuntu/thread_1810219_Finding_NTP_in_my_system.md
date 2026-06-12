---
title: "Finding NTP in my system"
date: 2011-07-22
forum: New to Ubuntu
---

### Post by grantmcduling on 2011-07-22
Hi, I need to change a server that my ntp syncs with but can't find it in my system. I have downloaded and installed it previously and I have it marked green in synaptic. But I can't find where it's stored to check and change the settings. Where can I start? I have tried lsntp but that produces nothing.

---

### Post by doas777 on 2011-07-22
do you have an /etc/ntp.conf file?
[http://www.ubuntugeek.com/network-time-protocol-ntp-server-and-clients-setup-in-ubuntu.html](http://www.ubuntugeek.com/network-time-protocol-ntp-server-and-clients-setup-in-ubuntu.html)
(check out the client configuration for linux section).

you may want to install somthing like ntpdate:
[http://www.cyberciti.biz/faq/set-date-time-network-time-protocol-ntp/](http://www.cyberciti.biz/faq/set-date-time-network-time-protocol-ntp/)

---

### Post by papibe on 2011-07-22
There's also a graphic way to configure it: check this [tutorial]("https://help.ubuntu.com/community/UbuntuTime").

Regards.

---

### Post by oldos2er on 2011-07-22
/etc/default/ntpdate

---

