---
title: "bcm4306 performance"
date: 2008-06-04
forum: Networking &amp; Wireless
---

### Post by jes-13 on 2008-06-04
I'm new to ubuntu, but not to *NIX.  What brought me here about a week ago, is a final attempt at a functional wireless linux laptop. Failure meant giving in to the darkside, MicroSnot, and my old laptop's eventual death by bloatware... :rolleyes:  My preferred distribution of linux is Slackware, a decision made before ubuntu was thought of... Having previously failed at getting an Intel miniPCI ...11g working, I have since upgraded the miniPCI to a BCM4306. I did the fwcutter thing with no luck and more research led me to believe I needed to try NetworkManager. That meant significant effort with KDE & Slackware. Rather than do that I thought I'd see what the rest of the linux world was been up to. I eliminated a few other distributions for various issues and decided that unbuntu looked the most promising. :D
After installing 8.04 desktop, I copied my b43 drivers and things looked promising but not yet functional. As soon as I turned on NetworkManager, wireless came up and connected with WPA. Part of exploring the minor variances of GMOME vs KDE, I soon discovered that the BCM4306 was capped at 1Mbps. :? After reading many tales of wireless woe here, I didn't feel as bad since my wireless is actually working, even if it's slow. While 1Mbps is OK for the average cyber-cafe, it's a irritant at home with 10Mbps Internet and the amount of file sharing I do... I've tried various things to bump the speed, but most result in non-functional wireless or even slower throughput. 

So finally the question... Is there any hope of getting the BCM4306 up to speed or should I just give up on a fast internal wireless solution for this laptop? I could switch back to the Intel ...g on ubuntu, that should at least give me a tick over 5Mbps, but still too slow for my home usage...

---

### Post by Ayuthia on 2008-06-04
If you have no problems with using NDISwrapper, that would be another option.  Did you try to adjust the speed through iwconfig rate?

---

### Post by jes-13 on 2008-06-04
> **Ayuthia said:**
> Did you try to adjust the speed through iwconfig rate?

yes, I tried combinations of 11M, 54M and auto. In some cases the throughput is slower, others it simply stops working even though is says it's connected.

---

