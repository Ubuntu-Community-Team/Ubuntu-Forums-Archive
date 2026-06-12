---
title: "Install-trouble E3372h on RPI and 21.10"
date: 2021-11-08
forum: Networking &amp; Wireless
---

### Post by gregszuh on 2021-11-08
Hi. 
(new here so my questions might be of the novis kind).

I used to run my RPI2 on Ubuntu 14-15-something and the Huawei E3372 worked like a charm but it was clearly time to upgrade and instead of going through the iterative routine I
put a clean installation of 21.04 on a card and booted the RPI.

Issue is that the stick doesn't work anymore.
Nothing in "ifconfig", mo modem under "mmcli -L". (Can paste details later)
What I've done so far beyond booting up: 

- lsusb shows the modem as a Huawei memory stick.
- used usb_modeswitch to make this a mobile/gsm stick: lsusb shows Huawei Mobile/networkcard (device ID 1506)
- usb_modeswitch log shows that switching is fine.
- mmcli -L shows still no modem found.
- under /dev/ there is only the cdc_wdm0 but no ttyUSBx.
- syslog/dmesg shows that a "wwan0" is renamed to "wwanXXXXXXXXX"  
- ifconfig -a shows a wwanXXXXXXX but is kind of stale/unconfigurable.
- modem.manager logs an error regarding the modem.

Any clues as where to go from here? :mrgreen:
Thanks!

 PS: My old Ubuntu 14.XX recognized the stick (as a 12f1:1506) and runs it without any issues.

Best, 
Greg

---

