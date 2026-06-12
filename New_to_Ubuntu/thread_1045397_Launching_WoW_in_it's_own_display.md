---
title: "Launching WoW in it's own display"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by Sarmacid on 2009-01-20
Hey, I'm a WoW player, and everything is running great. I heard that launching WoW in it's own display would significantly improve performance and I've tryed to do that but failed. This has worked with other games, but not with WoW so I'm a bit puzzled by it. To run it, I first run```
sudo X :3 -ac &
``` which creates the second display and I can access it pressing ctrl+alt+F9, obviously there's nothing there. Now to run WoW, I try this(The command I use to open WoW in the default display)```
DISPLAY=:3 padsp wine /media/linux/World\ of\ Warcraft/WoW.exe
```
The output of this command is```
fixme:advapi:SetSecurityInfo stub
archive Data\enUS\patch-enUS.MPQ opened
archive Data\patch.MPQ opened
archive Data\expansion.MPQ opened
archive Data\lichking.MPQ opened
archive Data\common.MPQ opened
archive Data\common-2.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
archive Data\enUS\expansion-locale-enUS.MPQ opened
archive Data\enUS\lichking-locale-enUS.MPQ opened
archive Data\enUS\expansion-speech-enUS.MPQ opened
archive Data\enUS\lichking-speech-enUS.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x39edbc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39ecac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f2d8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f434,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f5a0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f59c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f530,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f520,0x00000000), stub!
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":3.0"
      after 24 requests (16 known processed) with 0 events remaining.
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":3.0"
      after 553 requests (552 known processed) with 0 events remaining.

```
And the output of the terminal where I launched the second display is```
Backtrace:
0: X(xf86SigHandler+0x7e) [0x80c780e]
1: [0xb7f01420]
2: /usr/lib/xorg/modules//libfb.so(fbOddTile+0x118) [0xb692cb98]
3: /usr/lib/xorg/modules//libfb.so(fbTile+0x8c) [0xb692cc5c]
4: /usr/lib/xorg/modules//libfb.so(fbFillRegionTiled+0x19e) [0xb692d2ee]
5: /usr/lib/xorg/modules//libfb.so(fbPaintWindow+0x104) [0xb692d5a4]
6: /usr/lib/xorg/modules/drivers//nvidia_drv.so [0xb6b62464]

Fatal server error:
Caught signal 11.  Server aborting

```

Any ideas how can I do it?

---

