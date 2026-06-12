---
title: "Songbird error"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by adobrakic on 2009-04-16
I downloaded and installed Songbird 1.1.2 64-bit, but I cannot open it. In terminal, I get:

```
ado@ado-laptop:~$ sudo songbird
[sudo] password for ado: 
*** glibc detected *** ././songbird-bin: free(): invalid pointer: 0x00007fae1cebc5c0 ***
======= Backtrace: =========
/lib/libc.so.6[0x7fae3c3b7a58]
/lib/libc.so.6(cfree+0x76)[0x7fae3c3ba0a6]
/usr/lib/libvisual-0.4.so.0(visual_mem_free+0xe)[0x7fae14cb04ce]
/usr/lib/libvisual-0.4.so.0[0x7fae14ca9646]
/usr/lib/libvisual-0.4.so.0(visual_plugin_get_list+0x48)[0x7fae14ca97d8]
/usr/lib/libvisual-0.4.so.0(visual_init+0x243)[0x7fae14cb6703]
/usr/lib64/gstreamer-0.10/libgstlibvisual.so[0x7fae14ed7c24]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0x7fae2aba132a]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_plugin_load_file+0x64b)[0x7fae2aba1be3]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0x7fae2ababf41]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_registry_scan_path+0x11f)[0x7fae2abac0c4]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0x7fae2ab5c7a5]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0x7fae2ab5cc13]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0x7fae2ab5d1cf]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0x7fae2ab5d753]
/usr/lib/libglib-2.0.so.0(g_option_context_parse+0x528)[0x7fae38762908]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_init_check+0xd6)[0x7fae2ab5bb56]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_init+0x29)[0x7fae2ab5bc43]
/usr/share/Songbird/lib/sbGStreamerMediacore.so(_ZN18sbGStreamerService4InitEv+0xacc)[0x7fae287fdcb8]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0x7fae28804e51]
/usr/share/Songbird/xulrunner/libxul.so[0x7fae3a299e7f]
/usr/share/Songbird/xulrunner/libxul.so[0x7fae3a2999c9]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0x7fae2880a6d3]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0x7fae2880a700]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0x7fae28809ee8]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0x7fae28803b14]
/usr/share/Songbird/lib/sbGStreamerMediacore.so(_ZN27sbGStreamerMediacoreFactory4InitEv+0x4b)[0x7fae288040a1]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0x7fae28804dc1]
/usr/share/Songbird/xulrunner/libxul.so[0x7fae3a299e7f]
/usr/share/Songbird/components/sbMediacoreManager.so[0x7fae2d76bae3]
/usr/share/Songbird/components/sbMediacoreManager.so[0x7fae2d76bb20]
/usr/share/Songbird/components/sbMediacoreManager.so[0x7fae2d76b402]
/usr/share/Songbird/components/sbMediacoreManager.so(_ZN8nsCOMPtrI19sbIMediacoreFactoryEC1ERK15nsCOMPtr_helper+0x1c)[0x7fae2d757a24]
/usr/share/Songbird/components/sbMediacoreManager.so(_ZN18sbMediacoreManager4InitEv+0x1ff)[0x7fae2d7559cb]
/usr/share/Songbird/components/sbMediacoreManager.so[0x7fae2d755da0]
/usr/share/Songbird/xulrunner/libxul.so[0x7fae3a27a79a]
/usr/share/Songbird/xulrunner/libxul.so[0x7fae3a27ac6c]
/usr/share/Songbird/xulrunner/libxul.so[0x7fae39b4fc76]
/usr/share/Songbird/xulrunner/libxul.so(XRE_main+0x177d)[0x7fae39b4d947]
././songbird-bin[0x401417]
/lib/libc.so.6(__libc_start_main+0xe6)[0x7fae3c35c466]
././songbird-bin[0x401009]
======= Memory map: ========
00400000-00408000 r-xp 00000000 08:05 8463393                            /usr/share/Songbird/songbird-bin
00608000-00609000 rw-p 00008000 08:05 8463393                            /usr/share/Songbird/songbird-bin
0179f000-017c0000 rw-p 0179f000 00:00 0                                  [heap]
403bd000-403be000 ---p 403bd000 00:00 0 
403be000-40bbe000 rwxp 403be000 00:00 0 
411e9000-411ea000 ---p 411e9000 00:00 0 
411ea000-419ea000 rwxp 411ea000 00:00 0 
7fae132d1000-7fae132d2000 r-xp 00000000 08:05 8437798                    /usr/lib/tls/libnvidia-tls.so.180.11
7fae132d2000-7fae133d2000 ---p 00001000 08:05 8437798                    /usr/lib/tls/libnvidia-tls.so.180.11
7fae133d2000-7fae133d3000 rw-p 00001000 08:05 8437798                    /usr/lib/tls/libnvidia-tls.so.180.11
7fae14c97000-7fae14cd4000 r-xp 00000000 08:05 8064666                    /usr/lib/libvisual-0.4.so.0.0.0
7fae14cd4000-7fae14ed3000 ---p 0003d000 08:05 8064666                    /usr/lib/libvisual-0.4.so.0.0.0
7fae14ed3000-7fae14ed4000 r--p 0003c000 08:05 8064666                    /usr/lib/libvisual-0.4.so.0.0.0
7fae14ed4000-7fae14ed5000 rw-p 0003d000 08:05 8064666                    /usr/lib/libvisual-0.4.so.0.0.0
7fae14ed5000-7fae14edb000 r-xp 00000000 08:05 8077767                    /usr/lib/gstreamer-0.10/libgstlibvisual.so
7fae14edb000-7fae150da000 ---p 00006000 08:05 8077767                    /usr/lib/gstreamer-0.10/libgstlibvisual.so
7fae150da000-7fae150db000 r--p 00005000 08:05 8077767                    /usr/lib/gstreamer-0.10/libgstlibvisual.so
7fae150db000-7fae150dc000 rw-p 00006000 08:05 8077767                    /usr/lib/gstreamer-0.10/libgstlibvisual.so
7fae150dc000-7fae150ea000 r-xp 00000000 08:05 1368158                    /usr/lib/gstreamer-0.10/libgstmpegtsparse.so
7fae150ea000-7fae152e9000 ---p 0000e000 08:05 1368158                    /usr/lib/gstreamer-0.10/libgstmpegtsparse.so
7fae152e9000-7fae152ea000 r--p 0000d000 08:05 1368158                    /usr/lib/gstreamer-0.10/libgstmpegtsparse.so
7fae152ea000-7fae152eb000 rw-p 0000e000 08:05 1368158                    /usr/lib/gstreamer-0.10/libgstmpegtsparse.so
7fae152eb000-7fae152fa000 r-xp 00000000 08:05 8063925                    /usr/lib/libfaac.so.0.0.0
7fae152fa000-7fae154f9000 ---p 0000f000 08:05 8063925                    /usr/lib/libfaac.so.0.0.0
7fae154f9000-7fae154fa000 r--p 0000e000 08:05 8063925                    /usr/lib/libfaac.so.0.0.0
7fae154fa000-7fae154fd000 rw-p 0000f000 08:05 8063925                    /usr/lib/libfaac.so.0.0.0
7fae154fd000-7fae15502000 r-xp 00000000 08:05 1368115                    /usr/lib/gstreamer-0.10/libgstfaac.so
7fae15502000-7fae15701000 ---p 00005000 08:05 1368115                    /usr/lib/gstreamer-0.10/libgstfaac.so
7fae15701000-7fae15702000 r--p 00004000 08:05 1368115                    /usr/lib/gstreamer-0.10/libgstfaac.so
7fae15702000-7fae15703000 rw-p 00005000 08:05 1368115                    /usr/lib/gstreamer-0.10/libgstfaac.so
7fae15703000-7fae15713000 r-xp 00000000 08:05 8064232                    /usr/lib/libhal.so.1.0.0
7fae15713000-7fae15912000 ---p 00010000 08:05 8064232                    /usr/lib/libhal.so.1.0.0
7fae15912000-7fae15913000 r--p 0000f000 08:05 8064232                    /usr/lib/libhal.so.1.0.0
7fae15913000-7fae15914000 rw-p 00010000 08:05 8064232                    /usr/lib/libhal.so.1.0.0
7fae15914000-7fae15919000 r-xp 00000000 08:05 1368246                    /usr/lib/gstreamer-0.10/libgsthalelements.so
7fae15919000-7fae15b18000 ---p 00005000 08:05 1368246                    /usr/lib/gstreamer-0.10/libgsthalelements.so
7fae15b18000-7fae15b19000 r--p 00004000 08:05 1368246                    /usr/lib/gstreamer-0.10/libgsthalelements.so
7fae15b19000-7fae15b1a000 rw-p 00005000 08:05 1368246                    /usr/lib/gstreamer-0.10/libgsthalelements.so
7fae15b1a000-7fae15b80000 r-xp 00000000 08:05 8064621                    /usr/lib/libtag.so.1.5.0
7fae15b80000-7fae15d7f000 ---p 00066000 08:05 8064621                    /usr/lib/libtag.so.1.5.0
7fae15d7f000-7fae15d81000 r--p 00065000 08:05 8064621                    /usr/lib/libtag.so.1.5.0
7fae15d81000-7fae15d82000 rw-p 00067000 08:05 8064621                    /usr/lib/libtag.so.1.5.0
7fae15d82000-7fae15d8d000 r-xp 00000000 08:05 1368269                    /usr/lib/gstreamer-0.10/libgsttaglib.so
7fae15d8d000-7fae15f8c000 ---p 0000b000 08:05 1368269                    /usr/lib/gstreamer-0.10/libgsttaglib.so
7fae15f8c000-7fae15f8d000 r--p 0000a000 08:05 1368269                    /usr/lib/gstreamer-0.10/libgsttaglib.so
7fae15f8d000-7fae15f8e000 rw-p 0000b000 08:05 1368269                    /usr/lib/gstreamer-0.10/libgsttaglib.so
7fae15f8e000-7fae15f99000 r-xp 00000000 08:05 1368258                    /usr/lib/gstreamer-0.10/libgstossaudio.so
7fae15f99000-7fae16199000 ---p 0000b000 08:05 1368258                    /usr/lib/gstreamer-0.10/libgstossaudio.so
7fae16199000-7fae1619a000 r--p 0000b000 08:05 1368258                    /usr/lib/gstreamer-0.10/libgstossaudio.so
7fae1619a000-7fae1619b000 rw-p 0000c000 08:05 1368258                    /usr/lib/gstreamer-0.10/libgstossaudio.so
7fae1619b000-7fae161ac000 r-xp 00000000 08:05 8061420                    /usr/lib/libv4lconvert.so.0
7fae161ac000-7fae163ab000 ---p 00011000 08:05 8061420                    /usr/lib/libv4lconvert.so.0
7fae163ab000-7fae163ac000 r--p 00010000 08:05 8061420                    /usr/lib/libv4lconvert.so.0
7fae163ac000-7fae163ad000 rw-p 00011000 08:05 8061420                    /usr/lib/libv4lconvert.so.0
7fae163ad000-7fae163fd000 rw-p 7fae163ad000 00:00 0 
7fae163fd000-7fae16403000 r-xp 00000000 08:05 8061373                    /usr/lib/libv4l2.so.0
7fae16403000-7fae16602000 ---p 00006000 08:05 8061373                    /usr/lib/libv4l2.so.0
7fae16602000-7fae16603000 r--p 00005000 08:05 8061373                    /usr/lib/libv4l2.so.0
7fae16603000-7fae16607000 rw-p 00006000 08:05 8061373                    /usr/lib/libv4l2.so.0
7fae16607000-7fae1661d000 r-xp 00000000 08:05 1368271                    /usr/lib/gstreamer-0.10/libgstvideo4linux2.soCould not initialize GStreamer: Error re-scanning registry , child terminated by signal
ado@ado-laptop:~$ 


```

