---
title: "Ubuntu 14.04 - tools/utilities for internet usage monitor"
date: 2014-12-07
forum: Networking &amp; Wireless
---

### Post by la.khan on 2014-12-07
Hi all,

I have Ubuntu Linux 14.04 32 bit installed on my Dell Inspiron 1525 laptop. I am looking for an application that monitors my internet usage.

Some of my requirements are:
Configure monthly start date, specify my monthly usage limits, today's usage in MBs/GBs, cumulative usage since monthly start date, application starts automatically when laptop starts

I tried Network Traffic Monitor (NTM) using Ubuntu Software Center; but it does not find NTM. So, I searched on the web for NTM, downloaded deb file and installed it. When I try to run the application, I see a window open and then close right away. I don't see NTM running anywhere, except in System Monitor. I see NTM installed when I search in Unity but when I start it it closes right away. Is NTM incompatible with UL 14.04? If yes, how do I uninstall it?

Also, any good tools/utilities to monitor internet data usage? **I prefer ones with GUI vs command line tools**; if you need more information from my end, please let me know.

Thanks for your replies!

---

### Post by vasa1 on 2014-12-07
> **la.khan said:**
> ... I searched on the web for NTM, downloaded deb file and installed it. When I try to run the application, I see a window open and then close right away. I don't see NTM running anywhere, except in System Monitor. I see NTM installed when I search in Unity but when I start it it closes right away. Is NTM incompatible with UL 14.04? If yes, how do I uninstall it?

... if you need more information from my end, please let me know.

Thanks for your replies!
Could you provide the link/source from which you downloaded NTM? If you install any deb using the Software Center, you should be able to uninstall it from the Software Center.

Are you concerned about net usage because you have a limited internet plan?

Could your ISP have a site that provides you this information? Then all you need is a browser.

Edit: I found this link: [http://netramon.sourceforge.net/eng/index.html](http://netramon.sourceforge.net/eng/index.html) but it has this:> Tested with: Ubuntu 9.10 (Karmic Koala), Kubuntu 9.10, Xubuntu 9.10, Ubuntu 9.10 Netbook Remix, Ubuntu 9.04 (Jaunty Jackalope), Fedora 11, Fedora 12, ...So it's not surprising if it doesn't work as it should on Ubuntu 14.04.

---

### Post by la.khan on 2014-12-07
> **vasa1 said:**
> Could you provide the link/source from which you downloaded NTM? If you install any deb using the Software Center, you should be able to uninstall it from the Software Center.

Are you concerned about net usage because you have a limited internet plan?

Could your ISP have a site that provides you this information? Then all you need is a browser.

Hi vasa1,

I downloaded the NTM DEB file from here: [http://netramon.sourceforge.net/eng/index.html](http://netramon.sourceforge.net/eng/index.html)

Yes, I have a limited internet plan; my ISP does not have a website/portal/USSD code to retrieve consumed bandwidth.

I appreciate any suggestions on tools utilities for monitoring internet usage.

---

### Post by vasa1 on 2014-12-07
I found this: [SOLVED -- Network Traffic Monitor]("http://forums.linuxmint.com/viewtopic.php?f=157&t=168300") which points to [Web based Internet Bandwidth and Data Transfer Monitor - BitMeter OS]("http://linuxpoison.blogspot.in/2010/12/web-based-internet-bandwidth-and-data.html")

I have no first-hand knowledge of this program. I feel that an **unlimited** plan, even if of a lower speed, is essential nowadays.

---

### Post by la.khan on 2014-12-07
> **vasa1 said:**
> I found this: [SOLVED -- Network Traffic Monitor]("http://forums.linuxmint.com/viewtopic.php?f=157&t=168300") which points to [Web based Internet Bandwidth and Data Transfer Monitor - BitMeter OS]("http://linuxpoison.blogspot.in/2010/12/web-based-internet-bandwidth-and-data.html")

Hi vasa1,

I have installed BitMeter OS as per intructions; after installation, when I visit [http://localhost:2605](http://localhost:2605), Firefox/Chrome do not see the appln or webpage running. I see a page not found :( Any suggestions?

Also, how do I uninstall NTM and BitMeter OS? I find them installed using Unity but I can't find them in Ubuntu Software Center.

---

### Post by tahitiwibble on 2015-03-10
> **la.khan said:**
> Hi all,

I have Ubuntu Linux 14.04 32 bit installed on my Dell Inspiron 1525 laptop. I am looking for an application that monitors my internet usage.

Some of my requirements are:
Configure monthly start date, specify my monthly usage limits, today's usage in MBs/GBs, cumulative usage since monthly start date, application starts automatically when laptop starts

I tried Network Traffic Monitor (NTM) using Ubuntu Software Center; but it does not find NTM. So, I searched on the web for NTM, downloaded deb file and installed it. **When I try to run the application, I see a window open and then close right away. I don't see NTM running anywhere, except in System Monitor. I see NTM installed when I search in Unity but when I start it it closes right away. Is NTM incompatible with UL 14.04? If yes, how do I uninstall it?**

Also, any good tools/utilities to monitor internet data usage? **I prefer ones with GUI vs command line tools**; if you need more information from my end, please let me know.

Thanks for your replies!

I have the same thing happen (please see above in bold). Does anyone know why?

---

