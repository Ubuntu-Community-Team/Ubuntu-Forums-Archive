---
title: "AC1200 Driver on new install - Drivers working but can't hold connection"
date: 2020-03-23
forum: Networking &amp; Wireless
---

### Post by sp00nexe on 2020-03-23
Hey all,

I recently installed Ubuntu and managed to install the drivers for my WiFi adapter (Supola AC1200 USB 3.0 Dual Band) by researching previous threads - using the driver provided here.
[https://github.com/cilynx/rtl88x2bu](https://github.com/cilynx/rtl88x2bu)

However, now that I've installed the driver I am having constant issues with maintaining my WiFi connection. It rarely notices my 5GHz signal (only finding the 2.5GHz one) and It's a constant challenge to keep it connected. I am constantly fighting with it to make it connect to the signal - it sees it clearly and it works fine on all other devices in my house. It just keeps trying to connect - and gives up most of the time. When it does connect - it stays connected for a few minutes - before droppping out and returning to the vicious cycle of trying to connect over and over. Previously when I used Windows 10, I had no issues with my wireless adapter. I had a strong signal to my 5GHz signal, and never experienced any dropouts. 

Could this be a driver issue? Is there someway to fix this? I'm losing my mind browsing different threads desperately trying to find a solution. 

Thanks,

---

### Post by chili555 on 2020-03-23
Have you tried all the usual tips and tricks?

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

### Post by praseodym on 2020-03-25
Hi Chili,

this doesn't work as it is not an full-MAC driver, only supporting the cfg80211 subsystem

```
echo 'options 88x2bu rtw_country_code="IS"' | sudo tee /etc/modprobe.d/88x2bu_options.conf
```
and rebooting should do that trick. Maybe also this one

```
sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
sudo systemctl restart network-manager.service
```

---

