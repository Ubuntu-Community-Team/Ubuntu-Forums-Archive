---
title: "GRUB2 tty widescreen"
date: 2010-03-14
forum: New to Ubuntu
---

### Post by SpreX on 2010-03-14
Ok I read a lot of posts tutorials al around internet but still no solution.
First I wanted to se  which proccesses is started during boot but to also have grafical boot. I removed quiet i it worked. Even at startup because somebody said that xsplash in karmic doesn't support it.

Now I want to change the resolution of ttys (alt+F1-F6)
It's still 640x400. 
Output of sudo hwinfo --framebuffer is:

```
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.464]
  Unique ID: rdCR.X2B4pmx_r89
  Hardware Class: framebuffer
  Model: "(C) 1988-2005, ATI Technologies Inc.  M82"
  Vendor: "(C) 1988-2005, ATI Technologies Inc. "
  Device: "M82"
  SubVendor: "ATI ATOMBIOS"
  SubDevice: 
  Revision: "01.00"
  Memory Size: 16 MB
  Memory Range: 0xd0000000-0xd0ffffff (rw)
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+832), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x0320: 320x200 (+1280), 24 bits
  Mode 0x0393: 320x240 (+320), 8 bits
  Mode 0x0395: 320x240 (+640), 16 bits
  Mode 0x0396: 320x240 (+1280), 24 bits
  Mode 0x03b3: 512x384 (+512), 8 bits
  Mode 0x03b5: 512x384 (+1024), 16 bits
  Mode 0x03b6: 512x384 (+2048), 24 bits
  Mode 0x03c3: 640x350 (+640), 8 bits
  Mode 0x03c5: 640x350 (+1280), 16 bits
  Mode 0x03c6: 640x350 (+2560), 24 bits
  Mode 0x0383: 640x400 (+640), 8 bits
  Mode 0x0385: 640x400 (+1280), 16 bits
  Mode 0x0386: 640x400 (+2560), 24 bits
  Mode 0x0333: 720x400 (+768), 8 bits
  Mode 0x0335: 720x400 (+1472), 16 bits
  Mode 0x0336: 720x400 (+2944), 24 bits
  Mode 0x0353: 1152x864 (+1152), 8 bits
  Mode 0x0355: 1152x864 (+2304), 16 bits
  Mode 0x0356: 1152x864 (+4608), 24 bits
  Mode 0x0363: 1280x1024 (+1280), 8 bits
  Mode 0x0365: 1280x1024 (+2560), 16 bits
  Mode 0x0366: 1280x1024 (+5120), 24 bits
  Mode 0x0321: 640x480 (+2560), 24 bits
  Mode 0x0322: 800x600 (+3200), 24 bits
  Mode 0x0323: 1024x768 (+4096), 24 bits
  Mode 0x0324: 1280x1024 (+5120), 24 bits
  Mode 0x0343: 1400x1050 (+1408), 8 bits
  Mode 0x0345: 1400x1050 (+2816), 16 bits
  Mode 0x0346: 1400x1050 (+5632), 24 bits
  Mode 0x0373: 1600x1200 (+1600), 8 bits
  Mode 0x0375: 1600x1200 (+3200), 16 bits
  Mode 0x0376: 1600x1200 (+6400), 24 bits
  Mode 0x0383: 640x400 (+640), 8 bits
  Mode 0x0385: 640x400 (+1280), 16 bits
  Mode 0x0386: 640x400 (+2560), 24 bits
  Mode 0x03d3: 1856x1392 (+1856), 8 bits
  Mode 0x03d5: 1856x1392 (+3712), 16 bits
  Mode 0x03d6: 1856x1392 (+7424), 24 bits
  Mode 0x03e3: 1920x1440 (+1920), 8 bits
  Mode 0x03e5: 1920x1440 (+3840), 16 bits
  Mode 0x03e6: 1920x1440 (+7680), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```
I am using asus x59sl and resolution of my display is 1280x800 (16:10)
but there isn't any 1280x* here. I know that bios sometimes doesn't show all available resolutions. So I will be happy if any other works like 1280x1024. Everything bigger then 1024x768. But it cant. I added vga= in hexadecimal and decimal values too, still nothing. I addes to /etc/default/grub to both lines thee. After it didn't worked i deleted  everything modified except the part about deleting quiet.
This is /etc/default/grub:

```
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=640x400

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"

```

I also enabled background in grub.
Please help, I am stuck with this and cant make it work. Thanks in advance.

---

