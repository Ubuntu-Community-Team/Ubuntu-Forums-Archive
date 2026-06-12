---
title: "Toshiba Screen Resolution Problem"
date: 2011-05-27
forum: New to Ubuntu
---

### Post by Coachdbeard on 2011-05-27
I have a Toshiba laptop 1805-s204 with Lubuntu 10.10.  The resolution is set too low (800x600) with no option to raise it.  I think it needs to get to 1024x768.  Any help would be appreciated.  Here's some more info:

lspci:

00:00.0 Host bridge: ALi Corporation M1644/M1644T Northbridge+Trident (rev 01)
00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:04.0 IDE interface: ALi Corporation M5229 IDE (rev c3)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 01)
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:0a.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 0d)
00:11.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
00:11.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade XPAi1 (rev 82)
06:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)


xrandr:
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 800 x 600, maximum 1024 x 768
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
   400x300        60.0     56.0  
   320x240        60.0  
   [COLOR="Red"]1024x768_60.00   59.9  [/COLOR]

I added this last line (I attempted to make red) following another post.  It appears as a choice now, but it doesn't do anything.  Thanks for your help.

---

### Post by ubudog on 2011-05-28
Hi there, have you installed any graphics drivers yet?

---

### Post by Coachdbeard on 2011-05-28
I have not installed any graphics drivers yet that I know of.  I did do the "Additional Drivers" thing, but it just came up with some drivers for my wireless card and my on-board modem.

---

