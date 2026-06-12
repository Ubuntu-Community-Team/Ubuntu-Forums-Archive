---
title: "3C905 TX works, then stops"
date: 2008-04-06
forum: Networking &amp; Wireless
---

### Post by Blaze Falconburger on 2008-04-06
This is weird this one..
When installing it hung around 40% when scanning the mirror, so I killed the wget and sh processes to continue.  I then un-rem'd the lines in sources.list to give me some sources.  However when I now go into add/remove it tells me the repositories are out of date, do I want to download/update - I chose yes, it gets to file 7 of 28 and stops.

What seems to happen is the nic just gives up when there is a bit of traffic. If I boot up, I get an ip addy from my dhcp server.  I can ping other addresses fine.  If I leave the ping running when trying to update,  or even browse a web page, ping will fail with:
ping: sendmsg: no buffer space available

I thought the 3c905tx would be a fairly tried and tested card by now, can anyone shed any light?

---

