---
title: "Getting WiMAX card to work"
date: 2017-09-20
forum: Networking &amp; Wireless
---

### Post by Deep_Horizons on 2017-09-20
Hey all,

I'm trying to get a WiMAX card to work for testing purposes. The card I have is an Intel "Centrino Advanced-N + WiMAX 6250". I know Intel dropped support for the card, but the kernel still has the drivers. I think I'm close, but it's still not working.

I believe my main problem is the fact `rfkill` is reporting the card is soft blocked. When I try to unblock the card, `dmesg` reports

```

i2400m_usb 1-1.1:1.0: 'RF Control' (0x4602) command failed: -84 - invalid state (3)

```

I've tried multiple things, being near a WiMAX base station, disabling the wifi on the card, among others. I have compiled the wimax tools, network service, and other related components as well. When trying to start the wimaxd daemon, it just reports 

```

E: RFKILL: operation failed: -115
E: wimaxll_msg_write: generic netlink ack failed: -115

```

Here is my wireless-info report
[http://paste.ubuntu.com/25579564/](http://paste.ubuntu.com/25579564/)


Thanks!

---

