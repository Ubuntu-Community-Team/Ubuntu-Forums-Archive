---
title: "Intel Wireless 7260 can't connect to ZyXEL VMG1312"
date: 2015-06-17
forum: Networking &amp; Wireless
---

### Post by Alistair_Grant on 2015-06-17
Hi,

I've got a Dell XPS13-9333 with Intel Wireless 7260 running Ubuntu 15.04
that mostly fails to connect to a ZyXEL VMG1312-8308 router - it used to
work over half the time, but something changed recently and it has only
succeeded twice in about 30 attempts.  The behaviour got worse
immediately after a weekly Ubuntu update, but the ISP occasionally
updates the firmware in the router (without any notification), so I
can't be sure what has changed.

The problem is more likely with Ubuntu than the router as all other
devices in the house have no problem connecting to the router, and my
laptop has had problems connecting to a couple of other WiFi stations,
although it is rare enough for me not to be sure where the problem is.

The symptoms are that the laptop appears to connect successfully, the
"connected" popup appears, ifconfig shows that an IP address has been
assigned, and the output of "route -n" is the same as when connected via
ethernet, however no communication is possible - even pinging the router
fails.

My attempts at searching for any clues have failed, and I'm not even
sure where to turn next.

I've attached wireless-info.tar.gz as suggested in the "Before
posting..." post.

Any suggestions appreciated...

Thanks,
Alistair

---

