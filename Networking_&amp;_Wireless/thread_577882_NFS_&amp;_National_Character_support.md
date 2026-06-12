---
title: "NFS &amp; National Character support"
date: 2007-10-16
forum: Networking &amp; Wireless
---

### Post by mauritzius on 2007-10-16
Hey, 

I recently installed Ubuntu 7.04 on my laptop connected via ethernet to my server which runs SoL-Linux. The server exports its data via NFS to the laptop, mounting and accessing files work perfectly. 

However, problems arise with national characters, like ä, ö or ü in german. 
I *guess* the problem is the following:
$LANG is set to en_GB on the server
$LANG is set to en_US.UTF-8 on the client
-> there might be a character conversion problem

I then edited /etc/environment under Ubuntu to change $LANG to en_GB; The locale was changed, the characters however couldn't be read either.

On another machine running a version of SoL configured $LANG to en_GB, everything works as expected.

What else can I try?

thanks & greetings

---

