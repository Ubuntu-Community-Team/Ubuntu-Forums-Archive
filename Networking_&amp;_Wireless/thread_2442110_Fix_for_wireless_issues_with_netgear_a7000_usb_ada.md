---
title: "Fix for wireless issues with netgear a7000 usb adapter (rtl8814au, rtl8812au)"
date: 2020-04-29
forum: Networking &amp; Wireless
---

### Post by basblob on 2020-04-29
I had to make this post to help anyone else who might be having issues with this network adapter and possibly other network adapters which work with the realtek 8814au 8812au chipsets. I'm on ubuntu 20.04 with kernel 5.4.0-28-generic, and I own a netgear a7000 wireless adapter that works fine with windows but wouldnt function with my linux dual boot. 

All the threads i could fidn that addressed this subject were from 2018 at the earliest, and they all suggested drivers that haven't been updated in years and did not work on my install. After weeks of trial and error and a lot of frustration I found a much more recently updated version of the rtl8812au driver that ought to work with rtl8814au devices like mine as well, that isn't mentioned anywhere except some obscure link I found. 

You can find the drivers here and installation instructions for various linux distributions: [https://github.com/aircrack-ng/rtl8812au](https://github.com/aircrack-ng/rtl8812au).

On Ubuntu 20.04 you can install with these commands in terminal:

```
sudo apt update && sudo apt upgrade -y

sudo apt install dkms build-essential git

git clone https://github.com/aircrack-ng/rtl8812au.git

cd rtl8812au

sudo ./dkms-install.sh

reboot
```
That worked for me! Hopefully I can help someone else some headache!

---

### Post by jeremy31 on 2020-04-29
[https://ubuntuforums.org/showthread.php?t=2442071](https://ubuntuforums.org/showthread.php?t=2442071)
I actually forked that to add some devices on my own 6 months ago

---

### Post by DuckHook on 2020-04-29
Please refrain from non-standard fonts and styles. This can be difficult for those on small screens or with compromised vision.

---

