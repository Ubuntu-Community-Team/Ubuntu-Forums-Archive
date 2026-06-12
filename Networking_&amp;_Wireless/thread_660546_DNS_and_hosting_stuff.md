---
title: "DNS and hosting stuff"
date: 2008-01-06
forum: Networking &amp; Wireless
---

### Post by tmasboa on 2008-01-06
Hi. I basically have an actiontec router, and if you try to visit the ip, all you get is the admin page.

Do any of you network/internet buffs know the proper steps to take to bypass this? I believe I would need a DNS server, and is there a good tutorial on how to set this up? Apache is set up a bit, and works locally within the network, but the router takes charge over port 80

thanks!

---

### Post by stalker145 on 2008-01-07
> **tmasboa said:**
> Hi. I basically have an actiontec router, and if you try to visit the ip, all you get is the admin page.

Do any of you network/internet buffs know the proper steps to take to bypass this? I believe I would need a DNS server, and is there a good tutorial on how to set this up? Apache is set up a bit, and works locally within the network, but the router takes charge over port 80

thanks!

Not knowing which model of router you have, I would say to check the [Actiontec web page]("http://www.actiontec.com/support/index.php") for specifics. From the sound of it, and assuming that you are trying to access using the *external IP* (not 192.168.x.x or the *internal IP*), then it seems that your remote configuration is set up to capture port 80. If you are using the external IP, then you should check to make sure that remote management is either turned off or is set for a port other than 80. If you are using the internal IP, then this is normal.

---

