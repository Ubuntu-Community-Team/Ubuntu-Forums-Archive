---
title: "Ubuntu 7.10 server goes &quot;offline&quot; by idling"
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by eb0lac0la on 2008-05-22
Hello everyone...

I welcome myself here with an open heart... Or something. And to the point.

There was a thread about my problem already known as: "Network Connection Disconnects After Computers Sit Idle"

[http://ubuntuforums.org/showthread.php?t=318301]("http://ubuntuforums.org/showthread.php?t=318301")

But unfortunately there wasn't any solution to be shown. I seem to have the same problem with Ubuntu 7.10 which is running as a server.

For some reason its annoying to see that server goes offline after a while and it doesnt response to any outcoming traffic. In older post ppl managed to get puters online by using e.g. dhclient command etc.

I made some forensics science and manage to find out that the puter thinks its running normally when trying ifconfig (all up and running as they should be) but the puter is unreachable from outer world. Nothing goes that way.

I can interact with the puter but still network is down in a way. BUT it seems to be that any traffic going from server to outside world somehow opens the network. E.g. ping -c 1 [www.whatever.com](www.whatever.com) opens the nic both ways and the server works perfectly. For a while.

The NIC is older PCI card based (might be realtek chip) and the puter is older 800 MHz duron or something. I already tried to put ACPI off by giving grub loader acpi=off" line but that doesn't help. Now I have a workaround by using cron.hourly and pinging some www-server so the NIC won't go "offline".

Haven't seen any powersaving options in BIOS which would affect PCI cards...

Sincererly
Eb0laC0la :popcorn:

---

