---
title: "lspci doesn't show my integrated wifi card"
date: 2006-08-01
forum: Networking &amp; Wireless
---

### Post by zoubidoo on 2006-08-01
Platform: Acer Aspire 3613WLMi, Ubuntu 6.06, kernel 2.6.15-23-686, lspci 2.1.11

I'm trying to get WiFi running, but lspci doesn't list my wifi card (see output below).  According to [http://midtoad.homelinux.org:9080/frog/user/midtoad/article/2006-03-24/18](http://midtoad.homelinux.org:9080/frog/user/midtoad/article/2006-03-24/18) this laptop model has a Broadcom 4318.  I know the card exists, I have used it under XP!

Should the card definitely be listed by lspci or can I simply ignore its absence?  Is my kernel missing something? I'm using a standard ubuntu kernel (didn't compile myself).

Any suggestions?

zoubidoo@acer-laptop:~/SysAdmin/Wifi$ lspci
0000:00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
0000:00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
0000:00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:06:09.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
zoubidoo@acer-laptop:~/SysAdmin/Wifi$

---

### Post by zoubidoo on 2006-08-02
Fixed:  it turns out that when the laptop was serviced the wifi PCI card wasn't properly plugged in.  

](*,)

---

