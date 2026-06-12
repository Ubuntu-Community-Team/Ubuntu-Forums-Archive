---
title: "songbird removal"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by championboxes on 2009-03-14
So I installed songbird 1.0 not to long ago... with using it I really like the add-ons and stuff but somehow I broke it by installing possibly a bad add-on now when I open it, it will be in the processes but will not open up... Then if I try to open it again a thing pops up and says that songbird is already running and so on... Anyway I tried to remove songbird through Synaptic then reinstalling it but I am having the same problems... Are there any files that might be hidden in the filesystem that would be causing my problem???

---

### Post by kellemes on 2009-03-14
Don't use songbird myself so only guessing..
Probably there is some hidden directory in your homefolder, something like .songbird I guess.. could be a little corruption in there is causing the problem. Remove this directory and reinstall songbird.

From terminal you can enter "top" to get a view on running processes in your system, maybe songbird is still hanging around there?

---

### Post by gjoellee on 2009-03-14
[http://www.getdeb.net/release.php?id=4028](http://www.getdeb.net/release.php?id=4028)

---

### Post by championboxes on 2009-03-14
Yes there was a .songbird file in my home directory so I deleted that and reinstalled but I am still having problems with it... Top shows it is running but I still cant get it to show up on screen... I use HTop to kill the process to try it again but I still have the same problem... idk if this will help solve my problem but opening songbird from the terminal I get ```
*** glibc detected *** ././songbird-bin: double free or corruption (out): 0xb2b2d6c0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7cd1454]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb7cd34b6]
/usr/lib/libvisual-0.4.so.0(visual_mem_free+0x21)[0xb27ca141]
/usr/lib/libvisual-0.4.so.0[0xb27c1407]
/usr/lib/libvisual-0.4.so.0(visual_plugin_get_list+0x73)[0xb27c15e3]
/usr/lib/libvisual-0.4.so.0(visual_init+0x291)[0xb27d0ec1]
/usr/lib/gstreamer-0.10/libgstlibvisual.so[0xb29511f4]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3ea52f6]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_plugin_load_file+0x62f)[0xb3ea5bad]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3eb0822]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_registry_scan_path+0x135)[0xb3eb09c7]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3e60a44]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3e60f30]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3e61589]
/usr/share/Songbird/lib/libgstreamer-0.10.so[0xb3e61b44]
/usr/lib/libglib-2.0.so.0(g_option_context_parse+0x5b3)[0xb6ad27e3]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_init_check+0xf1)[0xb3e5fd1b]
/usr/share/Songbird/lib/libgstreamer-0.10.so(gst_init+0x32)[0xb3e5fe25]
/usr/share/Songbird/lib/sbGStreamerMediacore.so(_ZN18sbGStreamerService4InitEv+0x9ff)[0xb3d446a3]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3d4ca05]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3d55db6]
/usr/share/Songbird/xulrunner/libxul.so[0xb7575a85]
/usr/share/Songbird/xulrunner/libxul.so[0xb7574f47]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3d52e83]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3d52ead]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3d52659]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3d4b413]
/usr/share/Songbird/lib/sbGStreamerMediacore.so(_ZN27sbGStreamerMediacoreFactory4InitEv+0x46)[0xb3d4bbe0]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3d4c965]
/usr/share/Songbird/lib/sbGStreamerMediacore.so[0xb3d55db6]
/usr/share/Songbird/xulrunner/libxul.so[0xb7575a85]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb4f82e29]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb4f82e56]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb4f826f1]
/usr/share/Songbird/components/sbMediacoreManager.so(_ZN8nsCOMPtrI19sbIMediacoreFactoryEC1ERK15nsCOMPtr_helper+0x2d)[0xb4f6b705]
/usr/share/Songbird/components/sbMediacoreManager.so(_ZN18sbMediacoreManager4InitEv+0x1b7)[0xb4f692d7]
/usr/share/Songbird/components/sbMediacoreManager.so[0xb4f69654]
/usr/share/Songbird/xulrunner/libxul.so[0xb7552773]
/usr/share/Songbird/xulrunner/libxul.so[0xb7552d18]
/usr/share/Songbird/xulrunner/libxul.so[0xb6de6be0]
/usr/share/Songbird/xulrunner/libxul.so(XRE_main+0x19af)[0xb6de48c1]
././songbird-bin[0x8048f40]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7c78685]
././songbird-bin[0x8048bb1]
======= Memory map: ========
08048000-0804e000 r-xp 00000000 08:05 828110     /usr/share/Songbird/songbird-bin
0804e000-0804f000 rw-p 00006000 08:05 828110     /usr/share/Songbird/songbird-bin
094d0000-094f1000 rw-p 094d0000 00:00 0          [heap]
b27a8000-b27b0000 rw-p b27a8000 00:00 0 
b27b0000-b27ec000 r-xp 00000000 08:05 822753     /usr/lib/libvisual-0.4.so.0.0.0
b27ec000-b27ed000 r--p 0003b000 08:05 822753     /usr/lib/libvisual-0.4.so.0.0.0
b27ed000-b27ee000 rw-p 0003c000 08:05 822753     /usr/lib/libvisual-0.4.so.0.0.0
b27ee000-b27fe000 rw-p b27ee000 00:00 0 
b2803000-b2809000 r-xp 00000000 08:05 1245226    /usr/lib/gstreamer-0.10/libgstgoom2k1.so
b2809000-b280a000 r--p 00005000 08:05 1245226    /usr/lib/gstreamer-0.10/libgstgoom2k1.so
b280a000-b280b000 rw-p 00006000 08:05 1245226    /usr/lib/gstreamer-0.10/libgstgoom2k1.so
b280b000-b284b000 rw-p b280b000 00:00 0 
b284b000-b285a000 r-xp 00000000 08:05 598236     /usr/lib/libmpcdec.so.3.1.1
b285a000-b285b000 rw-p 0000e000 08:05 598236     /usr/lib/libmpcdec.so.3.1.1
b285b000-b2882000 r-xp 00000000 08:05 598320     /usr/lib/libsidplay.so.1.0.3
b2882000-b2892000 rw-p 00026000 08:05 598320     /usr/lib/libsidplay.so.1.0.3
b2892000-b289e000 rw-p b2892000 00:00 0 
b289e000-b28ad000 r-xp 00000000 08:05 745510     /lib/libbz2.so.1.0.4
b28ad000-b28ae000 r--p 0000f000 08:05 745510     /lib/libbz2.so.1.0.4
b28ae000-b28af000 rw-p 00010000 08:05 745510     /lib/libbz2.so.1.0.4
b28b0000-b28b6000 rw-p b28b0000 00:00 0 
b28b6000-b28c2000 r-xp 00000000 08:05 1245297    /usr/lib/gstreamer-0.10/libgstflvdemux.so
b28c2000-b28c3000 r--p 0000b000 08:05 1245297    /usr/lib/gstreamer-0.10/libgstflvdemux.so
b28c3000-b28c4000 rw-p 0000c000 08:05 1245297    /usr/lib/gstreamer-0.10/libgstflvdemux.so
b28c4000-b28e3000 r-xp 00000000 08:05 598214     /usr/lib/libdvdread.so.3.2.1
b28e3000-b28e4000 r--p 0001e000 08:05 598214     /usr/lib/libdvdread.so.3.2.1
b28e4000-b28e5000 rw-p 0001f000 08:05 598214     /usr/lib/libdvdread.so.3.2.1
b28e5000-b28fa000 r-xp 00000000 08:05 598216     /usr/lib/libdvdnav.so.4.1.2
b28fa000-b28fb000 r--p 00014000 08:05 598216     /usr/lib/libdvdnav.so.4.1.2
b28fb000-b28fc000 rw-p 00015000 08:05 598216     /usr/lib/libdvdnav.so.4.1.2
b28fc000-b2923000 r-xp 00000000 08:05 1245337    /usr/lib/gstreamer-0.10/libresindvd.so
b2923000-b2924000 r--p 00027000 08:05 1245337    /usr/lib/gstreamer-0.10/libresindvd.so
b2924000-b2925000 rw-p 00028000 08:05 1245337    /usr/lib/gstreamer-0.10/libresindvd.so
b2925000-b293d000 r-xp 00000000 08:05 844214     /usr/lib/gio/modules/libgvfsdbus.so
b293d000-b293e000 r--p 00017000 08:05 844214     /usr/lib/gio/modules/libgvfsdbus.so
b293e000-b293f000 rw-p 00018000 08:05 844214     /usr/lib/gio/modules/libgvfsdbus.so
b293f000-b294c000 r-xp 00000000 08:05 819634     /usr/lib/libgvfscommon.so.0.0.0
b294c000-b294d000 r--p 0000d000 08:05 819634     /usr/lib/libgvfscommon.so.0.0.0
b294d000-b294e000 rw-p 0000e000 08:05 819634     /usr/lib/libgvfscommon.so.0.0.0
b294f000-b2955000 r-xp 00000000 08:05 1245233    /usr/lib/gstreamer-0.10/libgstlibvisual.so
b2955000-b2956000 r--p 00005000 08:05 1245233    /usr/lib/gstreamer-0.10/libgstlibvisual.so
b2956000-b2957000 rw-p 00006000 08:05 1245233    /usr/lib/gstreamer-0.10/libgstlibvisual.so
b2957000-b296e000 r-xp 00000000 08:05 1245259    /usr/lib/gstreamer-0.10/libgsttcp.so
b296e000-b296f000 r--p 00016000 08:05 1245259    /usr/lib/gstreamer-0.10/libgsttcp.so
b296f000-b2970000 rw-p 00017000 08:05 1245259    /usr/lib/gstreamer-0.10/libgsttcp.so
b2970000-b297c000 r-xp 00000000 08:05 821389     /usr/lib/libSoundTouch.so.1.0.0
b297c000-b297e000 rw-p 0000b000 08:05 821389     /usr/lib/libSoundTouch.so.1.0.0
b297f000-b2985000 r-xp 00000000 08:05 1245310    /usr/lib/gstreamer-0.10/libgstmusepack.so
b2985000-b2986000 r--p 00005000 08:05 1245310    /usr/lib/gstreamer-0.10/libgstmusepack.so
b2986000-b2987000 rw-p 00006000 08:05 1245310    /usr/lib/gstreamer-0.10/libgstmusepack.so
b2987000-b2991000 r-xp 00000000 08:05 1

```

---

### Post by kellemes on 2009-03-14
Is this thread helping?
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1077351]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1077351")

---

### Post by championboxes on 2009-03-14
That worked!!! Thank you I looked around on the forums a bit but I wasnt able to find that solution

---

