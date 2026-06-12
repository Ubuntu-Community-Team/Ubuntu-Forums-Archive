---
title: "keeping router ip and /etc/hosts in sync?"
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by bhold on 2008-05-22
I have a simple home network consisting of 3 computers running Ubuntu 8.04, Win XP, and Vista. Wired network through a Linksys router.

So last night, power fails for a few minutes. When everything is back up my XP system (also the print server) is no longer 192.168.1.100, but instead is 192.168.1.101. I could not print or access shares from Ubuntu to XP until I made the change in /etc/hosts on the Ubuntu system.

Question - is there a better way to configure the home network, power fails are fairly common in our area and it would be great if everything would come back up with the home network functioning.

My ISP provides cable only so static ip to the outside world is not an option, only DHCP. My router doc says for this I need to keep the DHCP setting on but I'm not sure whether or not that has anything to do with ip re-assignment within my home network.

---

### Post by superprash2003 on 2008-05-22
i think setting a local static ip under system->administration->network should do!!set it to 192.168.1.100 so it will never change..if you have problems you can always revert back to DHCP

---

### Post by chili555 on 2008-05-22
It's not terribly clear to me from your post, but I think you are mixing apples with oranges. Between your ISP (cable modem) and your router is set up as DHCP and there is probably no option for you to change it to static. Your ISP _is_ willing to give you a static IP address if, for example, you want to host a website and use up tons of bandwidth, if you want to pay and pay and pay for the privilege. From your post, I doubt that's your situation.

Within your network, in 192.168.1.x land, is a whole different story, really mostly unrelated to the first outside story. You can have the router (the mayor of 192.168.1.x land) set to be a DHCP server or not. That doesn't affect the outside world. You can have static and DHCP addresses both in 192.168.1.x land. If you decide to have all static, you can unclick 'Enable DHCP server' or not; it will still work.

Like you, I have a printer attached to an Ubuntu desktop which I want to share with other computers on my network. The solution is to give it a static address, in my case 192.168.1.116 and set the */etc/hosts* files of the computers that want to access the printer accordingly.

Even if you have to have the DHCP server on to work and play well with the cable modem, which I doubt, that doesn't stop you from also having static IP addresses inside 192.168.1.x land. 

Short answer: set the XP/print server machine to static. It will prevent collisions if you pick a static address outside the range of the DHCP server; that is, if your router is set up to give 5 DHCP addresses starting at 192.168.1.100, then the highest it can give is x.104. Start your static addresses at x.110, for example.

---

