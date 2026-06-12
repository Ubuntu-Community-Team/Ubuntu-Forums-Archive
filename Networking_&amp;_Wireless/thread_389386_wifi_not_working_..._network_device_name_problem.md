---
title: "wifi not working ... network device name problem?"
date: 2007-03-20
forum: Networking &amp; Wireless
---

### Post by kpjoyce on 2007-03-20
I have just installed Edgy and my wireless is not working. 'Wireless Connection' shows up in 'network settings', but says that it is not configured. I cannot activate it.

When I use my Dapper liveCD, wireless works immediately.

I poked around with the various troubleshooting guides and have found a/the problem, but I don't know a way to resolve it.

My wireless card shows up when I run lshw, and the reported logical name is 'wifi0'.
When I run iwconfig, 'wifi0' shows 'no wireless extensions'.  All of the wireless parameters are assigned to 'ath0'.

What can I do about the discrepancy?

---

### Post by kpjoyce on 2007-03-20
Anybody?

I'm thinking that if I can convince the system to call my wireless card 'ath0' instead of 'wifi0', then the driver (who expects to find the hardware filed under 'ath0') will be happy.  I will be happy too ... of course I have not figured out how to do that yet.

Am I on the right track?

---

