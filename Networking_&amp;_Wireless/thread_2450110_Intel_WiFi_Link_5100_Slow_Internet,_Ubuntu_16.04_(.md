---
title: "Intel WiFi Link 5100 Slow Internet, Ubuntu 16.04 (After Upgrade from Ubuntu 14.04)"
date: 2020-09-07
forum: Networking &amp; Wireless
---

### Post by embargiel on 2020-09-07
Hi, 

I've been encountering some Wi-Fi slowdown issue after updating my Ubuntu from 14.04 to 16.04. 

It works just fine on other devices and operating systems (Android, Windows, Ubuntu 14.04), so I know that the Internet connection is fine.

I've tried changing the setting of gai.conf so that it would prioritize IPV4 vs. IPV6 (by uncommenting the "precedence ::ffff:0:0/96  100" line), and also disabling 11n, but to no avail.

Here is the content of my wireless-info file:

[https://paste.ubuntu.com/p/b8W4WMW89v/](https://paste.ubuntu.com/p/b8W4WMW89v/)

Thanks, and I would appreciate the help.

---

### Post by jeremy31 on 2020-09-07
Try this in terminal and reboot
```
sudo rm /etc/modprobe.d/intel_11n_disable.conf
echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```

---

### Post by chili555 on 2020-09-07
In addition to Jeremy's excellent suggestion, I recommend that you also undertake the usual, well-known Intel wireless tweaks.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Then set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
sudo nano /etc/default/crda
```
Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save (Ctrl+o followed by Enter) and close (Ctrl+x) the text editor.

---

### Post by embargiel on 2020-09-07
Hi, 

Thank you very much for your responses. 

I tried both of your suggestions (11n_disable and also default/crda to point to my country code), and unfortunately, they didn't seem to help. 

Note that I have not made any changes to my router settings, and the connection was fine with other devices and operating systems (such as Windows, Android, or even Ubuntu 14.04 before I updated it to 16.04 yesterday). 

I'm providing the new wireless-info:

[https://paste.ubuntu.com/p/7dd4B4m3HZ/](https://paste.ubuntu.com/p/7dd4B4m3HZ/)

Any other suggestions? 

Thank you in advance and I truly appreciate your help.

---

### Post by jeremy31 on 2020-09-07
It seems we forgot about disabling wifi power management, do this and reboot
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```

---

### Post by embargiel on 2020-09-07
I tried that and unfortunately, it still didn't fix it. 

For example, I still wasn't able to consistently run the 'Software Updater' without it running into the connection warning. 

Thank you.

---

### Post by embargiel on 2020-09-13
Any other ideas? 

The slowdown still persists, and I've tried everything that was suggested, and I even tried using a different connection (such tethering from my Android phone).

Here is the latest pastebin from running the wireless-info script

[https://paste.ubuntu.com/p/JQBQfpwBZn/](https://paste.ubuntu.com/p/JQBQfpwBZn/)

Thank you in advance.

---

### Post by jeremy31 on 2020-09-13
Go into Network Manager settings and set IPv6 to off or ignore

---

