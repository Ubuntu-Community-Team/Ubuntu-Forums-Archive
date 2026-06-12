---
title: "Wireless randomly disconnects"
date: 2007-11-11
forum: Networking &amp; Wireless
---

### Post by c_j on 2007-11-11
hi, im fairly new to linux, i managed to install ubuntu 7.10, dual booted with windows XP.

wireless worked straight away, but i have a few problems with it.
the main problem happens at random times, it might happen as soon as i connect to the network or after a whole day of using it. if im browsing the net, firefox just says its looking up the page, but it doesnt go further than that, then after a minute or so, the network manager displays 0% signal, then a bit later it will disconnect and try to reconnect again, which is usually unsuccessfull. i have to disable networking, unplug my wireless adapter, put it back in again then enable networking.

i dont really know where to start to fix this, does anyone have any solutions/ideas/links?

thanks

Chris

p.s. now im using ubuntu, i hate using windows :) although im stuck with it because i use need certain windows software.

EDIT:

when wireless is working, i get between 74 and 78% signal. in windows its always on "very good". so i dont think the 0% signal is because there is no signal.
also, im using a belkin 54g wireless usb adapter. i dont know how to find out any more information

---

### Post by CanofAltoids on 2007-11-11
I'm having almost the exact same problem, except my wireless adapter is a Realtek RTL8187.  Pretty sure the signal strength isn't an issue; Windows usually shows it as "Very Good" for me as well.  When I boot from the LiveCD, it simply asks me for my WEP key, connects, and stays that way.  So I'm thinking another program that I've installed in Gutsy is interfering with it somehow, but I'm really not sure.  Any help on this problem would be greatly appreciated... this is the only thing keeping me from never needing Windows again.

---

### Post by anansesem on 2007-11-11
are you using the ndiswrapper driver?  That was happening to me but when I switched to teh ndiswrapper driver, it seems to be working ok now.

---

### Post by CanofAltoids on 2007-11-11
Wow, now I AM using the ndiswrapper driver and it's working fine!  (so far...)

I installed it by following this beautiful guide:
[http://ubuntuforums.org/showthread.php?t=493958](http://ubuntuforums.org/showthread.php?t=493958)

Hope that helps any others with this problem.
Thanks.

---

### Post by c_j on 2007-11-12
although that article isnt for my adapter/driver should i try using ndiswrapper?

---

### Post by phillywize on 2007-11-15
> **CanofAltoids said:**
> I'm having almost the exact same problem, except my wireless adapter is a Realtek RTL8187.  Pretty sure the signal strength isn't an issue; Windows usually shows it as "Very Good" for me as well.  When I boot from the LiveCD, it simply asks me for my WEP key, connects, and stays that way.  So I'm thinking another program that I've installed in Gutsy is interfering with it somehow, but I'm really not sure.  Any help on this problem would be greatly appreciated... this is the only thing keeping me from never needing Windows again.

I don't know what adapter I have, but I use the RTL8187 driver -- I have an Asus M2N32 SLI Deluxe MoBo that comes with onboard Wifi.  I suspect it's the same wifi chipset.  Anyhow, it does the same thing:  randomly disconnects.  And I can't get it to reconnect for love or money.  In fact, it seems to be dead -- I get absolutely no life from the adapter (as in, no signal strength, no ap's, nothing) until I reboot.  Tried ifconfig up/down, network restart, stopping, restarting, and generally beating up on nm.  Nothing.  I would very much like to avoid using ndiswrapper, since I don't want to part with network manager.

---

