---
title: "Unable to connect to wifi, but able to search for networks (Intel Wifi Link 100bgn)"
date: 2014-06-24
forum: Networking &amp; Wireless
---

### Post by marius5 on 2014-06-24
[COLOR=#333333][FONT=UbuntuRegular]Previously, I have used ubuntu for a short while. And I have installed 14.04 back then and everything worked perfectly. I was able to connect to all wifi hotspots, to my router as well.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Today, after removing linux distro a couple of weeks ago, I installed ubuntu 14.04 back again and now I have this weird issue:[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I am unable to connect to my routers wifi, even though nothing changed in it. All the settings are the same. I have tried to disable routers wifi security - didn't help. I have tried to set up android hotspot and was able to connect to it without any issues. Where should I even start to dig in order to fix this problem?[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]My wifi card is Intel Wifi Link 1000bgn.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Settings of my wifi network (2.4GHz): Network mode: mixed; Channel width: auto; Channel: 6; SSID broacast: enabled[/FONT][/COLOR]

---

### Post by varunendra on 2014-06-26
Welcome to the forums marius5!

Please try some tweaks in the router to optimize it for the Linux driver -

1) If the "Channel width" means 20/40 MHz auto mode, try fixing it to 20 MHz, especially if the router supports 'N' channel.
2) Try setting the channel to 1 or 11.

Reboot the router after saving the changes.

If these two changes don't help, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

