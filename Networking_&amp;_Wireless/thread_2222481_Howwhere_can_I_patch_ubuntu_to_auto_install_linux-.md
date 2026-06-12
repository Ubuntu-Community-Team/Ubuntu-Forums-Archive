---
title: "How/where can I patch ubuntu to auto install linux-firmware-nonfree if need"
date: 2014-05-06
forum: Networking &amp; Wireless
---

### Post by harobed on 2014-05-06
How can I help to fix this issue : [https://bugs.launchpad.net/ubuntu/+source/linux-firmware-nonfree/+bug/1316816](https://bugs.launchpad.net/ubuntu/+source/linux-firmware-nonfree/+bug/1316816)

Now that I posted on launchpad, do you have some idea to fix this issue ?

---

### Post by varunendra on 2014-05-07
As you can see [here]("http://wireless.kernel.org/en/users/Drivers/b43#Supported_devices"), there are four variants of BCM4321 card, and none of them are known to work very well with the "b43" driver that makes use of the firmware you get with "linux-firmware-nonfree" package. So there *may not be* a definite fix for the card. For some people, it may be the native driver "b43" + the firmware, while for others it may be the proprietary "wl" driver that doesn't need the firmware to be installed externally.

In any case, it is currently the "Additional Drivers" (earlier it was "jockey" program presented with that name, not sure which one it is currently) feature/program that detects if a device needs a proprietary driver, and offers the user to install it. For broadcom cards it offers the "wl" driver. The firmware can't be distributed with Ubuntu due to licensing issues and using a different mechanism to offer a driver/firmware may conflict with the "Additional Drivers" program. So I think you may try to contact the team that develops/maintains the "Additional Drivers" program/feature and let them know your concerns.

Unfortunately, I can't help beyond the above advice, I don't know myself how to contact that particular team. Maybe others do, and maybe others can offer a better suggestion as well.

---

