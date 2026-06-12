---
title: "Strange network problem"
date: 2008-10-14
forum: Networking &amp; Wireless
---

### Post by Simon Ewins on 2008-10-14
I have an XP partition, OpenSUSE, DreamLinux, Kubuntu and Ubuntu Studio partitions.

The Studio is the newest install and is the only one with this problem.

After a seemingly random period of time between about 10 minutes and 90 minutes my internet access (actually access to my router) just stops.

I have a wired connection.

ifconfig shows that eth0 is still as it was when all was working but if I try to connect to my router it tells me that it isn't there.

If I ifdown eth0 it comes down but if I then ifup eth0 it shows the right mac for listening and sending then it shows a fallback to loop and then it just does endless DHCPDISCOVER with varying intervals.

Can anyone give me a hint as to what might be going on?

I am sure of the harware since all other distros and XP have no problems at all. Also, my wife's laptop on a wireless connect to the router is fine.

This is really a shame because of all the dozens of distros I have installed and used Ubuntu Studio seems almost perfect for me. I would love to be able to make it my main OS but this connection problem is frustrating that. :x

If a screenshot or configs is needed let me know.

Thanks in advance,
Simon

---

### Post by Simon Ewins on 2008-10-16
Fixed it.

Installed KDE, problems disappeared. Third distro this has happened to me... GNOME default has problems of varying sorts, install KDE and problems go away. GNOME seems to be very flakey.

Cheers

---

