---
title: "3d games not working"
date: 2010-10-21
forum: New to Ubuntu
---

### Post by HiddenKnowledge on 2010-10-21
I run Ubuntu 10.04.1 LTS with FVWM-Crystal and habe some experience with it.
I can't get most 3d games to work, at the last game I tried, Minecraft, I got this error:

```
*********************************WARN_ONCE*********************************
File radeon_swtcl.c function r100_swtcl_flush line 323
Rendering was 13 commands larger than predicted size. We might overflow  command buffer.
***************************************************************************
drmRadeonCmdBuffer: -22. Kernel failed to parse or rejected command stream. See dmesg for more info.

```The last couple of dmesg lines: 

```
[   38.236283] AC'97 1 does not respond - RESET
[   38.252114] AC'97 1 access is not valid [0xffffffff], removing mixer.
[   38.252130] ali mixer 1 creating error.
[   45.608033] eth0: no IPv6 routers present
[   46.972179] device eth0 entered promiscuous mode
[   46.986371] device eth0 left promiscuous mode
[   46.997002] device eth0 entered promiscuous mode
[   62.856195] padlock: VIA PadLock not detected.
[ 1804.416351] device eth0 left promiscuous mode
[ 1808.266737] device eth0 entered promiscuous mode
[ 1808.273626] device eth0 left promiscuous mode
[ 1808.280832] device eth0 entered promiscuous mode
[10707.993360] __ratelimit: 9 callbacks suppressed
[12823.284465] psmouse.c: TouchPad at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
[13682.772285] [drm:r100_cs_track_texture_check] *ERROR* No texture bound to unit 0
[13682.772297] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[14606.094625] [drm:r100_cs_track_texture_check] *ERROR* No texture bound to unit 0
[14606.094638] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[16170.216410] [drm:r100_cs_track_texture_check] *ERROR* No texture bound to unit 0
[16170.216422] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[16956.862042] [drm:r100_cs_track_texture_check] *ERROR* No texture bound to unit 0
[16956.862054] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[18292.905943] [drm:r100_cs_track_texture_check] *ERROR* No texture bound to unit 0
[18292.905955] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !

```lspci output (thought it might help :P):

```
00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01)
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
00:0a.1 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1

```Please tell me what else you need and I'll provide it, I really want this fixed.

---

### Post by I8NY on 2010-10-21
Do you have the video card drive installed, and if you do where did you get it from?  Did it work before you installed FVWM-Crystal?

---

### Post by RichardGv on 2010-10-21
It looks like a known bug, unfortunately, in radeon KMS.
See: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/557266](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/557266)
There's a patch to fix this issue, but it's in kernel 2.6.36. Some indicated downgrading to kernel 2.6.31 works, but the version is just too old.
ATI's closed source Catalyst drivers may help, but perhaps it does not support your graphic card.

---

### Post by HiddenKnowledge on 2010-10-21
I get the same error with gnome, and I never installed any drivers.

---

### Post by annoyingrob on 2010-10-22
I'm having the same problem with my X850XT running Radeon proprietary drivers. It drives me crazy because now I can't play most of my 3d games!

Even glxgears crashes out when I resize it.

---

### Post by J-Rod on 2010-10-29
Ok wow, I've had this issue for some time when playing a game called ToME4. I had almost given up hope trying to troubleshoot it. It's hard enough to keep 3d working on this old Radeon Mobility L6MY. (thinkpad R40)

I have never had to patch a kernel before, in fact the most I have done was compile from scratch on a Gentoo installation. Can anyone give me a low down and dirty on how it is done? Tutorials I have found refer to the patch as a .bz file, but the previous link appears to be just the code snippet. 

Any help at all on this would be GREATLY appreciated. Thanks!

My GLXGears also crashes on a resize. I have the exact same dmesg output using the drivers and modeset default with 10.10.

---

### Post by annoyingrob on 2010-10-29
I already tried the kernel patch, and it just caused it to crash on something else. That was just my experience though.

---

### Post by J-Rod on 2010-11-01
Anyone else maybe run into this? Maybe one day technology will evolve to allow a video bus that is standard as external. Would be nice if laptops had the option to change video cards by default. :)

---

### Post by DooM55 on 2010-11-01
install openGL Form package manger

---

### Post by J-Rod on 2010-11-02
DooM55 	
Re: 3d games not working
install openGL Form package manger 

Which package are you referring to?

---

