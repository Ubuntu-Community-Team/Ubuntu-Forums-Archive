---
title: "wpa_gui"
date: 2007-01-27
forum: Networking &amp; Wireless
---

### Post by mrrellim on 2007-01-27
when I type wpa_gui into the terminal I get the following message:
"Could not get status from wpa_supplicant."

Thanks for any suggestions

Mitch

---

### Post by francisco_athens on 2007-02-04
wpa_supplicant needs to be running (usually as a daemon) for wpa_gui to work properly.

first make sure your wireless driver is loaded with:

iwconfig

that should show a device with some kind of configuration.  If you dont have any wireless devices showing up at this point you will probably need to use ndiswrapper (which is also supported by wpa_supplicant.

if you do have a wireless device listed with iwconfig, see this howto on wpa_supplicant:

[http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136)

note: you may want to make sure networkmanager is not installed as setting up wpa_supplicant yourself will conflict.  

Personally I don't think networkmanager is quite ready for primetime as there are still some types of networks (at colleges and businesses) that it cant handle (phase 2 authentication for PAP for example) yet... while setting up wpa_supplicant yourself, you can login to just about anywhere you are authorized to connect.  

good luck!

---

