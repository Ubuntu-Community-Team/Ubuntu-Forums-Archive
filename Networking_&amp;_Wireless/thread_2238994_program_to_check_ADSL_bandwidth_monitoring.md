---
title: "program to check ADSL bandwidth monitoring"
date: 2014-08-11
forum: Networking &amp; Wireless
---

### Post by davidtuti2 on 2014-08-11
Hi,
There is some program from command line to check bandwidth monitoring of the different IP's of my lan to can check what of them is consuming more and what program is using

Many thanks and sorry for my English!

---

### Post by TheFu on 2014-08-11
Many routers support bandwidth graphing.  The aftermarket "tomato" firmware [http://www.howtogeek.com/74881/how-to-monitor-and-log-your-bandwidth-usage-with-tomato/?PageSpeed=noscript](http://www.howtogeek.com/74881/how-to-monitor-and-log-your-bandwidth-usage-with-tomato/?PageSpeed=noscript) is probably the easiest, if it supports your router.  It is impossible to monitor bandwidth from any device that is NOT in the required path - for most home setups, that means the router must perform this task.

Some routers will report bandwidth use over SNMP [http://www.uptimemadeeasy.com/monitoring/monitor-cisco-routers-cacti-graph-bandwidth-usage/](http://www.uptimemadeeasy.com/monitoring/monitor-cisco-routers-cacti-graph-bandwidth-usage/) - and you can setup a workstation to receive that data, generate reports/graphs as needed.  This method is more work than most normal users are willing to do.

---

