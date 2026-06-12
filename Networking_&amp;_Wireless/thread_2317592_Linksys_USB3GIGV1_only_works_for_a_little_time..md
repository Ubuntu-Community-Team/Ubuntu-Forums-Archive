---
title: "Linksys USB3GIGV1 only works for a little time."
date: 2016-03-17
forum: Networking &amp; Wireless
---

### Post by Raymond Day on 2016-03-17
I have a Linksys USB 3.0 to Gigabit adapter on my Ubuntu 15.10

When I plug it in and set it for a static IP it works for a little but then no connection. Something goes wrong.

So I put my Linksys USB 2.0 to Ethernet back on it and works good.

Is there some Ubuntu 15.10 driver that will make this adapter work?

It seems like as soon as you go to it after about 15 min it will load a little and then not be there.

In the dmesg log I don't see "1000Mbps" just 100Mbps so that may be it that it thinks it's a 100Mbps when it's a 1000Mbps.

Or what USB 3.0 to Gigabit is the best for Ubuntu 15.10?

-Raymond Day

---

### Post by Bucky Ball on 2016-03-18
*Thread moved to **Networking & Wireless**.*

---

### Post by Dawudd on 2016-12-18
I had the same issue. The device overheats and then stops working for a while, until it's cooled down. I spoke with Linksys tech support, and they knew about the overheating issue, and told me I need to use the updated Windows driver from their site. When I pointed out that I use Ubuntu, I was told that Linux isn't supported. When I pointed out that Chrome OS is listed as supported, and that it's Linux, I was told that Chrome OS uses a generic driver. But then Chrome OS should have the same overheating issue as Linux&#8212;which they won't fix. So they don't really support Chrome OS, do they?

It was at this point that I gave up on tech support and decided to return the device and buy something that actually supports Linux. For anyone who sees this, I suggest you do the same.

---

