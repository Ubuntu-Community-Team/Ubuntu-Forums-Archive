---
title: "how to set up ubuntu 10.04 to configure wireless"
date: 2014-02-16
forum: Networking &amp; Wireless
---

### Post by shad2 on 2014-02-16
if the college server's lease period runs out,all ips are changed except the DNS and i can't get internet.
what can i do to set up ubuntu 10.04 to automatically detect wireless networks(this it does)  and also set my ip-addresses dynamically without having to go to the college technician every after 2 days.

---

### Post by varunendra on 2014-02-16
> **shad2 said:**
> if the college server's lease period runs out,all ips are changed except the DNS and i can't get internet.
what can i do to set up ubuntu 10.04 to automatically detect wireless networks(this it does)  and also set my ip-addresses dynamically without having to go to the college technician every after 2 days.

Assuming you are talking about Ubuntu Desktop version, the 10.04 is no more supported, not that it makes a difference in how you configure your wireless.

Secondly, if the college server is configured to assign IPs via DHCP, your computer should automatically pick up a new, valid configuration unless you have set it up to use manual network configuration. Using DHCP (automatically get IP and related settings) is the default setting in Network Manager.

Thirdly, IF you are using manual network configuration for any reason, you'll end up visiting your college technician anyway.

And lastly, IF you are using "Automatic (DHCP)" method in Network Manager and are still unable to get the new lease automatically, then the problem may be with the server's capabilities, or your driver performance. In the former case, you can't do much about it. In the latter case, upgrade to the latest release (13.10) or latest LTS release (12.04) to get better drivers.

Further suggestions depend upon how much detailed information you can provide to us about your system and network setup.

---

