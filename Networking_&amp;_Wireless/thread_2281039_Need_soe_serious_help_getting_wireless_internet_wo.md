---
title: "Need soe serious help getting wireless internet working"
date: 2015-06-04
forum: Networking &amp; Wireless
---

### Post by Paul_J._Wesselkamp on 2015-06-04
I need some serious help getting my server connected to the internet so I can start to learn. I am a new linux user, and just now getting back into the tech game after a 10 year hiatus.
The situation I am currently in is I am trying to connect my server to the internet with a wireless usb device (a temporary deal until I get some better service going)
I was able to get the device configured and (i think) working properly, but now I am running into the issue of actually getting  connected to my wireless hotspot through the command line.
My server is running Ubuntu server 15.04.
My other computer (my laptop) is running Ubuntu 15.04 which I am currently able to connect to the internet with using the same hotspot.
any help in resolving this matter would be greatly appreciated.

Thank you for your time, if any further information is needed please let me know.


Respectfully,
Paul J. Wesselkamper

---

### Post by Bucky Ball on 2015-06-04
*Thread moved to **Networking & Wireless**.*

Welcome. For a start, you could try comparing your network configuration on the working machine with the one on the not working machine. Secondly, plug in the USB device and issue these commands, one after the other, with enter after each:

```
sudo lshw -C network
lsusb
```

Post the output back here between [code] tags (see the last link in my signature for how).

Just a note: using an interim release for a server is not ideal. Interim releases have nine months support, not really desirable for a server which is generally on most of the time if not 24/7 and sometimes for a year or two. Best to stick with LTS (long-term support) releases for server installs. 15.04 will only get you through to next January. You don't want to be upgrading a server every nine months (or every six if you install with each new release). 

Also, LTS releases can be upgraded directly to the next LTS release, i.e. 14.04 LTS> 16.04 LTS, leapfrogging the interim releases in between (14.04 LTS>14.10> 15.04> 15.10> 16.04 LTS). To get to 16.04 LTS via net upgrades and not full install would require upgrading path 15.04> 15.10> 16.04 LTS. Again, not ideal.

---

