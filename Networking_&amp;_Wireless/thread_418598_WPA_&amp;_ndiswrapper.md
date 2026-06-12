---
title: "WPA &amp; ndiswrapper"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by jarrett on 2007-04-22
Hi,

I have a problem connecting to my wireless lan which uses WPA encryption.
When i used the native bcm43xx it worked fine, though it was slow (11mbps).That's why i wanted the ndiswrapper one, which supposedly supported better speed.
I can connect fine to my neighbours access point which does not use any encryption, it's open to all. 
When I try to connect to my own wlan with (k)networkmanager it just says "Configuring the device" or "Configuring IP" and just twirls for a while (20 sec) and then just stops.
And... It's the same with all encryptions I've tried (WEP, WPA, WPA2).

What could be the problem? I would not want to go back to the open source bcm43xx driver because uploading stuff to my server is a pain with 11mbps connection.

btw, I use Kubuntu 7.04.

Thanks for the time!

---

### Post by mabelrxu on 2007-04-22
hm ... u could try using wext instead of ndiswrapper, i've heard that's supposed to work (why? i have no idea) ... here's a guide that doesn't use ndiswrapper at all ... maybe this is what you're looking for ... or not? [http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

---

### Post by jarrett on 2007-04-23
Hi, I got it working by compiling the latest source of ndiswrapper (1.42).
Works fine with WPA now :)

Cheers!

---

