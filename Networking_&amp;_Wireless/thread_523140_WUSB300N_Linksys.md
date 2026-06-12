---
title: "WUSB300N Linksys"
date: 2007-08-11
forum: Networking &amp; Wireless
---

### Post by airjer on 2007-08-11
Can anyone point me in the right direction of getting this adapter to work?


edit:: Sorry, searched after lol and I'm reviewing [http://ubuntuforums.org/showthread.php?p=2838963](http://ubuntuforums.org/showthread.php?p=2838963)

If anybody can provide any extra help, it would be appreciated :].

---

### Post by itsfullofstars on 2008-05-15
This was written on the Linksys forum:

**PROBLEM**

The WUSB300N frequently drops connections, making users very mad.

The WUSB300N uses a chipset called TOPDOG made by Marvell. This same chipset is in every 802.11n draft adapter implementation out there from what I can tell -- Linksys, Belkin, D-Link, etc. There might be a competing chipset, but I stopped investigating when I nailed down the source of the problems.

All these implementations use a driver made by Marvell, the manufacturer of the TOPDOG chipset. There are different versions out there, but apparently none that are OEM-specific.

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

No disconnects or crashes.

---

### Post by mastermindg on 2008-06-07
The driver on the CD works for 32-bit Hardy.

---

