---
title: "Win-11, have trouble with W-Lan stick"
date: 2021-08-06
forum: Networking &amp; Wireless
---

### Post by mustang700 on 2021-08-06
Hello,

I run Win-10, 2 months ago and installed Ubuntu 20.04 with W-Lan "rtl8812au"
Now I installed Win-11, and reinstalled also Ubuntu on a new partition, but the USB-Wlan stick won't work.
I have an old "ZYair g220" it works without a driver, just plug in and it is ready.

the installation always have been that:

```
sudo apt update
sudo apt install git dkms
sudo  git clone https://github.com/gnab/rtl8812au.git
sudo  cp -r rtl8812au /usr/src/rtl8812au-4.2.2
sudo dkms add -m rtl8812au -v 4.2.2
sudo  dkms build -m rtl8812au -v 4.2.2
sudo dkms install -m rtl8812au -v 4.2.2

```

is there maybe anything wrong with secure boot or this? which I hadn't when  I used Win-10
but I tried enable/disable it.

---

### Post by Frogs Hair on 2021-08-07
Moved to Networking & Wireless 

Windows 11 has not been released to the general public and is likely to change before the final release. The ability to dual boot with Linux is in question and an unknown until the official release date. There are new security protocols coming for Win 11.

---

### Post by morrownr on 2021-08-07
Hi mustang,

I can't speak to any issues that Windows might cause but I am somewhat skeptical of the rtl8812au driver that you installed. That driver is based on very old code.

Look here:

[https://github.com/morrownr/8812au](https://github.com/morrownr/8812au)

You'll need to clean out the other driver before installing the one above.

If you are inclined to get away from these problematic Realtek drivers:

[https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi)

Good luck.

---

### Post by mustang700 on 2021-08-09
well, this one works:
sudo apt update
sudo apt install git dkms
sudo git clone [https://github.com/aircrack-ng/rtl8812au](https://github.com/aircrack-ng/rtl8812au)
sudo cp -r rtl8812au /usr/src/rtl8812au-5.6.4.2
sudo dkms add -m rtl8812au -v 5.6.4.2
sudo dkms build -m rtl8812au -v 5.6.4.2
sudo dkms install -m rtl8812au -v 5.6.4.2

---

