---
title: "TKIP: replay detected"
date: 2007-05-01
forum: Networking &amp; Wireless
---

### Post by KhoaTon on 2007-05-01
I'm running Ubuntu 7.04 on a Dell Inspiron 8100 with a Linksys Wireless-G WPC54GS WiFi card.

This wireless card didn't work out of the box, so I followed this thread:
[http://ubuntuforums.org/showthread.php?t=405219&page=2]("http://ubuntuforums.org/showthread.php?t=405219&page=2")
I am now on the net, but...

The Connection Manager shows 11Mbps in Unbuntu, whereas Windows XP on the same system (dual boot) operates at 54Mbps.

I'm also getting these messages in /var/log/messages:
[  101.160000] TKIP: replay detected: STA=00:0f:66:52:aa:58 previous TSC 010200000000 received TSC 000000000127
[  102.184000] TKIP: replay detected: STA=00:0f:66:52:aa:58 previous TSC 010200000000 received TSC 000000000128
[  103.208000] TKIP: replay detected: STA=00:0f:66:52:aa:58 previous TSC 010200000000 received TSC 00000000012b

The main question is that does the TKIP: replay detected message mean I'm seeing a cryptographic replay hacking attempt to get onto my wireless LAN, or is it something normal?

Secondly, any hint as to why I'm only showing 11Mbps instead of 54Mbps?

Thanks!

---

### Post by spd106 on 2007-05-02
Replays happen when a old packet has been detected, it's usually just discarded and the connection continues. Due to the multiple paths a signal can take, reflections etc it's not too uncommon to see them occasionally. You only need to be concerned if you see hundreds per minute and even then TKIP has replay protection.

The bcm43xx driver is currently constrained to a default maximum data rate of 11Mbps , though work on higher rates is progressing. In real terms you won't see much difference in speed unless you are doing large file transfers and even then interference is likely to be a bigger disrupting factor. If you want to see the magical 54Mbps then you can choose to use ndiswrapper instead. A quick search on this forum will turn up 10 or more guides.

---

### Post by KhoaTon on 2007-05-02
Thanks so much for the very informative response!

---

