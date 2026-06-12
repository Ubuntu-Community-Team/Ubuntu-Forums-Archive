---
title: "Connected to internet, skype working, browsers reporting DNS not found"
date: 2017-03-30
forum: Networking &amp; Wireless
---

### Post by markjwgraham on 2017-03-30
Hi guys

I've got an HP Stream 11, and the in-built wifi has always been dodgy to the point of disconnecting every 10 seconds. I've been trying to fix it for months with various driver changes etc, but to no avail.

Finally ordered an Edimax wifi adapter to at least get a constant wifi connection to test the issue, which was MUCH better... for about an hour. Due to updates and various tests on the in-built card, I've now lost the ability to even load websites, even when the connection is good and I can see Skype is working. The fact I now can't even get the adapter to get my computer to work flawlessly online is REEEEEALLY pissing me off.

Chrome and Firefox both report EVERY website's DNS address cannot be found, which indicates DNS issues. I've tried setting global DNS servers to 8.8.8.8 and 8.8.4.4 as many threads suggest = doesn't fix it.

I've tried pinging 8.8.8.8, and I seem to get some results, but it's not clear to me what I'm looking for. I am genuinely at my wits end here and really can't think straight with the degree this issue has been ongoing.


 Can anyone help me sort this out? 

Mark

---

### Post by markjwgraham on 2017-03-31
Solved by a terminal restart of network-manager. For some reason after some updates the new external card and internal card were conflicting with each other in network-manager. Ugh. Glad it's sorted but what a pain.

---

