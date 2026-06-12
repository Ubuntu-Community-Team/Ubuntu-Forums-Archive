---
title: "what is the different between master mode and AP mode and how to set?"
date: 2014-01-22
forum: Networking &amp; Wireless
---

### Post by ryan43 on 2014-01-22
Hello, I am using ubuntu 12.04 now, and I tried to build a wifi hotspot, but I failed. I found that I should set the wireless card into master mode.
I used the command: iw list, below supported interface modes, I cannot find master, only AP and AP/VLAN, then I found:
 If there is 'AP' in the list of "Supported interface modes" your device will support the Access Point mode with hostapd.

So I think I can build hotspot, but when I used the command: sudo iwconfig wlan0 mode master, it shows:
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.

then I tried sudo iwconfig wlan0 mode AP, I shows:
Error for wireless request "Set Mode" (8B06) :
    invalid argument "AP".

So what can I do for build a hotspot? Thank you very much

---

### Post by ian-weisser on 2014-01-22
Master mode isn't supported on your wifi device.
So using iwconfig to change to (unsupported) master mode *should* fail.

Changing to AP may have failed due to a mere typo.

---

