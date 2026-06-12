---
title: "problem compiling sources"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by ubunlilluz on 2008-12-19
hi,
i'm trying to install kmediafactory by the sources but i got this error when i ran "make". 
Is there nobody out there able to help me?
thanks


```
Configure summary
----------------------------------------------------------------------
Mandatory
- FontConfig ..................... Yes
- msgfmt ......................... Yes
- zip ............................ Yes
- ImageMagick >= 6.0 ............. Yes
- dvdauthor ...................... Yes
- mjpegtools ..................... Yes
----------------------------------------------------------------------
Optional
- DV import plugin (libdv) ....... Yes
- DVD info dialog (libdvdread) ... Yes
- Own DVD player (libxine) ....... Yes
- Support theora files (libtheora) Yes
- Slideshow (dvd-slideshow) ...... Yes
- office macro install (unopkg) .. Yes
----------------------------------------------------------------------

Good - your configure finished. Start make now

drlillux@dr:~/dwhelper/kmediafactory-0.5.2.4$ make
make  all-recursive
make[1]: Entering directory `/home/drlillux/dwhelper/kmediafactory-0.5.2.4'
Making all in doc
make[2]: Entering directory `/home/drlillux/dwhelper/kmediafactory-0.5.2.4/doc'
Making all in .
make[3]: Entering directory `/home/drlillux/dwhelper/kmediafactory-0.5.2.4/doc'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/drlillux/dwhelper/kmediafactory-0.5.2.4/doc'
Making all in en
make[3]: Entering directory `/home/drlillux/dwhelper/kmediafactory-0.5.2.4/doc/en'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/drlillux/dwhelper/kmediafactory-0.5.2.4/doc/en'
make[2]: Leaving directory `/home/drlillux/dwhelper/kmediafactory-0.5.2.4/doc'
Making all in ffmpeg
make[2]: Entering directory `/home/drlillux/dwhelper/kmediafactory-0.5.2.4/ffmpeg'
Making all in libavutil
make[3]: Entering directory `/home/drlillux/dwhelper/kmediafactory-0.5.2.4/ffmpeg/libavutil'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/drlillux/dwhelper/kmediafactory-0.5.2.4/ffmpeg/libavutil'
Making all in libavcodec
make[3]: Entering directory `/home/drlillux/dwhelper/kmediafactory-0.5.2.4/ffmpeg/libavcodec'
Making all in i386
make[4]: Entering directory `/home/drlillux/dwhelper/kmediafactory-0.5.2.4/ffmpeg/libavcodec/i386'
if /bin/bash ../../../libtool --silent --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../..  -DHAVE_AV_CONFIG_H -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_GNU_SOURCE -DCONFIG_DECODERS -DCONFIG_ENCODERS -DCONFIG_MUXERS -DCONFIG_DEMUXERS -I../../../ffmpeg/libavcodec/i386 -I../../../ffmpeg/libavcodec -I../../../ffmpeg/libavutil -I/usr/include/kde -I/usr/share/qt3/include -I.  -DQT_THREAD_SUPPORT  -D_REENTRANT -std=gnu99 -w -fomit-frame-pointer -msse -Os -g1 `echo -W -Wall -Wchar-subscripts -Wshadow -Wpointer-arith -Wmissing-prototypes -Wwrite-strings -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -O2   -Wformat-security -Wmissing-format-attribute | sed -e ' s/-funroll-loops//g; s/-g[0-9]/-g1/g; s/-O[0-9]/-Os/g'` -MT dsputil_mmx.lo -MD -MP -MF ".deps/dsputil_mmx.Tpo" \
	  -c -o dsputil_mmx.lo `test -f 'dsputil_mmx.c' || echo './'`dsputil_mmx.c; \
	then mv -f ".deps/dsputil_mmx.Tpo" ".deps/dsputil_mmx.Plo"; \
	else rm -f ".deps/dsputil_mmx.Tpo"; exit 1; \
	fi
h264dsp_mmx.c: In function 'h264_h_loop_filter_luma_mmx2':
dsputil_mmx.c:621: error: can't find a register in class 'GENERAL_REGS' while reloading 'asm'
dsputil_mmx.c:621: error: can't find a register in class 'GENERAL_REGS' while reloading 'asm'
dsputil_mmx.c:621: error: can't find a register in class 'GENERAL_REGS' while reloading 'asm'
dsputil_mmx.c:621: error: 'asm' operand has impossible constraints
dsputil_mmx.c:621: error: 'asm' operand has impossible constraints
dsputil_mmx.c:621: error: 'asm' operand has impossible constraints
dsputil_mmx.c:621: error: 'asm' operand has impossible constraints
h264dsp_mmx.c:206: error: 'asm' operand has impossible constraints
dsputil_mmx.c:621: error: 'asm' operand has impossible constraints
dsputil_mmx.c:621: error: 'asm' operand has impossible constraints
make[4]: *** [dsputil_mmx.lo] Error 1
make[4]: Leaving directory `/home/drlillux/dwhelper/kmediafactory-0.5.2.4/ffmpeg/libavcodec/i386'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/drlillux/dwhelper/kmediafactory-0.5.2.4/ffmpeg/libavcodec'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/drlillux/dwhelper/kmediafactory-0.5.2.4/ffmpeg'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/drlillux/dwhelper/kmediafactory-0.5.2.4'
make: *** [all] Error 2

```

---

### Post by Michael.Godawski on 2008-12-19
hi,

why not use the version which is in the repos, and install it via Synaptic?

---

### Post by ubunlilluz on 2008-12-20
> **Michael.Godawski said:**
> hi,

why not use the version which is in the repos, and install it via Synaptic?

i tried it but it doesn't work it has some bugs

---

### Post by andrew.46 on 2008-12-20
Hi,

Have you tried to load all the -dev files used in the original Ubuntu compilation? The can be done easily with:

```
$ sudo apt-get build-dep kmediafactory
```

This one looks like a complex one to install with a list of heavy-weight dependencies:

[http://aryhma.oy.cx/damu/software/kmediafactory/download.html](http://aryhma.oy.cx/damu/software/kmediafactory/download.html)

In particular I hope that the program is happy to be compiled against the older versions of MPlayer and ffmpeg that are available in the Ubuntu repositories. Otherwise you may have to install the svn versions and I suspect the latest git x264 as well. Guides for this can be found on these forums.

All the best with this one!

  Andrew

---

