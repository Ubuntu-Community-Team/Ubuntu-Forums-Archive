---
title: "Ubuntu Router for network monitoring"
date: 2006-09-11
forum: Networking &amp; Wireless
---

### Post by Jabran Asghar on 2006-09-11
Hi, 

I want to configure an ubuntu box on a same subnet to configure routing between two machines. Following is how I want to setup:

Internet------|FireWall|--192.168.1.0--|Ubuntu Router|-- 192.168.1.0--|Rest of Ubuntu Desktops

Note that the subnet is same before and after the Ubuntu Router. I dont want to change the subnet to avoid changes on Firewall or desktops.

Actually I want to run Ethereal on the router to monitor all in/out traffic .

I have looked as Shorewall, GuardDog, and GuideDog. The later two seems promising but I could not get routing to work properly.

Will appreciate any hints or suggestions.

Thanks.

Jabran

---

### Post by tbonius on 2006-09-11
You can setup IPtables with two interfaces in bridging mode (add a 3rd if you want to configure some sort of static IP that you can connect to the monitoring tools with).  Then install a combination of MRTG (for bandwidth monitoring), and SNORT (for Intrusion detection).  That way you can have a passive router (and firewall if you want to filter ports) that monitors traffic.

Tools like Shorewall are nice and neat tools for what already exists.. IPtables.

- Shameless Plug -

[http://www.section6.net/wiki/index.php/Main_Page](http://www.section6.net/wiki/index.php/Main_Page)

Linux and BSD tutorials

Hope this helps

T

---

### Post by Jabran Asghar on 2006-09-12
Thanks for the information, it helped me. Currently, I am doing few more tests, so, will get back soon with results, and perhaps with few more questions ;-)

---

