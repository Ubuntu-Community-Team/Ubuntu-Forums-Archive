---
title: "Error resolving hostnames"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by Spky on 2007-10-30
Hey guys,

I have just upgraded to Ubuntu 7.10, all went well and most things are working again, all except networking. I have strange problems resolving hostnames. Firefox, and in that fact most other internet applications are failing, giving errors about the resolving of given hostnames. I next open a terminal and try to ping a website, only to see that it resolves the sites hostname and connects without error. This confused me further! My resolv.conf seems correct and, upon comparing it with another computer on my network (running on 7.07), I found that settings were exactly the same. Is this a known bug, or am I doing something wrong:(?

Sorry to come to this community with negative posts, but I am totally stumpt upon this matter.

Thanks, 
Sean.

---

### Post by Spky on 2007-10-30
Bumping is bad :o

---

### Post by nicean on 2007-10-30
One thing you might check:  if firestarter is installed, turn it off completely (I.E. sudo /etc/init.d/firestarter stop) and try to connect again.  If it works after you do this, then it's a firewall issue and you'll need to play with the settings in firestarter to fix it.

HTH

---

### Post by Spky on 2007-10-30
Nope, it's not the firewall.

Edit: Oh em gee! Yeh, anyways, NetworkManager decided to get off it's *** and do it's job.

---

