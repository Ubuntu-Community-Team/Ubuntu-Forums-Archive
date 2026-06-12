---
title: "Installing a video converter for PSP"
date: 2011-03-27
forum: New to Ubuntu
---

### Post by ASKidwai on 2011-03-27
I know that this has been posted many times here but I really need a more updated guide for installing it.
I tried installing it in terminal but it won't work. 
I installed the libraries and trees and stuff like that. This the result of installing the install.sh 
```
aleem@aleem-laptop:~/pspvc-install-0.3$ sudo sh install.sh
mkdir: cannot create directory `work': File exists
Installer force X264 installation
tar: Record size = 8 blocks
x264-svn/
x264-svn/matroska.h
x264-svn/configure
x264-svn/Makefile
x264-svn/matroska.c
x264-svn/doc/
x264-svn/doc/vui.txt
x264-svn/doc/ratecontrol.txt
x264-svn/doc/regression_test.txt
x264-svn/tools/
x264-svn/tools/checkasm.c
x264-svn/tools/avc2avi.c
x264-svn/tools/.cvsignore
x264-svn/tools/Jamfile
x264-svn/tools/countquant_x264.pl
x264-svn/tools/x264-rd.sh
x264-svn/tools/xyuv.c
x264-svn/tools/q_matrix_jvt.cfg
x264-svn/extras/
x264-svn/extras/getopt.h
x264-svn/extras/getopt.c
x264-svn/extras/stdint.h
x264-svn/gtk/
x264-svn/gtk/x264_gtk_i18n.h
x264-svn/gtk/x264_gtk_encode_status_window.h
x264-svn/gtk/x264.ico
x264-svn/gtk/x264_gtk_bitrate.c
x264-svn/gtk/x264_gtk_bitrate.h
x264-svn/gtk/Makefile
x264-svn/gtk/x264_gtk_encode_private.h
x264-svn/gtk/fr.po
x264-svn/gtk/x264_gtk_encode_encode.c
x264-svn/gtk/x264_gtk_encode_encode.h
x264-svn/gtk/x264_gtk_rc.c
x264-svn/gtk/x264_gtk_encode.c
x264-svn/gtk/x264gtk.rc
x264-svn/gtk/x264_gtk_private.h
x264-svn/gtk/x264_gtk_encode_main_window.c
x264-svn/gtk/test.c
x264-svn/gtk/x264_gtk_rc.h
x264-svn/gtk/x264_gtk_enum.h
x264-svn/gtk/x264_gtk_more.c
x264-svn/gtk/x264_gtk_more.h
x264-svn/gtk/x264_gtk_cqm.c
x264-svn/gtk/x264_gtk_encode_main_window.h
x264-svn/gtk/x264_gtk_cqm.h
x264-svn/gtk/x264_gtk.c
x264-svn/gtk/x264.png
x264-svn/gtk/x264_gtk_mb.h
x264-svn/gtk/x264_gtk_demuxers.h
x264-svn/gtk/x264_gtk.h
x264-svn/gtk/x264_gtk_mb.c
x264-svn/gtk/x264_gtk_encode_status_window.c
x264-svn/muxers.c
x264-svn/build/
x264-svn/build/win32/
x264-svn/build/win32/x264.dsw
x264-svn/build/win32/libx264.vcproj
x264-svn/build/win32/x264.sln
x264-svn/build/win32/x264.vcproj
x264-svn/build/win32/x264.dsp
x264-svn/build/win32/libx264.dsp
x264-svn/x264.c
x264-svn/x264.h
x264-svn/COPYING
x264-svn/encoder/
x264-svn/encoder/me.h
x264-svn/encoder/me.c
x264-svn/encoder/set.c
x264-svn/encoder/analyse.c
x264-svn/encoder/encoder.c
x264-svn/encoder/eval.c
x264-svn/encoder/analyse.h
x264-svn/encoder/macroblock.c
x264-svn/encoder/cavlc.c
x264-svn/encoder/slicetype.c
x264-svn/encoder/ratecontrol.c
x264-svn/encoder/set.h
x264-svn/encoder/macroblock.h
x264-svn/encoder/rdo.c
x264-svn/encoder/cabac.c
x264-svn/encoder/ratecontrol.h
x264-svn/common/
x264-svn/common/frame.c
x264-svn/common/pixel.h
x264-svn/common/visualize.h
x264-svn/common/set.c
x264-svn/common/dct.c
x264-svn/common/frame.h
x264-svn/common/cpu.c
x264-svn/common/macroblock.c
x264-svn/common/common.c
x264-svn/common/quant.h
x264-svn/common/visualize.c
x264-svn/common/common.h
x264-svn/common/amd64/
x264-svn/common/amd64/cpu-a.asm
x264-svn/common/amd64/mc-a.asm
x264-svn/common/amd64/pixel-a.asm
x264-svn/common/amd64/deblock-a.asm
x264-svn/common/amd64/dct-a.asm
x264-svn/common/amd64/mc-a2.asm
x264-svn/common/amd64/amd64inc.asm
x264-svn/common/amd64/pixel-sse2.asm
x264-svn/common/amd64/quant-a.asm
x264-svn/common/amd64/predict-a.asm
x264-svn/common/dct.h
x264-svn/common/mc.h
x264-svn/common/bs.h
x264-svn/common/display.h
x264-svn/common/quant.c
x264-svn/common/display-x11.c
x264-svn/common/mdate.c
x264-svn/common/predict.h
x264-svn/common/i386/
x264-svn/common/i386/cpu-a.asm
x264-svn/common/i386/mc-a.asm
x264-svn/common/i386/pixel.h
x264-svn/common/i386/pixel-a.asm
x264-svn/common/i386/deblock-a.asm
x264-svn/common/i386/mc-c.c
x264-svn/common/i386/dct-a.asm
x264-svn/common/i386/quant.h
x264-svn/common/i386/mc-a2.asm
x264-svn/common/i386/pixel-sse2.asm
x264-svn/common/i386/dct.h
x264-svn/common/i386/mc.h
x264-svn/common/i386/predict.h
x264-svn/common/i386/quant-a.asm
x264-svn/common/i386/predict-c.c
x264-svn/common/i386/i386inc.asm
x264-svn/common/i386/predict-a.asm
x264-svn/common/cabac.h
x264-svn/common/csp.c
x264-svn/common/set.h
x264-svn/common/predict.c
x264-svn/common/csp.h
x264-svn/common/clip1.h
x264-svn/common/sparc/
x264-svn/common/sparc/pixel.h
x264-svn/common/sparc/pixel.asm
x264-svn/common/ppc/
x264-svn/common/ppc/pixel.h
x264-svn/common/ppc/ppccommon.h
x264-svn/common/ppc/dct.c
x264-svn/common/ppc/dct.h
x264-svn/common/ppc/mc.h
x264-svn/common/ppc/pixel.c
x264-svn/common/ppc/mc.c
x264-svn/common/pixel.c
x264-svn/common/mc.c
x264-svn/common/macroblock.h
x264-svn/common/vlc.h
x264-svn/common/cabac.c
x264-svn/common/cpu.h
x264-svn/version.sh
x264-svn/muxers.h
x264-svn/config.guess
x264-svn/AUTHORS
Platform:   X86
System:     LINUX
avis input: no
mp4 output: no
pthread:    yes
gtk:        no
debug:      no
gprof:      no
PIC:        no
shared:     no
visualize:  no

