---
title: "Centrino Wireless-N 2230 slow connection in Ubuntu, in Windows 8 OK"
date: 2014-07-05
forum: Networking &amp; Wireless
---

### Post by albertredneck on 2014-07-05
Hi,

I'm getting 4-5 Mbs at [http://www.speedtest.net/](http://www.speedtest.net/), while in Windows 8 I get around 20-30 Mbs, with some dropdowns to 0 Mbs or even disconections.

I had the same problems with 13.10, but after the 14.04 release I clean installed it and the problems have showed up again. I've tried several solutions (disable IPv6, sudo modprobe iwlwifi 11n_disable=1) but none worked. I'm pretty sure some of these solutions worked in 13.10.

Here is my wifi info:
[ATTACH]254494[/ATTACH]

Any help will be highly appreciated, sice I'm a bit desperate on this :( almost two months with no solution

---

### Post by varunendra on 2014-07-06
Welcome to the forums Albert!

In your router/access-point, please change the encryption type to pure WPA2-PSK with AES (CCMP). Currently it is set to WPA/WPA2 mixed mode with TKIP. Also try changing the channel from 9 to 1 or 11. Reboot the router after saving the changes.

If this doesn't improve the speed, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222) Note that it is a significantly different script, providing much more details which may be helpful for further tweaking.

---

### Post by albertredneck on 2014-07-06
It worked, thank you! You saved me :')

So, I lived more than 1 year with an underperforming wifi configuration...

Thank you again!

Ps: I wonder if should I leave the 11n_disable=1 line or remove it...

---

### Post by varunendra on 2014-07-06
You're welcome! :)
> **albertredneck said:**
> Ps: I wonder if should I leave the 11n_disable=1 line or remove it...

I think you should try the connection quality without it. It is a compromise with 'N' channel capability, means you won't be able to get speeds higher than 54 Mbps with that parameter. Of course the router/AP also should be 'N' channel capable to be able to deliver higher speeds.

If removing that parameter seems to cause trouble, you can always redo it. But if the connection remains solid, you'll get the additional advantage of 'N' channel capability, wherever available.

---

