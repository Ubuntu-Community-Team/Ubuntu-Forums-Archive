---
title: "ip commands???"
date: 2007-06-07
forum: Networking &amp; Wireless
---

### Post by Hawk__0 on 2007-06-07
im trying to connect my wii to the internet.

what i have done is hooked a wireless router into my switch, which im connected to, however im unable to communicate with it thru wired.

what i tried was plugging my nic directly into a host port on the wireless router, but ubuntu still shows my same ip, which wAs obtained from my other router

what are all the commands for releasing, renewing, and that stuff for ubuntu/bash??

i need to config this router

---

### Post by Hendrixski on 2007-06-07
normally you can just log into the router.. it's address is usually 192.168.2.2  I think

something like that.  I've had problems doing this with firefox once or twice then tried it with Opera and it worked.

The command line commands for IP are usually ifconfig (or iwconfig for wireless) but in feisty you should just forget those exist because network manager handles all of that and if you tinker with it you may trip up the network manager.

---

### Post by Hawk__0 on 2007-06-07
actually, 192.168.0.1 = dlink, 192.168.1.1 = linksys
by default

---

