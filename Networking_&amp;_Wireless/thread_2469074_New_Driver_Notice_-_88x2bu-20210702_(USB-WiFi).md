---
title: "New Driver Notice - 88x2bu-20210702 (USB-WiFi)"
date: 2021-11-18
forum: Networking &amp; Wireless
---

### Post by morrownr on 2021-11-18
News: A new version of the Realtek driver for the 8812bu and 8822bu chipsets for USB WiFi adapters is now available. Testing has shown it to be a greatly improved driver over earlier versions of the driver. Managed (client)  mode has been performing good with previous versions of this driver but AP mode is now testing good as well and a real shocker is the results I am seeing from monitor mode. Monitor mode is turned on but you won't see it listed yet as I continue to test. Monitor mode supports various functions for those involved in security analysis and more.

It also appears that Concurrent mode is working. I'll try to get it documented soon. An example of Concurrent mode would be if you have an adapter connected to your desktop in client mode but also want the adapter to work as an AP at the same time. Most folks would call that a repeater. Interface combinations capability has been with us via the in-kernel drivers for a long time and Realtek seems to have been working on this for a few years but it seems there has been progress. Here is the link to the latest new driver:


[https://github.com/morrownr/88x2bu-20210702](https://github.com/morrownr/88x2bu-20210702)

There are also two other very recent, but already posted, updates for the 8812au chipset and the 8811au/8821au chipsets:

[https://github.com/morrownr/8812au-20210629](https://github.com/morrownr/8812au-20210629)
[https://github.com/morrownr/8821au-20210708](https://github.com/morrownr/8821au-20210708)




Reminder: For those considering a new USB WiFi adapter. The following site provides information and links to numerous USB WiFi adapters, N150 - AC1300, that use in-kernel drivers (plug and play): (Note: I do not receive any compensation for maintaining the site. It is simply a hobby.)


[https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi)




Anyone that has some spare time and would like to help maintain the sites or provide specific testing, please come on over and contact me via Issues or Discussions.

Regards

---

