---
title: "kppp doesn't work"
date: 2006-09-23
forum: Networking &amp; Wireless
---

### Post by bhintz on 2006-09-23
I am using Kubuntu 606 and have installed to my hard drive.  It seems that I have to edit "grub" whenever I boot to get a screen resolution that is reasonable (1024x768).  Otherwise it is something like 320x240.  This is a bother, but at least I now know how to do it.  

I am able to get on the internet with an external modem and "networking" but would like to get kppp working. Both "kppp" and "networking" programs seem to work the internal modem but do not connect.  "networking" does connect with external modem but I have to fill in information every time as it will not save data over a shut down.  I am getting skilled at doing this as well, but it is also a bother.  kppp will not connect even with the external modem.  I get the following message 

Sep 22 22:49:02 localhost pppd[5187]: The remote system is required to authenticate itself
Sep 22 22:49:02 localhost pppd[5187]: but I couldn't find any suitable secret (password) for it to use to do so.
Sep 22 22:49:02 localhost pppd[5187]: (None of the available passwords would let it use an IP address.)

I have no idea what this means or how to fix it.  

Any help would be appreciated. I like to program and love the philosophy, but I would really like to get it operating on a consistent basis.

Bob

---

### Post by Trm on 2006-09-23
[http://therandymon.com/content/view/31/79/](http://therandymon.com/content/view/31/79/)  If you haven't already done so you need to create an /etc/resolv.conf file.  Also by default kppp requires authentication to connect.  In the above link he changes the auth to noauth in /etc/ppp/options.  However, it states there not to change that setting but instead you should edit /etc/ppp/peers/kppp-options and edit out the # in front of noauth or change it to noauth.  I can't remember if /etc/ppp/peers/kppp-options was empty or read #noauth.  I know I'm not making this terribly clear  but if you read that link you should be able to connect.  Time for a nap!

---

