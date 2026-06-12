---
title: "I fooled network Manager to higher speed"
date: 2006-10-25
forum: Networking &amp; Wireless
---

### Post by joergenlie on 2006-10-25
I've had problems with network manager. When i use ndiswrapper I can't use network manager, I see the networks, but can't connect. When I use bcm43xx-fwcutter I get connection but nothing more than 11Mb/s. I doesn't help to change the rate. Then I found this:

i booted into ubuntu using the bcm43xx with fwcutter. This makes NM work, but only with the rate 11M.This is what nm says too, driver: bcm43xx Rate 11Mb/s. My interfaces file are commented out. then I did a rmmod bcm43xx and the internet connection went down. I did a modprobe ndiswrapper and connected to my network again through network manager. Bang! now I get connected at 54 Mb/s. NM says the driver is still bcm43xx though.

Have I fooled nm? Of course when i reboot with ndiswrapper I can't get nm to connect at all.

This tells me that it has to be possible to get nm to work at full speed. The question is how?

I tried to make a script, without luck, maybe I'm doing it wrong. Is it possible? Network manager are, in my opinion the finest wireless app out there. It would be nice to get it to work right at boot. I'm still working as h.... to try to figure it out and I have found out alot, but help would be appreciated.

Does anyone understand this?

Jørgen

---

