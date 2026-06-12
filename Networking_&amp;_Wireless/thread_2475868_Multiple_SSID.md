---
title: "Multiple SSID"
date: 2022-06-10
forum: Networking &amp; Wireless
---

### Post by Geoff_Lane on 2022-06-10
Appreciate, depending on the device, if any secondary SSIDs are enabled then isolation can be set but are there any performance advantages to a secondary SSID?

On my router I can put a secondary SSID into a vlan and I do use this to separate IoT devices from my main computer but as secondary SSIDs all have to be (on mine anyway) on the same WiFi channel is there any performance advantage in being on a less busy SSID albeit on the same channel and router?

Probably no straight forward answer with technology as it is now with smart electronic devices etc

Geoff

---

### Post by TheFu on 2022-06-10
SSIDs don't matter, what matters is channel overlaps and local interference.

2.4 Ghz channels in most of the world only have 3 of the 11 channels that don't overlap.  Those are ch1, 6, 11.  Picking any other channels will overlap.  In really busy wifi areas, there isn't any choice, but if you live in a detached home surrounded by an acre of land, then sticking with just those 3 channels in the 2.4Ghz range is the best choice.  5.8Ghz have different channels, different overlap, and different strengths.  5.8Ghz doesn't go through many walls. Nether channels go through concrete well.

Each channel has a maximum throughput capacity which isn't actually represented correctly by the "connection speed" shown in any GUI.  Local interference is constantly changing. Constantly, from msec to msec.  Traffic on the same channel can never exceed the total throughput available at that instant.  There is overhead in having multiple SSIDs, but not really on the RF channel, since the SSID is just a field inside the broadcast packets.  The overhead is in the router processing.

VLANs are just tags which can be ignored by any device on the wire.  If you want real security, use separate physical networks. If you are happy with a logical separation only, then vlans are fine, but the total bandwidth is still the total bandwidth.  There's no way to get 2Gbps on a wire that supports 1Gbps connections.  There are 2.5Gbps, 5Gbps, 10Gbps copper ethernet cables that need to be paired with network adapters that support those speeds.  If your router supports 2.5Gbps and you connect 2 systems, each with 1Gbps to it, then both of those systems can access up to nearly 1Gbps for traffic to/from the router.  Communications between the 2 computers will NOT exceed 1Gbps ... which in the real world is usually 920-940 Mbps.

If you want to know the real bandwidth for a connection, use **iperf3** between two systems to test it.

Older wifi standards were less good at multiplexing multiple devices, so the more devices that were 'connected' to the wifi access point, the slower the total throughput possible.  AC made large gains to improve that, but there is always overhead in having active connections.  Test the throughput with 5, 4, 3, 2, 1 wifi devices connected to get an idea.  Under wifi-G or wifi-N, you'd definitely see a difference.  Under wifi-AC, perhaps not.

If you are interested in this stuff, there are youtube videos by experts who explain the differences in wifi-6, wifi-5 (ac), wifi-N, wifi-G and earlier versions.  There was a presentation about this at SELF a few years ago by Zack.  They have a youtube channel, so that video should be there.

---

