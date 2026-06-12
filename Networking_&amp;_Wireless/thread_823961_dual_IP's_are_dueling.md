---
title: "dual IP's are dueling"
date: 2008-06-09
forum: Networking &amp; Wireless
---

### Post by ireuel on 2008-06-09
I should know this, but I can't fix this simple prob, and it's making me crazy. I have an XP computer at the front of my store which has been running printers just fine. (I'm a copy/print shop.) Now I've put DSL/wireless into the store, it's also working fine. 

I'm trying to get Internet to the front computer, but it's got two IP's, and they seem to hate each other. I run the printers on static IP over cat5. But I can't get Internet over wireless. When I disable the LAN, the wireless works great. 

I got a tip that said I should leave the gateway blank on the LAN. Tried it...didn't work. Any other suggestions?

Thanks a gob in advance.

---

### Post by Rocket2DMn on 2008-06-09
Since nobody else seems to have any ideas, perhaps manually inputting DNS server info from System->Administration->Network, DNS tab will help.

---

### Post by issih on 2008-06-09
Only thing I can think of is that some of the ip addresses being used on the two separate nics are being duplicated, so when both networks are up the system can't resolve the conflicting ip address to a unique device.

what are the ip addresses you are using on the different networks.

i.e. what is the static ip address of the wired ethernet card and the printers it connects to, and what is the ip address of the wireless router?

---

### Post by ireuel on 2008-06-10
Got it fixed. Thanks for the help. I had both cards on 192.168.50.xx. Switched the statics to 192.168.0.xx, but then I had to go into Printers and switch the ports to 0 there too. 

Couldn't have found it without your suggestions. Thx.

---

### Post by issih on 2008-06-10
Excellent, glad that worked, I had similar problems a while ago with a network access point and a statically configured wireless card....thats why I thought of it :)

---

