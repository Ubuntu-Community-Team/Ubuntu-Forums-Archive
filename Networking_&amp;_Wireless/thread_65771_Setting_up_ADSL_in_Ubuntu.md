---
title: "Setting up ADSL in Ubuntu"
date: 2005-09-15
forum: Networking &amp; Wireless
---

### Post by TuxicGuy on 2005-09-15
Hi folks!
           I installed Ubuntu yesterday in dual-boot configuration with XP on my HP Pavilion PC. Everything works well except for my ADSL configuration. This is strange because :
  (1) I set interface eth0 as having static IP Address - and entered the IP address as 192.168.1.2 / Gateway is 192.168.1.1 ( the Modem) - I'm not sure whether my ADSL uses DHCP.

 (2) I can actually ping 192.168.1.1 ( the modem) successfully from applications->network tools. I can even perform lookups from here for various websites.

 BUT
    when i open firefox to visit any website, it just says ...Connecting to [http://www.yahoo.com](http://www.yahoo.com) and times out. upon investigating further, i discovered that if i go back to network tools and perform DNS lookup for [www.yahoo.com](www.yahoo.com) and then try to use firefox to open the site, it loads up the site - but further lookups from within the browser fail! - ( as images for yahoo are loaded from another server) 

 I'm using a UTSTAR Modem. I would appreciate it if you knowledgeable people could share your thoughts on this problem. Thanks in advance,


TuxicGuy

---

### Post by kahping on 2005-09-15
did u try running Terminal and executing this? :

```
sudo pppoeconf
```

most of the options you can just stick to default except username and password of course  ;-) 

kahping

---

### Post by TuxicGuy on 2005-09-15
Thanks for responding!

Yes, I did run sudo pppoeconf - but it keeps reporting that it is unable to find the access concentrator at eth0. Hope that helps.

TuxicGuy

---

### Post by TuxicGuy on 2005-09-15
Yahoo!!...I'm posting this from Ubuntu - I figured out the problem - The DNS server was incorrect - it was having the same IP as the Modem - Thanks for responding!

---

### Post by kahping on 2005-09-16
no problem. too bad i wasn't much help.

congrats all the same on getting your internet connection up and running ;-)

kahping

---

