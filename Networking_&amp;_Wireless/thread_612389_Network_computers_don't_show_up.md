---
title: "Network computers don't show up"
date: 2007-11-13
forum: Networking &amp; Wireless
---

### Post by BlastOButter42 on 2007-11-13
Hi. I've got a wireless router in my apartment, and I have a home network/workgroup ("GOOBER") set up with a Windows XP desktop computer (named "Geoffrey") and my laptop (which dual-boots XP and Gutsy). I can access files and printers on Geoffrey from the laptop when running XP. In Gutsy, I should be able to do this by going to Places>Network>Windows Network (right?), but nothing shows up. Anyone know how to fix this?

Any help would be greatly appreciated. I'm pretty new to Ubuntu so I'd appreciate it if help could be given as un-technically and easy-to follow as possible.

---

### Post by Digitallysick on 2007-11-13
try going to Administration, shared folders, and click the general properties tab, and type in your network    GOOBER     , not sure if this will help but you want them on the same network

---

### Post by Peter09 on 2007-11-14
There seems to be a problem with Gutsy in name resolution. Try going to places->connect to server.


Select from the drop down menu the type of share.
In the server name field put the ip address of the server which is presenting the share and put the share in the share name, try that.

---

