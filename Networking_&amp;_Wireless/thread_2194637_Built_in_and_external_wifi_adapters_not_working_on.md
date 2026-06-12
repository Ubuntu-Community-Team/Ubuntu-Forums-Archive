---
title: "Built in and external wifi adapters not working on Dell Inspiron 1545 w/Ubuntu 12.04"
date: 2013-12-19
forum: Networking &amp; Wireless
---

### Post by sean345 on 2013-12-19
I've read over quite a few [SOLVED] threads started by people experiencing almost this exact same issue, but none of the solutions have gained me any headway.

Wired internet connection works just fine, but when I try to connect to my wifi, whether I use my internal card, or my external "TP-LINK" wireless USB adapter, I get the exact same problem. A notification keeps popping up every few moments asking me to enter my wifi password. In between these annoying popups, it seems to be trying to connect, but simply can't. Clicking "cancel" instead of the other option simply reduces the frequency of these popups, I have to disable wifi to get rid of them entirely. Like I said, this happens no matter how I try to connect to a wireless network.

Any help would be GREATLY appreciated.

---

### Post by chili555 on 2013-12-20
Let's see if we can troubleshoot the internal wireless first. Please detach the USB wireless, open a terminal and run and post:```
lspci -nn | grep 0280
```

---

### Post by sean345 on 2013-12-20
Okay, here's what I got:
```
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
```

---

### Post by chili555 on 2013-12-20
Please hook up the ethernet and open a terminal and do:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install firmware-b43-lpphy-installer
```Detach the ethernet, reboot and tell us how it's going.

---

### Post by sean345 on 2013-12-20
Thanks for trying to help, but I asked a friend of mine who also has Ubuntu, and he managed to get it working fine.

---

### Post by chili555 on 2013-12-20
> **sean345 said:**
> Thanks for trying to help, but I asked a friend of mine who also has Ubuntu, and he managed to get it working fine.For the benefit of the searchers, would you please ask your friend to detail what fixed it? Inquiring minds want to know!

---

### Post by sean345 on 2013-12-20
He told me he purged the broadcom drivers, then reinstalled them. After that he just rebooted.
Is that what the code you told me to use would have done, by the way?

---

### Post by chili555 on 2013-12-20
> **sean345 said:**
> He told me he purged the broadcom drivers, then reinstalled them. After that he just rebooted.
Is that what the code you told me to use would have done, by the way?Nope. My code would have purged the Broadcom STA driver and then installed the firmware to use the native b43 driver.

As long as it's working as expected, there is nothing else to do.

---

