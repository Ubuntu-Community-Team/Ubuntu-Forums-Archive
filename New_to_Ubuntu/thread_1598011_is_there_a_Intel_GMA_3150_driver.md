---
title: "is there a Intel GMA 3150 driver?"
date: 2010-10-16
forum: New to Ubuntu
---

### Post by opendevlite on 2010-10-16
is there a driver for this or it doesnt exist yet?

---

### Post by jtarin on 2010-10-16
I found [this]("http://linux-tipps.blogspot.com/2010/06/setting-up-vaapi-hardware-accelerated.html") to be the closest to work as of yet.....if someone has something more up-to-date they should post.
Check the links and postings in that article and do a search on the poulsbo driver.
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/"]Read this in its entirety.](")

I won't dissaude you from using this driver....just know that it takes some work to get running. There are alternatives on that last link.

---

### Post by opendevlite on 2010-10-16
i think its for GMA 500

maybe the integrated graphics driver is already installed, when i open Sysinfo, Hardware>Graphics Card it says, 

VGA compatible controller
  Intel corporation N10 Family Integrated Graphics controller
  Subsystem: Acer Incorporated [ALI] device 0349

---

### Post by jtarin on 2010-10-16
In your terminal issue the comand ```
lsmod
``` and post the results. Then the command ```
lspci
``` and post the results.

---

### Post by jtarin on 2010-10-16
[Some info on Intel Graphics]("http://en.wikipedia.org/wiki/Intel_GMA") with chipsets listed. You want to find a driver for your chipset. We can find this information from the command I gave you "lspci".

---

### Post by opendevlite on 2010-10-31
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)


the code above is with lspci

---

### Post by opendevlite on 2011-03-08
bump

---

