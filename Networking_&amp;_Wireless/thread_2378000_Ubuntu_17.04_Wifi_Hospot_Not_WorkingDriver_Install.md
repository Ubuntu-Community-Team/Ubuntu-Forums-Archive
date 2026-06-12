---
title: "Ubuntu 17.04 Wifi Hospot Not Working/Driver Installation."
date: 2017-11-18
forum: Networking &amp; Wireless
---

### Post by !!?? on 2017-11-18
Hello, I've been trying to create a Wifi Hotspot from my Thinkpad T410 which has an [Intel Centrino Advanced-N 6200]("https://downloadcenter.intel.com/product/59470/Intel-Centrino-Advanced-N-6200-Dual-Band") network adapter. 

I first tried the method described here, 

[https://askubuntu.com/questions/762846/how-to-create-wifi-hotspot-in-ubuntu-16-04-since-ap-hotspot-is-no-longer-working](https://askubuntu.com/questions/762846/how-to-create-wifi-hotspot-in-ubuntu-16-04-since-ap-hotspot-is-no-longer-working)

When I follow the steps exactly as instructed, I get an error, 

[I]"[COLOR=#111111][FONT=Ubuntu]Failed to activate connection: (2) Connection ' [Network Name]' is not available on the device wlp3s0 at this time."

[/FONT][/COLOR][/I][FONT=Ubuntu, Arial, libra sans, sans-serif][COLOR=#111111]I've also tried going into Network, and selecting "Use as Hotpot", but the hotspot is created for a second and then disappears. My devices can't recognize it. [/COLOR][/FONT]

[FONT=Ubuntu, Arial, libra sans, sans-serif][COLOR=#111111]After browsing the web somebody mentioned to somebody else with the same problem that it might be a driver problem and to install the most recent proprietary drivers.

So then I looked to install new drivers through the website below. 

[/COLOR][/FONT]https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi

I followed the instructions, but it seems all I did was install the firmware. It says, "[COLOR=#333333][FONT=Arial]You can now load the driver."

[/FONT][/COLOR]How exactly? Nothing really changed, and when I go into "Software and Devices" -> "Additional Drivers" there are no new proprietary drivers to use. What is the next step here? All I want to do is create a wireless hotspot from my usb tethered wired connection. 

As the title says, I am using Ubuntu 17.04.

Thank you beforehand!

---

### Post by litlesam on 2017-11-18
Hi, I came across this [thread]("https://forums.linuxmint.com/viewtopic.php?f=53&t=257005") over at Mint and tried it with no problems. :)

---

### Post by mörgæs on 2017-11-19
17.04 is about to run out of support and there is no point in troubleshooting it. 

I suggest that you begin with a fresh install of 17.10 using wired internet access. When that works we can take a look at the wifi problems if they also appear in 17.10.

---

