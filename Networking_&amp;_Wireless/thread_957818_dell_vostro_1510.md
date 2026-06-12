---
title: "dell vostro 1510"
date: 2008-10-24
forum: Networking &amp; Wireless
---

### Post by m_pourfathi on 2008-10-24
Hi all,

I have a dell vostro 1510 laptop. my wireless adapter is broadcom. 
I used the following command to install the wireless driver.

sudo apt-get install wl

it downloaded about 18 Mbytes of data but my wlan adapter's light is still off and it doesn't work. What should I do know?

regards

---

### Post by Ayuthia on 2008-10-24
Please try going to System->Administration->Hardware Drivers and enable the Broadcom STA (wl) driver.  It might be helpful if you can get the system up to date also because I am thinking that the driver works better in the more recent kernel.

---

### Post by iwc5893 on 2008-10-24
You may want to try the instructions in this thread, as it has worked for my 1510.  You will have to use the Dell driver that comes with your computer, instead of the one listed in the instructions.

[http://ubuntuforums.org/showthread.php?t=760568](http://ubuntuforums.org/showthread.php?t=760568)

and below is my post where I listed the driver.

> **iwc5893 said:**
> I was able to get the wifi adapter on my Dell Vostro 1510 working using this procedure, but I had to use the drivers that were in my C:/drivers/network/R189335 directory.

---

