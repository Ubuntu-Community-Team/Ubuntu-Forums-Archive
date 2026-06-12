---
title: "UNR on Acer Aspire One D250: WiFi Problem!"
date: 2009-08-13
forum: New to Ubuntu
---

### Post by ramoj02 on 2009-08-13
I have UNR 9.04 (Jaunty) on my Acer Aspire One D250. I'm using the ath5k driver for WiFi and I noticed that the WiFi led isn't working. So, I looked online how do I fix it, luckily, I fixed it by installing the madwifi driver. The led worked but the WiFi signal is dropping when I'm using madwifi driver. When I'm using the ath5k driver, I'm getting good signal but no WiFi led. When I'm using madwifi driver, I'm getting WEAK signal but the WiFi led works.

I want to get GOOD WiFi signal with the working WiFi led.

Thanks in advance!

---

### Post by LewRockwell on 2009-08-13
I'm using the "regular" Ubuntu 9.04 Jaunty Jackalope on my triple-boot Acer Aspire One AOA-150-1864 and everything, including the led, works just fine with the regular install

It has the Dell 1390 WLAN Mini-card for wifi(broadcom chipset)

[http://ubuntuforums.org/showthread.php?t=1222961](http://ubuntuforums.org/showthread.php?t=1222961)

.

---

### Post by ramoj02 on 2009-08-13
> **LewRockwell said:**
> I'm using the "regular" Ubuntu 9.04 Jaunty Jackalope on my triple-boot Acer Aspire One AOA-150-1864 and everything, including the led, works just fine with the regular install

It has the Dell 1390 WLAN Mini-card for wifi(broadcom chipset)

[http://ubuntuforums.org/showthread.php?t=1222961](http://ubuntuforums.org/showthread.php?t=1222961)

.

You have the D150, I think. I have the D250 and it has Acer InviLink 802.11b/g WiFi card.

---

### Post by mrothgeb on 2009-08-13
I'm having a problem very close to this, using 9.04 on an acer travelmate 4000 with the Intel 2200bg built in wireless.  I'm new to linux.  I have the newest driver and firmware downloaded but I have NO idea how to install.

---

### Post by LewRockwell on 2009-08-13
> **mrothgeb said:**
> I'm having a problem very close to this, using 9.04 on an acer travelmate 4000 with the Intel 2200bg built in wireless.  I'm new to linux.  I have the newest driver and firmware downloaded but I have NO idea how to install.

According to a post in this old thread the 2200bg has been supported by Ubuntu since 2006?

[http://ubuntuforums.org/showthread.php?t=137381](http://ubuntuforums.org/showthread.php?t=137381)

strange...

.

---

### Post by mrothgeb on 2009-08-13
> **LewRockwell said:**
> According to a post in this old thread the 2200bg has been supported by Ubuntu since 2006?

[http://ubuntuforums.org/showthread.php?t=137381](http://ubuntuforums.org/showthread.php?t=137381)

strange...

.

I'd found a post similaur to that as well.  The reason I installed Ubuntu is that this laptop had been my fathers who went to um... sites of ill repute.  Caught more virus' than a sailor, then took the box to a repair shop in the local flea market who did a real hatchet job on it and I never could get the wifi to work right with windows.

Edit:
which may actually be the problem.... maybe after the kiddo goes to sleep i'll get buzy with the screwdriver

---

### Post by LewRockwell on 2009-08-13
> **mrothgeb said:**
> I'd found a post similaur to that as well.  The reason I installed Ubuntu is that this laptop had been my fathers who went to um... sites of ill repute.  Caught more virus' than a sailor, then took the box to a repair shop in the local flea market who did a real hatchet job on it and I never could get the wifi to work right with windows.

Edit:
which may actually be the problem.... maybe after the kiddo goes to sleep i'll get buzy with the screwdriver

I think you might be on the right path with the revelation that someone else has been inside the box

Depending on how much disassembly is required for your investigating you might do some spring cleaning in there as well

.

---

### Post by mrothgeb on 2009-08-13
> **LewRockwell said:**
> I think you might be on the right path with the revelation that someone else has been inside the box

Depending on how much disassembly is required for your investigating you might do some spring cleaning in there as well

.

Interesting development: I took a moment to do a bit more troubleshooting and plugged in my linksys usb wifi.  then when i mouse over the wireless network it listed the both of them (for the first time showing the name of the Intel) but both of them said underneith 'wireless is disabled'

I am root, I've tripple checked that I have privlages to use wireless under system / admin / users and groups.


I have a very funny feeling that im missing something right under my nose.

---

### Post by LewRockwell on 2009-08-13
> **mrothgeb said:**
> Interesting development: I took a moment to do a bit more troubleshooting and plugged in my linksys usb wifi.  then when i mouse over the wireless network it listed the both of them (for the first time showing the name of the Intel) but both of them said underneith 'wireless is disabled'

I am root, I've tripple checked that I have privlages to use wireless under system / admin / users and groups.


I have a very funny feeling that im missing something right under my nose.

pull your usb wifi out...reboot...and see what happens then

I have seen systems "mysteriously" "find" a seemingly dead device

I don't have an explanation, I just know it has happened to myself and others multiple times

.

---

### Post by LewRockwell on 2009-08-13
guess we shouldn't have hijacked this thread...hehehe

.

---

### Post by mrothgeb on 2009-08-13
> **LewRockwell said:**
> guess we shouldn't have hijacked this thread...hehehe

.
lol it's not a hijack if its still closely related to the topic.

sigh.

there is a bloody button on the front edge of the computer that toggles power to the antenna.


wow.

occums razor FTW.

thanks for the replies Lew!

---

