---
title: "Static IP"
date: 2007-10-28
forum: Networking &amp; Wireless
---

### Post by johnny9794 on 2007-10-28
I have 3 desktops that are ethernet, 1 lap top that is wireless, 1 xbox 360 that is wireless and one xbox with ethernet.

2 desktops and the lappy has XP on them and the other desktop "mine" has ubuntu.

I am trying to figure out how to make all the devices on my network static addressed, 

Main reason of this is that I been trying to share off of the ubuntu machine to other devices on my network and in order to do this, I need to setup static on my router.

I am just lost.

I did call my isp and got there pri and sec DNS server address so that will help later i believe.
 
I believe I will be able to handle the xp machines from this tut
[http://portforward.com/networking/static-xp.htm](http://portforward.com/networking/static-xp.htm)

but i do not know about ubuntu.

thanx.

---

### Post by chippy99 on 2007-10-29
System->Administration->Network

Then select your interface and click properties, Select static ip and fill in the boxes for the ip address etc.

You can also make the same changes by editing the file /etc/network/interfaces.

---

