---
title: "weird samba issue"
date: 2007-07-05
forum: Networking &amp; Wireless
---

### Post by Borzo on 2007-07-05
Hi All,

I had samba working fine for some time now, I didnt have the need to use it for some time untill today. Here's the situation :

Linux shares are visible on windows
windows shares are not visible on Linux

smbclient -L LINACER result:
timeout connecting to 208.69.32.130:445
timeout connecting to 208.69.32.130:139
Error connecting to 208.69.32.130 (Operation already in progress)
Connection to LINACER failed

I ping the windows shares SG-HOME and at seems ok except for the weird IP

the fun part is that i don't understand where the 208.69.32.130 comes from, it should be 192.168.2.2! the 208.69.32.130 is nowhere to be found in the config files i don't know where that comes from, any ideas?? i'm not sure why is windows visible as 208.69.32.130, it's assigned IP by DHCP is 192.168.2.2 

I' pretty sure noone messed with the config files

thanks!

---

### Post by Borzo on 2007-07-05
I have noticed that when my router isn't connected to the internet everything works normally, as soon as it reconnects the 208.69.32.130 is up again, very weird since the router's setup didn't change since it worked. I think this started acting up after some packages being updated... sot sure when though.

---

