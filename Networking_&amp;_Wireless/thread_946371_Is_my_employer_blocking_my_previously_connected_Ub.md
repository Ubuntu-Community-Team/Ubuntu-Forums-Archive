---
title: "Is my employer blocking my previously connected Ubuntu machine?"
date: 2008-10-13
forum: Networking &amp; Wireless
---

### Post by american.swan on 2008-10-13
For almost 6 months I have been running a desktop Ubuntu machine at my place of employment.  For reference I also had a small wireless "internet phone" AP connect also.
 
Last week, after what I was told were server "upgrades" my ubuntu machine lost Internet connectivity.  It was also using DHCP or "roaming" before.  Now I guess they changed it to static.  So I had to plug my computer into my "Internet phone" AP.  
 
My "phone" AP lost connection over the weekend.  So now my phone doesn't get any internet connectivity and neither does my ubuntu.
 
At first I thought it was a wiring problem, but some maintenence guy was able to get Windows connected to the network using my LAN cable and wall socket, so I figure it's something specific to Ubuntu.
 
So my main question.  I have some supposedly working IP and gateway numbers.  How do I properly set up my "static" information to confirm once and for all that Ubuntu isn't the problem and that my machine is blocked due to OS.  [wifi phone isn't "windows" either]
 
Second question.  Would it be possible to get windows XP to share it's web connection to my ubuntu box without the "blocking" computer knowing it?
 
[whole company uses XP and I am 99.9% sure the gateway is windows too.]
 
[side note:  local phone company has a wifi phone that makes very cheap international and local calls.]

---

### Post by superprash2003 on 2008-10-13
have you tried using static ip in ubuntu?? do you have a windows machine as well?? most cases dhcp has been disabled for your network and every client has to enter static ip... thats what i think they have done.. so then even for your wifi phone you need to do the same . enter ip manually..

---

### Post by Iowan on 2008-10-13
If your desktop has 2 NIC's, you could set up ICS... If they've provided you with a static IP address, Ubuntu can be set up to use it.
Unpleasant as it may be, your employer DOES own their network - so they get to choose what will/won't run on it.

---

