---
title: "advice needed: high gain external usb wi-fi"
date: 2015-08-01
forum: Networking &amp; Wireless
---

### Post by andrea-cimatoribus on 2015-08-01
Dear all,
I need to buy an external usb wi-fi adapter, with a high gain antenna (unfortunately I cannot pull cables nor use a repeater nor move the router in a better place etc).
At the moment I am trying to use an Alfa AWUS036AC but I am having a very bad experience with it. It connects and disconnects at random, it is often less sensitive than the internal wi-fi card, it drains so much power from the usb that the laptop seldom cannot keep it alive. It is basically unusable and a waste of money ](*,) I know that with a powered external usb hub I could solve the issue of the power, but then the driver doesn't work any more.

So, what I would need is:
- external usb wi-fi adapter
- chip with built-in linux driver, well tested on different recent kernels (>3.13). 
- It doesn't have to be new as long as I can find it say on ebay in Europe with some ease
- high-gain antenna, either built-in, or detachable with a standard coaxial plug (but then, which antenna?)
- it should work!!!

Any suggestion based on your direct experience? Thank you very much!

---

### Post by praseodym on 2015-08-01
Please show the outputs of
```
uname -a
lsusb
lsmod
iwconfig
rfkill list
iwlist chan
sudo iwlist scan
```

---

### Post by andrea-cimatoribus on 2015-08-01
Hi, thank you for your reply, but I already spent a lot of time debugging this device. I do not have the time to do more of this. I just need something that works, which means something else. I have used in the past external wi-fi which work great under linux(but are not powerful enough for what I need now), I am sure there are others I can use.

For the benefit of others having the same needs:
I am having a good experience with TP-Link TL-WN722N, which I found cheap online, the drivers are in the kernel and it has a solid performance, much better than the internal wifi (I guess thanks to the external antenna) and way ahead of the Alfa. Hopefully it will last...

---

