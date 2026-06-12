---
title: "Network Manager Cannot See Stored Network After Suspend"
date: 2018-09-25
forum: Networking &amp; Wireless
---

### Post by jeffhoogland on 2018-09-25
I have the following wireless device:

Card-2: Realtek Device b822 driver: r8822be

When I suspend my system and then resume it using 18.04, my stored 5ghz network is not listed or connected to again. The 2.4ghz network on my router is there to connect to and my neighbor's 5ghz wireless networks are listed as well.

Restarting the network manager / wireless from the command line or by checking / unchecking wireless on the widget does not correct the issue. Unloading / reloading the driver via modprobe, allows me to see the network again as expected via the commands:

jeff@hoogltop:~$ sudo modprobe -r r8822be
jeff@hoogltop:~$ sudo modprobe r8822be

I suppose I can add these commands to when I unsuspend, but wondering if there is a better way to correct the issue outside of doing this.

Thanks!

---

