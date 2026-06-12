---
title: "Wi-Fi Dongle"
date: 2019-12-30
forum: Networking &amp; Wireless
---

### Post by ray42 on 2019-12-30
What is an easy to set up Wi-Fi Dongle for a Desktop PC that plays well with Ubuntu?

25 feet coverage needed through single brick wall or 2 x wooden doors that leads to room with router.

---

### Post by slickymaster on 2019-12-30
*Thread moved to **Networking & Wireless**.*

---

### Post by chili555 on 2019-12-30
Please check here: [https://ubuntuforums.org/showthread.php?t=2397914](https://ubuntuforums.org/showthread.php?t=2397914)

---

### Post by ray42 on 2020-01-01
I see.

So the title is:

[h=1]"TP-Link Nano USB Wifi Dongle 150Mbps High Gain Wireless Network Adapter for PC Desktop and Laptops. Supports Win10/8.1/8/7/XP, Linux 2.6.18~4.4.3, Mac OS 10.9~10.13 (TL-WN722N)"[/h]
So dispute its says up Linux 4.4.3 it works with later versions.

I perhaps should have an internal card pci card such as:


[h=1]"TP-Link TL-WN881ND 300 Mbps Wireless N PCI Express Adapter"[/h]
Although TP Link when asked in an email say that one is also not supported past 4.1

I also use a Medion Akoya Laptop winch is now getting old, but works fine with Linux. Is that because it's built in and updates with Linux are for the chip set?

i.e. CPU: Intel i3-2350M (4) @ 2.300GHz & Intel Sandybridge Mobile

---

### Post by him610 on 2020-01-02
This device, TP-Link WN823N RTL8192EU, works with release 18.10
This device, EdiMax EW-7811Un, works with release 18.04+ (also works with Raspbian 9.1 Stretch)

---

### Post by ray42 on 2020-01-03
How old is your EdiMax EW-7811Un dongle, sometimes they change the chip set and then it doesn't work. The RS website makes no mention of it working with Linux

[http://https://uk.rs-online.com/web/p/products/7603621/?grossPrice=Y&cm_mmc=UK-PPC-DS3A-_-google-_-3_UK_EN_Wireless+Adapters+%26+WiFi+dongles_Edimax_Exact-_-Edimax+-+Wireless+Adapters+%26+WiFi+dongles+-+7603621-_-edimax+ew+7811un&matchtype=e&kwd-22872133906&s_kwcid=AL!7457!3!290240302684!e!!g!!edimax%20ew%207811un&gclid=EAIaIQobChMItJrQ7s7n5gIVyrTtCh2X4wC6EAAYASAAEgIUSPD_BwE&gclsrc=aw.ds](http://https://uk.rs-online.com/web/p/products/7603621/?grossPrice=Y&cm_mmc=UK-PPC-DS3A-_-google-_-3_UK_EN_Wireless+Adapters+%26+WiFi+dongles_Edimax_Exact-_-Edimax+-+Wireless+Adapters+%26+WiFi+dongles+-+7603621-_-edimax+ew+7811un&matchtype=e&kwd-22872133906&s_kwcid=AL!7457!3!290240302684!e!!g!!edimax%20ew%207811un&gclid=EAIaIQobChMItJrQ7s7n5gIVyrTtCh2X4wC6EAAYASAAEgIUSPD_BwE&gclsrc=aw.ds)

The TP-Link WN823N RTL8192EU on Amazon website says it OK upto kernel Linux 2.6.24~4.9.60:

[https://www.amazon.co.uk/TP-Link-TL-WN823N-Wireless-Supports-10-9-10-13/dp/B0088TKTY2/ref=sr_1_fkmr0_1?keywords=TP-Link+WN823N+RTL8192EU&qid=1578061276&sr=8-1-fkmr0](https://www.amazon.co.uk/TP-Link-TL-WN823N-Wireless-Supports-10-9-10-13/dp/B0088TKTY2/ref=sr_1_fkmr0_1?keywords=TP-Link+WN823N+RTL8192EU&qid=1578061276&sr=8-1-fkmr0)

---

### Post by captainquack2 on 2020-06-30
is there anything that works with 5+ kernel?

---

### Post by chili555 on 2020-06-30
> **captainquack2 said:**
> is there anything that works with 5+ kernel?
Please start your own new question and add the result of the terminal command:

```
lsusb
```

---

### Post by walts48 on 2020-07-01
I'm happy with the Edimax EW-781UN I recently purchased from a recommendation in a post on this site. May be this thread.

Plugged it into my PC, booted into Ubuntu 20.04 and it just worked.

Rebooted into 18.04.4 and it just worked.

I had an Asus AC1200 USB-AC53 Nano that I constantly had to rebuild the driver for after a kernel upgrade on 18.04 and didn't work with 20.04 or couldn't find a driver that would work, so I had to drag the Ethernet cable across the room and hook it up to the computer.

So far it has worked with every LiveCD Linux I have toyed with in my spare time.

Nope it was this thread.

[https://ubuntuforums.org/showthread.php?t=2443349](https://ubuntuforums.org/showthread.php?t=2443349)

---

