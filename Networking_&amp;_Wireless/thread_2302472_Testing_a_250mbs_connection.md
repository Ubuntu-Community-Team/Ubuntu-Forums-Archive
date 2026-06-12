---
title: "Testing a 250mb/s connection"
date: 2015-11-10
forum: Networking &amp; Wireless
---

### Post by faroutliving on 2015-11-10
I use a couple linux servers in a  remote location, and recently the internet connection to the facility  was reworked to now use a microwave connection and a 250mb/s fiber  connection upstream.

However, when moving a large file from there I see the top speed is  always much less than that. No matter what method I used, 110mb/s is the  top speed I've obtained. I've copied multiple files at the same time,  and can get a combined 220mb/s consistently. So would I expect a per  connection throttle somewhere? Ubuntu, the fiber coming in or ?? If the  ISP, then I suppose I am stuck with it, but if Ubuntu is the culprit can  that be changed?

Thanks,
Deron

---

### Post by TheFu on 2015-11-10
Not that I'm aware. 

First, "mb/s" isn't perfectly clear. Is  this  MB/s or Mb/s?
Second, what NICs are used?
What protocol is used to perform the copy?
Why not use iperf?
Is there a VPN or/and  other encryption that could impact performance?
How fast are the disk subsystems? Use the same units of measure to keep this easy. For example, most cheap SATA disks can't do 100MB/s writes on a normal server because there are always other processes.

So, when testing this, test each part for limitations.  Check the disk reads, LAN, disk writes first. Don't touch the WAN.  After you've validated the equipment on both sides, only then test all the way from point-A to point-B.

---

