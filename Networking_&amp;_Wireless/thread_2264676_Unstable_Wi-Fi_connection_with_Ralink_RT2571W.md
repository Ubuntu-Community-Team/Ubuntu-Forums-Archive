---
title: "Unstable Wi-Fi connection with Ralink RT2571W"
date: 2015-02-09
forum: Networking &amp; Wireless
---

### Post by glacoon on 2015-02-09
Hi all,

I'm on Kubuntu 14.04 and since I changed my ISP modem-routeur, I have a quite unstable Wi-Fi connection with my Wi-Fi USB adapter D-Link DWA-110. Note: on Windows, the Wi-Fi is very stable though, so the problem doesn't strictly come from the equipment or the modem.

Here are the details of my equipment:

```
$ lsusb 
Bus 002 Device 009: ID 07d1:3c07 D-Link System DWA-110 Wireless G Adapter(rev.A1) [Ralink RT2571W]

```

The Wi-Fi connection is generally working fine, except when used intensively (it especially crashes after 1-2 min of Skype). Once it has crashed, I have to unplug/replug it.

I always find the same messages in the kernel logs, but I don't know if they are strictly related to the Wi-Fi crash though:

```
$ dmesg
[20820.500029] ieee80211 phy2: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[20820.788022] ieee80211 phy2: rt2x00usb_watchdog_tx_dma: Warning - TX queue 2 DMA timed out, invoke forced forced reset
[20870.832268] ieee80211 phy2: rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110

```

I've read in other thread the power management could be a possible failure reason, but it crashes even if I disable the power management:
```

sudo iwconfig wlan0 power off

```

I've checked that the binary driver included in Ubuntu is the last made by Mediatek, so that I don't have any ideas.

Do you have some ideas?

Thanks a lot!

---

