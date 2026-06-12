---
title: "Installing 10.04 wireless drivers into 8.04 [bt4, etc.]"
date: 2010-09-06
forum: New to Ubuntu
---

### Post by LordVaati on 2010-09-06
I have been having issues getting wireless drivers to work on ubuntu 8.04 based distros.... [namely backtrack 4]....However....I have 10.04 LTS installed on another partition with wireless working perfectly out of the box

Is there a way I can take the 10.04 drivers and get them to work on 8.04?

'lspci' in 10.04 lists my wlan0 device as "Realtek Semiconductor Co., Ltd. Device 8171 (rev10)"

---

### Post by aysiu on 2010-09-07
It's probably not as easy as that. Wireless support is built into the Linux kernel. Upgrading the kernel isn't so easy. You might have to recompile it from scratch. Almost would just be easier to install 10.04, to be honest.

---

