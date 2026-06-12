---
title: "Ubuntu 18.04 Network Unavailable (Airplane mode)"
date: 2020-03-04
forum: Networking &amp; Wireless
---

### Post by mr-zx on 2020-03-04
Hi,

Since I updated some months ago to 18.04 I have been having strange network problems, especially from boot after shutdown where my wifi will not work. I have read various post here and tried several solutions, none of them work. The wifi (or network) comes back randomly after boot, it can be 1 reboot or 20 reboots (completely random it seems).

However I think I have narrowed the problem down to the following. My network card following the sticky post seems to be Broadcom and the following is the outcome when I run this code ( lspci -nn -d 14e4:)

```

01:00.0 Ethernet controller [0200]: Broadcom Inc. and subsidiaries NetXtreme BCM57786 Gigabit Ethernet PCIe [14e4:16b3] (rev 01)
01:00.1 SD Host controller [0805]: Broadcom Inc. and subsidiaries BCM57765/57785 SDXC/MMC Card Reader [14e4:16bc] (rev 01)

```

I was wondering if the Card reader could be interfering or as usual I'm looking at the wrong information. For what's worth the following here is the [outcome of wireless script]("https://pastebin.com/j98ELnPE"). 

_Additional Info:_
I noticed every time I do a a sudo apt update, or any updates from the software module, I loose the network following a reboot.

Also it indicates there's a hard block, but this is not true as Ubuntu identifies the wifi button's when pressed, it just doesn't do anything. When I log in using the unity/wayland (can't remember the exact name), it shows airplane block, but everytime I press the button a sign comes on the screen indicating "Airplane mode ...". Unfortunately the message is incomplete so I don't know if it is enabled/disabled.

Any help will be greatly appreciated

---

### Post by praseodym on 2020-03-05
Please run the script again when its not working

---

### Post by mr-zx on 2020-03-07
Will do

---

