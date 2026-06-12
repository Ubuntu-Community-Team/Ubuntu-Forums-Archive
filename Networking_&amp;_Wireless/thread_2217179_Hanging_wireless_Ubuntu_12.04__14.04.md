---
title: "Hanging wireless Ubuntu 12.04 / 14.04"
date: 2014-04-15
forum: Networking &amp; Wireless
---

### Post by stormyk88 on 2014-04-15
So, I recently upgraded to 14.04 and have been getting quite a few updates, I'm guessing since what I installed was pre official release. 

Basically what I have is a Toshiba Satellite with and Atheros Chipset, and a DLink USB wireless dongle. With 12.04, I had to install the drivers for the USB adapter as listed [http://bernaerts.dyndns.org/linux/74-ubuntu/229-ubuntu-precise-dlink-dwa160-revb2]("http://bernaerts.dyndns.org/linux/74-ubuntu/229-ubuntu-precise-dlink-dwa160-revb2") here, with the same issue. I have checked LQ, linuxlaptops, and here, and most seem to be having problems with no wireless, not lagging/hanging. Since installing 14.04, both seem to work, but not reliably.

My wireless hangs using the USB adapter as well as onboard wireless. Most of the time, I can 'unstick' it (I know, highly technical term), by disconnecting and reconnecting to the AP, and sometimes have to refresh the webpage as well. Having the same issue connecting to both my router and a repeater which is setup as an AP, wired to router. Ran something from the command line (nn something) to show signal strength, and both show decent to excellent signals, anywhere from -70 to -40 as verified with my phone. 

specs and details (ask for more if needed)

```
lspci
...
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
...
```

```
lsusb
...
Bus 002 Device 005: ID 2001:3c1a D-Link Corp. DWA-160 802.11abgn Xtreme N Dual Band Adapter(rev.B2) [Ralink RT5572]
...
```

Both seem to be recognized ...

My best guess is that I need to find updated drivers if available, but any help would be appreciated (where to start looking?).

As always, thanks for the help.

---

