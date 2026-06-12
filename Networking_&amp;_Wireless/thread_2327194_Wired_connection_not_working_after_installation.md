---
title: "Wired connection not working after installation"
date: 2016-06-08
forum: Networking &amp; Wireless
---

### Post by scott135 on 2016-06-08
Hello friends! I am new to the world of Linux and I just installed Ubuntu 16.04 for the first time on my desktop, which was previously running Windows 10. Since the installation, I've had no internet connection. Im not really sure what to do, any advice would be greatly appreciated :)

---

### Post by Zanden on 2016-06-08
Could be a driver issue. Check the make of your Network card and search if there are drivers for the device.

---

### Post by jeremy31 on 2016-06-08
Open a terminal window and enter the following
```
lspci -nnk | grep -iA2 net
```
Post redults

---

### Post by scott135 on 2016-06-08
> **jeremy31 said:**
> Open a terminal window and enter the following
```
lspci -nnk | grep -iA2 net
```
Post redults

"03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8161/8411 PCI Express Gigabit Ethernet Controller [10e:8168] (rev 0c) 
        Subsystem: Gigabyte Technology Co., Ltd. Motherboard [1458:e000] 
        Kernel driver in use: r8169"

---

### Post by X-RED_Tech on 2016-06-08
Did it work when installing or live session?
Your card has been well supported for decades so it shouldn't be an issue. I never had an Ethernet card (except once with a brand new Atheros Killer(?)) not working in Linux unless already defective.

I'm assuming it works in Windows?

---

### Post by scott135 on 2016-06-08
Initially it was working during the installation, but now it just keeps giving me notifications that I'm getting "disconnected" from the network. 

I've never had any problems with the card on Windows, not sure why it's acting up all of a sudden.

---

### Post by X-RED_Tech on 2016-06-08
Does it work as expected in a live session? If so then it's something you did/installed/tweaked after the installation...

---

### Post by jeremy31 on 2016-06-08
There are some here who believe that the kernel module r8169 isn't the best choice for that ethernet and there is an alternative [http://mirrors.kernel.org/ubuntu/pool/universe/r/r8168/r8168-dkms_8.040.00-1_all.deb](http://mirrors.kernel.org/ubuntu/pool/universe/r/r8168/r8168-dkms_8.040.00-1_all.deb) but you would have to find a way to install the dependencies unless you have wireless available and then you could just ```
sudo apt-get install r8168-dkms
```

---

