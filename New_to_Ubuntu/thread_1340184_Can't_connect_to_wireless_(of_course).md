---
title: "Can't connect to wireless (of course)"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by metallicamike on 2009-11-28
My brother's comp. is not able to connect to my wireless network. The pass is set to WPA personal. Whenever I try to connect to it the pass I entered changes into something different that is about 30 characters. Please help, my brother is getting pissed.

EDIT: He is running Jaunty.

---

### Post by Some Penguin on 2009-11-28
You've

1) read [https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo) ?
2) ensured that any MAC filtering on the router is either disabled, or configured to accept the MAC of the wireless card?
3) ensured that your router is broadcasting its SSID?  (or, you have modified wpa_supplicant.conf based on [http://ubuntuforums.org/archive/index.php/t-191016.html](http://ubuntuforums.org/archive/index.php/t-191016.html) if for some reason you want to not broadcast the SSID?)
4) ensured that the client is set to WPA-PSK, and that the TKIP vs CCMP+AES setting is the same as the router?

If you've done all that, you might have to show what the router is logging (if anything) when a connection is attempted, and what the network manager is specifying as well.

---

### Post by bkratz on 2009-11-28
> **metallicamike said:**
> My brother's comp. is not able to connect to my wireless network. The pass is set to WPA personal. Whenever I try to connect to it the pass I entered changes into something different that is about 30 characters. Please help, my brother is getting pissed.

EDIT: He is running Jaunty.



By the way, don't worry about the 30 character string you are seeing---it has just translated your passcode string to something it understands.

---

