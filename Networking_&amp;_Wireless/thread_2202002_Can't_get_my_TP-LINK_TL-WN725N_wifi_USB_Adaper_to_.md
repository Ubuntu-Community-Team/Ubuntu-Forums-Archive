---
title: "Can't get my TP-LINK TL-WN725N wifi USB Adaper to work"
date: 2014-01-26
forum: Networking &amp; Wireless
---

### Post by londonryan on 2014-01-26
Hi everyone,

I'm not too familiar with Ubuntu but I can usually get most things working.  I have installed Ubuntu 13.10 on my computer and I can't get my USB Wifi dongle to work.  I've gone through the forums and used nsdiswrapper to install a netrtwlanu driver for it, but my computer won't even recognize the adapter. 

In nsdiswrapper, after I installed the driver, it says "Hardware present: Yes", but I don't see it on the network info at the top right of the OS.  I can see the device using "lsusb", it shows "Bus 001 Device 002: ID 0bda:8179 Realtek Semiconductor Corp.".  So the computer knows it's plugged in, I just don't know why it's not recognizing it since I installed the driver.

Is there something I'm missing?  If there's any guidance someone could provide me with, I'm not very experienced using terminal so a thorough explaination would be appreaciated :)

Thanks,


Ryan

---

### Post by londonryan on 2014-01-27
I found [this download]("http://h-node.org/wifi/view/en/1277/TP-LINK-TL-WN725N-v2--Realtek-RTL8188EUS-/1/1/undef/undef/undef/undef/undef/tl-wn725n"), but it's a .bin file and I don't know how to configure it.

---

### Post by chili555 on 2014-01-27
> **londonryan said:**
> I found [this download]("http://h-node.org/wifi/view/en/1277/TP-LINK-TL-WN725N-v2--Realtek-RTL8188EUS-/1/1/undef/undef/undef/undef/undef/tl-wn725n"), but it's a .bin file and I don't know how to configure it.I know what to do with it; don't download unknown stuff from, at least to me, unknown places. Sometimes, when you shake hands with a stranger, you get the flu.> Bus 001 Device 002: ID 0bda:8179 Realtek Semiconductor Corp.Please see my answer here: [http://askubuntu.com/questions/377470/tp-link-wn725n-unable-to-get-drivers-to-work-with-13-04-after-upgrade-worked-o](http://askubuntu.com/questions/377470/tp-link-wn725n-unable-to-get-drivers-to-work-with-13-04-after-upgrade-worked-o)

I believe the required firmware is installed by default.

I suggest you remove the ndiswrapper install:```
sudo ndiswrapper -e <whatever>
```...where <whatever> is the name of the file you find from:```
ndiswrapper -l
```

---

### Post by londonryan on 2014-01-27
Thank you very much!  It worked perfectly!  I removed the ndiswrapper install, then followed your instructions and wireless now works perfect :)

Thanks again,


Ryan

---

### Post by chili555 on 2014-01-27
Glad to hear it's working. You have compiled the driver for your current running kernel only. When Update Manager offers a newer kernel, also known as linux-image, after you reboot, recompile:```
cd ~/rtl8188eu-master
make clean
make
sudo make install
sudo modprobe 8188eu
```Please retain these instructions and the file for that time.

---

### Post by londonryan on 2014-01-27
Thank you, I will do that. 

I found out that it didn't work on a reboot, and that's becauuse the module is only loaded into the kernel temporarily.  After a quick Google search, I found that if I put the name of the driver in the /etc/modules file, it allows the system recognize the wifi adapter every time the system starts up.  I'm begginning to really love Ubuntu :)  It seems to work a lot better than it has in the past, or maybe it's that I'm learning more as I use it more often.  Either way, it's exciting to solve problems.

---

