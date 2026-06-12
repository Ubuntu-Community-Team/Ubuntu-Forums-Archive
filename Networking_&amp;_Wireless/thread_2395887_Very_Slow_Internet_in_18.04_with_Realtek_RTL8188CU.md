---
title: "Very Slow Internet in 18.04 with Realtek RTL8188CUS"
date: 2018-07-08
forum: Networking &amp; Wireless
---

### Post by geekprophet on 2018-07-08
Hello all,

I recently set up an Ubuntu 18.04 64-bit desktop. I am using a Realtek RTL8188CUS-based USB dongle for WiFi, and it is working extremely slowly. Speeds are under 1 mb down, often as low as 50kb down, and the tests I have been able to run all crash or declare network problems before registering any up speed at all.

I have tried a number of fixes, including special drivers and a variety of configuration changes, but nothing seems to work. lsusb shows: Bus 001 Device 004: ID 7392:7811 Edimax Technology Co., Ltd EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS]

I have run the wireless testing script, and here are the results on pastebin: [http://paste.ubuntu.com/p/M7VZVWBQ6b/](http://paste.ubuntu.com/p/M7VZVWBQ6b/)

I hope someone can give me a good suggestion. I am concerned that I have tried so many changes that I'll need to reinstall Ubuntu to clean up and start over.

Thank you in advance!

---

### Post by wildmanne39 on 2018-07-08
*Thread moved to **Networking & Wireless for a more appropriate fit**.*

---

### Post by praseodym on 2018-07-08
Hi,

use the native driver rtl8xxxu instead of the self-compiled 8192cu or the other native rtl8192cu

---

### Post by chili555 on 2018-07-08
Please check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Then set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
sudo nano /etc/default/crda
```Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

After making these changes, try the native driver as suggested:```
sudo modprobe -r 8192cu
sudo modprobe rtl8xxxu
```Any improvement? If so, we'll make it permanent.

---

### Post by geekprophet on 2018-07-08
Hello all,

I was about to post a long response when I got the opportunity to run a simple test. I got hold of a Windows machine and tried it there. It was just as bad. Hardware issue for the win.

Thank you for your assistance.

---

