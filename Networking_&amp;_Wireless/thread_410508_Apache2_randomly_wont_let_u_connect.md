---
title: "Apache2 randomly wont let u connect"
date: 2007-04-15
forum: Networking &amp; Wireless
---

### Post by geminias on 2007-04-15
Hi, I'm experiencing this major issue of my web server deciding its just not going to let anyone communicate with it anymore.  Nothing shows up in the logs to say that it is going down, in fact it doesn't seem to be going down because I can still connect to it on my internal ip.  Once I connect to it on my internal ip people can communicate with my server again...  For a short time until it feels like no longer communicating again and then i have to type my internal ip in the web browser to get it working again... and so on so forth... 

I'd like to assume this has nothing to do with apache2 and blame it on my router, i have a dlink 624 revision c, could anyone give me a tip?  Thanks.

---

### Post by dmizer on 2007-04-15
most likely causes (in no particular order)

1) router problems ... try rebooting it.
2) local dns issues? are you using opendns ... could cause this problem.
3) firewall.  did you install firestarter?

---

### Post by Clarencemark on 2007-04-17
Yes, I have Firestarter installed. On a hunch, I decided to stop Firestarter and low and behold I can access the internet. Oh, for the record, I using Fiesty Beta.

What's up? I never had this issue before in Edgy.

---

