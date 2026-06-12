---
title: "Any cisco folks out there?"
date: 2007-07-08
forum: Networking &amp; Wireless
---

### Post by crisponions on 2007-07-08
I am having an annoying problem with apt, and i think I have narrowed it down to my Cisco 837 ADSL router.  Whenever I download packages/updates I start out strong then I will trickle down to 8000 Bps, after a while it might speed up again, then it slows down again.

I dont have this problem at work, so it has to do with my connection.  It happens both with my Debian Etch and Ubuntu desktops, but I dont have issues with other types of downloads (browser etc.) only with apt.

Router has plenty of memory and CPU resources available and I have a really simple config.  Any ideas?

Thanks

---

### Post by Amplidude on 2007-07-08
Hi Crisponion
Actually this may not have anything to do with your router or setup at all. Seems to me that if the download is fast at times the router/setup is fine. It could depend on several other things: 
1. The phone company specifies the total bandwidth available to different areas (e.g. a group of suburbs) and if a lot of people are on line in that area at the same time it chokes up.  Work areas are allocated more bandwidth than residential areas, hence it's slower at home.
2. If the site you are connecting to is visited frequently your ISP will have the site cached, and the response time and rate will be a lot faster (you're not actually using international bandwidth)
3. If the site is not cached, download will be slower because you will be downloading from a distance.
4. if you are connected to a remote site, the download speed is governed by that site's available bandwidth. Sometimes this can be quite low, and if there is a lot of traffic to the site, best have a cup of tea.
I know this doesn't help much because there's nothing you can do about it, but before you tamper with the setup, check the sites that are downloading slowly and try downloading at a time when there is less load on their server (say midnight their time).  If the download is faster, the problem is with them, not with you. 
Ciao

---

