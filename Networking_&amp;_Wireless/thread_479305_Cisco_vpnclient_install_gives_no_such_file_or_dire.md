---
title: "Cisco vpnclient install gives no such file or directory error"
date: 2007-06-20
forum: Networking &amp; Wireless
---

### Post by Baumsich on 2007-06-20
Hi,

I have a macbook with ubuntu 7.04, 2.6.20-15-generic and tried to install the cisco vpnclient as described in:

[http://tuxx-home.at/archives/2007/05/29/T16_34_26/](http://tuxx-home.at/archives/2007/05/29/T16_34_26/)

All works fine (install gives a few warnings but installs fine) but when I do
$ vpnclient

I get the following error message:
bash: /usr/local/bin/vpnclient: No such file or directoy

This is not true, the file is there, it does not help to execute the binary directly and it is not the permissions of the file either. So I guess the installation comes up with some corrupted file ?

Any ideas?
Thanks.
Baumsich

ps I did all the vpn client installation successfully on another laptop (same kernel) ...

---

### Post by Baumsich on 2007-06-21
Fixed by removing the 64bit version and installing standard version.

---

