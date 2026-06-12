---
title: "Toshiba Satellite A200-27R Wireless Help."
date: 2008-07-14
forum: Networking &amp; Wireless
---

### Post by heingericke on 2008-07-14
Hello, I have a Toshiba Satellite A200-27R running Vista home premium. I installed Ubuntu 8.04 LTS within windows(wubi). Everything was fine initially, during the install I had the ethernet lead connected to trigger the updates. All was well. Though I didn't get the wifi to work, It did acknowledge there was a wifi card in my machine (intel(R) pro/wireless 3945ABG). I also found the driver on vista and installed it with ndiswrapper. Still no luck. Then after a reboot(had to go out) ubuntu does'nt even hint at knowing about the wifi card.

Could use some help. I'm prepared to do a clean install if need be. So someone help a fool out?

Thanks.

---

### Post by adldesigner on 2008-07-14
Open up a terminal (Applications > Accessories > Terminal) and try the following commands:

(Lists all your PCI devices)
```
lspci
```
(Lists all your USB devices)
```
lsusb
```
(Lists your hardware and extracts Network entries)
```
sudo lshw -C -network
```
(Lists any wireless network available in your area)
```
iwlist scan
```

Post the output of each one of those commands enclosed by CODE tags (for better code readability).
This should help us start to diagnose your issue.

---

### Post by heingericke on 2008-07-22
I wanted to thank you adldesigner for replying and also apologies for taking so long, I was out of town.

I solved the issue by simply dowloading Wubi from the Wubi website and automating the install that is downloaded via Wubi, as opposed to the install on the 8.04 LTS cd that I got from shipit.

---

### Post by adldesigner on 2008-08-02
Oh ok, no worries man! :)
Glad it worked out for you that way!

---

