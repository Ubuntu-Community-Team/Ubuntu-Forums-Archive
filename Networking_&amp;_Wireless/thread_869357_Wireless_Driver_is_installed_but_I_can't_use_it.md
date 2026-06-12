---
title: "Wireless Driver is installed but I can't use it?"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by Xikkub on 2008-07-24
I finally got ndiswrapper installed and working properly. I used the "ndiswrapper -i driver.inf" command to install the Windows98 driver for my TrendNet Wireless Usb Adapter (TEW-424UB firmw-3.1). When I use "ndiswrapper -l" to list the drivers, I see...

sis163u :driver installed

However, I have not been able to get Ubuntu (8.04) to recognize the actual hardware. iwconfig only gives me my lo (loopback) and eth0 (PCI Ethernet Card for Wired-Lan). I don't see wifi0 or wlan0 or anything related to that.

When running an lsusb, the USB Adapter shows up as...

0dba:8189 Realtek Semiconductor Corp.

Why can't I use my Wireless USB Adapter? When I go to System -> Administration -> Hardware Drivers Ubuntu tells me that there no proprietary  drivers are in use, and nothing appears in the component list.

I think I'm missing something simple. Thanks, and I am glad to finally join a Linux forum!

---

### Post by ModelM on 2008-07-24
Your command:

ndiswrapper -i driver.inf

is correct & links the Windows driver to ndiswrapper. The next step is to load ndiswrapper like you would a module, like this:

sudo modprobe ndiswrapper

---

### Post by ModelM on 2008-07-24
I just noticed the response to ndiswrapper -l:

sis163u :driver installed

In my machine the words "hardware present" are included also. It's possible this driver won't work for you. Some folks have had to try different drivers from windows 'till they found one which worked. You might try a driver for XP instead of '98.

---

### Post by Xikkub on 2008-07-24
> **ModelM said:**
> 
sudo modprobe ndiswrapper

I'm sorry, I neglected to say that I have already modprobe'd it and dumprep -a'd it. I think that's all I've done so far (I'm writing down my steps to keep as a reference) so if you could provide a few more steps then that could get me in the right direction.

I have quite a few drivers that I can try out and I will. I had to install ndiswrapper with .deb packages instead of compiling it myself. The make and make install commands were giving me errors. (FYI). But ndiswrapper installed correctly anyway.

Also, do you know WHY some drivers for certain versions of windows work and some drivers don't? Is there a certain OS (ME, 98, XP etc) that Ubuntu driver installation gravitates to? I've heard that XP/2000 drivers work best.

Thanks! You sure do know what you're doing!

---

### Post by ModelM on 2008-07-24
I also have read that the XP drivers work best. I don't have a lot of experience with ndiswrapper because it simply worked for me. I installed ndiswrapper from the repositories, installed the Win XP driver for my wireless card, and I was finished. I didn't even need to reboot.

So I'm not skilled at troubleshooting it, because I've never had to.

---

### Post by Xikkub on 2008-07-27
Okay, I tried all of the drivers I have. My chipset is 0bda:8189 (Realtek) but nothing I download works. I looked here

[http://linux-wless.passys.nl/query_part.php?brandname=TRENDware](http://linux-wless.passys.nl/query_part.php?brandname=TRENDware)

but it says that my adapter isn't supported, even though I'm sure people have gotten it to work. I am clueless and very tired. I don't want to buy another adapter because I bought this one because it was a good deal. I've also looked into the zd1211 drivers but I can't "make" then when I try to compile it.

SOLVED~! I downloaded the RTL8187B drivers (RTL8187B_5_6.1135.0625.2008_Silent_Install.zip) and now the hardware is present! I just need to set up the network so that I can USE it now.

---

