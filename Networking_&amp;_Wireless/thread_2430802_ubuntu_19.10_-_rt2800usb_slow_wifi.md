---
title: "ubuntu 19.10 - rt2800usb slow wifi"
date: 2019-11-07
forum: Networking &amp; Wireless
---

### Post by alexander-thimm on 2019-11-07
Hi everyone. I've read several related topics here about my rt2800usb driver and slow wifi connections. But i still don't get good results. Best i can get on Ubuntu 19.10 is 10Mbit, on Windows i get 100Mbit. 
I started that wireless-info tool. Here are my settings: [https://pastebin.com/Zst1CJd8](https://pastebin.com/Zst1CJd8)

I hope someone can help me fix my wifi and reduce my headaches :)
If i did something wrong or if you need more info, please let me know.

---

### Post by alexander-thimm on 2019-11-08
After several hours of pain I finally did it!

My mainboard has several usb ports. First I tried one usb 3.1 port on the backside of my computer. 10Mbit. Then I tried the two usb 2 ports and the two usb 3.0 ports on the frontpanel. 10Mbit. After all the configuration possibilities I found on the internet I tried one last usb 3.0 port on the back and it worked! ~80-100Mbit. 

I would really like to know how this could be. Because on every other port the network manager says the wifi rate is nearly perfect with 270-300Mbit. 
It would be great if someone could tell me why there are differences in the usb ports.

---

### Post by praseodym on 2019-11-10
Check your USB trees via

```
lsusb -t
```
and the stick plugged in the respective slots. You may see how many devices are actively uptaking current from each tree. This might explain it

---

