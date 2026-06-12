---
title: "Which WiFi dongle should I buy for 5.x kernels?"
date: 2020-05-14
forum: Networking &amp; Wireless
---

### Post by Agnishom_Chattopadhyay on 2020-05-14
I know this has been asked several times on this forum. However, it seems that all the answers I can find only advertise that they work up to some kernel version 4.x. I am not sure whether they run on 5.x

I am specifically running 5.3.0-51-generic with Ubuntu 18.04. I am willing to compile drivers, etc if necessary.

I had previously used [this]("https://www.amazon.com/gp/product/B07XXQTW27/ref=ppx_od_dt_b_asin_title_s00?ie=UTF8&psc=1") and it worked fine after I downloaded and installed the driver from their website. However, this seems to be currently unavailable on Amazon.

---

### Post by Agnishom_Chattopadhyay on 2020-06-10
[https://www.amazon.com/gp/product/B002SZEOLG/ref=ppx_yo_dt_b_asin_title_o04_s00?ie=UTF8&psc=1](https://www.amazon.com/gp/product/B002SZEOLG/ref=ppx_yo_dt_b_asin_title_o04_s00?ie=UTF8&psc=1) Works absolutely fine out of the box.

---

### Post by morrownr on 2020-06-11
The USB Wifi adapter referenced in msg #2 is the TP-Link TL-WN722N. I have a TL-WN722N. I have had it for over 5 years and it indeed does work well with current kernels. I have read that recently produced versions of the TL-WN722N have changed chipsets. The version I have has the Atheros AR 9271 chipset which is well supported. TP-Link has a habit of changing chipsets without changing the name and model number of their products. Use caution when buying TP-Link products.

Since the OP did not mention what his/her use case was, it can be hard to suggest solutions. I make heavy use of USB Wifi adapters and will suggest this device:

[Alfa Long-Range Dual-Band AC1200 Wireless USB 3.0 Wi-Fi Adapter]("https://smile.amazon.com/dp/B00VEEBOPG/?coliid=IGIXNAPRDRYXL&colid=8U2PX153MLY4&psc=1&ref_=lv_ov_lig_dp_it")

This device has been in use here for some time. It runs cool and is fast and perfectly stable.  It is based on the Realtek Semiconductor Corp. RTL8812AU chipset.

The driver I use is located here: [https://github.com/aircrack-ng/rtl8812au](https://github.com/aircrack-ng/rtl8812au)

The default driver at this site is v5.6.4.2. I use v5.7.0. The easiest way to use this driver is to install DKMS and follow the installation instructions on the driver site.

---

### Post by SeijiSensei on 2020-06-12
The Driver Manager now compiles and installs the driver for the RTL8812AU chipset.  I have an older Archer T4U.  If I plug it into a machine running 20.04 and run System Settings > Driver Manager, it recognizes the device and offers to build the driver from the source code.  I don't know if that same facility exists in 18.04.

These days I prefer the small dongles for laptops like this Edimax device: [https://www.amazon.com/Edimax-EW-7811Un-150Mbps-Raspberry-Supports/dp/B003MTTJOY/](https://www.amazon.com/Edimax-EW-7811Un-150Mbps-Raspberry-Supports/dp/B003MTTJOY/).  It has a surprisingly long range for such a small device.  I also have a TP-Link TL-WN722N, which works well, but is much too obtrusive on a laptop.  I used it to provide networking to a standalone desktop computer attached to my TV.

---

### Post by captainquack2 on 2020-06-30
I'm in the same boat. we're running a very old WIFI dongle on current Ubuntu Studio version and would like to get her up to 5g. I tried to with a archer t4u and spent 6 hours pulling my hair out. I just coldn't figure out how to install the driver. I am not much of a linux user. I can install it and do a few command line things but that is all. she's running 5.4.3-37-lowlatancy kernal. everything seems to be just for 4+ kernels. I can barely compile. github is a mystery. is there anything that is just plug it in and have it picked up and work?

Captain Quack.

---

### Post by kurt18947 on 2020-07-01
> **captainquack2 said:**
> I'm in the same boat. we're running a very old WIFI dongle on current Ubuntu Studio version and would like to get her up to 5g. I tried to with a archer t4u and spent 6 hours pulling my hair out. I just coldn't figure out how to install the driver. I am not much of a linux user. I can install it and do a few command line things but that is all. she's running 5.4.3-37-lowlatancy kernal. everything seems to be just for 4+ kernels. I can barely compile. github is a mystery. is there anything that is just plug it in and have it picked up and work?

Captain Quack.

Did you try what SeijiSensei suggested? Plug the device in and go to additional drivers? Don't make things more complicated than they need to be.

---

### Post by Agnishom_Chattopadhyay on 2020-07-20
I recently bought t[his device]("https://www.amazon.com/gp/product/B07XXQTW27/ref=ppx_yo_dt_b_asin_title_o03_s00?ie=UTF8&psc=1") and it works great on Ubuntu 20.04 with kernel 5.4. I had to install the drivers from their website, but it works fine otherwise. I bought this one because the last one I was using did not support 5 GHz networks

---

