---
title: "sb4200 usb cable modem problem"
date: 2005-04-27
forum: Networking &amp; Wireless
---

### Post by AlraM on 2005-04-27
I have the Ubuntu live cd and I tried to get internet running properly... though I spent several hours on this, I haven't really succeed much. I have an external cable modem, model motorola SB4200. After trying out a few things, I noticed, to my great surprise, that on the website of my internet provider there was linux support to be found. 

The instructions there were pretty much these (sorry if I translate anything badly):
To configure the settings for your modem in Linux you should use the following commands:
[root@user root]# /sbin/ifconfig eth0 xxx.xxx.xxx.xxx netmask 255.255.255.0
[root@user root]# /sbin/route add default gw 213.164.250.1 (to add the gateway)

okay, all's well and great, but when I type in /sbin/ifconfig eth0 xxx.xxx.xxx.xxx netmask 255.255.255.0 I get a little error saying xxx.xxx.xxx.xxx - host name lookup failure

I'm not really very sure what to do next.
I've already tried configuring it from networking, and although the connection seemed to get enabled just fine when it came to opening a browser it was pretty obvious that something is going wrongly...

I would greatly appreciate any ideas... Thank you in advance.
AlraM

---

