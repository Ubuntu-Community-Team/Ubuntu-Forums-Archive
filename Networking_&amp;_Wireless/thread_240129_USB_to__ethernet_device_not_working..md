---
title: "USB to  ethernet device not working."
date: 2006-08-20
forum: Networking &amp; Wireless
---

### Post by voicestreams on 2006-08-20
Hi all,
I have an anonymous looking USB device to set up a network interface. The device provides a RJ-45 socket.

The device succesfully established network interface on Windows XP system with the supplied Windows drivers. When installing on Windows it identified as ST 268 USB NIC USB to Fast Ethernet Adapter.

If possible, I would like to use this device on a Linux system which has a defective on board NIC. I did an insmod rtl8150.ko, and it is detected as ST268 USB NIC. But, i'm not able to connect to the network. 

Please help !! 

i'm using COMPAQ pressario 1200 (an old laptop) and ubuntu 5.1.

thanks for your time.

best,
Amith

---

### Post by coffeecat on 2006-08-20
I have a 'Sitecom' brand USB to ethernet adapter that works absolutely fine with Ubuntu Dapper (6.06) on my old Compaq Presario 1200. Or at least it did until the Compaq died. I didn't need to do anything beyond plug it in so clearly the driver is compiled into the kernel, or possibly as a module. I've read on another forum that most of these devices have a common chipset but since yours is 'anonymous' it may have something not recognised by Ubuntu. Sorry I can't help more.

Another possibility is that your USB port is faulty. Have you checked it with another USB device? If it's not working I'll tell you for free that the combination of a PCMCIA to USB card and the USB-ethernet adapter didn't work. Sorry. :(

**Edit:** Just noticed that you're using Breezy (5.10). Try installing Dapper instead. You'll need more memory than comes with the machine. As far as I remember I had an extra 128Mb on my Compaq making 160 Mb altogether

---

