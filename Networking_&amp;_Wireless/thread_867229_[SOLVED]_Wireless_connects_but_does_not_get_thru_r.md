---
title: "[SOLVED] Wireless connects but does not get thru router"
date: 2008-07-22
forum: Networking &amp; Wireless
---

### Post by rtrdom on 2008-07-22
Will two MAC addresses (Netgear access point and Linksys booster)within 50 ft. straight line of each other, with no barriers on same network, prevent wireless in Ubuntu from
sending traffic through, even when wireless does connect to network?
.

---

### Post by rtrdom on 2008-08-07
FOUND IT! After trying many many suggestions, resetting nearly every setting in the wireless portion of Ubuntu. The solution was simple. For any
one else with the problem...Do you have two routers, access points, booster
or some combination of them?  If so, the problem is probably that they are
interfering one with the other and scrambling the data packets before they
get through the (pick one of the above). The solution to my problem was
solved by unpluging a booster which was within 50 feet of an access point.
When I cut power to the booster, all computers could access the internet via the access point only. There was no physical connection between the two, just wireless connection. At first I thought it was just the Ubuntu
computer's problem because a Windoze computer did get thru most of the time
and the Ubuntu sometimes. After securing power to the access point, again,
ALL computers can access the internet all the time. All this on an
open (unsecured) public network. Hope everyone with this problem can solve
it.:)

---

