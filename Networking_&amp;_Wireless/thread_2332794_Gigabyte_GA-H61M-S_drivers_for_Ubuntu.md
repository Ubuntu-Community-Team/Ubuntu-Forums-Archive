---
title: "Gigabyte GA-H61M-S drivers for Ubuntu"
date: 2016-08-04
forum: Networking &amp; Wireless
---

### Post by harry947 on 2016-08-04
Hi,
Guys these are all the drivers for my mobo: [http://www.gigabyte.com/products/product-page.aspx?pid=4873#driver](http://www.gigabyte.com/products/product-page.aspx?pid=4873#driver) 
Gigabyte doesn't offer any of these drivers for Ubuntu, and i need some of them as my internet connection is not working smoothly(getting low speed) .

Please help guys
Thanks

PS I'm running 16.04 LTS

---

### Post by QIII on 2016-08-04
Hello!

Unlike Windows, you need not install a bunch of motherboard drivers.  It is very rare that a driver is not already rolled into the kernel as you install or available to insert into the kernel later.

If you are having trouble with your internet connection, please start a new thread in the [Networking & Wireless]("https://ubuntuforums.org/forumdisplay.php?f=336") sub-forum.  Some network chipsets are problematic for Linux due to poor OEM support.  Others are difficult for other reasons.

Cheers!

---

### Post by harry947 on 2016-08-04
Thanks :)

Hi,
Guys these are all the drivers for my mobo: [http://www.gigabyte.com/products/pro...id=4873#driver](http://www.gigabyte.com/products/pro...id=4873#driver)
Gigabyte doesn't offer any of these drivers for Ubuntu, and i need some of them as my internet connection is not working smoothly(getting low speed) .

Please help guys
Thanks

PS I'm running 16.04 LTS

---

### Post by gordintoronto on 2016-08-04
Linux and Windows take very, very different approaches to drivers. Linux has most drivers built-in, but just occasionally it uses the wrong one for a specific piece of hardware. Your motherboard has been around for a while, so it should be fully supported.

Is your Internet connection by Ethernet or wireless?

Can you run these two commands and copy the results into "code blocks"? 
lspci
lsusb

Please post the results of these two commands:

lspci
lsusb

Are you using Ethernet or wireless?

---

### Post by papibe on 2016-08-04
Threads merged.

---

### Post by harry947 on 2016-08-13
> **gordintoronto said:**
> Please post the results of these two commands:

lspci
lsusb

Are you using Ethernet or wireless?

Sorry for the delay, I just got myself TP-Link TL-WN781ND and the speed which I'm getting now is meh..., kind of satisfactory :)

Here's the result 
harry@Harry:~$ lspci
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation H61 Express Chipset Family LPC Controller (rev 05)
00:1f.2 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 4 port SATA IDE Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
00:1f.5 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 2 port SATA IDE Controller (rev 05)
02:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
harry@Harry:~$ lsusb
Bus 002 Device 003: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 1a2c:0c21 China Resource Semico Co., Ltd 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
harry@Harry:~$ 



Thanks
for the help

---

