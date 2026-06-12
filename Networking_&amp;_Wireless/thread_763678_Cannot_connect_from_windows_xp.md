---
title: "Cannot connect from windows xp"
date: 2008-04-23
forum: Networking &amp; Wireless
---

### Post by nblit on 2008-04-23
Hi All,

I have an issue connecting to an SMB share on an Ubuntu machine.
My network is as follows

2 LAN PC's
  Galaxy - Ubuntu 7.10
  Saturn - Windows XP Home
1 Wireless Laptop
  Mercury - Ubuntu 8.04
1 Linksys router - Firmware: DD-WRT v23 SP2 (09/15/06) vpn

I have created an smb share on Galaxy that i would like to connect to from Saturn.
When i attempt to use Start --> Run, \\Galaxy, OK, on Saturn i get "no network provider accepted the given network path".
When i attempt tp ping Galaxy from Saturn i get "Ping request could not find host galaxy. Please check the name and try again", when pinging by ip address it works.

When i use "nslookup galaxy", from Saturn, the ip address is resolved correctly.

My goal is to use Galaxy as a backup server.

I look forward for any advice.
nblit

---

### Post by dstew on 2008-04-23
Seems too simple, but could it be that "Galaxy" and "galaxy" are being treated differently by ping, nslookup and the XP mounting software? Maybe the samba server needs the correct case to be transmitted, but I don't really know for sure...

---

### Post by jonandrews on 2008-04-23
Have a look at my step by step guide to Windows /Ubuntu networking:

[http://www.europe.eclipse.co.uk/Ubuntu/](http://www.europe.eclipse.co.uk/Ubuntu/)

I hope it is helpful

---

