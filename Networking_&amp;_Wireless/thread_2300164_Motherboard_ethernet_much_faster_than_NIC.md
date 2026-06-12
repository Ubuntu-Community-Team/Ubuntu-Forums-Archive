---
title: "Motherboard ethernet much faster than NIC"
date: 2015-10-24
forum: Networking &amp; Wireless
---

### Post by lwfx on 2015-10-24
I have been using my built in gigabit ethernet on the motherboard getting my usual ~180Mbps, decided to pop in my gigabit intel NIC PCI-E card and with that get ~60Mbps.

Any idea why this is? I have yet to test in Windows but will here in a few hours, but thought I'd put this thread up now.

```

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
    Subsystem: Biostar Microtech Int'l Corp Device 230a
    Kernel driver in use: r8169
06:00.0 Ethernet controller: Intel Corporation 82574L Gigabit Network Connection
    Subsystem: Intel Corporation Gigabit CT Desktop Adapter
    Kernel driver in use: e1000e


```

---

### Post by Bucky Ball on 2015-10-24
Test it in Windows and get back to us (if you test every solution you can think of or find before posting you will save some time getting support). :)

There are many reasons why your wireless may be running slow. It will always be a little slower than ethernet, but not half the speed. There's something happening there. Have you tried moving the laptop right next to the router and testing the speed there? If you are getting much closer to 160mbps, then your regular spot is possibly behind some obstacle. Any large metal girders between you and the router or a major conduit containing electrical wiring?

Also, with the dongle plugged in, post the results of this, please:

```
sudo lshw -C network
```

... between code tags (see the last link in my signature).

---

### Post by lwfx on 2015-10-24
This is all wired. Looks like it is the card or motherboard itself as it does the same thing in Windows so I basically made a pointless post.

---

### Post by Bucky Ball on 2015-10-24
Ah, right. My mistake. They are both ethernet cards. Doh! :D

Ok, yea. That second one is obviously inferior and possibly runs that fast. Older I suspect. You could look up the specs of each and find out for sure or run the command in my last post and that will show you more detail, capabilities, etc. 

Please mark the thread as solved by following the first link in my signature. Thanks and good luck. :)

(The Intel looks to be from about 2008 from a quick look about ...)

---

