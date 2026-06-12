---
title: "Can i change this to 1080p?"
date: 2010-11-01
forum: New to Ubuntu
---

### Post by D3SI on 2010-11-01
in this guide it says replace this with this .... on and on
#

[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)


for example:
replace
```
#GRUB_GFXMODE=640x480
```

with
```
GRUB_GFXMODE=1280x1024
```

----------------------------------------

can i replace it with
```
GRUB_GFXMODE=1920x1080
```

will it work fine? (1920x1080)

---

### Post by buntudawg on 2010-11-01
If your graphics card and monitor support that resolution then yes you can change it to that.

---

### Post by D3SI on 2010-11-01
tried but didn't work..

some txt came up for 1 second and went away....  No Ubuntu Logo on loading screen

---

### Post by buntudawg on 2010-11-01
Hmm.

Did you enter your desired resolution at all the appropriate places? Is your GPU ATI or NVIDIA? As far as I know the fix is only for them. See:

[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

which is the same process, but is a little more condensed so easier to read and check your steps. Also it outlines the prerequisite hardware and software.

Be careful with the hwinfo output though, it is only for resolutions your video card supports. If you choose one that is too high your monitor won't display it.

Good luck

---

### Post by D3SI on 2010-11-01
I've got Nvidia 8600GT

results using first command:
>   Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x030f: 320x200 (+1280), 24 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x0330: 320x200 (+320), 8 bits
  Mode 0x0331: 320x400 (+320), 8 bits
  Mode 0x0332: 320x400 (+640), 16 bits
  Mode 0x0333: 320x400 (+1280), 24 bits
  Mode 0x0334: 320x240 (+320), 8 bits
  Mode 0x0335: 320x240 (+640), 16 bits
  Mode 0x0336: 320x240 (+1280), 24 bits
  Mode 0x033d: 640x400 (+1280), 16 bits
  Mode 0x033e: 640x400 (+2560), 24 bits
  Mode 0x0345: 1600x1200 (+1600), 8 bits
  Mode 0x0346: 1600x1200 (+3200), 16 bits
  Mode 0x0347: 1400x1050 (+1400), 8 bits
  Mode 0x0348: 1400x1050 (+2800), 16 bits
  Mode 0x0349: 1400x1050 (+5600), 24 bits
  Mode 0x034a: 1600x1200 (+6400), 24 bits
  Mode 0x0352: 2048x1536 (+8192), 24 bits
  Mode 0x0360: 1280x800 (+1280), 8 bits
  Mode 0x0361: 1280x800 (+5120), 24 bits
  Mode 0x0362: 768x480 (+768), 8 bits
  Mode 0x0364: 1440x900 (+1440), 8 bits
  Mode 0x0365: 1440x900 (+5760), 24 bits
  Mode 0x0368: 1680x1050 (+1680), 8 bits
  Mode 0x0369: 1680x1050 (+6720), 24 bits
  Mode 0x037c: 1920x1200 (+1920), 8 bits
  Mode 0x037d: 1920x1200 (+7680), 24 bits

my monitor supports 1920x1080  but not 1920x*1200   why didn't that come up :|

---

### Post by drs305 on 2010-11-01
You can see what resolutions Grub2 is capable of supporting during the boot process. At the Grub2 menu, press "c" to enter the G2 terminal mode. Then type:
```
vbeinfo
```

It will show the displays that Grub2 is capable of showing. You can enter any of results in your /etc/default/grub file and after you run "sudo update-grub" they should work at the next boot.

---

