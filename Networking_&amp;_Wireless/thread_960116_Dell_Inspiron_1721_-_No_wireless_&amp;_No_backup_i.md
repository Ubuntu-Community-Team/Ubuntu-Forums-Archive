---
title: "Dell Inspiron 1721 - No wireless &amp; No backup internet"
date: 2008-10-27
forum: Networking &amp; Wireless
---

### Post by MacGyverist on 2008-10-27
Wireless is my only means of connecting to the internet.  I'm using free wifi and don't have any jacks, modems, or routers to plug into.

My wireless, and probably lots of other things like my built in webcam, doesn't work on Ubuntu 8.04.  I searched and found other people with problems, but their guides assume you have an alternate method connecting to the internet, and tend to leave people guessing still.  To my knowledge, I can't access a repository or use things like wget and apt-get without at least one way to connect to the internet, correct?  (I'm not a command line guy, so I don't know)

I logged back into Windows, and I googled for things like NDISwrapper, but I'm not sure which one to get, I found a handful of slightly different named results.  Windows Device manager tells me my built in wireless is named "Dell Wireless 1395 Mini-Card" and the driver I'm using is bcmwl6.sys.

I don't know what to do.  I've tried Ubuntu 3 times in as many years, usually after reading a motivating "Linux is Ready!"  article, and I always end up going back to Windows.  First to Google for help, then ask on IRC, then well... to stay until the next time I try Ubuntu.  Not a good trend.

---

### Post by Ayuthia on 2008-10-27
The bcmwl6.inf file does not work with ndiswrapper (not supported yet).  Here is a link that might help but it does require you to download a bcmwl5 file:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

However, the 8.04.1 version of Ubuntu should work with your card.  All you would need to do is go into System->Administration->Hardware Drivers and enable the Broadcom STA (wl) driver.  Unfortunately, the driver came out between 8.04 and 8.04.1.  You could also wait until Intrepid (8.10) is released.  It also has the driver that you need.

---

