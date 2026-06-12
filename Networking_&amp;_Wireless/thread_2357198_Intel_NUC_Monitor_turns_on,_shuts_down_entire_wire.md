---
title: "Intel NUC: Monitor turns on, shuts down entire wireless network"
date: 2017-03-30
forum: Networking &amp; Wireless
---

### Post by j-fab on 2017-03-30
I am at a total loss.

If my Intel NUC's screen is off, my wifi works. I mean my entire wireless network, not the wifi connection on the NUC.

If I wiggle the mouse or press a key so the monitor wakes up, all the devices on my network lose wifi connectivity. They can't even reach the router, or see the network. But they can all connect and have internet connectivity if you plug them in with an ethernet cable.

This happens whether or not I enable or disable wifi on the NUC -- even if I just have the wired connection enabled, activating the screen kills the wireless network. 

I have the monitor plugged in with a displayport cable. 

I have tested this over and over - it's consistent, across all devices -- as soon as the NUC's monitor wakes up, the wifi network dies. 

How is this possible?

---

### Post by chili555 on 2017-03-31
I think this is possible because when you wake the NUC, the wireless also awakes and contacts the router to say, in effect, "I'm baaaaack!!!" I suspect there is something amiss in the wireless driver or the router setup or both.

Let's start with the wireless driver. Please open a terminal and run and post:```
lspci -nnk | grep 0280 -A2
```And for the router:```
sudo nmcli dev wifi list
```

---

