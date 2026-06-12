---
title: "Wi Fi Hoptspot Network Connection Failure"
date: 2020-11-02
forum: Networking &amp; Wireless
---

### Post by davehor on 2020-11-02
Hi,

Not the most versed Ubuntu/Linux user. Would like to set-up a hotpot on my PC to be able to transfer files between PC and Laptop, and give me Internet access for Laptop and Smartphone.

So what happens is that using the graphic interface I try and start the hotspot.

It starts and is never visible to my other devices, and after about 30 seconds I get an error: Connection failed... Activation of network connection failed

using the WiFi dongle to connect to other networks is no problem.

The Dongle:
Bus 001 Device 002: ID 0bda:8179 Realtek Semiconductor Corp. RTL8188EUS 802.11n Wireless Network Adapter

Any help is much appreciated.

Thanks,
David

---

### Post by davehor on 2020-11-02
So I solved this myself:

I updated the driver from github. Will I have to manually update this every time the kernel is updated?

And I changed the mode from Adhoc to AP/Hotspot

With WAP security it even works with Android now.

---

