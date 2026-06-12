---
title: "network monotoring with linux"
date: 2011-06-05
forum: New to Ubuntu
---

### Post by Smooth Operator on 2011-06-05
Which programs do you recommend and why?..

---

### Post by Frogs Hair on 2011-06-05
There are some commands that can be used without any installations .[http://www.cyberciti.biz/tips/top-linux-monitoring-tools.html](http://www.cyberciti.biz/tips/top-linux-monitoring-tools.html)

---

### Post by alphacrucis2 on 2011-06-05
> **Smooth Operator said:**
> Which programs do you recommend and why?..

For packet capture and analysis there's wireshark, or just for capturing packets you can use tcpdump from the command line. If you want to monitor performance you can use things like [MRTG]("http://oss.oetiker.ch/mrtg/") for monitoring Cisco routers and switches and the like. [Smokeping]("http://oss.oetiker.ch/smokeping/") is quite useful for monitoring end to end connectivity and latency.

---

