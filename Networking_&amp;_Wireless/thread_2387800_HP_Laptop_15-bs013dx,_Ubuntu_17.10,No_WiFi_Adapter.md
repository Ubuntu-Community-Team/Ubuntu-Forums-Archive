---
title: "HP Laptop 15-bs013dx, Ubuntu 17.10,No WiFi Adapter Found"
date: 2018-03-23
forum: Networking &amp; Wireless
---

### Post by heliac0303 on 2018-03-23
Hello,

I'm a new ubuntu user and am having issues with the wifi adapter not not being found.

I've gone through the sticky and have downloaded the wireless info script which is attached to this message.
I've also looked for the driver here:
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek#PCI](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek#PCI)

I'm not sure if i am missing anything and i'm hoping that i won't have to try the NDIS wrapper if there is a better solution i am just not aware of.

Has anyone had a similar issue with an HP laptop in the past?
Would appreciate any support

---

### Post by wildmanne39 on 2018-03-23
Please do:
```
sudo apt-get install linux-headers-generic linux-headers-$(uname -r) build-essential
```

Then follow the directions at the following link.

[https://askubuntu.com/questions/961299/cannot-see-my-wifi-10ecd723-when-trying-ubuntu?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa](https://askubuntu.com/questions/961299/cannot-see-my-wifi-10ecd723-when-trying-ubuntu?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa)

---

### Post by firefox_user2 on 2018-03-23
I have a similar H.P. laptop 15- BDO11DX just got it and having the identical problem. Your not alone. I 'll follow along and see what advice you get. Good luck.

---

### Post by wildmanne39 on 2018-03-23
Hello firefox_user2, please start your own thread so you can get the help you need, we do not even know if you have the same wifi card and we only allow one person getting help per thread so it does not get confusing.

You are welcome to watch the thread of course but not the best way to get help.

Thanks

---

### Post by heliac0303 on 2018-03-24
Thanks for the link wildmanne39 that worked!

---

### Post by wildmanne39 on 2018-03-24
Your welcome! please use thread tools at the top of the page to mark the thread solved.

Thanks

---

