---
title: "Optimizing your internet connection speed"
date: 2006-12-02
forum: Networking &amp; Wireless
---

### Post by Handssolow on 2006-12-02
Are there any tweaks to improve my download speed?

In October I upgraded from a 1 Mbps ADSL to a 8 Mbps ADSL connection. My Netgear WLAN router DG834PN reports in the statistics section (just now) that it's downloading at 8128 kbps and uploading at 448 kbps, hey not bad. But when browsing ebay and a couple of forums which I visit, things don't seem that fast, not much faster that my previous 1 Mbps. Is it them, me, my ISP or the internet?

Apart from speakeasy which seems to be based in the USA, are there other speed test sites suitable for Linux?

[http://www.speakeasy.net/speedtest/](http://www.speakeasy.net/speedtest/)

Are there any settings in the router or in Ubuntu that need optimized for 8 Mbps ADSL?

---

### Post by diskotek on 2007-06-18
bump.... i'm also looking for that.

---

### Post by bollix47 on 2007-06-18
Not sure about the settings bit but for another speed test site try:

[www.speedtest.net](www.speedtest.net)

They have multiple servers to choose from.

---

### Post by Rui Pais on 2007-06-18
Hi.
There are [those tips here]("http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed#Broadband_Internet").

But i never noted any special difference... i may confess.

I think that those high speeds are only possible for continuous downloads, that retries a big package or an iso in ininterrupt flux. 
Html pages requires accesses to remote server, verification of protocols, download of images and icons one by one (not without more access and more validation of remote page) render of pages... etc. 
Not a continuous process but a very fragmented one. :(

---

### Post by nymphaeles on 2007-06-18
Many sites use traffic shaping to limit your throughput, therefore, you can only go up to a certain speed for a typical connection.  Many other sites are too busy as so many people trying to get to it, so your fast big pipe to your machine can't help it.
I don't believe there is anything within your machine that you can (or should) fine tune to make it sending and receiving faster, except eliminating those malware that eating up your bandwidth.
You can; however, eliminate bandwidth consumming traffics such as ads, banners, pop-ups, and other Internet junks from http traffic by using a firewall with appropriate proxy filters.  That would drop those packets and let only useful traffic to your machine.  The benefits are obvious.

---

### Post by Handssolow on 2007-07-24
I was checking my old postings and seeing the replies, I  thought I add a post-script.

Essentially my internet download speeds have been satisfactory for some time but this was only after the fault at our local telephone exchange had been sorted. I had to first prove to my ISP that my dowlload speeds were slow before they would report the matter to British Telecom . My direct phone calls to BT were met with a brick wall because my contract was with my ISP.

---

