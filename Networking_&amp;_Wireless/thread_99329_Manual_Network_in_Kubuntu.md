---
title: "Manual Network in Kubuntu"
date: 2005-12-05
forum: Networking &amp; Wireless
---

### Post by markr on 2005-12-05
When I start up Kubuntu,  it seems to take minutes just sat at the configuring network line.  I'm assuming it is trying to negotaite an IP address via DHCP over my wireless network even though I'm in the office with no wireless connection available.

I notice in my interfaces file the line "auto wlan0"; if I remove this line will it not try and configure it at boot time?

I'm assuming I can still issue a "ifup wlan0" from the command line if I do want to connect to the internet (and I'm in range of my wireless router)?

Mark.

---

### Post by carlosqueso on 2005-12-05
I'm pretty much a n00b, but I did it the other way (commented out the "auto eth0") on my laptop at home (I use wifi all the time), and it seems to have worked.   Also, if you comment that line out, you can still use the "ifup" command to bring any network up.   Hope this helps.

---

