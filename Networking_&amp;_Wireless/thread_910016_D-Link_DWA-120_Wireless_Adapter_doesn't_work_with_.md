---
title: "D-Link DWA-120 Wireless Adapter doesn't work with Ubuntu."
date: 2008-09-04
forum: Networking &amp; Wireless
---

### Post by thinhhoangdinh95 on 2008-09-04
Hello and pleasant to meet you. I'm using Ubuntu 8.04 for my laptop. Recently, my company has just opened Wifi for all employees .Unfortunately, my laptop doesn't have a Wifi card. So, I purchased a D-Link DWA-120 USB Wireless Adapter but it doesn't work with Ubuntu. Please help me to figure this out. Thank you!

---

### Post by Gordone on 2008-09-30
Hi,

sorry I've been meaning to get back to you for a while. Unfortunately this device doesn't work out of the box, unlike a lot of things do in Ubuntu, but with a bit work you'll have it up and running in no time.

The issue is that there is no Open Source driver for this device, so you have to use the proprietary Windows one. You can do this using a nifty system program called ndiswrapper. This is a comprehensive link as how to set it up: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

A caveat however, for everyone running 64 bit Ubuntu - as it stands you can't get this to work. The manufacturer only provides 64bit drivers for Vista, which don't seem to work with ndiswrapper. Very sad.

Cheers,
Gordon

---

