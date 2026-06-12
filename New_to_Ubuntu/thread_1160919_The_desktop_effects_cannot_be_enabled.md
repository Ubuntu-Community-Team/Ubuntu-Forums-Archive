---
title: "The desktop effects cannot be enabled"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by kubes on 2009-05-16
I'm using jaunty. My current desktop effects are set to 'None' by default. When i try to change it to normal, i get this message 'The desktop effects cannot be enabled'. I searched about it and installed compiz but it doesn't seem to support my hardware. Is there a workaround?

  Before using 9.04, i was using hardy and i didn't face this problem then. It seems to be the problem with jaunty in my case.

---

### Post by anewguy on 2009-05-16
Do lspci in a terminal window and post the output back here.

Dave :)

---

### Post by kubes on 2009-05-16
administrator@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by kukibird1 on 2009-05-16
> **kubes said:**
> administrator@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

There are issues with Intel  in 9.04. This may help.
[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4")

[http://www.ubuntu.com/getubuntu/releasenotes/904]("http://www.ubuntu.com/getubuntu/releasenotes/904")

---

### Post by kubes on 2009-05-17
Thanks for the links...:)

But it didn't work for me..Its a shame really because it used to work perfectly fine in 8.04. And now it doesn't. :confused::-(

---

### Post by devosion on 2009-05-17
[http://www.h-online.com/open/Updated-graphics-drivers-for-Ubuntu-9-04--/news/113261]("http://www.h-online.com/open/Updated-graphics-drivers-for-Ubuntu-9-04--/news/113261")

The above link is to a how-to on unstable new versions of the intel drivers, as well as AMD/ATI as well. The drivers are experimental but they work for my GM965 on my Acer Extensa, allowing me to effectively turn on desktop effects to full. Give them a shot if you're interested, but remember they are still in development.

---

