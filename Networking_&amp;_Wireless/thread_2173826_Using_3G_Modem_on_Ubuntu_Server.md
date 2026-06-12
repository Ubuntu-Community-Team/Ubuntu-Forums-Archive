---
title: "Using 3G Modem on Ubuntu Server"
date: 2013-09-11
forum: Networking &amp; Wireless
---

### Post by chrislynch8 on 2013-09-11
Hi,

I have a Hawuei E173 working correctly in Ubuntu 12.04 Desktop Edition. When I issue lsusb I get the following Vender:Product ID12D1:1436. In the Syslog and DMESG log on the Desktop Edition, I see a message that usb-modeswitch switch to 12D1:1436. The USB Modem Works correctly and I can get on the Internet etc..

On Ubuntu Server 10.04 I connect the Same Device and in the Syslog I see usb-modeswitch switched to 12D1:140C

I am assuming that the first one if correct as the Mobile 3G is working and that on the File Server edition the 140C is referring to the Storage Part of the Modem Device. 

What commands can I issue to check which ID is correct and on the 12.04 where can I find the usb_modeswitch information that is telling it to presumably switch from 140C to 1436

Rgds
Chris

---

