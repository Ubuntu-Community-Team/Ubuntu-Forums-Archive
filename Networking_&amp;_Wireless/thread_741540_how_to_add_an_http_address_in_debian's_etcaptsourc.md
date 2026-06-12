---
title: "how to add an http address in debian's /etc/apt/sources.list"
date: 2008-04-01
forum: Networking &amp; Wireless
---

### Post by Oldsoldier2003 on 2008-04-01
> **Auston said:**
> hi guys cn u assists me on this one,how can i add an http address in the file /etc/apt/sources.list in debian,so that if i want to get a certain package in debian's stable distribution,i'll just run apt-get install <packages> it will install in the system..my present /etc/apt/sources.list is below,I would like to include the address packages in stable distro in the search,is it possible & how to do it and put in the this file below..if u'll add additional enlightment.I will be very glad to..thanks in advance guys...

deb cdrom:[Debian GNU/Linux 4.0 r0 _Etch_ - Official i386 CD Binary-2 20070407-$deb cdrom:[Debian GNU/Linux 4.0 r0 _Etch_ - Official i386 CD Binary-1 20070407-$

deb [http://security.debian.org/](http://security.debian.org/) etch/updates main contrib
deb-src [http://security.debian.org/](http://security.debian.org/) etch/updates main contrib

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_add_extra_repositories) shows you the way to properly add repositories manually.

---

