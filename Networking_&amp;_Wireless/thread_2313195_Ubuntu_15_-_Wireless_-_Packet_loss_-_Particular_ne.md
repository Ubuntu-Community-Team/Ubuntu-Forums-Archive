---
title: "Ubuntu 15 - Wireless - Packet loss - Particular network"
date: 2016-02-10
forum: Networking &amp; Wireless
---

### Post by biosboy4 on 2016-02-10
Hello,

I have been using Lubuntu 15 with a Belkin N300 wireless card. The card works great out of the box. However, ALL OF A SUDDEN (Just started happening this morning, it worked fine before this for many many days) I'm getting an average of 40%-70% packet loss on the wireless at work. When I tether through my phone everything works fine.

Why are the AP's at my work all of a sudden not agreeing with my Ubuntu workstation? How in the world do I fix this? 

Thank you,

PS: Nothing has changed on my computer from yesterday till today, and I can't imagine anything has changed with the Ubiquiti AP's either.

---

### Post by biosboy4 on 2016-02-10
Got it! I tethered through my phone, went through the vpn tunnel, hit the linux server up that hosts the wireless controller to find the open ports. Eventually hit the right port, logged in and rebooted all the AP's. Now I am back to 0% packet loss when connected to the internal wireless network.

Whew, that took me a freaking hour!

Thanks guys!

---

### Post by biosboy4 on 2016-02-10
Update#2: So after a short period of time, my packet loss jumped back up to 70%..  When I took another look at the controller I noticed that the almost every nic on the plant floor was connected to a single AP. After some load balancing, Internet connectivity via the wireless network is faster than I have ever seen it. Oh yea, and no packet loss. :)

---

