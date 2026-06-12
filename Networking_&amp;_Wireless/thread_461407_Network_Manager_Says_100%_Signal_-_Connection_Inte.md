---
title: "Network Manager Says 100% Signal - Connection Intermmitant"
date: 2007-06-01
forum: Networking &amp; Wireless
---

### Post by coldstatue on 2007-06-01
I have an Atheros AR5005G wireless card. Feisty recognized it, but it wouldn't work with ndiswrapper. I tried MadWiFi, which can handle a lot of Atheros chipsets, but no luck. I finally went for the Linux Ant Driver Loader. ( I used the free trial.) This did the trick... kind of. As long as I have all security turned off at the router, (except MAC filtering) I can connect, but it never lasts. It will work great for a few minutes, then I have no internet, or filesharing capabilities. The thing is, that network manager says I'm still connected at 100%. If I plug in the ethernet, it reconnects. Sometimes, if I reselect the wireless network, or turn the wireless off and back on with the button on the laptop, it will reconnect, but not always. I have installed the wpa supplicant, and it is working, but I don't see how that could even be an issue, because this happens with all security turned off.  

At this point, I am ready to get an Intel 2200BG on ebay, because I've read here that it just works out of the box. What would you suggest? I am pretty sick of messing with it. If you need me to post some terminal info let me know, but if you know of another mini PCI card that will literally pop in and run, please let me know I'd like to have some options for ebay. 

Thanks.

---

### Post by lukew on 2007-06-02
> **coldstatue said:**
> I have an Atheros AR5005G wireless card. Feisty recognized it, but it wouldn't work with ndiswrapper. I tried MadWiFi, which can handle a lot of Atheros chipsets, but no luck. I finally went for the Linux Ant Driver Loader. ( I used the free trial.) This did the trick... kind of. As long as I have all security turned off at the router, (except MAC filtering) I can connect, but it never lasts. It will work great for a few minutes, then I have no internet, or filesharing capabilities. The thing is, that network manager says I'm still connected at 100%. If I plug in the ethernet, it reconnects. Sometimes, if I reselect the wireless network, or turn the wireless off and back on with the button on the laptop, it will reconnect, but not always. I have installed the wpa supplicant, and it is working, but I don't see how that could even be an issue, because this happens with all security turned off.  

At this point, I am ready to get an Intel 2200BG on ebay, because I've read here that it just works out of the box. What would you suggest? I am pretty sick of messing with it. If you need me to post some terminal info let me know, but if you know of another mini PCI card that will literally pop in and run, please let me know I'd like to have some options for ebay. 

Thanks.

Might be conflicts with other devices on the same frequency. I would try changing the channel / frequency you use.

---

### Post by coldstatue on 2007-06-02
At this point, I've fiddled around so much that it won't connect at all, so I  removed Driver Loader and the WPA supplicant for a fresh start. I will reinstall tomorrow. If it doesn't work, then I'm swapping out the wireless card. i Have a new one on the way.  I will post my results with some specifics about the old card for anyone else who might need it.

I'm on a new frequency now, so hopefully that will do the trick.

Thank you.

---

### Post by coldstatue on 2007-06-05
holy cow. I set my ap to limit the number of DHCP clients to 2. . It needed to be 3. feel free to point and laugh.

---

