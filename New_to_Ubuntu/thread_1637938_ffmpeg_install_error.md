---
title: "ffmpeg install error"
date: 2010-12-05
forum: New to Ubuntu
---

### Post by Yours3lf22 on 2010-12-05
Hi,

I've just migrated from windows (because I'm developing for Linux), and I wanted to record my desktop using ffmpeg. On a vmware virtual pc, previously I could do it, but I dont know why now I get an error when installing ffmpeg.

So here it is:
yours3lf@yours3lf-PC:~$ sudo apt-get install ffmpeg
[sudo] password for yours3lf: 
Csomaglisták olvasása... Kész
Függ&#337;ségi fa építése       
Állapot adatok olvasása... Kész
The following packages were automatically installed and are no longer required:
  libkonq5-templates libknewstuff2-4 libqca2-plugin-ossl libqt4-test
  lib32nss-mdns libkonq5 ttf-symbol-replacement winbind python-iniparse
Töröld az 'apt-get autoremove' paranccsal!
Az alábbi extra csomagok kerülnek telepítésre:
  libavfilter1
Az alábbi ÚJ csomagok lesznek telepítve:
  ffmpeg libavfilter1
0 frissített, 2 újonnan telepített, 0 eltávolítandó és 0 nem frissített.
Letöltend&#337; az archívumokból: 0B/350kB
E m&#369;velet után további 1.249kB lemez-területetet használok fel.
Folytatni akarod [Y/n]? y
FIGYELEM: Az alábbi csomagok nem hitelesíthet&#337;k!
  libavfilter1 ffmpeg
Valóban telepíted e csomagokat ellen&#337;rzés nélkül (i/N)? y
(Adatbázis olvasása ... Most 170048 fájl és könyvtár telepített.)
Kicsomagolás: libavfilter1 innen: .../libavfilter1_4%3a0.6-2ubuntu6_amd64.deb ...
dpkg: hibás feldolgozás: /var/cache/apt/archives/libavfilter1_4%3a0.6-2ubuntu6_amd64.deb (--unpack):
 hibás fájlrendszer tarfájl -- hibás csomag archívum
Kicsomagolás: ffmpeg innen: .../ffmpeg_4%3a0.6-2ubuntu6_amd64.deb ...
dpkg-deb (alfolyamat): adatok: internal gzip read error: '<fd:0>: invalid distance too far back'
dpkg-deb: <decompress> alfolyamat 2 hibakóddal kilépett
dpkg: hibás feldolgozás: /var/cache/apt/archives/ffmpeg_4%3a0.6-2ubuntu6_amd64.deb (--unpack):
 short read on buffer copy for háttér dpkg-deb `./etc/ffserver.conf' során
Hibák történtek a feldolgozáskor:
 /var/cache/apt/archives/libavfilter1_4%3a0.6-2ubuntu6_amd64.deb
 /var/cache/apt/archives/ffmpeg_4%3a0.6-2ubuntu6_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

(sorry, half of it is in Hungarian since my ubuntu is too, well it says that the .tar file is wrong)

So any ideas? I get the same error using synaptics. I use Ubuntu 10.10 64bit (2.6.35).

Yours3lf

---

### Post by realzippy on 2010-12-05
...sorry,but suggest to change the language settings temporarily to english and post again,have no clue whats going wrong...something with gunzip..?
Have a link to that .tar file?

---

### Post by sikander3786 on 2010-12-05
> **realzippy said:**
> ...sorry,but suggest to change the language settings temporarily to english and post again,have no clue whats going wrong...something with gunzip..?
Have a link to that .tar file?
I make a guess that there is some problem with archives.

**To the OP:**

Welcome to the forums :-)

Try cleaning up your apt cache by,

```
sudo apt-get clean
```

And then try to re-install the packages. If it doesn't help, we need to see your output in English please ;-)

---

### Post by Yours3lf22 on 2010-12-05
pfff, i was so upset that I reinstalled the ubuntu, and now it just went flawlessly... dunno what i did wrong :(

but anyways thanks for your help :)

---

### Post by Yours3lf22 on 2010-12-06
found the source of the problem:

I have the ESET anti-virus software which blocks the install of all programs:) even if I try it as an admin...

I sent them an e-mail, we'll see if there's a solution for this...

---

### Post by Yours3lf22 on 2010-12-07
They wrote back it's gonna be corrected in the next release :)

---

