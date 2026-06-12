---
title: "songbird - 2 copies of it open, nothing appears on screen"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by jamesey on 2009-03-24
I installed the newest songbird from Getdeb. 

When I go to the applications menu to open it, nothing happens. However, I noticed in system manager that 2 copies of songbird were running. I successfully tried uninstalling and re-installing songbird through terminal and package manager. Unfortunately I still get the same issue. I've tried deleting my songbird profile in my home folder, but that didnt help. Any suggestions?

---

### Post by MrWES on 2009-03-24
> **jamesey said:**
> I installed the newest songbird from Getdeb. 

When I go to the applications menu to open it, nothing happens. However, I noticed in system manager that 2 copies of songbird were running. I successfully tried uninstalling and re-installing songbird through terminal and package manager. Unfortunately I still get the same issue. I've tried deleting my songbird profile in my home folder, but that didnt help. Any suggestions?

Try starting songbird from the terminal and monitor for error messages.

Bill

---

### Post by jamesey on 2009-03-24
> **MrWES said:**
> Try starting songbird from the terminal and monitor for error messages.

Bill

```
james@james-ubuntu:~$ songbird
*** glibc detected *** ././songbird-bin: double free or corruption (out): 0xb3980da0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7d83454]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb7d854b6]
/usr/lib/libvisual-0.4.so.0(visual_mem_free+0x21)[0xb33c3141]
/usr/lib/libvisual-0.4.so.0[0xb33ba407]
/usr/lib/libvisual-0.4.so.0(visual_plugin_get_list+0x73)[0xb33ba5e3]
/usr/lib/libvisual-0.4.so.0(visual_init+0x291)[0xb33c9ec1]
/usr/lib/gstreamer-0.10/libgstlibvisual.so[0xb35141f4]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3ea52f6]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_plugin_load_file+0x62f)[0xb3ea5bad]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3eb0822]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_registry_scan_path+0x135)[0xb3eb09c7]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3e60a44]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3e60f30]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3e61589]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3e61b44]
/usr/lib/libglib-2.0.so.0(g_option_context_parse+0x5b3)[0xb6b83803]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_init_check+0xf1)[0xb3e5fd1b]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_init+0x32)[0xb3e5fe25]
/usr/share/Songbird/lib/sbGStreamerMediacore.so(_ZN18sbGStreamerService4InitEv+0x9ff)[0xb3dfa6a3]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3e02a05]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3e0bdb6]
/usr/share/Songbird/xulrunner/libxul.so[0xb7631a85]
/usr/share/Songbird/xulrunner/libxul.so[0xb7630f47]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3e08e83]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3e08ead]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3e08659]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3e01413]
/usr/share/Songbird/lib/sbGStreamerMediacore.so(_ZN27sbGStreamerMediacoreFactory4InitEv+0x46)[0xb3e01be0]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3e02965]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3e0bdb6]
/usr/share/Songbird/xulrunner/libxul.so[0xb7631a85]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb5939e29]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb5939e56]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb59396f1]
/usr/share/Songbird/components/sbMediacoreManager.so(_ZN8nsCOMPtrI19sbIMediacoreFactoryEC1ERK15nsCOMPtr_helper+0x2d)[0xb5922705]
/usr/share/Songbird/components/sbMediacoreManager.so(_ZN18sbMediacoreManager4InitEv+0x1b7)[0xb59202d7]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb5920654]
/usr/share/Songbird/xulrunner/libxul.so[0xb760e773]
/usr/share/Songbird/xulrunner/libxul.so[0xb760ed18]
/usr/share/Songbird/xulrunner/libxul.so[0xb6ea2be0]
/usr/share/Songbird/xulrunner/libxul.so(XRE_main+0x19af)[0xb6ea08c1]
././songbird-bin[0x8048f40]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7d2a685]
././songbird-bin[0x8048bb1]
======= Memory map: ========
08048000-0804e000 r-xp 00000000 08:03 958921     /usr/share/Songbird/songbird-bin
0804e000-0804f000 rwxp 00006000 08:03 958921     /usr/share/Songbird/songbird-bin
09f02000-09f23000 rwxp 09f02000 00:00 0          [heap]
b23ff000-b2407000 rwxp b23ff000 00:00 0 
b339b000-b33a9000 rwxp b339b000 00:00 0 
b33a9000-b33e5000 r-xp 00000000 08:03 16648637   /usr/lib/libvisual-0.4.so.0.0.0
b33e5000-b33e6000 r-xp 0003b000 08:03 16648637   /usr/lib/libvisual-0.4.so.0.0.0
b33e6000-b33e7000 rwxp 0003c000 08:03 16648637   /usr/lib/libvisual-0.4.so.0.0.0
b33e7000-b3408000 r-xp 00000000 08:03 16647986   /usr/lib/libexif.so.12.2.0
b3408000-b3410000 r-xp 00020000 08:03 16647986   /usr/lib/libexif.so.12.2.0
b3410000-b3411000 rwxp 00028000 08:03 16647986   /usr/lib/libexif.so.12.2.0
b3411000-b3419000 r-xp 00000000 08:03 16648770   /usr/lib/libiptcdata.so.0.3.2
b3419000-b341b000 rwxp 00007000 08:03 16648770   /usr/lib/libiptcdata.so.0.3.2
b341b000-b34c2000 r-xp 00000000 08:03 16647984   /usr/lib/libexempi.so.3.1.3
b34c2000-b34c3000 r-xp 000a7000 08:03 16647984   /usr/lib/libexempi.so.3.1.3
b34c3000-b34c6000 rwxp 000a8000 08:03 16647984   /usr/lib/libexempi.so.3.1.3
b34c6000-b34d6000 r-xp 00000000 08:03 12361847   /usr/lib/gstreamer-0.10/libgstmetadata.so
b34d6000-b34d7000 r-xp 0000f000 08:03 12361847   /usr/lib/gstreamer-0.10/libgstmetadata.so
b34d7000-b34d8000 rwxp 00010000 08:03 12361847   /usr/lib/gstreamer-0.10/libgstmetadata.so
b34d8000-b34e8000 r-xp 00000000 08:03 16648271   /usr/lib/libhal.so.1.0.0
b34e8000-b34e9000 r-xp 0000f000 08:03 16648271   /usr/lib/libhal.so.1.0.0
b34e9000-b34ea000 rwxp 00010000 08:03 16648271   /usr/lib/libhal.so.1.0.0
b34ec000-b34f4000 rwxp b34ec000 00:00 0 
b34f9000-b3507000 r-xp 00000000 08:03 16648792   /usr/lib/libjack.so.0.0.28
b3507000-b3508000 r-xp 0000e000 08:03 16648792   /usr/lib/libjack.so.0.0.28
b3508000-b350a000 rwxp 0000f000 08:03 16648792   /usr/lib/libjack.so.0.0.28
b350a000-b3512000 rwxp b350a000 00:00 0 
b3512000-b3518000 r-xp 00000000 08:03 16654867   /usr/lib/gstreamer-0.10/libgstlibvisual.so
b3518000-b3519000 r-xp 00005000 08:03 16654867   /usr/lib/gstreamer-0.10/libgstlibvisual.so
b3519000-b351a000 rwxp 00006000 08:03 16654867   /usr/lib/gstreamer-0.10/libgstlibvisual.so
b351a000-b351f000 r-xp 00000000 08:03 16654904   /usr/lib/gstreamer-0.10/libgsthalelements.so
b351f000-b3520000 r-xp 00004000 08:03 16654904   /usr/lib/gstreamer-0.10/libgsthalelements.so
b3520000-b3521000 rwxp 00005000 08:03 16654904   /usr/lib/gstreamer-0.10/libgsthalelements.so
b3521000-b3540000 r-xp 00000000 08:03 16648313   /usr/lib/libjpeg.so.62.0.0
b3540000-b3541000 rwxp 0001e000 08:03 16648313   /usr/lib/libjpeg.so.62.0.0
b3545000-b3547000 rwxp b3545000 00:00 0 
b3547000-b354e000 r-xp 00000000 08:03 12361845   /usr/lib/gstreamer-0.10/libgstjack.so
b354e000-b354f000 r-xp 00006000 08:03 12361845   /usr/lib/gstreamer-0.10/libgstjack.so
b354f000-b3550000 rwxp 00007000 08:03 12361845   /usr/lib/gstreamer-0.10/libgstjack.so
b3550000-b3588000 r-xp 00000000 08:03 12361849   /usr/lib/gstreamer-0.10/libgstmodplug.so
b3588000-b3589000 r-xp 00037000 08:03 12361849   /usr/lib/gstreamer-0.10/libgstmodplug.so
b3589000-b358c000 rwxp 00038000 08:03 12361849   /usr/lib/gstreamer-0.10/libgstmodplug.so
b358c000-b35b8000 rwxp b358c000 00:00 0 
b35b8000-b35bd000 r-xp 00000000 08:03 16648164   /usr/lib/libgpm.so.2.0.0
b35bd000-b35be000 r-xp 00004000 08:03 16648164   /usr/lib/libgpm.so.2.0.0
b35be000-b35bf000 rwxp 00005000 08:03 16648164   /usr/lib/libgpm.so.2.0.0
b35bf000-b365a000 r-xp 00000000 08:03 8601727    /lib/libslang.so.2.1.3
b365a000-b365d000 r-xp 0009a000 08:03 8601727    /lib/libslang.so.2.1.3
b365d000-b366a000 rwxp 0009d000 08:03 8601727    /lib/libslang.so.2.1.3
b366a000-b36a0000 rwxp b366a000 00:00 0 
b36a0000-b36cd000 r-xp 00000000 08:03 8601677    /lib/libncurses.so.5.6
b36cd000-b36d0000 rwxp 0002c000 08:03 8601677    /lib/libncurses.so.5.6
b36d0000-b36e8000 r-xp 00000000 08:03 16647788   /usr/lib/libaa.so.1.0.4
b36e8000-b36e9000 r-xp 00018000 08:03 16647788   /usr/lib/libaa.so.1.0.4
b36e9000-b36ea000 rwxp 00019000 08:03 16647788   /usr/lib/libaa.so.1.0.4
b36ea000-b36ec000 rwxp b36ea000 00:00 0 
b36ec000-b36f9000 r-xp 00000000 08:03 16654908   /usr/lib/gstreamer-0.10/libgstjpeg.so
b36f9000-b36fa000 r-xp 0000c000 08:03 16654908   /usr/lib/gstreamer-0.10/libgstjpeg.so
b36fa000-b36fb000 rwxp 0000d000 08:03 16654908   /usr/lib/gstreamer-0.10/libgstjpeg.so
b36fb000-b36fe000 r-xp 00000000 08:03 16654879   /usr/lib/gstreamer-0.10/libgstaasink.so
b36fe000-b36ff000 r-xp 00003000 08:03 16654879   /usr/lib/gstreamer-0.10/libgstaasink.so
b36ff000-b3700000 rwxp 00004000 08:03 16654879   /usr/lib/gstreamer-0.10/libgstaasink.so
b3700000-b3705000 r-xp 00000000 08:03 16648520   /usr/lib/libraw1394.so.8.2.0
b3705000-b3706000 r-xp 00004000 08:03 16648520   /usr/lib/libraw1394.so.8.2.0
b3706000-b3707000 rwxp 00005000 08:03 16648520   /usr/lib/libraw1394.so.8.2.0
b3707000-b3713000 r-xp 00000000 08:03 16648299   /usr/lib/libiec61883.so.0.1.0
b3713000-b3714000 rwxp 0000b000 08:03 16648299   /usr/lib/libiec61883.so.0.1.0
b3714000-b3717000 r-xp 00000000 08:03 16648529   /usr/lib/librom1394.so.0.3.0
b3717000-b3718000 rwxp 00002000 08:03 16648529   /usr/lib/librom1394.so.0.3.0
b3718000-b371b000 r-xp 00000000 08:03 16647833   /usr/lib/libavc1394.so.0.3.0
b371b000-b371c000 rwxp 00002000 08:03 16647833   /usr/lib/libavc1394.so.0.3.0
b371e000-b3729000 r-xp 00000000 08:03 16654916   /usr/lib/gstreamer-0.10/libgstossaudio.so
b3729000-b372a000 r-xp 0000a000 08:03 16654916   /usr/lib/gstreamer-0.10/libgstossaudio.so
b372a000-b372b000 rwxp 0000b000 08:03 16654916   /usr/lib/gstreamer-0.10/libgstossaudio.so
b372b000-b375f000 r-xp 00000000 08:03 967370     /usr/share/Songbird/gst-plugins/libgstffmpegcolorspace.so
b375f000-b3760000 rwxp 00033000 08:03 967370     /usr/share/Songbird/gst-plugins/libgstffmpegcolorspace.so
b3760000-b3761000 rwxp b3760000 00:00 0 
b3761000-b3765000 r-xp 00000000 08:03 16647780   /usr/lib/libXv.so.1.0.0
b3765000-b3766000 r-xp 00003000 08:03 16647780   /usr/lib/libXv.so.1.0.0
b3766000-b37

```

