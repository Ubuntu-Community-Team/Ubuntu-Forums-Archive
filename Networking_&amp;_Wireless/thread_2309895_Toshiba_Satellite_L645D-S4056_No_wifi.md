---
title: "Toshiba Satellite L645D-S4056 No wifi"
date: 2016-01-14
forum: Networking &amp; Wireless
---

### Post by Redalien0304 on 2016-01-14
Have a Toshiba Satellite L645D-S4056 with Ubuntu 14.04 & Win 10 with Wifi was Working. Wifi Stopped working on Ubuntu 14.04 & Win 10. I did install Kernel 4.4 Installed on Ubuntu 14.04 Wifi did not work after install So i removed Kernel 4.4 from laptop via Synaptic. Now still no more wifi. Still Have kernel 4.2, 4.1.3,4.1.0, & 3.16 kernel line. Still no Wifi on Ubuntu 14.04 & Win 10. Have searched all over for a Solution? The Fn F8 does not Appear to work? Fn F8 is hardware switch for wifi turn on/off. Possibly a Hardware Problem with Wifi? Lan Ethernet still works, The Two Wifi Usb Dongles i have do not work on this Laptop. They do Work on my other Laptops with Ubuntu. Also Pulled Hdd out & swapped Hdd out & installed Ubuntu 16.04 daily Still no Wifi? 
Thanks in Advance for any help.

---

### Post by slickymaster on 2016-01-14
*Moved to the ***[COLOR=#000000]Networking & Wireless[/COLOR]*** sub-forum*

Please download and run the [wireless info script]("https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info"), which will gather information to help diagnose your system. It will create the file "wireless-info.txt" at the location it is run from, and depending on its size, an additional archive called "wireless-info.tar.gz", for attaching on the forums.

---

### Post by Redalien0304 on 2016-01-14
Ok Downloaded & ran wireless info script. Results are here at pastebin[URL="http://pastebin.com/4kWVJthY"]
http://pastebin.com/4kWVJthY[/URL]

---

### Post by Redalien0304 on 2016-01-14
Bump Anyone??

---

### Post by jeremy31 on 2016-01-15
It has a hard block on wifi and since I can't find anything about a switch on your model for wifi, please try this

Shutdown your computer, remove power cord and battery, then hold the power button for 20 seconds.

Reconnect battery and power cord then boot it up, then check ```
rfkill list all
```

---

### Post by Redalien0304 on 2016-01-15
Found Solution Booted to Win 7 & did Fn F8. Fn key combo worked here. Also worked there after in Ubuntu 14.04. So solved. Thanks

---

