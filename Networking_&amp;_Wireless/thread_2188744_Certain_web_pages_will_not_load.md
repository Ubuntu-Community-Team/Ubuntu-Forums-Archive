---
title: "Certain web pages will not load"
date: 2013-11-18
forum: Networking &amp; Wireless
---

### Post by Bhakti108 on 2013-11-18
Has anyone experienced the following problem, if so what is the fix?

I recently took out an account with outlook.com in order to be able to use a sharepoint collaberation with people overseas. At first all was fine, then last week I couldn't sign in on any of microsofts live.com sites. The pages would simply sit blank with the little circle in the tab going round and round. Then this behaviour also happened on ebay.au site sign in page as well. 

However other pages open normally, sign in for here was fast as normal etc. 

I used bleachbit to clear all caches and vacuem firefox, tried chrome, and epiphany on Ubuntu 13.04, also tried Chrome, Firefox, IE on win 7 on this computer and still the same across OS and browsers.

I decided to reinstall 13,04 which I have just completed - formatting the root drive to make sure there were no issues there. 

and no change -- in fact ebay has just returned a "server taking too long to respond" error after 9 minutes of trying to connect. 

My speed is good and my signal excellent  


Test run on **19/11/2013** @ **11:00 AM**


 	 	Mirror: **Optus**
	Data: **21 MB**
	Test Time: **10 secs**
 	 	Your line speed is **17.5 Mbps** (17504 kbps).
	Your download speed is **2.14 MB/s** (2188 KB/s).

Any ideas anyone?  :confused:

---

### Post by TheFu on 2013-11-18
Well, if your subnet is full of known spammers (email/blog), lots of websites will block the entire subnet range.  I do.  Heck, I block entire countries using Country-to-IP address tables, which are not perfect. If this is the situation, and I don't know that it is, then the only solution is to make your request look like it comes from somewhere else using a proxy service.  I block a few proxy services too, however, but only after they abuse my servers first.

Sometimes governments will require ISPs to filter/block certain domains. Pakistan, China, lots of middle eastern countries do this all the time.  Had someone contact me from UAE last month trying to get access to my blog. I wasn't blocking anything ... both his home and work IPs couldn't get to that specific server. I never figured out why, since it wasn't on my end.

There is an idea of "network near" between different locations in the world.  About a year ago, I was trying to view a webpage on a server in rural France.  From my location, it was over 64 "hops" to get there.  In our network stacks, there is a parameter called TTL - Time To Live - it is part of IP to prevent lost packets from bouncing around the internet forever.  Basically, if a transmitted packet doesn't reach the destination within 64 hops, then it gets dropped.  Each router along the way, reduces the TTL value by 1. At zero, it is dead.

Then some ISP "somewhere" could have routing mistakes. Once in a while this happens and prevents packets.  I think a small ISP bumped almost all of China off the internet a few years ago by a simple, tiny mistake. The rest of the world thought it was changes to the "great firewall", but it wasn't.

There might be lots of other reasons beyond my knowledge too.

---

