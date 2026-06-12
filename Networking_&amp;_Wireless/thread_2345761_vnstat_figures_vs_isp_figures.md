---
title: "vnstat figures vs isp figures"
date: 2016-12-07
forum: Networking &amp; Wireless
---

### Post by netcom61 on 2016-12-07
Hello
Hoping someone is savvy about bandwidth and vnstat and similar such bandwidth monitoring apps.
We've got vnstat installed on home computers/laptops, and bandwidth monitors on our mobile devices, however, the results we are seeing do not compare to our ISP's figures.
We are on monitored bandwidth, and our ISP's bandwidth figures are almost double that indicated by our bandwidth monitoring apps.  Might vnstat read figures/bandwidth for incoming and outgoing data differently than how the ISP is measuring them? Is there a definitive way to know bandwidth data usage if not vnstat? 
Thanks

---

### Post by netcom61 on 2016-12-08
Nobody?

---

### Post by Vergo on 2016-12-09
You don't mention much details regarding which Ubuntu release is being used, which version of vnStat is running and what kind of internet connection you have. When configured correctly, vnStat will see exactly what the kernel sees which in turn is very close to what your ISP sees unless there are lots of resends or other errors. The catch there is "when configured correctly" as old versions of vnStat have the default configuration tuned for rather slow connections based on today's standards. More recent versions have partial autodetection available for the relevant settings, at least for wired connections, but the version of vnStat usually depends on the Ubuntu release you are using.

Based on past experiences, it's usually a configuration issue if vnStat shows the traffic readings wrong.

---

### Post by netcom61 on 2016-12-12
Thank you for your reply

The version of Ubuntu is 14.04, and the version of vnstat is 1.11

Our ISPs usage site, and the corresponding bill shows double the amount of data/bandwidth used as compared to our data-monitoring apps. The apps are on laptops and mobile devices and added together, they only account for half what our ISP claims was used. I just can't see there being that much discrepancy.   Many of our neighbors with the same ISP are claiming they are being billed for what seems an inordinate amount of data/bandwidth too.

---

### Post by Vergo on 2016-12-14
Check the content of [FONT=Courier New]/etc/vnstat.conf[/FONT] and locate a line starting with [FONT=Courier New]MaxBandwidth[/FONT]. If the value on that line is smaller than the bandwidth you have towards your ISP then that's the problem. In that case, adjust the value accordingly and restart the daemon. That should fix the issue.

---

