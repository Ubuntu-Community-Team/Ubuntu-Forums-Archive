---
title: "Wifi extremely slow on Ubuntu 18.04 LTS"
date: 2018-06-25
forum: Networking &amp; Wireless
---

### Post by allan.barnes on 2018-06-25
Hey everyone, relatively new to Linux and unsure how to proceed with diagnosing this issue. Basically wi-fi is very slow on my ASUS Vivobook Pro using the built-in adapter, but only in Ubuntu; runs fine in Windows 10. When wired, it works great either way. The wireless network works normally with all my other devices, including other computers running Ubuntu (though they do have older versions). Currently running wired because posting this was proving to be impossible on wi-fi.

Relevant pastebin here: [http://paste.ubuntu.com/p/yPmgwwVmNZ/](http://paste.ubuntu.com/p/yPmgwwVmNZ/)

Thanks for your time.

---

### Post by chili555 on 2018-06-26
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

Finally, I suggest that you disable power saving in Network Manager:```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```Did I mention that your driver and old Chili hate hate hate TKIP?

---