Does that show anything?

---

### Post by MrWES on 2009-03-24
> **jamesey said:**
> ```
james@james-ubuntu:~$ songbird
*** glibc detected *** ././songbird-bin: double free or corruption (out): 0xb3980da0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7d83454]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb7d854b6]
/usr/lib/libvisual-0.4.so.0(visual_mem_free+0x21)[0xb33c3141]
/usr/lib/libvisual-0.4.so.0[0xb33ba407]
/usr/lib/libvisual-0.4.so.0(visual_plugin_get_list+0x73)[0xb33ba5e3]
/usr/lib/libvisual-0.4.so.0(visual_init+0x291)[0xb33c9ec1]
/usr/lib/gstreamer-0.10/libgstlibvisual.so[0xb35141f4]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3ea52f6]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_plugin_load_file+0x62f)[0xb3ea5bad]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3eb0822]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_registry_scan_path+0x135)[0xb3eb09c7]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3e60a44]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3e60f30]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3e61589]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3e61b44]
/usr/lib/libglib-2.0.so.0(g_option_context_parse+0x5b3)[0xb6b83803]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_init_check+0xf1)[0xb3e5fd1b]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_init+0x32)[0xb3e5fe25]
/usr/share/Songbird/lib/sbGStreamerMediacore.so(_ZN18sbGStreamerService4InitEv+0x9ff)[0xb3dfa6a3]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3e02a05]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3e0bdb6]
/usr/share/Songbird/xulrunner/libxul.so[0xb7631a85]
/usr/share/Songbird/xulrunner/libxul.so[0xb7630f47]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3e08e83]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3e08ead]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3e08659]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3e01413]
/usr/share/Songbird/lib/sbGStreamerMediacore.so(_ZN27sbGStreamerMediacoreFactory4InitEv+0x46)[0xb3e01be0]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3e02965]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3e0bdb6]
/usr/share/Songbird/xulrunner/libxul.so[0xb7631a85]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb5939e29]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb5939e56]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb59396f1]
/usr/share/Songbird/components/sbMediacoreManager.so(_ZN8nsCOMPtrI19sbIMediacoreFactoryEC1ERK15nsCOMPtr_helper+0x2d)[0xb5922705]
/usr/share/Songbird/components/sbMediacoreManager.so(_ZN18sbMediacoreManager4InitEv+0x1b7)[0xb59202d7]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb5920654]
/usr/share/Songbird/xulrunner/libxul.so[0xb760e773]
/usr/share/Songbird/xulrunner/libxul.so[0xb760ed18]
/usr/share/Songbird/xulrunner/libxul.so[0xb6ea2be0]
/usr/share/Songbird/xulrunner/libxul.so(XRE_main+0x19af)[0xb6ea08c1]
././songbird-bin[0x8048f40]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7d2a685]
././songbird-bin[0x8048bb1]
======= Memory map: ========
08048000-0804e000 r-xp 00000000 08:03 958921     /usr/share/Songbird/songbird-bin
0804e000-0804f000 rwxp 00006000 08:03 958921     /usr/share/Songbird/songbird-bin
09f02000-09f23000 rwxp 09f02000 00:00 0          [heap]
b23ff000-b2407000 rwxp b23ff000 00:00 0 
b339b000-b33a9000 rwxp b339b000 00:00 0 
b33a9000-b33e5000 r-xp 00000000 08:03 16648637   /usr/lib/libvisual-0.4.so.0.0.0
b33e5000-b33e6000 r-xp 0003b000 08:03 16648637   /usr/lib/libvisual-0.4.so.0.0.0
b33e6000-b33e7000 rwxp 0003c000 08:03 16648637   /usr/lib/libvisual-0.4.so.0.0.0
b33e7000-b3408000 r-xp 00000000 08:03 16647986   /usr/lib/libexif.so.12.2.0
b3408000-b3410000 r-xp 00020000 08:03 16647986   /usr/lib/libexif.so.12.2.0
b3410000-b3411000 rwxp 00028000 08:03 16647986   /usr/lib/libexif.so.12.2.0
b3411000-b3419000 r-xp 00000000 08:03 16648770   /usr/lib/libiptcdata.so.0.3.2
b3419000-b341b000 rwxp 00007000 08:03 16648770   /usr/lib/libiptcdata.so.0.3.2
b341b000-b34c2000 r-xp 00000000 08:03 16647984   /usr/lib/libexempi.so.3.1.3
b34c2000-b34c3000 r-xp 000a7000 08:03 16647984   /usr/lib/libexempi.so.3.1.3
b34c3000-b34c6000 rwxp 000a8000 08:03 16647984   /usr/lib/libexempi.so.3.1.3
b34c6000-b34d6000 r-xp 00000000 08:03 12361847   /usr/lib/gstreamer-0.10/libgstmetadata.so
b34d6000-b34d7000 r-xp 0000f000 08:03 12361847   /usr/lib/gstreamer-0.10/libgstmetadata.so
b34d7000-b34d8000 rwxp 00010000 08:03 12361847   /usr/lib/gstreamer-0.10/libgstmetadata.so
b34d8000-b34e8000 r-xp 00000000 08:03 16648271   /usr/lib/libhal.so.1.0.0
b34e8000-b34e9000 r-xp 0000f000 08:03 16648271   /usr/lib/libhal.so.1.0.0
b34e9000-b34ea000 rwxp 00010000 08:03 16648271   /usr/lib/libhal.so.1.0.0
b34ec000-b34f4000 rwxp b34ec000 00:00 0 
b34f9000-b3507000 r-xp 00000000 08:03 16648792   /usr/lib/libjack.so.0.0.28
b3507000-b3508000 r-xp 0000e000 08:03 16648792   /usr/lib/libjack.so.0.0.28
b3508000-b350a000 rwxp 0000f000 08:03 16648792   /usr/lib/libjack.so.0.0.28
b350a000-b3512000 rwxp b350a000 00:00 0 
b3512000-b3518000 r-xp 00000000 08:03 16654867   /usr/lib/gstreamer-0.10/libgstlibvisual.so
b3518000-b3519000 r-xp 00005000 08:03 16654867   /usr/lib/gstreamer-0.10/libgstlibvisual.so
b3519000-b351a000 rwxp 00006000 08:03 16654867   /usr/lib/gstreamer-0.10/libgstlibvisual.so
b351a000-b351f000 r-xp 00000000 08:03 16654904   /usr/lib/gstreamer-0.10/libgsthalelements.so
b351f000-b3520000 r-xp 00004000 08:03 16654904   /usr/lib/gstreamer-0.10/libgsthalelements.so
b3520000-b3521000 rwxp 00005000 08:03 16654904   /usr/lib/gstreamer-0.10/libgsthalelements.so
b3521000-b3540000 r-xp 00000000 08:03 16648313   /usr/lib/libjpeg.so.62.0.0
b3540000-b3541000 rwxp 0001e000 08:03 16648313   /usr/lib/libjpeg.so.62.0.0
b3545000-b3547000 rwxp b3545000 00:00 0 
b3547000-b354e000 r-xp 00000000 08:03 12361845   /usr/lib/gstreamer-0.10/libgstjack.so
b354e000-b354f000 r-xp 00006000 08:03 12361845   /usr/lib/gstreamer-0.10/libgstjack.so
b354f000-b3550000 rwxp 00007000 08:03 12361845   /usr/lib/gstreamer-0.10/libgstjack.so
b3550000-b3588000 r-xp 00000000 08:03 12361849   /usr/lib/gstreamer-0.10/libgstmodplug.so
b3588000-b3589000 r-xp 00037000 08:03 12361849   /usr/lib/gstreamer-0.10/libgstmodplug.so
b3589000-b358c000 rwxp 00038000 08:03 12361849   /usr/lib/gstreamer-0.10/libgstmodplug.so
b358c000-b35b8000 rwxp b358c000 00:00 0 
b35b8000-b35bd000 r-xp 00000000 08:03 16648164   /usr/lib/libgpm.so.2.0.0
b35bd000-b35be000 r-xp 00004000 08:03 16648164   /usr/lib/libgpm.so.2.0.0
b35be000-b35bf000 rwxp 00005000 08:03 16648164   /usr/lib/libgpm.so.2.0.0
b35bf000-b365a000 r-xp 00000000 08:03 8601727    /lib/libslang.so.2.1.3
b365a000-b365d000 r-xp 0009a000 08:03 8601727    /lib/libslang.so.2.1.3
b365d000-b366a000 rwxp 0009d000 08:03 8601727    /lib/libslang.so.2.1.3
b366a000-b36a0000 rwxp b366a000 00:00 0 
b36a0000-b36cd000 r-xp 00000000 08:03 8601677    /lib/libncurses.so.5.6
b36cd000-b36d0000 rwxp 0002c000 08:03 8601677    /lib/libncurses.so.5.6
b36d0000-b36e8000 r-xp 00000000 08:03 16647788   /usr/lib/libaa.so.1.0.4
b36e8000-b36e9000 r-xp 00018000 08:03 16647788   /usr/lib/libaa.so.1.0.4
b36e9000-b36ea000 rwxp 00019000 08:03 16647788   /usr/lib/libaa.so.1.0.4
b36ea000-b36ec000 rwxp b36ea000 00:00 0 
b36ec000-b36f9000 r-xp 00000000 08:03 16654908   /usr/lib/gstreamer-0.10/libgstjpeg.so
b36f9000-b36fa000 r-xp 0000c000 08:03 16654908   /usr/lib/gstreamer-0.10/libgstjpeg.so
b36fa000-b36fb000 rwxp 0000d000 08:03 16654908   /usr/lib/gstreamer-0.10/libgstjpeg.so
b36fb000-b36fe000 r-xp 00000000 08:03 16654879   /usr/lib/gstreamer-0.10/libgstaasink.so
b36fe000-b36ff000 r-xp 00003000 08:03 16654879   /usr/lib/gstreamer-0.10/libgstaasink.so
b36ff000-b3700000 rwxp 00004000 08:03 16654879   /usr/lib/gstreamer-0.10/libgstaasink.so
b3700000-b3705000 r-xp 00000000 08:03 16648520   /usr/lib/libraw1394.so.8.2.0
b3705000-b3706000 r-xp 00004000 08:03 16648520   /usr/lib/libraw1394.so.8.2.0
b3706000-b3707000 rwxp 00005000 08:03 16648520   /usr/lib/libraw1394.so.8.2.0
b3707000-b3713000 r-xp 00000000 08:03 16648299   /usr/lib/libiec61883.so.0.1.0
b3713000-b3714000 rwxp 0000b000 08:03 16648299   /usr/lib/libiec61883.so.0.1.0
b3714000-b3717000 r-xp 00000000 08:03 16648529   /usr/lib/librom1394.so.0.3.0
b3717000-b3718000 rwxp 00002000 08:03 16648529   /usr/lib/librom1394.so.0.3.0
b3718000-b371b000 r-xp 00000000 08:03 16647833   /usr/lib/libavc1394.so.0.3.0
b371b000-b371c000 rwxp 00002000 08:03 16647833   /usr/lib/libavc1394.so.0.3.0
b371e000-b3729000 r-xp 00000000 08:03 16654916   /usr/lib/gstreamer-0.10/libgstossaudio.so
b3729000-b372a000 r-xp 0000a000 08:03 16654916   /usr/lib/gstreamer-0.10/libgstossaudio.so
b372a000-b372b000 rwxp 0000b000 08:03 16654916   /usr/lib/gstreamer-0.10/libgstossaudio.so
b372b000-b375f000 r-xp 00000000 08:03 967370     /usr/share/Songbird/gst-plugins/libgstffmpegcolorspace.so
b375f000-b3760000 rwxp 00033000 08:03 967370     /usr/share/Songbird/gst-plugins/libgstffmpegcolorspace.so
b3760000-b3761000 rwxp b3760000 00:00 0 
b3761000-b3765000 r-xp 00000000 08:03 16647780   /usr/lib/libXv.so.1.0.0
b3765000-b3766000 r-xp 00003000 08:03 16647780   /usr/lib/libXv.so.1.0.0
b3766000-b37

```

Does that show anything?

This doesn't appear to be good;
```
*** glibc detected *** ././songbird-bin: double free or corruption (out): 0xb3980da0 ***
```

I don't know exactly what it is, but I googled it and found several threads with people having the same problems.

Bill

---

### Post by zhengdj on 2009-05-23
I simply did sudo apt-get remove libvisual-0.4-plugins and Songbird finally opened ok!

---

### Post by tICT on 2009-06-21
> sudo apt-get remove libvisual-0.4-plugins

works for me too!

cheers

---

### Post by fastfret79 on 2009-08-02
> **zhengdj said:**
> I simply did sudo apt-get remove libvisual-0.4-plugins and Songbird finally opened ok!

Worked for me too, although I removed this package through Synaptic to check if anything depended on this. LiVES was the only effected app which I don't use, so I removed that too.

---

