---
title: "Dlink AirPlus DWL-G630 Not working in Edgy"
date: 2006-10-31
forum: Networking &amp; Wireless
---

### Post by akamarshall on 2006-10-31
Hi everyone, 
I recently installed 6.10 Edgy on my Thinkpad X30, now after the install my D-Link DWL-G630, doesn't work. I can go into the networking settings and I see the card, and I can enable it, but when I go into the network connections all I see is lo. This card used to work in 6.06. Any help would be greatly appreciated.

Thanks

---

### Post by Ynem on 2007-04-04
yep, same problem here. When put into my x21, i see wmaster0 and wlan0. I fill in my wep pasword, but nothing happens. Can anyone give a simple, step by step procedure to solve this problem? I read a lot about ndiswrapper and max (or mad) wifi, but nothing worked.

Y

---

### Post by baidaraka on 2007-04-04
Hi,
Install networkmanager applet on your machine,
hope it will help you,

---

### Post by otual on 2007-04-12
I also have had no luck with this card. I have tried ndiswrapper, the driver seems to install fine, but the lights on the card don't come on. They flicker 1ce on startup but then nothing. 
What is this networkmanager aplet you mentioned, and what does it do????

---

### Post by otual on 2007-04-12
Just a little more info on my problem, others may want to try this too

this is a snippet from my terminal when I tried using modprobe on the wireless network connection

root@blah blah# *modprobe wlan0*
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-11-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument


Now I'm assuming this means that ndiswrapper has had problems installing/using the driver. Maybe I should remove ndiswrapper and start again.

One more relative query..... If I have the card inserted before I add ndiswrapper, and ubuntu detects the device (doesn't appear in networking selection though) how can I remove/disable the system chosen driver for wireless card?

---

