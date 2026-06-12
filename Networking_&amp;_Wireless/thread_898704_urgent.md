---
title: "urgent"
date: 2008-08-23
forum: Networking &amp; Wireless
---

### Post by mohammed85 on 2008-08-23
hi there,

I am new user of Ubunto and I really love it, however I do have a problem with the wireless network. I use ubunto now at work for my development but at home there is a wireless network which is called default without a password. I was trying to connect to it for a week but no success at all, the problem is that when i try to connect to it, it connects and the operating system says i am connected but when i try to open a page i can not, moreove when i try to ping google from the terminal i can not, any reason? 

This is my first post and I hope I will not be disappointed:).

---

### Post by pfdevil on 2008-08-23
Hey when you are connected to the wireless, open the terminal and type lspci search for the wlan0 <-- may be different. Check that the ip-address and default gateways is correct. Is your router dhcp enabled?

---

### Post by mohammed85 on 2008-08-23
hi ,

thank you very much for the quick reply, to be honest i have no idea about the router settings because i have no access to it .....any more idea please:)

---

### Post by pfdevil on 2008-08-23
O.k then, connect to wireless. Then open the terminal and type lspci , post the output here please.

---

### Post by mohammed85 on 2008-08-23
thank you very very much, i would not expect help as fast as this even in my dreams, i am not at home now but i am going to post it when i arrive there:)

---

### Post by mohammed85 on 2008-08-23
helllo ,

this is the out put from the command

mohammed@mohammed-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:19.0 Ethernet controller: Intel Corporation 82566MC Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
01:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:0b.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
05:0b.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
05:0b.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

---

### Post by pfdevil on 2008-08-24
Hey you will need to install drivers from here, just follow the instructions.

[http://intellinuxwireless.org/?n=Info]("http://intellinuxwireless.org/?n=Info")

---

### Post by mohammed85 on 2008-08-24
thank you very much for that help my friend, can you please let me kow how to install them. it is a little bit difficult me to follow the instruction in the read me:)

i hope to hear from you soon

---

