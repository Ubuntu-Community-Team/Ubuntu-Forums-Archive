---
title: "How can I get my ip address"
date: 2007-08-17
forum: Networking &amp; Wireless
---

### Post by pacsum on 2007-08-17
Is there any command so I can see my real ip because my ISP uses two ip's: the one that everybody sees on the internet 201.200.213.54 and the real one which should start with 192.xxx.xx.xx?

---

### Post by kevdog on 2007-08-17
Your WAN address is 201.xxx.xxx.xxx.  Your LAN address is 192.xxx.xxx.xxx.  To get your LAN address type ifconfig.  To get your WAN address you either need to query your router or some web site like [http://showmyip.com](http://showmyip.com).  This could be automated to be done through script also.

---

### Post by defconoii on 2007-08-17
copy paste this in gedit or cat >>ip and paste in terminal
#!/bin/bash

echo Your external IP Address is:
wget [http://Www.whatismyip.com](http://Www.whatismyip.com) -O - -o /dev/null | grep '<TITLE>' | sed -r 's/<TITLE>WhatIsMyIP\.com \- //g' | sed -r 's/<\/TITLE>//g'

exit 0
then chmod +x ip
then ./ip
results will look like this
Your external IP Address is:
71.111.111.111
root@ion:~#

---

### Post by Strykaas on 2007-08-21
> **kevdog said:**
> Your WAN address is 201.xxx.xxx.xxx.  Your LAN address is 192.xxx.xxx.xxx.  To get your LAN address type ifconfig.  To get your WAN address you either need to query your router or some web site like [http://showmyip.com](http://showmyip.com).  This could be automated to be done through script also.

ifconfig/iwconfig  give me everything !

---

