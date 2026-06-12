---
title: "HP Pavilion DM1 ~ Fun with a SIM Card?"
date: 2010-08-14
forum: New to Ubuntu
---

### Post by Andavane on 2010-08-14
Hi -
I noticed that my new HP Ultramobile 11.6" PC has a SIM Card slot tucked in right behind the battery housing. I became excited, as atm I do have a spare SIM Card, for use in the right Android phone for me comes along ~ I thought by that putting it in, I could just turn this PC into a mobile phone.

However, it appears to be a weird HP Mobile Phone commercial service thingie.

I was wondering if anyone who was good with electronics would know what this is and if there's any function you get with it?

---

### Post by ronnielsen1 on 2010-08-14
> It called WWAN – (wireless wide area network).
[http://h30434.www3.hp.com/t5/Other-Notebook-PC-questions/HP-Pavilion-dm1-1111ea-mobile-sim-card/td-p/302989](http://h30434.www3.hp.com/t5/Other-Notebook-PC-questions/HP-Pavilion-dm1-1111ea-mobile-sim-card/td-p/302989)

[http://foomagic.org/wiki/index.php/Using_the_Sierra_mc8755_WWAN_card_under_linux](http://foomagic.org/wiki/index.php/Using_the_Sierra_mc8755_WWAN_card_under_linux)

The 2nd link may or may not be yours. What's the output of lspci and lsusb?

---

### Post by Andavane on 2010-08-14
> **ronnielsen1 said:**
> [http://h30434.www3.hp.com/t5/Other-Notebook-PC-questions/HP-Pavilion-dm1-1111ea-mobile-sim-card/td-p/302989](http://h30434.www3.hp.com/t5/Other-Notebook-PC-questions/HP-Pavilion-dm1-1111ea-mobile-sim-card/td-p/302989)

[http://foomagic.org/wiki/index.php/Using_the_Sierra_mc8755_WWAN_card_under_linux](http://foomagic.org/wiki/index.php/Using_the_Sierra_mc8755_WWAN_card_under_linux)

The 2nd link may or may not be yours. What's the output of lspci and lsusb?

Thanks for finding the links.
The 1st is certainly very similar to mine, but it's not me.

The first command reveals this:

> andavane@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)


The second command shows:

> andavane@ubuntu:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 03f0:2a1d Hewlett-Packard 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 5986:0182 Acer, Inc 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
andavane@ubuntu:~$ 


---

