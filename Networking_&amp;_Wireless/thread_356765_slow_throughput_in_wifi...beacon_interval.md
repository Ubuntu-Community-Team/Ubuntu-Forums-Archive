---
title: "slow throughput in wifi...beacon interval"
date: 2007-02-08
forum: Networking &amp; Wireless
---

### Post by cityismine on 2007-02-08
Hi, In windows my latency in games seems to jump up and down. My internet browsing also shows slow throughput some times. I checked my pci card's wifi utility and on the statistics page it showing alot of beacon losses.

So I went into my router's configuration and changed the beacon interval from 100 to 10. And wow, my internet browsing seemed smoother and my latency in games was reduced. But another problem popped up, with the beacon interval reduced, the other computer's in house can't see the AP/SSID.

I'm using an Encore wifi pci card, and other two pcs are using D-link wifi pci cards. The wifi router is a motorola brand. Maybe someone knows what's going on, as I'd like to get a smooth connection on all the computers. I've no idea why my wifi card won't function properly at the default beacon interval of 100.

---

### Post by ukripper on 2007-02-09
What is your download/upload speed and latency? find out by running this [http://www.speedtest.net/](http://www.speedtest.net/) and paste tall details here.

---

### Post by cityismine on 2007-02-09
download         upload           latency
2809 kb/s  	128 kb/s  	195 ms
4019 kb/s  	379 kb/s  	55 ms


Okay I ran the test test. I put the beacon interval at 100, and then at 10. As you can see my encore wifi card likes the lower beacon interval. What puzzles me is, why does it need such a low beacon interval. Once I lower the beacon interval, the other computers in my house can't see the AP/SSID. Is there anyway to get the encore wifi working properly at the default 100 beacon interval?

I checked around on google, and found out that the encore wifi is running on the Marvell Libertas 8335 chipset. I don't know if this help.

---

### Post by ukripper on 2007-02-12
Have you got Adsl or cable at home? latency is too high for download, shockingly latency is better while doing upload then downloading:confused: . 

Carry out the same test on wired connection and paste it here that will prove the exact ratio of your connection latency.

---

### Post by cityismine on 2007-02-14
I got a cable modem. The two measurements are not of upload and download. There of beacon intervals of 10 and 100. I set the beacon interval at 10 on my router and ran the test. Then I ran it again after changing the beacon interval to 100.

---

