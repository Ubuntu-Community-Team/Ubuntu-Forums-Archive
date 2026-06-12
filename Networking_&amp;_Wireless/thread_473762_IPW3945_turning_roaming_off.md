---
title: "IPW3945 turning roaming off"
date: 2007-06-14
forum: Networking &amp; Wireless
---

### Post by mjuang on 2007-06-14
I'm running Edgy (6.10), kernel 2.6.17-10 on my IBM T60 Thinkpad, which uses the Intel Pro/Wireless 3945ABG network adapter, using ipw3945-1.2.0.  My wireless configuration works.

However, I'd like to be able to turn roaming off--after I've connected to an AP, I don't want the driver automatically reassociating with another AP (with the same SSID) in range when the signal strength of the original AP drops.  Or rather, I don't want it automatically switching APs ever (for that matter, stopping active scanning would be nice too).  How can this be done?

I see the device level sysfys helper file: /sys/bus/pci/drivers/ipw3945/0000:03:00.0/roam.  There was a 1 there that I changed to a 0, but that didn't seem to address the issue.

Any kind of solution would be acceptable.  I was thinking of a few ways to indirectly stop roaming:
1.  fix the channel to that that the AP is on (I only don't want roaming within a relatively small coverage area of 5-6 APs)...except once the signal level goes too low, the driver seems to automatically change channels to associate with a nearby AP
2.  turn the sensitivity down such that even while I'm out of range, I'll still be counted as associated to the out-of-range AP...but sens isn't supported for ipw3945?

What does the scan_age parameter do?  As far as I can tell (not much), it just keeps a longer list for "iwlist scan", showing those APs whose last beacons were under the scan_age value time ago.

In case that didn't make sense, here's my current situation so you can see the actual issue at hand:  I'm collecting wireless network measurements at school as part of a research project.  At this stage, I'm concerned with different performance metrics as they pertain to distance from an AP (and thus link quality).  Thus, collecting active measurements from one AP is dicey when the driver is automatically associating to other APs as I move away.

---

