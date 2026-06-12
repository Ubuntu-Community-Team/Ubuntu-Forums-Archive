---
title: "Can't connect"
date: 2007-09-03
forum: Networking &amp; Wireless
---

### Post by Don DeGregori on 2007-09-03
I have a Fujitsu P5010D laptop, with Ubuntu 7.04 (dual boot XP).
Wireless is Broadcom BCM4306 chipset. Want to use WPA. Made Passphrase same as login password. Downloaed and installed libpam-keyring to stop nag for password. Downloaded and installed  BCM43xx procedure by B. Martin. Followed his instructions. Before I did that I showed no signal strength from any wirless. Now, I have good bar strength. **But, still can't connect **to my wireless router. XP is OK using  laptop BCM wireless. Tried AirLink USB wireless and works, but not 100% of the time. 
Can someone give me idea of what to try next, for really want to use internal wireless.

Don

---

### Post by teramonger on 2007-09-04
I don't know if this will help but i see you've been waiting.

Are you sure you can not connect to the router?  Have you pinged it?

Do you have lines like this in your /etc/network/interfaces?:
   dns-nameservers 192.168.0.1
   dns-search domainname.com

Can you connect w/o wireless encryption?

I think you have not gotten answered because more information is required, first and foremost being the ouput of "ifconfig".

---

