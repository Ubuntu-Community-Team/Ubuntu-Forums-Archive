---
title: "[Which one?] WPA-PSK or WPA2-PSK or WPA/WPA2-PSK mixed"
date: 2020-05-18
forum: Networking &amp; Wireless
---

### Post by linuxyogi on 2020-05-18
Which security should I set on my WiFi router ?
Please see attachment.

[ATTACH=CONFIG]285913[/ATTACH]

---

### Post by chili555 on 2020-05-18
Here is the advice I give often that has proven to be helpful.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I recommend a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router.

---

### Post by linuxyogi on 2020-05-18
> **chili555 said:**
>  First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP.

Kindly see my attachment. I don't see [COLOR=#ff0000]**WPA2-AES.**[/COLOR]

---

### Post by chili555 on 2020-05-18
Not every consumer-grade router allows for users to manipulate every parameter. As well, older routers manufactured before AES, also known as CCMP, was introduced, obviously don't show that as a selection. In those cases, all we can do is work with what selections are available. I therefore suggest WPA2-PSK.

---

### Post by linuxyogi on 2020-05-18
> **chili555 said:**
>  I therefore suggest WPA2-PSK.

WPA2-PSK is selected by default. Marking as solved. Thanks.

---

