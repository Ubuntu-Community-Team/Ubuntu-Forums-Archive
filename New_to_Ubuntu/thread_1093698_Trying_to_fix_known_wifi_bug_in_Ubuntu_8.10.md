---
title: "Trying to fix known wifi bug in Ubuntu 8.10"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by jacatone on 2009-03-11
I'm running Ubuntu 8.10. I've found that there is a known bug with the wifi driver rtl8187b. It unexpectedly drops my connection while the network manager still shows it's connected. Since kernel 2.6.27, RTL8187B is supported natively by the RTL8187 driver. I've installed the Win98 rtl8187b driver using ndiswrapper and it shows as installed, but when I "blacklist" the default rtl8187 driver, my wifi won't connect. How would I fix this?

The link below recommends forcibly removing the default driver, but I'm afraid I'll just makes things worse. Thanks.

[http://en.gentoo-wiki.com/wiki/RTL8187#Troubleshooting](http://en.gentoo-wiki.com/wiki/RTL8187#Troubleshooting)

---

