---
title: "Need help with Linksys WUSB300N DESPERATE"
date: 2007-12-25
forum: Networking &amp; Wireless
---

### Post by martinsulistio on 2007-12-25
Hi guys, I need a serious help. I finally was able to configure how to get wireless internet using Linksys WUSB300N by using ndiswrapper and Linksys driver. Now the problem:

My 2 roommates and my laptop uses XP, and they complain that their wireless connection suddenly drops dead when I turn on my Ubuntu wireless. Can any1 help me? please? before i get slaughtered. 1 of my roommate is an adult and he needs the internet for work.

---

### Post by Sam Liu on 2008-04-27
I know this thread is really old but to point to a quick installation guide I wrote:

[http://www.sammyliu.com/2008/04/27/guide-linksys-wusb300n-linux-installation/](http://www.sammyliu.com/2008/04/27/guide-linksys-wusb300n-linux-installation/)

---

### Post by itsfullofstars on 2008-05-15
**CAUSE**
 
Two manufacturers NICs experienced the same issues -- Linksys, and D-Link. I didn't try any others. Both cause disconnects (manufacturer's wifi manager managing the connection) or system hangs/crashes (XP managing the connection through WZC). The failure seems to only occur when a large number of TCP connections are being managed by the system, as well as a high rate of connection attempts to different hosts.
 
This sort of environment is exactly what happens in P2P applications. Most common are bittorrent clients, and on-line gaming.
 
I could blow out the WUSB300N within a minute or two by firing up Azureus (bitorrent), with a lot of seeding torrents (60).
 
Problem #1 is the Linksys WUSB300N implementation. It's flaky hardware. I had two, and both behaved exactly the same on my WinXP machine with the latest driver available from Linksys (v1.0.1.7, IIRC).
 
The DWA-142 Wireless N USB adapter from D-Link performed much better regardless of the driver. The Marvell driver installed from the CD was version 1.0.1.2; Both NICs worked with this driver, and average throughput was about 25% faster than with v1.0.1.7 shipped with the WUSB300N. As noted, WUSB300N died within a minute or two of cranking up the connections and connrate. D-Link ran for as long as 2 hours without a problem, then same failure mode.
 
This was true with all three Marvell driver versions I had: 1.0.1.7 from Linksys, 1.0.1.2 from D-Link, and one other, 1.0.5.5 that came from a Microsoft optional update. Again, both mfg adapters worked with all these drivers, all failed in the same way, D-Link was massively more stable (and a little faster) than Linksys.
 
**THE SOLUTION**
 
Marvell apparently has fixed these problems in their latest driver. It is version 1.0.6.4. The only place I could find it was on the D-Link website, in the support section, available as a beta download for the DWA-142. Unfortunately, this is a package (v1.2) that includes all the D-Link custom monitor apps and other crapola, and the driver files (inf, sys, cat) are buried in a cab file, so it's not easy to install just the driver. You have to install the package. However, once installed, I was configured and running in no time, and started testing.
 
Solid as a rock.
Fast.

---

