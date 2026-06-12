---
title: "Having trouble with my ADSL connection."
date: 2007-12-19
forum: Networking &amp; Wireless
---

### Post by Ltmboy on 2007-12-19
I just installed xubuntu on an old Pentium 3 computer, but during the installation, xubuntu told me that no network interfaces were found. My laptop can connect just fine using a wireless connection, but the wired connection on the Pentium 3 desktop isn't working. The router is a Siemens SpeedStream 6520 and is connected to the desktop with a USB connection since Ethernet is not an option. When connected, the modem's usb light lights up, but still nothing. I'm not all that great with network connections, so now I'm absolutely lost. The output of```
 lspci
``` was ```

00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRo133x] (rev 44)
00:01.0 Pci bridge: VIA Technologies, Inc VT82C598/694x [Apollo MvP3/Pro133xAGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C596 ISA [Mobile South] (rev 23)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PICP Bus Master IDE (rev 10)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI Usb 1.1 Controller (rev 11)
00:07.3 Host Bridge: VIA Technologies, Inc. VT82C596 Power Management (rev 30)
00:09.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)
00:0a.0 Communication Controller: Conexant HCF 56k Data/Fax/Voice modem (rev 08)
01:00.0 VGA compatible Controller: ATI Technologies Inc. 3D rage Pro AGP 1x/2x (rev 5c)  
```
And ```
ifconfig
``` spits out this ```

lo     Link encap:Local Loopback
        inet addr:127.0.0.1 Mask: 255.0.0.0
        inet6 addr:  ::1/128 Scope:Host
        UP LOOPBACK RUNNING MTU:16436 Metric: 1
        RX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
        collisions:0 (0.0b)  TX bytes:0 (0.0b)
```

Hope that helps. Like I said, I have no idea what to do next, so any help would be appreciated. :)

---

### Post by Claus7 on 2007-12-20
Hello,

may this will help you, but is not exactly for your modem. I had problems with usb modems and I avoided them by buying an ethernet card.

[http://ubuntuforums.org/showthread.php?t=445701](http://ubuntuforums.org/showthread.php?t=445701)

Hope you will find a solution,
Regards!

---

### Post by kevinatkins on 2007-12-20
Hi,

I'd definitely suggest buying a PCI ethernet card and popping that in the desktop machine - it will save endless grief trying to make the USB connection work... Network cards really aren't very expensive now.

---

