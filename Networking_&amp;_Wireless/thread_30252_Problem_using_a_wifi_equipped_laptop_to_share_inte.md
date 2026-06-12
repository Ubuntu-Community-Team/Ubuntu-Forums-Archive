---
title: "Problem using a wifi equipped laptop to share internet"
date: 2005-04-27
forum: Networking &amp; Wireless
---

### Post by skimitar on 2005-04-27
Hi,

Networking is NOT my forte, so any assistance would be greatly appreciated!

I have a laptop connected by wireless to a router which is all working fine.
I want to use the laptop to connect to an XBox which I am using as a media centre so that it can connect to the net via the laptop. I don't want to run cable to the router and I'm not interested in connecting the XBox via wireless.

The network looks like:

eth0 on XBOX----- eth0 on laptop <> ath0 on laptop----eth0 on wifi router
(192.168.1.2)_____(192.168.1.1)_____(192.168.0.2)_____(192.168.0.1)


Now, I can get two way traffic between the router and the laptop and two way traffic between the XBox and the laptop, but can't seem to get traffic from the router to the XBox.

I have set the gateway for traffic going from the XBox to the router as 192.168.1.1 and the gateway for traffic going the other way as 192.168.0.2.

For the life of me, I cannot get this to work which means that I am doing something dumb. Am I expecting too much of the routing table? Should I be using iptables or a solution such as Firestarter? On the KISS principle, I'd like to avoid this but maybe it's the only way...

For the record, this is the only major frustration I have encountered in 3 months of using Ubuntu, which speaks wonders for the distribution!

Thanks
Jon.

---

