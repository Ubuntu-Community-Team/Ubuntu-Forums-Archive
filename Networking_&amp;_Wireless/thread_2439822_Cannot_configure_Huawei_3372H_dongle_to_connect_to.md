---
title: "Cannot configure Huawei 3372H dongle to connect to internet"
date: 2020-04-01
forum: Networking &amp; Wireless
---

### Post by mmichmich on 2020-04-01
[COLOR=#121112][FONT=&amp]Hello!

[/FONT][/COLOR]
[COLOR=#121112][FONT=&amp]I have a Huawei E3372H mobile network usb dongle for connecting to the internet. I am using HiLink mode on another computer (Win 10) and after automatically installing the hilink manager the browser pops up automatically with the 192.168.8.1. After configuring the SIM card profile it works, the light blue indicator on the dongle is constant and I can access the internet. Next, I try plugging the dongle into a Ubuntu desktop 18.04 LTS and it works automatically too.

However, when I try to plug the dongle into a development board with Xubuntu 18.04 LTS, the dongle turns to constant light blue showing that the 4G network is connected but I cannot connect it to the internet. It does not appear as a virtual ethernet device in ifconfig like i would expect it to.

1) lsusb gives 12d1:14dc for this device
2) tried adding in /lib/udev/rules.d/40-usb_modeswitch.rules the line [COLOR=#242729][FONT=Consolas]ATTR{idVendor}=="12d1", ATTR{idProduct}=="14dc", RUN +="usb_modeswitch '/%k'" [/FONT][/COLOR]but there is no difference. I think the generic entry for Huawei models already works
3) checked that ModemManager is running too

May I know what else I can do?[/FONT][/COLOR]

---

