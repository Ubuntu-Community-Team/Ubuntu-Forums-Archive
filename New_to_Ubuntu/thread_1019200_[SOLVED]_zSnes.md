---
title: "[SOLVED] zSnes"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by adobrakic on 2008-12-22
I downloaded zSnes from [here](http://www.zsnes.com/), but have no idea how to install it. I looked for .deb files, but couldn't find anymore.
Any help? :D

--edit--
Nevermind, I found it in the repos, but when I click on it, it doesnt open.

This is what I get via terminal:

```

ado@ado-desktop:~$ sudo zsnes
[sudo] password for ado: 
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check http://www.zsnes.com/ for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
ManyMouse: 2 mice detected.
Using ManyMouse for:
Mouse 0: ImExPS/2 Generic Explorer Mouse
Mouse 1: Macintosh mouse button emulation
*** buffer overflow detected ***: zsnes terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7ca9558]
/lib/tls/i686/cmov/libc.so.6[0xb7ca7680]
zsnes[0x8056c1b]
======= Memory map: ========
08048000-08303000 r-xp 00000000 08:01 573589     /usr/bin/zsnes
08303000-08304000 r--p 002ba000 08:01 573589     /usr/bin/zsnes
08304000-08343000 rw-p 002bb000 08:01 573589     /usr/bin/zsnes
08343000-088f7000 rw-p 08343000 00:00 0 
09348000-09392000 rw-p 09348000 00:00 0          [heap]
b6b74000-b76a3000 rw-p b6b74000 00:00 0 
b76a3000-b76c5000 r-xp 00000000 08:01 1903378    /usr/lib/libaudiofile.so.0.0.2
b76c5000-b76c8000 rw-p 00021000 08:01 1903378    /usr/lib/libaudiofile.so.0.0.2
b76c8000-b76d1000 r-xp 00000000 08:01 1903554    /usr/lib/libesd.so.0.2.39
b76d1000-b76d2000 r--p 00008000 08:01 1903554    /usr/lib/libesd.so.0.2.39
b76d2000-b76d3000 rw-p 00009000 08:01 1903554    /usr/lib/libesd.so.0.2.39
b76d3000-b7721000 r-xp 00000000 08:01 598068     /usr/lib/libpulse.so.0.4.1
b7721000-b7722000 r--p 0004d000 08:01 598068     /usr/lib/libpulse.so.0.4.1
b7722000-b7723000 rw-p 0004e000 08:01 598068     /usr/lib/libpulse.so.0.4.1
b7723000-b772f000 r-xp 00000000 08:01 598070     /usr/lib/libpulse-simple.so.0.0.1
b772f000-b7730000 r--p 0000b000 08:01 598070     /usr/lib/libpulse-simple.so.0.0.1
b7730000-b7731000 rw-p 0000c000 08:01 598070     /usr/lib/libpulse-simple.so.0.0.1
b773c000-b773f000 r-xp 00000000 08:01 1925608    /usr/lib/ao/plugins-2/libalsa09.so
b773f000-b7741000 rw-p 00002000 08:01 1925608    /usr/lib/ao/plugins-2/libalsa09.so
b7741000-b7769000 r-xp 00000000 08:01 1081457    /lib/libpcre.so.3.12.1
b7769000-b776a000 r--p 00027000 08:01 1081457    /lib/libpcre.so.3.12.1
b776a000-b776b000 rw-p 00028000 08:01 1081457    /lib/libpcre.so.3.12.1
b776b000-b7820000 r-xp 00000000 08:01 1901363    /usr/lib/libglib-2.0.so.0.1800.2
b7820000-b7821000 r--p 000b4000 08:01 1901363    /usr/lib/libglib-2.0.so.0.1800.2
b7821000-b7822000 rw-p 000b5000 08:01 1901363    /usr/lib/libglib-2.0.so.0.1800.2
b7822000-b7826000 r-xp 00000000 08:01 1904680    /usr/lib/libgthread-2.0.so.0.1800.2
b7826000-b7827000 r--p 00003000 08:01 1904680    /usr/lib/libgthread-2.0.so.0.1800.2
b7827000-b7828000 rw-p 00004000 08:01 1904680    /usr/lib/libgthread-2.0.so.0.1800.2
b7828000-b782b000 r-xp 00000000 08:01 1901368    /usr/lib/libgmodule-2.0.so.0.1800.2
b782b000-b782c000 r--p 00002000 08:01 1901368    /usr/lib/libgmodule-2.0.so.0.1800.2
b782c000-b782d000 rw-p 00003000 08:01 1901368    /usr/lib/libgmodule-2.0.so.0.1800.2
b782d000-b7832000 r-xp 00000000 08:01 1903364    /usr/lib/libartsc.so.0.0.0
b7832000-b7833000 r--p 00004000 08:01 1903364    /usr/lib/libartsc.so.0.0.0
b7833000-b7834000 rw-p 00005000 08:01 1903364    /usr/lib/libartsc.so.0.0.0
b7834000-b7849000 r-xp 00000000 08:01 1903236    /usr/lib/libICE.so.6.3.0
b7849000-b784a000 rw-p 00014000 08:01 1903236    /usr/lib/libICE.so.6.3.0
b784a000-b784c000 rw-p b784a000 00:00 0 
b784c000-b7899000 r-xp 00000000 08:01 1903322    /usr/lib/libXt.so.6.0.0
b7899000-b789d000 rw-p 0004c000 08:01 1903322    /usr/lib/libXt.so.6.0.0
b789d000-b78b3000 r-xp 00000000 08:01 1903376    /usr/lib/libaudio.so.2.4
b78b3000-b78b4000 r--p 00015000 08:01 1903376    /usr/lib/libaudio.so.2.4
b78b4000-b78b5000 rw-p 00016000 08:01 1903376    /usr/lib/libaudio.so.2.4
b78b6000-b78b7000 r-xp 00000000 08:01 1925610    /usr/lib/ao/plugins-2/libesd.so
b78b7000-b78b9000 rw-p 00000000 08:01 1925610    /usr/lib/ao/plugins-2/libesd.so
b78b9000-b78bc000 r-xp 00000000 08:01 1081386    /lib/libcap.so.1.10
b78bc000-b78bd000 rw-p 00002000 08:01 1081386    /lib/libcap.so.1.10
b78bd000-b78bf000 r-xp 00000000 08:01 1925613    /usr/lib/ao/plugins-2/libpulse.so
b78bf000-b78c1000 rw-p 00001000 08:01 1925613    /usr/lib/ao/plugins-2/libpulse.so
b78c1000-b78c3000 r-xp 00000000 08:01 1925612    /usr/lib/ao/plugins-2/liboss.so
b78c3000-b78c5000 rw-p 00001000 08:01 1925612    /usr/lib/ao/plugins-2/liboss.so
b78c5000-b78cf000 r-xp 00000000 08:01 1099114    /lib/tls/i686/cmov/libnss_files-2.8.90.so
b78cf000-b78d0000 r--p 00009000 08:01 1099114    /lib/tls/i686/cmov/libnss_files-2.8.90.so
b78d0000-b78d1000 rw-p 0000a000 08:01 1099114    /lib/tls/i686/cmov/libnss_files-2.8.90.so
b78d1000-b78da000 r-xp 00000000 08:01 1099118    /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b78da000-b78db000 r--p 00008000 08:01 1099118    /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b78db000-b78dc000 rw-p 00009000 08:01 1099118    /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b78dc000-b78f1000 r-xp 00000000 08:01 1099108    /lib/tls/i686/cmov/libnsl-2.8.90.so
b78f1000-b78f2000 r--p 00014000 08:01 1099108    /lib/tls/i686/cmov/libnsl-2.8.90.so
b78f2000-b78f3000 rw-p 00015000 08:01 1099108    /lib/tls/i686/cmov/libnsl-2.8.90.so
b78f3000-b78f5000 rw-p b78f3000 00:00 0 
b78f5000-b78fc000 r-xp 00000000 08:01 1099110    /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b78fc000-b78fd000 r--p 00006000 08:01 1099110    /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b78fd000-b78fe000 rw-p 00007000 08:01 1099110    /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b78fe000-b7901000 rw-p b78fe000 00:00 0 
b7901000-b7905000 r-xp 00000000 08:01 1903292    /usr/lib/libXdmcp.so.6.0.0
b7905000-b7906000 rw-p 00003000 08:01 1903292    /usr/lib/libXdmcp.so.6.0.0
b7906000-b7908000 r-xp 00000000 08:01 1903281    /usr/lib/libXau.so.6.0.0
b7908000-b7909000 rw-p 00001000 08:01 1903281    /usr/lib/libXau.so.6.0.0
b7909000-b7920000 r-xp 00000000 08:01 1904368    /usr/lib/libxcb.so.1.0.0
b7920000-b7921000 r--p 00016000 08:01 1904368    /usr/lib/libxcb.so.1.0.0
b7921000-b7922000 rw-p 00017000 08:01 1904368    /usr/lib/libxcb.so.1.0.0
b7922000-b7923000 r-xp 00000000 08:01 1904364    /usr/lib/libxcb-xlib.so.0.0.0
b7923000-b7924000 r--p 00000000 08:01 1904364    /usr/lib/libxcb-xlib.so.0.0.0
b7924000-b7925000 rw-p 00001000 08:01 1904364    /usr/lib/libxcb-xlib.so.0.0.0
b7925000-b7926000 rw-p b7925000 00:00 0 
b7926000-b792d000 r-xp 00000000 08:01 1099127    /lib/tls/i686/cmov/librt-2.8.90.so
b792d000-b792e000 r--p 00007000 08:01 1099127    /lib/tls/i686/cmov/librt-2.8.90.so
b792e000-b792f000 rw-p 00008000 08:01 1099127    /lib/tls/i686/cmov/librt-2.8.90.so
b792f000-b7936000 r-xp 00000000 08:01 1903514    /usr/lib/libdrm.so.2.3.1
b7936000-b7937000 r--p 00006000 08:01 1903514    /usr/lib/libdrm.so.2.3.1
b7937000-b7938000 rw-p 00007000 08:01 1903514    /usr/lib/libdrm.so.2.3.1
b7938000-b793c000 r-xp 00000000 08:01 1903298    /usr/lib/libXfixes.so.3.1.0
b793c000-b793d000 rw-p 00003000 08:01 1903298    /usr/lib/libXfixes.so.3.1.0
b793d000-b793f000 r-xp 00000000 08:01 1903290    /usr/lib/libXdamage.so.1.1.0
b793f000-b7940000 rw-p 00001000 08:01 1903290    /usr/lib/libXdamage.so.1.1.0
b7940000-b7944000 r-xp 00000000 08:01 1903336    /usr/lib/libXxf86vm.so.1.0.0
b7944000-b7945000 r--p 00003000 08:01 1903336    /usr/lib/libXxf86vm.so.1.0.0
b7945000-b7946000 rw-p 00004000 08:01 1903336    /usr/lib/libXxf86vm.so.1.0.0
b7946000-b7947000 rw-p b7946000 00:00 0 
b7947000-b7954000 r-xp 00000000 08:01 1903296    /usr/lib/libXext.so.6.4.0
b7954000-b7956000 rw-p 0000c000 08:01 1903296    /usr/lib/libXext.so.6.4.0
b7956000-b7a41000 r-xp 00000000 08:01 598062     /usr/lib/libX11.so.6.2.0
b7a41000-b7a42000 r--p 000ea000 08:01 598062     /usr/lib/libX11.so.6.2.0
b7a42000-b7a44000 rw-p 000eb000 08:01 598062     /usr/lib/libX11.so.6.2.0
b7a44000-b7a45000 rw-p b7a44000 00:00 0 
b7a45000-b7a58000 r-xp 00000000 08:01 1903500    /usr/lib/libdirect-1.0.so.0.1.0
b7a58000-b7a59000 r--p 00012000 08:01 1903500    /usr/lib/libdirect-1.0.so.0.1.0
b7a59000-b7a5a000 rw-p 00013000 08:01 1903500    /usr/lib/libdirect-1.0.so.0.1.0
b7a5a000-b7a61000 r-xp 00000000 08:01 1903604    /usr/lib/libfusion-1.0.so.0.1.0
b7a61000-b7a62000 r--p 00006000 08:01 1903604    /usr/lib/libfusion-1.0.so.0.1.0
b7a62000-b7a63000 rw-p 00007000 08:01 1903604    /usr/lib/libfusion-1.0.so.0.1.0
b7a63000-b7ac7000 r-xp 00000000 08:01 1903502    /usr/lib/libdirectfb-1.0.so.0.1.0
b7ac7000-b7ac8000 r--p 00063000 08:01 1903502    /usr/lib/libdirectfb-1.0.so.0.1.0
b7ac8000-b7ac9000 rw-p 00064000 08:01 1903502    /usr/lib/libdirectfb-1.0.so.0.1.0
b7ac9000-b7aca000 rw-p b7ac9000 00:00 0 
b7aca000-b7acc000 r-xp 00000000 08:01 1099103    /lib/tls/i686/cmov/libdl-2.8.90.so
b7acc000-b7acd000 r--p 00001000 08:01 1099103    /lib/tls/i686/cmov/libdl-2.8.90.so
b7acd000-b7ace000 rw-p Aborted
ado@ado-desktop:~$ 

```

---

### Post by taurus on 2008-12-22
There's zsnes in the repos.

```
sudo apt-get update
sudo apt-get install zsnes
```

---

### Post by nhasian on 2008-12-22
are you using Ubuntu 8.04 or 8.10?  the one in the repos doesnt work with 8.10.

---

### Post by DirtDawg on 2008-12-22
Hi. Try the Snes9x gtk port found [here]("http://www.snes9x.com/phpbb2/viewtopic.php?p=22874&sid=f379151c5033320bcabc9bd1c85a7d1c"). It's a great emulator. There's both a binary and a deb package available on the linked page. I have not tried the deb package with Ibex. However, the precompiled binary works great as long as you have the proper dependencies installed (I was only missing libportaudio2), a list of which are provided in a README included in the download.

---

### Post by adobrakic on 2008-12-23
> **nhasian said:**
> are you using Ubuntu 8.04 or 8.10?  the one in the repos doesnt work with 8.10.

I have Mint 6, but that's based off of 8.10.
Any idea when it will work?

--edit--

> 
Hi. Try the Snes9x gtk port found here. It's a great emulator. There's both a binary and a deb package available on the linked page. I have not tried the deb package with Ibex. However, the precompiled binary works great as long as you have the proper dependencies installed (I was only missing libportaudio2), a list of which are provided in a README included in the download.


This installed perfect with the repos, actually. Thanks!

---

### Post by nhasian on 2008-12-23
although the one in the repos dont work with Ubuntu 8.10 the one from this page does:

[http://board.zsnes.com/phpBB2/viewtopic.php?t=11513](http://board.zsnes.com/phpBB2/viewtopic.php?t=11513)

---

### Post by DirtDawg on 2008-12-23
> **adobrakic said:**
> This installed perfect with the repos, actually. Thanks!

I think the version in the repository might be an older version of the same thing. Or it may be an entirely different port. I'm not really sure. Still, glad it works :D

---

