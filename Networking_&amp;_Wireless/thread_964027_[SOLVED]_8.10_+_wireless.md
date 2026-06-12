---
title: "[SOLVED] 8.10 + wireless"
date: 2008-10-30
forum: Networking &amp; Wireless
---

### Post by PatrickMoore on 2008-10-30
im running the live disk and im reluctant to do a full install simply because i dont have a wired connection at this time so i dont want to be stuck anyone had problems with broadcom wireless cards? rumor has it that its completely compatable out of the box.

---

### Post by mrm48 on 2008-10-30
I had to download the fwcutter before my broadcom wireless card worked, so I had to have a wired connection at first.

---

### Post by mikewhatever on 2008-10-30
Well, rumor has it that broadcom cards used in Dell notebooks should get a compatibility boots. You seem to have an HP, so I suggest investigating further. <sudo lshw -C network> command will show more info on your card.

---

### Post by jbrown96 on 2008-10-30
Is wireless not working? You may need to bring the interface up. Go to a terminal (apps-->accessories-->terminal) and try ```
iwconfig
```, if that lists a device with wireless extensions (wlan0, eth1, ath0, something similar, but not wmaster-0), then try bringing the interface up with ```
sudo ifconfig INTERFACE up
``` replace INTERFACE with the interface you just found. Then, you can try network-manager (top right) to view/connect to wireless. If that doesn't work, post back with your hardware with ```
lspci | grep Network
```

---

### Post by ww711 on 2008-10-30
My Laptop has a Broadcom wireless device chipset

Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

I done a fresh install with ii 8.10 and enabled the Broadcom STA wireless driver and was connected in a few seconds.

As other people have have suggested, find out the exact Broadcom model/revision and take it from there.

---

### Post by PatrickMoore on 2008-10-30
> **ww711 said:**
> My Laptop has a Broadcom wireless device chipset

Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

I done a fresh install with ii 8.10 and enabled the Broadcom STA wireless driver and was connected in a few seconds.

As other people have have suggested, find out the exact Broadcom model/revision and take it from there.

im able to download and install the restricted driver but i cant read a wireless  connection at all. its kinda confusing. i have  fwcutter and broadcom chipsets on a flashdrive as well as my instructions saved. i dual booted for the time being since i need the internet.

---

### Post by PatrickMoore on 2008-10-30
> **PatrickMoore said:**
> im able to download and install the restricted driver but i cant read a wireless  connection at all. its kinda confusing. i have  fwcutter and broadcom chipsets on a flashdrive as well as my instructions saved. i dual booted for the time being since i need the internet.

i as well have the 4311 chipset

---

### Post by jbrown96 on 2008-10-30
Don't worry about fwcutter. The whole process is automated to install fwcutter and the firmware since 7.10 (maybe 8.04). However, as Mike said, Broadcomm is supposed to have native drivers out now. Check the proprietary drivers manager System-->Admin-->Hardware Drivers and see if there is an option. However, you won't be able to test this on the LiveCD because it requires a restart to enable them.

---

### Post by PatrickMoore on 2008-10-30
i played with it and now its fine although i had to toggle with my  lan connection to get it to read the wireless connection

---

