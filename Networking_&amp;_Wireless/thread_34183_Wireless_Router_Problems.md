---
title: "Wireless Router Problems"
date: 2005-05-13
forum: Networking &amp; Wireless
---

### Post by Craigavonite on 2005-05-13
I just installed 5.0.4 (complete noob, just switched from winxp literally an hour ago)

the install went fine with no problems, and everything seems to be working fine

the problem im having is that i cannot connect to the net. i can see the wireless router in the network connections window, and it has filled in the ip address and domain name for it automatically...i can also ping it, yet i cant connect to it or the net in firefox???

anyone have any ideas?

btw im on xp on my other hdd right now usign the same router, so its not a hardware issue

thanks

---

### Post by crmanski on 2005-05-13
Curious if you can ping a remote IP address vs. pinging a host name.
If you try to ping [www.ubuntu.com](www.ubuntu.com) does it work?
If not how about if you just ping the IP address...
82.211.81.130

If the IP address is works but the name does not then it is most likely that your dns settings are incorrect.

To add a dns server...
If you go to the System Menu, slide down to Administration, choose Networking, double click on your Ethernet Connection and then the DNS tab. Is there anything there? If not then add the IP address of your router, which will usually handle the dns. To get other DNS addresses log on to your routers remote admin and see what it got from your ISP.

---

### Post by Craigavonite on 2005-05-13
thanks, but i got it working eventually

i just formatted and reinstalled, and now it works...but i didnt change any settings the first time round, its exactly the same, but now it works, pretty strange, but i aint complaining

thanks man  :)

---

