---
title: "Broadcom [14e4:1677] (rev 01)"
date: 2015-01-27
forum: Networking &amp; Wireless
---

### Post by kell2 on 2015-01-27
My wireless card doesn't appear in the list of Broadcom cards in the Broadcom section of the forum.
I ran the wireless script:
[http://pastebin.ubuntu.com/9898890/](http://pastebin.ubuntu.com/9898890/)
which shows
[COLOR=#000000][FONT=sans-serif]Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)[/FONT][/COLOR]

booted in windows, device manager shows:

[COLOR=#000000][FONT=sans-serif]802.11n USB Wireless LAN Card [/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]Ralink Technology Corp [/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]Port_#0005.Hub_#0005 [/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]Broadcom NetExtreme 57xx Gigabit Controller [/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]Teredo Tunneling Pseudo-Interface

I also tried this
[/FONT][/COLOR]https://wireless.wiki.kernel.org/en/users/drivers
[COLOR=#000000][FONT=sans-serif]
not sure what to do next.
I am running Ubuntu 12.04 from a live usb.

Any help is appreciated[/FONT][/COLOR]

---

### Post by kc1di on 2015-01-27
Hello kell2 and Welcome to Ubuntu,

The BCM5751 is not a wireless card it's a Ethernet card
According to your the script you rand the  wireless is an Ralink Technology, Corp. RT5370 Wireless Adapter usb adapter. 
[This page]("https://wiki.debian.org/rt2800usb") even though it's for Debian should work to get it going.

---

### Post by kell2 on 2015-01-27
This is a dual boot computer with no ethernet connection.  The wifi only works in windows.  So I can't execute those commands in linux.  Can you point me to instructions for doing this offline?

---

### Post by chili555 on 2015-01-27
With all respect to my esteemed colleague kc1di, I doubt that you need do anything. You have the correct driver:> rt2800usb              22644  0 
rt2800lib              71740  1 rt2800usb
crc_ccitt              12627  1 rt2800lib
rt2x00usb              20161  1 rt2800usb
rt2x00lib              53673  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              534884  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              416271  2 rt2x00lib,mac80211You have a wireless interface:> wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:onIt scans and sees networks; presumably including yours:> Wireless Access Points 
    TWCWiFi-Passpoint: Infra, <MAC 'TWCWiFi-Passpoint' [AC8]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 82 WPA2 Enterprise
    Moore Back:      Infra, <MAC 'Moore Back' [AC4]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 39 WPA2
    OFFICE:          Infra, <MAC 'OFFICE' [AC3]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    Moore-3rd Floor: Infra, <MAC 'Moore-3rd Floor' [AC11]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA2
    FRONT_RECEPTION: Infra, <MAC 'FRONT_RECEPTION' [AC6]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    179_2.4GHz:      Infra, <MAC '179_2.4GHz' [AC7]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
<snip>Network Manager will default to wired ethernet if available. Please detach the ethernet cable, click the NM icon, see your network and try to connect. What happens or doesn't?

---

### Post by kc1di on 2015-01-28
Thanks chili555  - kc1di :)

---

