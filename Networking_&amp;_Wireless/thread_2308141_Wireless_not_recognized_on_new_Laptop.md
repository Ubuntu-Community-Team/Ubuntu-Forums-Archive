---
title: "Wireless not recognized on new Laptop"
date: 2015-12-31
forum: Networking &amp; Wireless
---

### Post by garyed on 2015-12-31
I just bought a new laptop Toshiba Satellite model: C55T-C5300 & booted from an Ubuntu 14.0.3 live usb drive. Ubuntu doesn't seem to recognize the wifi at all. It came pre-installed with Windows 10 & the wireless works fine in Windows. It's been a while since I've messed with a laptop so I'm not sure of my next step. Any help appreciated.

---

### Post by slickymaster on 2015-12-31
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by garyed on 2015-12-31
Sorry about posting in the wrong forum, one thing I failed to mention is I want to get the wireless working from a live usb before I install Ubuntu. This way I can take the laptop back if I can't get the wireless working in Linux. The laptop is hooked up wired to the internet now so i can download what i need.

---

### Post by slickymaster on 2015-12-31
Please download and run the [wireless info script]("https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info"), which will gather information to help diagnose your system. It will create the file "wireless-info.txt" at the location it is run from, and depending on its size, an additional archive called "wireless-info.tar.gz", for attaching on the forums.

---

### Post by garyed on 2015-12-31
Thanks for the ideas,

I found this page & it explained everything perfectly.   [http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers)  
The commands all worked booting from a live usb stick & got my wireless up & running. I then figured it was safe to install Ubuntu & then reissued the commands so thedrivers are now loaded on the HD permanently. It's simple once someone else figures it out but I don't think i could have figured this one out myself.

---

