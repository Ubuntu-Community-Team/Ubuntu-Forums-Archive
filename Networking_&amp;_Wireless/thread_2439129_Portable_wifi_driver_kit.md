---
title: "Portable wifi driver kit?"
date: 2020-03-23
forum: Networking &amp; Wireless
---

### Post by thegear on 2020-03-23
I have an HP Envy laptop running Windows 10 that I occasionally need to run with Ubuntu from a DVD.  It has Broadcom 43142 WiFi hardware, which of course is not part of the Ubuntu distribution.  How can I create a kit (say, on a USB memory stick) that will have the Broadcom support on it, so I can easily get up on the network?  I'm somewhat linux-literate (but not internals) and have been a Unix user since about '85.  The gaps in my knowledge on this subject have to do with how to find and download the installation kit and then direct the installer to the memory stick.  Thanks for any help.

---

### Post by u666sa on 2020-03-23
A. It’s easier to buy atheros or broadcom card that is supported out of the box. Cheap, 5 bucks or with shipping.
B. Dual boot from HDD.

---

### Post by tea for one on 2020-03-23
> **thegear said:**
>  I occasionally need to run with Ubuntu from a DVD.  It has Broadcom 43142 WiFi hardware, which of course is not part of the Ubuntu distribution.

Here are a couple of suggestions.

Using an Ubuntu 18.04.1-desktop-amd64.iso, you can add the Broadcom drivers in a **live** session.

Open a terminal and enter 

```
sudo apt install bcmwl-kernel-source
```

After the driver has been installed/activated, then navigate to the wireless icon in the top right corner and enter your authentication details.

PS. I couldn't get it to work with Ubuntu 19.10 version.

Alternatively MX-19 has the Broadcom drivers built-in to their distro. [https://mxlinux.org/products/](https://mxlinux.org/products/)

Good luck

---

### Post by slickymaster on 2020-03-23
Thread moved to **Networking & Wireless** for a better fit

---

