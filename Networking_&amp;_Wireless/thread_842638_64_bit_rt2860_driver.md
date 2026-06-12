---
title: "64 bit rt2860 driver"
date: 2008-06-27
forum: Networking &amp; Wireless
---

### Post by kavermeer on 2008-06-27
Hi,

I'm trying to get my rt2860 chipset wireless card to work. I was unable to get it to work with the linux driver, so I want to try to ndiswrapper-route. However, I'm running 64 bit linux, so I need a 64 bit driver.

The driver at [http://www.ralinktech.com/ralink/Home/Support/Windows.html](http://www.ralinktech.com/ralink/Home/Support/Windows.html) includes a Win XP 64 bit driver, but I have only access to a 32 bit XP. So, if I install the driver package, I only get the 32 bit driver. Would anyone here be able to help me out by installing this on a 64 bit XP, and mailing me the installed drivers?

Best,
Koen Vermeer

---

### Post by Master Chief on 2008-06-28
What about using:

[http://www.ralinktech.com.tw/data/drivers/2008_0522_RT2860_Linux_STA_v1.6.1.0.tar.bz2](http://www.ralinktech.com.tw/data/drivers/2008_0522_RT2860_Linux_STA_v1.6.1.0.tar.bz2)

instead of a Windows driver?  You can run: ```
sudo make install
``` (after you unpacked the file) and compile the driver on your amd64 installation (amd64: that's the name yes). 

Perhaps you tried this already and ran into some make errors?

---

### Post by strongboww on 2008-08-04
ive got the same problem and actually no clue what to do, the readme included in the packed file is not really helpful cause i cant really follow the instructions what to do

anyone could post kind of a "step-by-step"?

---

### Post by scarf on 2008-11-21
did you try downloading the [_latest driver_](http://www.ralink.com.tw/Home/Support/Linux.html) (first link, not the WebUI) and following [_these instructions_](http://ubuntuforums.org/showpost.php?p=5114684&postcount=41)?  this worked for me but i'm in 32-bit, however i am only connected at 54 Mb/s....

---

