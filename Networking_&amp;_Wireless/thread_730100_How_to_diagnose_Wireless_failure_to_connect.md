---
title: "How to diagnose Wireless failure to connect"
date: 2008-03-20
forum: Networking &amp; Wireless
---

### Post by windyweather on 2008-03-20
Just got a ZyXEL G-202 adapter for my 7.10 system running on Via G7 processor.

I am using a WPA secure wireless network from a Linksys WR54G adapter with a 64 character hex key.

I carried the WPA key on a USB key to the system and copy / pasted it into the wirelss config.
Tried both WPA Personal and WPA2 Personal settings. No Joy.
Set for DHCP.
This system was on wired network and was fine. DNS addresses were set manually.

System will not connect. Not even to the router page at 192.168.1.1

Here's some of the system log. These messages come out every few seconds.

Can someone help with how to diagnose this?


Update: This looks like good news. [Indicates that 7.10 supports this adapter OOTB.]("http://yoten.blogspot.com/2007/07/zyxel-zyair-g-202-in-linux-step-by-step.html")

Update: I've tried [WICD and no change]("http://wicd.sourceforge.net/"). Can't tell from WICD about the signal level, apparently. That would be nice. I'll check on their site.

Thanks,
- Windy

 ```
Mar 20 11:56:46 blue-diamond kernel: [323476.904000] SoftMAC: Open Authentication completed with 00:0f:66:cb:c2:65
Mar 20 11:56:51 blue-diamond kernel: [323481.424000] SoftMAC: Open Authentication completed with 00:0f:66:cb:c2:65
Mar 20 11:56:55 blue-diamond kernel: [323485.952000] SoftMAC: Open Authentication completed with 00:0f:66:cb:c2:65
Mar 20 11:57:00 blue-diamond kernel: [323490.456000] SoftMAC: Open Authentication completed with 00:0f:66:cb:c2:65
Mar 20 11:57:04 blue-diamond kernel: [323494.972000] SoftMAC: Open Authentication completed with 00:0f:66:cb:c2:65
Mar 20 11:57:09 blue-diamond kernel: [323499.484000] SoftMAC: Open Authentication completed with 00:0f:66:cb:c2:65
Mar 20 11:57:13 blue-diamond kernel: [323503.996000] SoftMAC: Open Authentication completed with 00:0f:66:cb:c2:65
Mar 20 11:57:18 blue-diamond kernel: [323508.512000] SoftMAC: Open Authentication completed with 00:0f:66:cb:c2:65
Mar 20 11:57:22 blue-diamond kernel: [323513.024000] SoftMAC: Open Authentication completed with 00:0f:66:cb:c2:65
Mar 20 11:57:27 blue-diamond kernel: [323517.540000] SoftMAC: Open Authentication completed with 00:0f:66:cb:c2:65
Mar 20 11:57:32 blue-diamond kernel: [323522.048000] SoftMAC: Open Authentication completed with 00:0f:66:cb:c2:65
Mar 20 11:57:36 blue-diamond kernel: [323526.564000] SoftMAC: Open Authentication completed with 00:0f:66:cb:c2:65
Mar 20 11:57:41 blue-diamond kernel: [323531.076000] SoftMAC: Open Authentication completed with 00:0f:66:cb:c2:65
Mar 20 11:57:45 blue-diamond kernel: [323535.592000] SoftMAC: Open Authentication completed with 00:0f:66:cb:c2:65
Mar 20 11:57:50 blue-diamond kernel: [323540.096000] SoftMAC: Open Authentication completed with 00:0f:66:cb:c2:65
Mar 20 11:57:54 blue-diamond kernel: [323544.612000] SoftMAC: Open Authentication completed with 00:0f:66:cb:c2:65
Mar 20 11:57:59 blue-diamond kernel: [323549.132000] SoftMAC: Open Authentication completed with 00:0f:66:cb:c2:65

```

---

### Post by windyweather on 2008-03-20
Problem solved... Looks like a bug handling the key, but probably not a bug in Wicd.

There are several Windoze, a PS3 and an Ubuntu system on the wireless network. The WPA key was a very random 64 character key [only hex digits] and windoze and PS3 [with great difficulty in entering the key] were all happy on the network.

Ubuntu would not connect and after some fiddling around, it seems that a 60 character string would work just fine with Ubuntu.

But the PS3 would not work with that.

After some investigation, it seems the PS3 will work with a 16 character key [32 apparently failed].

So, all is working. Not sure where the bug is in Ubuntu that prevents a 64 character key when all other systems accept it.

I'll look for a place to report the problem.

- Windy

---

