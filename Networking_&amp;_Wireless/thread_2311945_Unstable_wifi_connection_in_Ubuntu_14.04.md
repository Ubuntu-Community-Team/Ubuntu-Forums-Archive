---
title: "Unstable wifi connection in Ubuntu 14.04"
date: 2016-01-31
forum: Networking &amp; Wireless
---

### Post by pg1338 on 2016-01-31
I recently installed (clean install) Ubuntu 14.04, but the wifi connection is unstable.
Every half an hour or so, the wireless disconnects. Turning off wifi on my laptop and turning it on again reconnects it.


I tried the following from other similar threads:


1) Setting IPv6 to Ignore.


2)


```
sudo -i
echo "options rtl8723be fwlps=0"  >  /etc/modprobe.d/rtl8723be.conf
modprobe -r rtl8723be
modprobe rtl8723be
exit



```3) Added the following to /etc/modprobe.d/iwlwifi.conf


```
options iwlwifi 11n_disable=1
options iwlwifi swcrypto=1

```

There are also suggestions to upgrade the kernel to 3.18, but my original kernel was 3.19, which I upgraded to 4.2, but the problem persists.


Here are the details of my wireless: [http://pastebin.com/DpYJmq1c](http://pastebin.com/DpYJmq1c)


Any suggestions?


Thanks in advance!

---

