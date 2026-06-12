---
title: "WLan slow and unstable (Broadcom Chipset, Ubuntu 15.04)"
date: 2015-08-30
forum: Networking &amp; Wireless
---

### Post by kaizer3 on 2015-08-30
Hey folks,

I've got major problems with my WLan connection. It does give me download speeds of up to 3MB/s, but sometimes its painfully slow at just a few KB. It also tends to crash, especially when I use it a lot. Reconnecting the WLan usually fixes it, but downloads in progress won't continue anyways. It's a major pain in the ass since it prevents me from installing any bigger updates.
I'm running Ubuntu 15.04 on an Acer Aspire E-112, chipset apparently is a Broadcom BCM43142 802.11b/g/n. Right now I'm using the proprietary STA drivers from bcmwl-kernel-source. According to the Broadcom-guide this one should be fine from 14.04 LTS and higher, but I'm still having trouble.

Here are my scripts results:

[ATTACH]264118[/ATTACH]

Anyone got any further ideas on this? Help would be very much appreciated. Thanks!

---

### Post by praseodym on 2015-08-30
There is another wireless driver loaded:
```

sudo modprobe -rfv rt2800usb wl
sudo modprobe -v wl
```

---

### Post by kerry_s on 2015-08-30
try:
sudo apt-get install firmware-b43-installer

i had to do that on mine, cause the 1 from bcmwl-kernel-source was causing kernel crash on suspend. i didn't remove it, just have them all installed.

---

### Post by kaizer3 on 2015-08-30
That was my USB Stick. I tried it as an alternative but it didnt really do much better. It works perfectly fine on my desktop PC (win7) though... I removed the driver again but of course going back to status quo here didnt help. :(

I tried installing b43 before too which was suggested somewhere else. But the software-center doesnt even show that one up (even after deactivating STA) so i couldnt manage to choose it. Do you know the terminal commands by chance to switch em?

---

### Post by kerry_s on 2015-08-30
just run the command in terminal "sudo apt-get install firmware-b43-installer"
then reboot, it will load the right driver on it's own.

---

### Post by kaizer3 on 2015-08-30
I've already had it installed, but nevertheless the STA drivers are still running and the only ones shown in the software center.

---

