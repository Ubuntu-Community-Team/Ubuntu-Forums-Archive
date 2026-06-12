---
title: "USB Wi-Fi adapter no longer connecting to internet, Realtek 8812au and Panda PAU09"
date: 2020-06-18
forum: Networking &amp; Wireless
---

### Post by vivz753 on 2020-06-18
Hi, I'm running Ubuntu 18.04 LTS on my PC and recently my [BrosTrend Wifi adapter]("https://www.amazon.com/BrosTrend-1200Mbps-Adapter-Wireless-Antennas/dp/B01IEU7UZ0/ref=sxts_sxwds-bia-wc-p13n1_0?cv_ct_cx=brostrend+usb+wifi+adapter&dchild=1&keywords=brostrend+usb+wifi+adapter&pd_rd_i=B01IEU7UZ0&pd_rd_r=fd75f0d9-8328-42cc-8f58-05a81ba68bfa&pd_rd_w=trClU&pd_rd_wg=lO5B9&pf_rd_p=1da5beeb-8f71-435c-b5c5-3279a6171294&pf_rd_r=2FSQK0WRCF3YYHV7MQ8J&psc=1&qid=1592509066&sr=1-1-70f7c15d-07d8-466a-b325-4be35d7258cc") which uses Realtek 8812au stopped connecting to Wifi, even though it can still detect the nearby networks. I also have windows dual booted on my PC and the Wifi connects perfectly fine there, so it leads me to believe that this is a compatability issue with the Wifi Adapter on Ubuntu, or maybe the driver is no longer compatible with the Linux kernel (even though I have software updates disabled). For the past few months I had been using this driver I found on Github here [https://github.com/gnab/rtl8812au](https://github.com/gnab/rtl8812au) and it has worked perfectly fine. I followed the instructions, ran make and insmod and copied the 8812au.ko file into ```
/lib/modules/5.3.0-51-generic/kernel/drivers/net/wireless
``` (I didn't need do any of the dkms stuff, and I don't have the command downloaded, so please don't ask me to do any dkms commands) 

But now, it doesn't connect at all to any network. To troubleshoot, I tried deleting the 8812au.ko file, re-running make, and re-running insmod and re-copying it to that folder, rebooting, etc. Nothing worked, so I purchased the Panda Wireless USB Adapter PAU09 since it was advertised as plug n play and supports Ubuntu 18.04, and I didn't want to go through any obscure tutorials anymore or rely on a driver on the internet that isn't regularly maintained which will probably stop working in the future anyway. To my surprise, it also didn't work! It also has the same issue as the other wifi adapter--the wifi settings say "Connecting" after selecting a network only to never connect. What is my issue here? And FYI my PC does not have an internal Wifi card.

---

### Post by vivz753 on 2020-07-01
I ended up reinstalling Ubuntu from scratch and got rid of my BrosTrend Wifi adapter. Panda Wireless adapter works perfectly now with the newly installed OS.

---

