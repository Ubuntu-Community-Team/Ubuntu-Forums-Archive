---
title: "songbird wont start"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by tadcan on 2009-07-07
I installed songbird from the repos, but it wont start. If I try to start it a second time I get a message saying songbird is already running but not responding. In system monitor songbird is listed as 'sleeping'. 

Any ideas?

---

### Post by nhasian on 2009-07-07
try to start songbird from the terminal to see what error messages it produces when it tries to run.  post them here so we can help you further troubleshoot.

---

### Post by tadcan on 2009-07-07
Hopefully someone will know what this means ;)

```
*** glibc detected *** ././songbird-bin: free(): invalid pointer: 0xb066be20 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7d7f604]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb7d815b6]
/usr/lib/libvisual-0.4.so.0(visual_mem_free+0x21)[0xb057c141]
/usr/lib/libvisual-0.4.so.0[0xb0573407]
/usr/lib/libvisual-0.4.so.0(visual_plugin_get_list+0x73)[0xb05735e3]
/usr/lib/libvisual-0.4.so.0(visual_init+0x291)[0xb0582ec1]
/usr/lib/gstreamer-0.10/libgstlibvisual.so[0xb05b5273]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb339fb2a]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_plugin_load_file+0x93f)[0xb33a06f1]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb33acab6]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_registry_scan_path+0x135)[0xb33acc5b]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb335834f]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb335883b]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3358ea6]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb335946e]
/usr/lib/libglib-2.0.so.0(g_option_context_parse+0x5ab)[0xb6b5fdcb]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_init_check+0xf1)[0xb335760b]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_init+0x32)[0xb3357715]
/usr/share/Songbird/lib/sbGStreamerMediacore.so(_ZN18sbGStreamerService4InitEv+0x9ff)[0xb32009e7]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3209a01]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb321da56]
/usr/share/Songbird/xulrunner/libxul.so[0xb762fb89]
/usr/share/Songbird/xulrunner/libxul.so[0xb762f04b]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb321aa3f]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb321aa69]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb321a215]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3208071]
/usr/share/Songbird/lib/sbGStreamerMediacore.so(_ZN27sbGStreamerMediacoreFactory4InitEv+0x46)[0xb32088e0]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3209961]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb321da56]
/usr/share/Songbird/xulrunner/libxul.so[0xb762fb89]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb43891c5]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb43891f2]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb4388a8d]
/usr/share/Songbird/components/sbMediacoreManager.so(_ZN8nsCOMPtrI19sbIMediacoreFactoryEC1ERK15nsCOMPtr_helper+0x2d)[0xb4370159]
/usr/share/Songbird/components/sbMediacoreManager.so(_ZN18sbMediacoreManager4InitEv+0x1b9)[0xb436d15b]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb436d4f4]
/usr/share/Songbird/xulrunner/libxul.so[0xb760c877]
/usr/share/Songbird/xulrunner/libxul.so[0xb760ce1c]
/usr/share/Songbird/xulrunner/libxul.so[0xb6e9c7a0]
/usr/share/Songbird/xulrunner/libxul.so(XRE_main+0x19af)[0xb6e9a481]
././songbird-bin[0x8048f40]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7d26775]
././songbird-bin[0x8048bb1]
======= Memory map: ========
08048000-0804e000 r-xp 00000000 08:02 240253     /usr/share/Songbird/songbird-bin
0804e000-0804f000 rw-p 00006000 08:02 240253     /usr/share/Songbird/songbird-bin
089e1000-08a02000 rw-p 089e1000 00:00 0          [heap]
b0562000-b059e000 r-xp 00000000 08:02 10305      /usr/lib/libvisual-0.4.so.0.0.0
b059e000-b059f000 r--p 0003b000 08:02 10305      /usr/lib/libvisual-0.4.so.0.0.0
b059f000-b05a0000 rw-p 0003c000 08:02 10305      /usr/lib/libvisual-0.4.so.0.0.0
b05a8000-b05ae000 rw-p b05a8000 00:00 0 
b05b3000-b05b9000 r-xp 00000000 08:02 38484      /usr/lib/gstreamer-0.10/libgstlibvisual.so
b05b9000-b05ba000 r--p 00005000 08:02 38484      /usr/lib/gstreamer-0.10/libgstlibvisual.so
b05ba000-b05bb000 rw-p 00006000 08:02 38484      /usr/lib/gstreamer-0.10/libgstlibvisual.so
b05bb000-b05c4000 r-xp 00000000 08:02 129140     /usr/lib/gstreamer-0.10/libgstdvdspu.so
b05c4000-b05c5000 r--p 00008000 08:02 129140     /usr/lib/gstreamer-0.10/libgstdvdspu.so
b05c5000-b05c6000 rw-p 00009000 08:02 129140     /usr/lib/gstreamer-0.10/libgstdvdspu.so
b05c6000-b05e0000 r-xp 00000000 08:02 9506       /usr/lib/libcdio.so.7.1.0
b05e0000-b05e1000 r--p 00019000 08:02 9506       /usr/lib/libcdio.so.7.1.0
b05e1000-b05e2000 rw-p 0001a000 08:02 9506       /usr/lib/libcdio.so.7.1.0
b05e2000-b05e6000 rw-p b05e2000 00:00 0 
b05e6000-b05fc000 r-xp 00000000 08:02 23285      /usr/lib/libmpeg2.so.0.0.0
b05fc000-b05fd000 r--p 00015000 08:02 23285      /usr/lib/libmpeg2.so.0.0.0
b05fd000-b05fe000 rw-p 00016000 08:02 23285      /usr/lib/libmpeg2.so.0.0.0
b05fe000-b0700000 rw-p b05fe000 00:00 0 
b0704000-b0717000 r-xp 00000000 08:02 129165     /usr/lib/gstreamer-0.10/libgstnsf.so
b0717000-b0718000 r--p 00012000 08:02 129165     /usr/lib/gstreamer-0.10/libgstnsf.so
b0718000-b0719000 rw-p 00013000 08:02 129165     /usr/lib/gstreamer-0.10/libgstnsf.so
b0719000-b0722000 rw-p b0719000 00:00 0 
b0722000-b0725000 r-xp 00000000 08:02 127689     /usr/lib/gstreamer-0.10/libgstcdio.so
b0725000-b0726000 r--p 00002000 08:02 127689     /usr/lib/gstreamer-0.10/libgstcdio.so
b0726000-b0727000 rw-p 00003000 08:02 127689     /usr/lib/gstreamer-0.10/libgstcdio.so
b0727000-b0794000 r-xp 00000000 08:02 10201      /usr/lib/libschroedinger-1.0.so.0.1.0
b0794000-b0795000 r--p 0006d000 08:02 10201      /usr/lib/libschroedinger-1.0.so.0.1.0
b0795000-b0796000 rw-p 0006e000 08:02 10201      /usr/lib/libschroedinger-1.0.so.0.1.0
b0796000-b0797000 rw-p b0796000 00:00 0 
b0797000-b0842000 r-xp 00000000 08:02 103579     /usr/lib/i686/cmov/libavformat.so.52.31.0
b0842000-b0843000 r--p 000ab000 08:02 103579     /usr/lib/i686/cmov/libavformat.so.52.31.0
b0843000-b0849000 rw-p 000ac000 08:02 103579     /usr/lib/i686/cmov/libavformat.so.52.31.0
b0849000-b0895000 rw-p b0849000 00:00 0 
b0895000-b0d53000 r-xp 00000000 08:02 103557     /usr/lib/i686/cmov/libavcodec.so.52.20.0
b0d53000-b0d54000 r--p 004be000 08:02 103557     /usr/lib/i686/cmov/libavcodec.so.52.20.0
b0d54000-b0d5d000 rw-p 004bf000 08:02 103557     /usr/lib/i686/cmov/libavcodec.so.52.20.0
b0d5d000-b106a000 rw-p b0d5d000 00:00 0 
b106a000-b10fb000 r-xp 00000000 08:02 10226      /usr/lib/libsmbios.so.2.1.0
b10fb000-b10ff000 r--p 00090000 08:02 10226      /usr/lib/libsmbios.so.2.1.0
b10ff000-b1100000 rw-p 00094000 08:02 10226      /usr/lib/libsmbios.so.2.1.0
b1100000-b1200000 rw-p b1100000 00:00 0 
b1202000-b1209000 r-xp 00000000 08:02 50770      /usr/lib/gstreamer-0.10/libgstgconfelements.so
b1209000-b120a000 r--p 00006000 08:02 50770      /usr/lib/gstreamer-0.10/libgstgconfelements.so
b120a000-b120b000 rw-p 00007000 08:02 50770      /usr/lib/gstreamer-0.10/libgstgconfelements.so
b120b000-b1215000 r-xp 00000000 08:02 127828     /usr/lib/gstreamer-0.10/libgstmpeg2dec.so
b1215000-b1216000 r--p 00009000 08:02 127828     /usr/lib/gstreamer-0.10/libgstmpeg2dec.so
b1216000-b1217000 rw-p 0000a000 08:02 127828     /usr/lib/gstreamer-0.10/libgstmpeg2dec.so
b1217000-b1249000 r-xp 00000000 08:02 12724      /usr/lib/gstreamer-0.10/libgstffmpeg.so
b1249000-b124a000 r--p 00031000 08:02 12724      /usr/lib/gstreamer-0.10/libgstffmpeg.so
b124a000-b124b000 rw-p 00032000 08:02 12724      /usr/lib/gstreamer-0.10/libgstffmpeg.so
b124b000-b125d000 r-xp 00000000 08:02 38511      /usr/lib/gstreamer-0.10/libgstvideo4linux.so
b125d000-b125e000 r--p 00012000 08:02 38511      /usr/lib/gstreamer-0.10/libgstvideo4linux.so
b125e000-b125f000 rw-p 00013000 08:02 38511      /usr/lib/gstreamer-0.10/libgstvideo4linux.so
b125f000-b126f000 r-xp 00000000 08:02 231785     /usr/lib/libhal.so.1.0.0
b126f000-b1270000 r--p 0000f000 08:02 231785     /usr/lib/libhal.so.1.0.0
b1270000-b1271000 rw-p 00010000 08:02 231785     /usr/lib/libhal.so.1.0.0
b1272000-b1276000 r-xp 00000000 08:02 129176     /usr/lib/gstreamer-0.10/libgstscaletempoplugin.so
b1276000-b1277000 r--p 00003000 08:02 129176     /usr/lib/gstreamer-0.10/libgstscaletempoplugin.so
b1277000-b1278000 rw-p 00004000 08:02 129176     /usr/lib/gstreamer-0.10/libgstscaletempoplugin.so
b1278000-b1282000 r-xp 00000000 08:02 127708     /usr/lib/gstreamer-0.10/libgstdvdread.so
b1282000-b1283000 r--p 00009000 08:02 127708     /usr/lib/gstreamer-0.10/libgstdvdread.so
b1283000-b1284000 rw-p 0000a000 08:02 127708     /usr/lib/gstreamer-0.10/libgstdvdread.so
b1284000-b129e000 r-xp 00000000 08:02 26086      /usr/lib/gio/modules/libgvfsdbus.so
b129e000-b129f000 r--p 00019000 08:02 26086      /usr/lib/gio/modules/libgvfsdbus.so
b129f000-b12a0000 rw-p 0001a000 08:02 26086      /usr/lib/gio/modules/libgvfsdbus.so
b12a0000-b12b2000 r-xp 00000000 08:02 20100      /usr/lib/libgvfscommon.so.0.0.0
b12b2000-b12b3000 r--p 00012000 08:02 20100      /usr/lib/libgvfscommon.so.0.0.0
b12b3000-b12b4000 rw-p 00013000 08:02 20100      /usr/lib/libgvfscommon.so.0.0.0
b12b4000-b12be000 r-xp 00000000 08:02 13034      /usr/lib/libgstapp-0.10.so.0.0.0
b12be000-b12bf000 r--p 00009000 08:02 13034      /usr/lib/libgstapp-0.10.so.0.0.0
b12bf000-b12c0000 rw-p 0000a000 08:02 13034      /usr/lib/libgstapp-0.10.so.0.0.0
b12c0000-b12c5000 r-xp 00000000 08:02 50774      /usr/lib/gstreamer-0.10/libgsthalelements.so
b12c5000-b12c600

```

---

### Post by nhasian on 2009-07-07
try removing the following packages and then starting songbird:

```
sudo apt-get remove libvisual-0.4-plugins libvisual-projectm
```

---

### Post by tadcan on 2009-07-07
That worked, thanks

---

### Post by Teabicky on 2009-07-09
> **nhasian said:**
> try removing the following packages and then starting songbird:

```
sudo apt-get remove libvisual-0.4-plugins libvisual-projectm
```

This worked for me too, thanks!!

---

### Post by JairunCaloth on 2009-07-15
> **nhasian said:**
> try removing the following packages and then starting songbird:

```
sudo apt-get remove libvisual-0.4-plugins libvisual-projectm
```

This worked for me on a similar crash in 64 bit Jaunty. Song bird was installed from download off the songbird site.

---

