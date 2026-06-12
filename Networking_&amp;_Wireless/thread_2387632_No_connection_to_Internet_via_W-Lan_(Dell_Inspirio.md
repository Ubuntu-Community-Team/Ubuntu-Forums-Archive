---
title: "No connection to Internet via W-Lan (Dell Inspirion 15 3000; Ubuntu 16.04)"
date: 2018-03-21
forum: Networking &amp; Wireless
---

### Post by aquariuus on 2018-03-21
Hello,

Ubuntu is quite new for me. From the beginning there is a problem with the internet access.

- there is a sufficient connection to w-lan router
- not able to connect to internet via browser
- the connection via cable (ethernet) works well
- if I disconnect the ethernet, sometimes the wireles internet connection is working, somtimes not
- mostly after a restart it is not working anymore via wireles-lan

I would be thankfull for any hint

Here Is the Pastebin: [http://paste.ubuntu.com/p/H9zVr5tDzn/](http://paste.ubuntu.com/p/H9zVr5tDzn/)

aquariuus

---

### Post by chili555 on 2018-03-23
We're sorry that your post has been unanswered for two days. All of us here try hard but we sometimes miss one.

First, your wireless info shows a nice, strong connection to wireless as well as ethernet. In order to diagnose your issue, we'd like to see another wireless info report without ethernet attached and, if possible, struggling to connect.

We note that your router is reported to be on channel 7. That's a pretty unusual selection since there is considerable channel overlap at channel 7. Is it possible that your router is set to auto channel selection? I think many Linux wireless drivers struggle to connect to an ever-changing channel offered by the router.

Here are some useful tips for your router setup. I have honed a few techniques in several years and thousands of forum posts.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

I am also disturbed by this in the message log:> [  143.078362] ath: EEPROM indicates we should expect a country code
[  143.078371] ath: doing EEPROM country->regdmn map search
[  143.078380] ath: country maps to regdmn code: 0x37
[  143.078388] ath: Country alpha2 being used: DE
[  143.078396] ath: Regpair used: 0x37
[  143.078406] ath: regdomain 0x8114 dynamically updated by country IESo are you located in Germany (DE) or Ireland (IE)?  Whichever is the case, I think we ought to set the CRDA file to the correct locale.

Please make the router changes, detach the ethernet and give us a new report.

---

