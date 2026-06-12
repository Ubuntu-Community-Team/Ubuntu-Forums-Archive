---
title: "wifi connection ?"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by garyed on 2009-07-28
I'm runnung Xubuntu Hardy on my laptop with wireless internet connection.
Sometimes even though it shows on the menu bar that I'm connected I'm not.
I can't ping anything either. If I reboot then everyting works fine.
With my desktop ethernet connection I can use ifdown & ifup to reset if things don't connect right. Is there a command to reset the wireless?

---

### Post by llamabr on 2009-07-28
you can use ifup and ifdown with wireless too.  There's also iwconfig

---

### Post by garyed on 2009-07-28
> **llamabr said:**
> you can use ifup and ifdown with wireless too.  There's also iwconfig

I think I tried ```
ifup -a
``` but I'll try it again using eth? next time.

---

### Post by llamabr on 2009-07-28
use the ifconfig command to see all available network devices.  I think your ethernet ones will be called eth1, etc, and wireless ones wlan1, etc.  But linux doesn't care if it's wired or not.  It treats them the same.

---

### Post by mapes12 on 2009-07-29
What wifi adapter do you have? Post the output to ```
lspci
```

---

### Post by garyed on 2009-07-29
> **mapes12 said:**
> What wifi adapter do you have? Post the output to ```
lspci
```

output from lspci:
> 00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 05)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 05)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go] (rev a3)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
02:0a.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
02:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
02:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
gary@t2-laptop:~$ 



---

### Post by mapes12 on 2009-07-30
You may need additional support for your wifi adapter to work properly. Here are some suggested posts / links:

[http://www.google.co.uk/search?hl=en&q=PRO%2FWireless+2200BG+ubuntu&btnG=Search&meta=](http://www.google.co.uk/search?hl=en&q=PRO%2FWireless+2200BG+ubuntu&btnG=Search&meta=)

---

