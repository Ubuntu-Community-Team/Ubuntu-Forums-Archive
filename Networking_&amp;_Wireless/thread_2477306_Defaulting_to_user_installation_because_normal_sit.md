---
title: "Defaulting to user installation because normal site-packages is not writeable"
date: 2022-07-20
forum: Networking &amp; Wireless
---

### Post by chat-4432 on 2022-07-20
i try to install requirements [https://openwrt.org/toh/xiaomi/xiaomi_mi_router_4c](https://openwrt.org/toh/xiaomi/xiaomi_mi_router_4c)
 pip3 install -r requirements.txt
it shows
```
Defaulting to user installation because normal site-packages is not writeable
Requirement already satisfied: requests in /usr/lib/python3/dist-packages (from -r requirements.txt (line 1)) (2.25.1)

```what should i do ??

---

### Post by TheFu on 2022-07-21
Why are you trying to setup openwrt on an Ubuntu system?  That doesn't make any sense.

openwrt is normally distributed as a firmware package for specific hardware.  One .bin file has to be "flashed" onto router hardware. This is typically, never, a regular PC running Linux.

Of course, if you ARE trying to setup openwrt on an x86-64 system, that wouldn't be Ubuntu and help would better come from a forum dedicated to openwrt. It is a different skillset than most people here, including me, would have.  I've run openwrt, but only on router-specific hardware from linksys, buffalo, or tp-link.

---

### Post by Holger_Gehrke on 2022-07-21
@TheFu: reading the linked page explains it quite clearly. The router chat-4432 is trying to install openwrt to has  no official way to put it on there, you need to exploit a flaw in it's firmware to get a telnet shell. A python script exists to do that exploit.

@chat-4432: When executing pip3 without root privileges, the installation of python packages can't be done system wide, instead the packages are installed to a user specific directory (~/.local/lib/). That's what the first message tells you. The second message tells you that the package 'requests' (which is all that is listed in requirements.txt) is already installed system wide, so no installation was done. You should now be able to go to the next step of the instructions.

Holger

---

### Post by chat-4432 on 2022-07-22
thankyou.

---