You can run 'make' or 'make fprofiled' now.
rm -f .depend
( echo -n "`dirname common/mc.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer common/mc.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/predict.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer common/predict.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/pixel.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer common/pixel.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/macroblock.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer common/macroblock.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/frame.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer common/frame.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/dct.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer common/dct.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/cpu.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer common/cpu.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/cabac.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer common/cabac.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/common.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer common/common.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/mdate.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer common/mdate.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/csp.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer common/csp.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/set.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer common/set.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/quant.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer common/quant.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/analyse.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer encoder/analyse.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/me.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer encoder/me.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/ratecontrol.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer encoder/ratecontrol.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/set.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer encoder/set.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/macroblock.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer encoder/macroblock.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/cabac.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer encoder/cabac.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/cavlc.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer encoder/cavlc.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/encoder.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer encoder/encoder.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/eval.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer encoder/eval.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/i386/mc-c.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer common/i386/mc-c.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/i386/predict-c.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer common/i386/predict-c.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname x264.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer x264.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname matroska.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer matroska.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname muxers.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer muxers.c -MM -g0 ) 1>> .depend;
gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o x264.o x264.c
gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o muxers.o muxers.c
muxers.c: In function ‘read_frame_y4m’:
muxers.c:281: warning: dereferencing type-punned pointer will break strict-aliasing rules
gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o encoder/set.o encoder/set.c
nasm -O2 -f elf -Icommon/i386/ -o common/i386/dct-a.o common/i386/dct-a.asm
make: nasm: Command not found
make: *** [common/i386/dct-a.o] Error 127
-e \E[01;31mERROR during compilation or installation of X264

```I was hoping that there would be a easy way to install a converter in Ubuntu. 
I tried Transmageddon but some plugins are not available in the packages. 
avidemux is long and I can't actually understand how to install it.

I am fairly new to Ubuntu. I can use the terminal and stuff like that but I am not really good at Ubuntu.
If it doesn't work, I may have to use the converters in Windows :ew: :(:(:(

BTW, I am using Ubuntu 10.04 LTS

---

### Post by ASKidwai on 2011-04-02
Arista Transcoder works :D

---

### Post by HermanAB on 2011-04-02
Well, ffmpeg can convert anything to anything without tears.  PSP conversion instructions are in the documentation files on LibAV.org.

---

### Post by qyot27 on 2011-04-02
The two problems with that script:
The error occurs because you likely have not installed NASM, since that's what stops the compile.

The version of x264 there is ancient (exactly *how* ancient, I'm not sure, but...).  x264 moved to Git a long time ago, and uses YASM now.

According to the latest x264 newsletter ([http://mailman.videolan.org/pipermail/x264-devel/2011-March/008353.html](http://mailman.videolan.org/pipermail/x264-devel/2011-March/008353.html)), "--device and automatic --level restriction support is in the works, as part of Google Code-In.  The patch is done, but needs review."  This means that conceivably, compliant PSP encodes would be doable with a minimum of effort from a normally-compiled x264 once the patch is committed (so long as the PSP is one of said devices, anyway).

---

