---
title: "WiFi slow on Ubuntu 18.04 dual boot"
date: 2018-09-01
forum: Networking &amp; Wireless
---

### Post by polywongpham on 2018-09-01
My WiFi has been perfectly fine on my Windows 10 boot, but on Ubuntu I've been getting terrible download speeds. 

My windows is around 150-180 mbps, while on Ubuntu I get 2-4 mbps. My laptop is a Dell XPS 15 with an Intel 9260 card.

I tried this command on another thread but it didn't do anything for me.

[COLOR=#000000]echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf

[/COLOR]
The output for the wireless info script is here [https://pastebin.ubuntu.com/p/C7Q2H94j4x/](https://pastebin.ubuntu.com/p/C7Q2H94j4x/)

---

### Post by chili555 on 2018-09-02
I own and use successfully two Intel wireless devices. I have honed a few techniques in several years and thousands of forum posts.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Then set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
sudo nano /etc/default/crda
```Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Is there any improvement?

---

