---
title: "Rhythmbox crashes while transferring files to mp3 player"
date: 2011-01-19
forum: New to Ubuntu
---

### Post by GavinWiggins on 2011-01-19
I'm running Lucid and Rhythmbox 0.12.8.

I just bought a Sony mp3 player, model number NWZ-S544. I was able to transfer most of my music onto it with no problem, but three albums caused Rhythmbox to crash each time I tried. I ran dmesg and this is the only message I found pertaining to R-box:

[ 8114.693404] rhythmbox[4200]: segfault at b36d7988 ip 043397de sp b5e2cda0 error 4 in libpixbufloader-jpeg.so[4338000+4000]

I should also mention that my previous mp3 player, a Sony NWZ-A816, never had any such problem.

Just to be sure, I installed Banshee and tried to use it to transfer the albums which were causing the crash, and it did not work either.

Does anyone know how I can fix this?  Thanks.

---

