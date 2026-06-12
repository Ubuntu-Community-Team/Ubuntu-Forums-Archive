---
title: "cannot connect to my AP"
date: 2007-10-29
forum: Networking &amp; Wireless
---

### Post by astorm on 2007-10-29
Hi

I have just switched to ubuntu (gutsy gibbon) after my last attempt to upgrade SuSE went astray. I am having trouble getting the wireless card to connect to my AP. It works fine in my local Starbucks and works fine when I run windows, but the ubuntu/my AP combination does not work. Normally I am using WPA but I have also tried no encryption and WEP - nothing works. when using no encryption network manager seems to connect to the AP, but it says 'connected to (my network essid) (0%)' and no traffic gets through. The 0% seems to indicate to me that it hasn't connected properly. I also tried manually configuring network manager, which didn't work either.

It is a Broadcom 4306 wireless card, ubuntu used the bcm43xx driver and downloaded the firmware - that seems to be working since it picks up the APs in the vicinity and works in Starbucks. The AP is a Linksys WAP54g.

I tried connecting via the command line as described elsewhere in this forum but the dhclient step didn't work - it just isn't connecting so no traffic gets through to the DHCP server.

Does anyone out there have any suggestions?

Thanks
Andrew

---

### Post by astorm on 2007-10-29
Hi

In case someone out there is watching this thread - I have it working. It was as simple as changing the channel. Previously I had the channel set to 11, and now it is working after changing the channel to 1. This would appear to be a bug with the driver? I will have to investigate further.

Andrew

---

