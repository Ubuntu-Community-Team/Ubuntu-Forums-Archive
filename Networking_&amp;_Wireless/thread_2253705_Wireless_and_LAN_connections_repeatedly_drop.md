---
title: "Wireless and LAN connections repeatedly drop"
date: 2014-11-21
forum: Networking &amp; Wireless
---

### Post by pelle989 on 2014-11-21
I'm having issues with 11 cloned units that I've built 1 identical image of Ubuntu 14.04 systems.
The issue began from a wireless perspective, mainly drops and complete disconnects...requiring a reboot to fix the connection. However, due to such a high degree of wireless issues, we've tried using the ethernet connection, which continues to have drops on 3 of the units.
We've tried an internal rtl8723ae based driver, we've tried a Panda Mid-Range USB adapter rt2800usb, and tried a ThinkPenguin Dual Band [TPE-NUSBDB]("https://www.thinkpenguin.com/gnu-linux/penguin-wireless-n-dual-band-usb-adapter-gnu-linux-tpe-nusbdb") running on ath9k_htc.

with iwconfig:
rtl8723ae would report high Invalid Misc. 3,000+ (8hrs)
rt2800usb would report high TX excessive retries 400+ and Invalid Misc 1000+ (8hrs)
ath9k_htc has been the best solution for packet drops with TX excessive at 4 and invalid Misc at 600+ (8hr)
Plus the Think Penguin Dual band is running at 5GHz

So the issue of too much interference is out the window.

I've attempted the following fixes one by one without improvement:
Kernel 3.16.7
Kernel 3.14.24
iw reg set US
Disabled IPv6
Wrote a script to rfkill wifi if unable to ping the DNS server
Disabled the internal wireless cards bluetooth

We use TeamViewer to remote into these units, so I can see the 3 units coming back online over and over...If I'm in one, it doesn't stay connected for very long. I dont know if this is equipment not getting along with the Cisco router they're using or if I am experiencing a Network Manager bug?

I am out of ideas to continue to try, and was hoping to provide a log file of types to someone so that I can either identify the Router as the issue or can apply a fix.

Thank you,
Joe

---

