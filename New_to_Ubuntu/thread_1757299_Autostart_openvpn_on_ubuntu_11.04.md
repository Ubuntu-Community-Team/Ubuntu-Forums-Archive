---
title: "Autostart openvpn on ubuntu 11.04"
date: 2011-05-13
forum: New to Ubuntu
---

### Post by jvl@aaa on 2011-05-13
Hi.

I am setting up a bridged openvpn connection on my new Ubuntu Server 11.04 Natty Narwhal. I succeeded in getting it up and running nicely so far. But now I would like to invoke my VPN-server at startup-time of my computer. 
To do this I entered the instruction : ¨/etc/init.d/openvpn¨ in System > Preferences > Startup Applications. However when I run:

sudo /etc/init.d/openvpn restart

I get the first time around the message that VPN is not running.  

When I start up Samba with  ¨/etc/init.d/smbd¨ and ¨/etc/init.d/smbd¨  in System > Preferences > Startup Applications, it starts running without a hitch.So why is openvpn not starting and, more important, what should I do to get it up and running at startup-time?

---

