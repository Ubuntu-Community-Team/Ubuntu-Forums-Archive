---
title: "usb wireless"
date: 2005-07-15
forum: Networking &amp; Wireless
---

### Post by clumsy1007 on 2005-07-15
Hi,

I'm running Ubuntu 5.04 and I have a Zonet WLAN USB Dongle with a model number ZEW2000PF. My maching dual boots in Windows XP Professional Service Pack 2, with which the wireless adapter works fine (I'm using it right now to write this post).

I installed ndiswrapper and used the netvusbr.inf driver from the cd that came with the wireless adapter and tried "sudo ndiswrapper -i netvusbr.inf" but it said the driver installation failed.

I read another post that tried a magical python script "ndiswrapper_wrapper.py" which i ran using "sudo ./ndiswrapper_wrapper.py" and it launched a window asking me to put in the Ubuntu cd and press return, but whenever I pressed return it just opened the cd drive again.

My router, which I will reiterate works in Windows, does not use any form of encryption, so that shouldn't be an issue. When plugged in using either operating system, both the "power" and "link" LEDs on the adapter are on.

I can't think of much more info that would be relevant to this post, but let me know if I left something out. Thanks so much for your anticipated help!

---

### Post by clumsy1007 on 2005-07-16
Well since this doesn't seem to strike any ideas anyone, let me update you on my progress. I removed ndiswrapper and deleted all the contents of the associated folders per the other threads on wireless networking. I downloaded the bcmwl5.sys and bcmwl5.inf and installed them successfullly, "ndiswrapper -l" lists a successfully installed driver. the problem is getting the hardware to be recognized. it is plugged in and both the power and link leds are on, and it is listed as a wireless adapter in the device manager. however, after doing "sudo modprobe" i check the networking window and all it lists are ethernet and dial up.

what do i have to do to get it to recognize my usb wireless ethernet adapter? i already have the driver installed!

---

### Post by Nequeo on 2005-07-16
[QUOTE=clumsy1007]Well since this doesn't seem to strike any ideas anyone, let me update you on my progress. I removed ndiswrapper and deleted all the contents of the associated folders per the other threads on wireless networking. I downloaded the bcmwl5.sys and bcmwl5.inf and installed them successfullly, "ndiswrapper -l" lists a successfully installed driver. the problem is getting the hardware to be recognized. it is plugged in and both the power and link leds are on, and it is listed as a wireless adapter in the device manager. however, after doing "sudo modprobe" i check the networking window and all it lists are ethernet and dial up.

what do i have to do to get it to recognize my usb wireless ethernet adapter? i already have the driver installed![/QUOTE]
 Heya,

I'm sorry my script didn't work for you... But if it's any consolation the script just runs automatically through the steps you've already taken by hand. So you would have ended up with the same error reguardless.

Can I ask, when you type 'ndiswrapper -l' - does it say 'Hardware present'? Because if it doesn't, then those drivers will not work for your dongle. 

Meanwhile... You say the device manager lists the wireless device before you do a 'sudo modprobe'. In that case, can you see it when you type 'iwconfig'? If so, what is the device name? (e.g. wlan0 or similar).

Cheers,

---

### Post by clumsy1007 on 2005-07-16
When I type 'ndiswrapper -l' - it doesn't say "hardware present" - it just says driver installed. If this driver won't work, what driver will work?

iwconfig says no wireless extensions are installed. it doesn't list wlan0 as one of them, its just eth0, lo and something else (ppp maybe?). wlan0 isnt listed in the networking window under system administration, either.

so if device manager can detect the wireless card in the usb port, how do i get the networking window to?

---

### Post by Third Thoughts on 2005-07-22
Maybe you should just ditch ndiswrapper and try the linux-wlan-ng tools. They are available here. [www.linux-wlan.org](www.linux-wlan.org). I checked out the hardware compatibility list and it doesn't have your specific adapter but it has the Zonet ZEW1000P, so maybe they're similar enough. I'm not really familar with Zonet so I can't say. I use a Microsoft wireless usb adapter and I have no trouble getting it to work linux-wlan-ng. It does require some compiling from source, but I nothing too difficult. If you need more help just ask.

~Andrew S.

---