---

### Post by ChaiTan on 2009-04-16
Try removing libvisual-0.4-plugins and then run songbird(there's no need to run it as root).
```
sudo apt-get remove libvisual-0.4-plugins
```

---

### Post by adobrakic on 2009-04-16
Thanks, it worked. :D

I get the following errors:

```

ado@ado-laptop:~$ songbird
/home/ado/.themes/Dust/gtk-2.0/gtkrc:698: error: unexpected identifier `highlight_shade', expected character `}'
/home/ado/.themes/Dust/gtk-2.0/gtkrc:698: error: unexpected identifier `highlight_shade', expected character `}'
/home/ado/.themes/Dust/gtk-2.0/gtkrc:698: error: unexpected identifier `highlight_shade', expected character `}'
/home/ado/.themes/Dust/gtk-2.0/gtkrc:698: error: unexpected identifier `highlight_shade', expected character `}'
ado@ado-laptop:~$ 

```

But I don't think it's anything to worry about.

---

### Post by aitjcize on 2009-07-25
> **ChaiTan said:**
> Try removing libvisual-0.4-plugins and then run songbird(there's no need to run it as root).
```
sudo apt-get remove libvisual-0.4-plugins
```

any side effects?

---

### Post by Durden on 2009-07-25
In your first post you had: "ado@ado-laptop:~$ sudo songbird"

Why are you running songbird as root?

---

