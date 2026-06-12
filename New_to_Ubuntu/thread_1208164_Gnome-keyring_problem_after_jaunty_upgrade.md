---
title: "Gnome-keyring problem after jaunty upgrade"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by markblyman on 2009-07-08
I recently upgraded to Jaunty, but when ever I boot up I receive an "Your session lasted less than 10 seconds ..." error. The contents of my ~/.xsession-errors file are:

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Failed to run gnome-keyring-daemon: Failed to execute child process "gnome-keyring-daemon" (No such file or directory)

(xfce4-panel:3076): xfce4-panel-WARNING **: xfce4-panel is not running
xfdesktop[3077]: starting up
[31;01merror: option -s not recognized[0m

[01mHP Linux Imaging and Printing System (ver. 3.9.2)[0m
[01mSystem Tray Status Service ver. 2.0[0m

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.


[01mUsage: hp-systray [OPTIONS][0m


[01m[OPTIONS][0m
  Set the logging     -l<level> or --logging=<level>                        
  level:                                                                    
                      <level>: none, info*, error, warn, debug (*default)   
  Run in debug mode:  -g (same as option: -ldebug)                          
  This help           -h or --help                                          
  information:                                                              

  Startup even if no  -x or --force-startup                                 
  hplip CUPS queues                                                         
  are present:                                                              

*** glibc detected *** x-session-manager: corrupted double-linked list: 0x088b34e8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb73f9009]
/lib/tls/i686/cmov/libc.so.6[0xb73fab8d]
/lib/tls/i686/cmov/libc.so.6(__libc_malloc+0x95)[0xb73fc9c5]
/usr/lib/libICE.so.6(IceAcceptConnection+0xd7)[0xb7ed3d07]
x-session-manager[0x8050d0a]
/usr/lib/libglib-2.0.so.0[0xb7575dad]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1e8)[0xb753eb88]
/usr/lib/libglib-2.0.so.0[0xb75420eb]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1ca)[0xb75425ba]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb9)[0xb7acb7d9]
x-session-manager[0x805146d]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb739f775]
x-session-manager[0x8050811]
======= Memory map: ========
08048000-08065000 r-xp 00000000 08:05 284310     /usr/bin/xfce4-session
08065000-08066000 r--p 0001c000 08:05 284310     /usr/bin/xfce4-session
08066000-08067000 rw-p 0001d000 08:05 284310     /usr/bin/xfce4-session
08867000-088cc000 rw-p 08867000 00:00 0          [heap]
b6600000-b6621000 rw-p b6600000 00:00 0 
b6621000-b6700000 ---p b6621000 00:00 0 
b6721000-b672e000 r-xp 00000000 08:05 486851     /lib/libgcc_s.so.1
b672e000-b672f000 r--p 0000c000 08:05 486851     /lib/libgcc_s.so.1
b672f000-b6730000 rw-p 0000d000 08:05 486851     /lib/libgcc_s.so.1
b6730000-b6750000 r-xp 00000000 08:05 324758     /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
b6750000-b6751000 r--p 00020000 08:05 324758     /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
b6751000-b6752000 rw-p 00021000 08:05 324758     /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
b6752000-b6753000 ---p b6752000 00:00 0 
b6753000-b6f53000 rw-p b6753000 00:00 0 
b6f53000-b6f5a000 r-xp 00000000 08:05 292299     /usr/lib/libltdl.so.7.2.0
b6f5a000-b6f5b000 r--p 00006000 08:05 292299     /usr/lib/libltdl.so.7.2.0
b6f5b000-b6f5c000 rw-p 00007000 08:05 292299     /usr/lib/libltdl.so.7.2.0
b6f5c000-b6f68000 r-xp 00000000 08:05 292302     /usr/lib/libtdb.so.1.1.3
b6f68000-b6f69000 r--p 0000b000 08:05 292302     /usr/lib/libtdb.so.1.1.3
b6f69000-b6f6a000 rw-p 0000c000 08:05 292302     /usr/lib/libtdb.so.1.1.3
b6f6a000-b6f6e000 r-xp 00000000 08:05 285976     /usr/lib/libogg.so.0.5.3
b6f6e000-b6f6f000 r--p 00003000 08:05 285976     /usr/lib/libogg.so.0.5.3
b6f6f000-b6f70000 rw-p 00004000 08:05 285976     /usr/lib/libogg.so.0.5.3
b6f70000-b6f8b000 r-xp 00000000 08:05 286175     /usr/lib/libvorbis.so.0.4.0
b6f8b000-b6f8c000 r--p 0001a000 08:05 286175     /usr/lib/libvorbis.so.0.4.0
b6f8c000-b6f9a000 rw-p 0001b000 08:05 286175     /usr/lib/libvorbis.so.0.4.0
b6f9a000-b6fa1000 r-xp 00000000 08:05 286179     /usr/lib/libvorbisfile.so.3.2.0
b6fa1000-b6fa2000 r--p 00006000 08:05 286179     /usr/lib/libvorbisfile.so.3.2.0
b6fa2000-b6fa3000 rw-p 00007000 08:05 286179     /usr/lib/libvorbisfile.so.3.2.0
b6fa3000-b6fb0000 r-xp 00000000 08:05 292304     /usr/lib/libcanberra.so.0.1.4
b6fb0000-b6fb1000 r--p 0000d000 08:05 292304     /usr/lib/libcanberra.so.0.1.4
b6fb1000-b6fb2000 rw-p 0000e000 08:05 292304     /usr/lib/libcanberra.so.0.1.4
b6fc1000-b6fcb000 r-xp 00000000 08:05 505342     /lib/tls/i686/cmov/libnss_files-2.9.so
b6fcb000-b6fcc000 r--p 00009000 08:05 505342     /lib/tls/i686/cmov/libnss_files-2.9.so
b6fcc000-b6fcd000 rw-p 0000a000 08:05 505342     /lib/tls/i686/cmov/libnss_files-2.9.so
b6fcd000-b6fd6000 r-xp 00000000 08:05 505344     /lib/tls/i686/cmov/libnss_nis-2.9.so
b6fd6000-b6fd7000 r--p 00008000 08:05 505344     /lib/tls/i686/cmov/libnss_nis-2.9.so
b6fd7000-b6fd8000 rw-p 00009000 08:05 505344     /lib/tls/i686/cmov/libnss_nis-2.9.so
b6fd8000-b6fed000 r-xp 00000000 08:05 505339     /lib/tls/i686/cmov/libnsl-2.9.so
b6fed000-b6fee000 r--p 00014000 08:05 505339     /lib/tls/i686/cmov/libnsl-2.9.so
b6fee000-b6fef000 rw-p 00015000 08:05 505339     /lib/tls/i686/cmov/libnsl-2.9.so
b6fef000-b6ff1000 rw-p b6fef000 00:00 0 
b6ff1000-b6ff8000 r-xp 00000000 08:05 505340     /lib/tls/i686/cmov/libnss_compat-2.9.so
b6ff8000-b6ff9000 r--p 00006000 08:05 505340     /lib/tls/i686/cmov/libnss_compat-2.9.so
b6ff9000-b6ffa000 rw-p 00007000 08:05 505340     /lib/tls/i686/cmov/libnss_compat-2.9.so
b6ffe000-b7001000 r-xp 00000000 08:05 292306     /usr/lib/libcanberra-gtk.so.0.0.4
b7001000-b7002000 r--p 00002000 08:05 292306     /usr/lib/libcanberra-gtk.so.0.0.4
b7002000-b7003000 rw-p 00003000 08:05 292306     /usr/lib/libcanberra-gtk.so.0.0.4
b7003000-b7007000 r-xp 00000000 08:05 326190     /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
b7007000-b7008000 r--p 00003000 08:05 326190     /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
b7008000-b7009000 rw-p 00004000 08:05 326190     /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
b7009000-b7048000 r--p 00000000 08:05 325457     /usr/lib/locale/en_US.utf8/LC_CTYPE
b7048000-b7049000 r--p 00000000 08:05 325899     /usr/lib/locale/en_US.utf8/LC_NUMERIC
b7049000-b704a000 r--p 00000000 08:05 325523     /usr/lib/locale/en_US.utf8/LC_TIME
b704a000-b7135000 r--p 00000000 08:05 32470      /usr/lib/locale/en_US.utf8/LC_COLLATE
b7135000-b7139000 rw-p b7135000 00:00 0 
b7139000-b713d000 r-xp 00000000 08:05 285330     /usr/lib/libXdmcp.so.6.0.0
b713d000-b713e000 rw-p 00003000 08:05 285330     /usr/lib/libXdmcp.so.6.0.0
b713e000-b7140000 r-xp 00000000 08:05 284087     /usr/lib/libXau.so.6.0.0
b7140000-b7141000 r--p 00001000 08:05 284087     /usr/lib/libXau.so.6.0.0
b7141000-b7142000 rw-p 00002000 08:05 284087     /usr/lib/libXau.so.6.0.0
b7142000-b7149000 r-xp 00000000 08:05 505349     /lib/tls/i686/cmov/librt-2.9.so
b7149000-b714a000 r--p 00006000 08:05 505349     /lib/tls/i686/cmov/librt-2.9.so
b714a000-b714b000 rw-p 00007000 08:05 505349     /lib/tls/i686/cmov/librt-2.9.so
b714b000-b714f000 r-xp 00000000 08:05 292197     /usr/lib/libgthread-2.0.so.0.2000.1
b714f000-b7150000 r--p 00003000 08:05 292197     /usr/lib/libgthread-2.0.so.0.2000.1
b7150000-b7151000 rw-p 00004000 08:05 292197     /usr/lib/libgthread-2.0.so.0.2000.1
b7151000-b7152000 rw-p b7151000 00:00 0 
b7152000-b719b000 r-xp 00000000 08:05 284797     /usr/lib/libORBit-2.so.0.1.0
b719b000-b71a3000 r--p 00049000 08:05 284797     /usr/lib/libORBit-2.so.0.1.0
b71a3000-b71a5000 rw-p 00051000 08:05 284797     /usr/lib/libORBit-2.so.0.1.0
b71a5000-b71c9000 r-xp 00000000 08:05 285545     /usr/lib/libexpat.so.1.5.2
b71c9000-b71cb000 r--p 00023000 08:05 285545     /usr/lib/libexpat.so.1.5.2
b71cb000-b71cc000 rw-p 00025000 08:05 285545     /usr/lib/libexpat.so.1.5.2
b71cc000-b71d2000 r-xp 00000000 08:05 292203     /usr/lib/libxcb-render.so.0.0.0
b71d2000-b71d3000 r--p 00005000 08:05 292203     /usr/lib/libxcb-render.so.0.0.0
b71d3000-b71d4000 rw-p 00006000 08:05 292203     /usr/lib/libxcb-render.so.0.0.0
b71d4000-b71d7000 r-xp 00000000 08:05 292205     /usr/lib/libxcb-render-util.so.0.0.0
b71d7000-b71d8000 r--p 00002000 08:05 292205     /usr/lib/libxcb-render-util.so.0.0.0
b71d8000-b71d9000 rw-p 00003000 08:05 292205     /usr/lib/libxcb-render-util.so.0.0.0
b71d9000-b71fd000 r-xp 00000000 08:05 284564     /usr/lib/libpng12.so.0.27.0
b71fd000-b71fe000 r--p 00023000 08:05 284564     /usr/lib/libpng12.so.0.27.0
b71fe000-b71ff000 rw-p 00024000 08:05 284564     /usr/lib/libpng12.so.0.27.0
b71ff000-b7200000 rw-p b71ff000 00:00 0 
b7200000-b7213000 r-xp 00000000 08:05 284452     /usr/lib/libdirect-1.0.so.0.1.0
b7213000-b7214000 r--p 00012000 08:05 284452     /usr/lib/libdirect-1.0.so.0.1.0
b7214000-b7215000 rw-p 00013000 08:05 284452     /usr/lib/libdirect-1.0.so.0.1.0
b7215000-b721c000 r-xp 00000000 08:05 284472     /usr/lib/libfusion-1.0.so.0.1.0
b721c000-b721d000 r--p 00006000 08:05 284472     /usr/lib/libfusion-1.0.so.0.1.0
b721d000-b721e000 rw-p 00007000 08:05 284472     /usr/lib/libfusion-1.0.so.0.1.0
b721e000-b7282000 r-xp 00000000 08:05 284453     /usr/lib/libdirectfb-1.0.so.0.1.0
b7282000-b7283000 r--p 00063000 08:05 284453     /usr/lib/libdirectfb-1.0.so.0.1.0
b7283000-b7284000 rw-p 00064000 08:05 284453     /usr/lib/libdirectfb-1.0.so.0.1.0
b7284000-b72c4000 r-xp 00000000 08:05 284110     /usr/lib/libpixman-1.so.0.13.2
b72c4000-b72c6000 r--p 0003f000 08:05 284110     /usr/lib/libpixman-1.so.0.13.2
b72c6000-b72c7000 rw-p 00041000 08:05 284110     /usr/lib/libpixman-1.so.0.13.2
b72c7000-b72df000 r-xp 00000000 08:05 486829     /lib/libselinux.so.1
b72df000-b72e0000 r--p 00017000 08:05 486829     /lib/libselinux.so.1
b72e0000-b72e1000 rw-p 00018000 08:05 486829     /lib/libselinux.so.1
b72e1000-b72e2000 rw-p b72e1000 00:00 0 
b72e2000-b7312000 r-xp 00000000 08:05 487377     /lib/libpcre.so.3.12.1
b7312000-b7313000 r--p 0002f000 08:05 487377     /lib/libpcre.so.3.12.1
b7313000-b7314000 rw-p 00030000 08:05 487377     /lib/libpcre.so.3.12.1
b7314000-b7318000 r-xp 00000000 08:05 285335     /usr/lib/libXfixes.so.3.1.0
b7318000-b7319000 rw-p 00003000 08:05 285335     /usr/lib/libXfixes.so.3.1.0
b7319000-b731b000 r-xp 00000000 08:05 285328     /usr/lib/libXdamage.so.1.1.0
b731b000-b731c000 rw-p 00001000 08:05 285328     /usr/lib/libXdamage.so.1.1.0
b731c000-b731e000 r-xp 00000000 08:05 285324     /usr/lib/libXcomposite.so.1.0.0
b731e000-b731f000 r--p 00001000 08:05 285324     /usr/lib/libXcomposite.so.1.0.0
b731f000-b7320000 rw-p 00002000 08:05 285324     /usr/lib/libXcomposite.so.1.0.0
b7320000-b7321000 rw-p b7320000 00:00 0 
b7321000-b7329000 r-xp 00000000 08:05 285326     /usr/lib/libXcursor.so.1.0.2
b7329000-b732a000 rw-p 00007000 08:05 285326     /usr/lib/libXcursor.so.1.0.2
b732a000-b7330000 r-xp 00000000 08:05 292219     /usr/lib/libXrandr.so.2.2.0
b7330000-b7331000 r--p 00006000 08:05 292219     /usr/lib/libXrandr.so.2.2.0
b7331000-b7332000 rw-p 00007000 08:05 292219     /usr/lib/libXrandr.so.2.2.0
b7332000-b733a000 r-xp 00000000 08:05 292217     /usr/lib/libXi.so.6.0.0
b733a000-b733b000 r--p 00007000 08:05 292217     /usr/lib/libXi.so.6.0.0
b733b000-b733c000 rw-p 00008000 08:05 292217     /usr/lib/libXi.so.6.0.0
b733c000-b733e000 r-xp 00000000 08:05 285343     /usr/lib/libXinerama.so.1.0.0
b733e000-b733f000 rw-p 00001000 08:05 285343     /usr/lib/libXinerama.so.1.0.0
b733f000-b7347000 r-xp 00000000 08:05 285355     /usr/lib/libXrender.so.1.3.0
b7347000-b7348000 r--p 00007000 08:05 285355     /usr/lib/libXrender.so.1.3.0
b7348000-b7349000 rw-p 00008000 08:05 285355     /usr/lib/libXrender.so.1.3.0
b7349000-b7357000 r-xp 00000000 08:05 284042     /usr/lib/libXext.so.6.4.0
b7357000-b7358000 r--p 0000d000 08:05 284042     /usr/lib/libXext.so.6.4.0
b7358000-b7359000 rw-p 0000e000 08:05 284042     /usr/lib/libXext.so.6.4.0
b7359000-b735a000 rw-p b7359000 00:00 0 
b735a000-b735b000 r-xp 00000000 08:05 285315     /usr/lib/libXRes.so.1.0.0
b735b000-b735c000 rw-p 00001000 08:05 285315     /usr/lib/libXRes.so.1.0.0
b735c000-b7364000 r-xp 00000000 08:05 286126     /usr/lib/libstartup-notification-1.so.0.0.0
b7364000-b7365000 rw-p 00007000 08:05 286126     /usr/lib/libstartup-notification-1.so.0.0.0
b7365000-b7367000 r-xp 00000000 08:05 505336     /lib/tls/i686/cmov/libdl-2.9.so
b7367000-b7368000 r--p 00001000 08:05 505336     /lib/tls/i686/cmov/libdl-2.9.so
b7368000-b7369000 rw-p 00002000 08:05 505336     /lib/tls/i686/cmov/libdl-2.9.so
b7369000-b7381000 r-xp 00000000 08:05 284350     /usr/lib/libxcb.so.1.1.0
b7381000-b7382000 r--p 00017000 08:05 284350     /usr/lib/libxcb.so.1.1.0
b7382000-b7383000 rw-p 00018000 08:05 284350     /usr/lib/libxcb.so.1.1.0
b7383000-b7386000 r-xp 00000000 08:05 486761     /lib/libuuid.so.1.2
b7386000-b7387000 r--p 00002000 08:05 486761     /lib/libuuid.so.1.2
b7387000-b7388000 rw-p 00003000 08:05 486761     /lib/libuuid.so.1.2
b7388000-b7389000 rw-p b7388000 00:00 0 
b7389000-b74e5000 r-xp 00000000 08:05 505327     /lib/tls/i686/cmov/libc-2.9.so
b74e5000-b74e6000 ---p 0015c000 08:05 505327     /lib/tls/i686/cmov/libc-2.9.so
b74e6000-b74e8000 r--p 0015c000 08:05 505327     /lib/tls/i686/cmov/libc-2.9.so
b74e8000-b74e9000 rw-p 0015e000 08:05 505327     /lib/tls/i686/cmov/libc-2.9.so
b74e9000-b74ec000 rw-p b74e9000 00:00 0 
b74ec000-b7501000 r-xp 00000000 08:05 505347     /lib/tls/i686/cmov/libpthread-2.9.so
b7501000-b7502000 r--p 00014000 08:05 505347     /lib/tls/i686/cmov/libpthread-2.9.so
b7502000-b7503000 rw-p 00015000 08:05 505347     /lib/tls/i686/cmov/libpthread-2.9.so
b7503000-b7505000 rw-p b7503000 00:00 0 
b7505000-b75bb000 r-xp 00000000 08:05 292191     /usr/lib/libglib-2.0.so.0.2000.1
b75bb000-b75bc000 r--p 000b5000 08:05 292191     /usr/lib/libglib-2.0.so.0.2000.1
b75bc000-b75bd000 rw-p 000b6000 08:05 292191     /usr/lib/libglib-2.0.so.0.2000.1
b75bd000-b75eb000 r-xp 00000000 08:05 284260     /usr/lib/libgconf-2.so.4.1.5
b75eb000-b75ec000 ---p 0002e000 08:05 284260     /usr/lib/libgconf-2.so.4.1.5
b75ec000-b75ed000 r--p 0002e000 08:05 284260     /usr/lib/libgconf-2.so.4.1.5
b75ed000-b75ef000 rw-p 0002f000 08:05 284260     /usr/lib/libgconf-2.so.4.1.5
b75ef000-b762b000 r-xp 00000000 08:05 292195     /usr/lib/libgobject-2.0.so.0.2000.1
b762b000-b762c000 r--p 0003b000 08:05 292195     /usr/lib/libgobject-2.0.so.0.2000.1
b762c000-b762d000 rw-p 0003c000 08:05 292195     /usr/lib/libgobject-2.0.so.0.2000.1
b762d000-b762e000 rw-p b762d000 00:00 0 
b762e000-b7664000 r-xp 00000000 08:05 486848     /lib/libdbus-1.so.3.4.0
b7664000-b7665000 r--p 00035000 08:05 486848     /lib/libdbus-1.so.3.4.0
b7665000-b7666000 rw-p 00036000 08:05 486848     /lib/libdbus-1.so.3.4.0
b7666000-b7682000 r-xp 00000000 08:05 292055     /usr/lib/libdbus-glib-1.so.2.1.0
b7682000-b7683000 r--p 0001b000 08:05 292055     /usr/lib/libdbus-glib-1.so.2.1.0
b7683000-b7684000 rw-p 0001c000 08:05 292055     /usr/lib/libdbus-glib-1.so.2.1.0
b7684000-b7690000 r-xp 00000000 08:05 286054     /usr/lib/libxfconf-0.so.2.0.0
b7690000-b7691000 r--p 0000b000 08:05 286054     /usr/lib/libxfconf-0.so.2.0.0
b7691000-b7692000 rw-p 0000c000 08:05 286054     /usr/lib/libxfconf-0.so.2.0.0
b7692000-b7695000 r-xp 00000000 08:05 292193     /usr/lib/libgmodule-2.0.so.0.2000.1
b7695000-b7696000 r--p 00002000 08:05 292193     /usr/lib/libgmodule-2.0.so.0.2000.1
b7696000-b7697000 rw-p 00003000 08:05 292193     /usr/lib/libgmodule-2.0.so.0.2000.1
b7697000-b76c2000 r-xp 00000000 08:05 284108     /usr/lib/libfontconfig.so.1.3.0
b76c2000-b76c3000 r--p 0002a000 08:05 284108     /usr/lib/libfontconfig.so.1.3.0
b76c3000-b76c4000 rw-p 0002b000 08:05 284108     /usr/lib/libfontconfig.so.1.3.0
b76c4000-b76c5000 rw-p b76c4000 00:00 0 
b76c5000-b76d9000 r-xp 00000000 08:05 487374     /lib/libz.so.1.2.3.3
b76d9000-b76da000 r--p 00013000 08:05 487374     /lib/libz.so.1.2.3.3
b76da000-b76db000 rw-p 00014000 08:05 487374     /lib/libz.so.1.2.3.3
b76db000-b774d000 r-xp 00000000 08:05 284486     /usr/lib/libfreetype.so.6.3.20
b774d000-b7751000 r--p 00071000 08:05 284486     /usr/lib/libfreetype.so.6.3.20
b7751000-b7752000 rw-p 00075000 08:05 284486     /usr/lib/libfreetype.so.6.3.20
b7752000-b7792000 r-xp 00000000 08:05 292211     /usr/lib/libpango-1.0.so.0.2400.1
b7792000-b7793000 ---p 00040000 08:05 292211     /usr/lib/libpango-1.0.so.0.2400.1
b7793000-b7794000 r--p 00040000 08:05 292211     /usr/lib/libpango-1.0.so.0.2400.1
b7794000-b7795000 rw-p 00041000 08:05 292211     /usr/lib/libpango-1.0.so.0.2400.1
b7795000-b780c000 r-xp 00000000 08:05 292207     /usr/lib/libcairo.so.2.10800.6
b780c000-b780e000 r--p 00076000 08:05 292207     /usr/lib/libcairo.so.2.10800.6
b780e000-b780f000 rw-p 00078000 08:05 292207     /usr/lib/libcairo.so.2.10800.6
b780f000-b787a000 r-xp 00000000 08:05 292189     /usr/lib/libgio-2.0.so.0.2000.1
b787a000-b787b000 ---p 0006b000 08:05 292189     /usr/lib/libgio-2.0.so.0.2000.1
b787b000-b787c000 r--p 0006b000 08:05 292189     /usr/lib/libgio-2.0.so.0.2000.1
b787c000-b787d000 rw-p 0006c000 08:05 292189     /usr/lib/libgio-2.0.so.0.2000.1
b787d000-b7887000 r-xp 00000000 08:05 292212     /usr/lib/libpangocairo-1.0.so.0.2400.1
b7887000-b7888000 r--p 00009000 08:05 292212     /usr/lib/libpangocairo-1.0.so.0.2400.1
b7888000-b7889000 rw-p 0000a000 08:05 292212     /usr/lib/libpangocairo-1.0.so.0.2400.1
b7889000-b788a000 rw-p b7889000 00:00 0 
b788a000-b78ae000 r-xp 00000000 08:05 505337     /lib/tls/i686/cmov/libm-2.9.so
b78ae000-b78af000 r--p 00023000 08:05 505337     /lib/tls/i686/cmov/libm-2.9.so
b78af000-b78b0000 rw-p 00024000 08:05 505337     /lib/tls/i686/cmov/libm-2.9.so
b78b0000-b78c8000 r-xp 00000000 08:05 284152     /usr/lib/libgdk_pixbuf-2.0.so.0.1600.1
b78c8000-b78c9000 r--p 00017000 08:05 284152     /usr/lib/libgdk_pixbuf-2.0.so.0.1600.1
b78c9000-b78ca000 rw-p 00018000 08:05 284152     /usr/lib/libgdk_pixbuf-2.0.so.0.1600.1
b78ca000-b78f1000 r-xp 00000000 08:05 292213     /usr/lib/libpangoft2-1.0.so.0.2400.1
b78f1000-b78f2000 r--p 00026000 08:05 292213     /usr/lib/libpangoft2-1.0.so.0.2400.1
b78f2000-b78f3000 rw-p 00027000 08:05 292213     /usr/lib/libpangoft2-1.0.so.0.2400.1
b78f3000-b790c000 r-xp 00000000 08:05 292056     /usr/lib/libatk-1.0.so.0.2609.1
b790c000-b790d000 r--p 00019000 08:05 292056     /usr/lib/libatk-1.0.so.0.2609.1
b790d000-b790e000 rw-p 0001a000 08:05 292056     /usr/lib/libatk-1.0.so.0.2609.1
b790e000-b7997000 r-xp 00000000 08:05 284146     /usr/lib/libgdk-x11-2.0.so.0.1600.1
b7997000-b7998000 ---p 00089000 08:05 284146     /usr/lib/libgdk-x11-2.0.so.0.1600.1
b7998000-b799a000 r--p 00089000 08:05 284146     /usr/lib/libgdk-x11-2.0.so.0.1600.1
b799a000-b799b000 rw-p 0008b000 08:05 284146     /usr/lib/libgdk-x11-2.0.so.0.1600.1
b799b000-b7d44000 r-xp 00000000 08:05 284065     /usr/lib/libgtk-x11-2.0.so.0.1600.1
b7d44000-b7d48000 r--p 003a8000 08:05 284065     /usr/lib/libgtk-x11-2.0.so.0.1600.1
b7d48000-b7d4a000 rw-p 003ac000 08:05 284065     /usr/lib/libgtk-x11-2.0.so.0.1600.1
b7d4a000-b7d4d000 rw-p b7d4a000 00:00 0 
b7d4d000-b7d83000 r-xp 00000000 08:05 292385     /usr/lib/libwnck-1.so.22.3.18
b7d83000-b7d84000 r--p 00035000 08:05 292385     /usr/lib/libwnck-1.so.22.3.18
b7d84000-b7d85000 rw-p 00036000 08:05 292385     /usr/lib/libwnck-1.so.22.3.18
b7d85000-b7d92000 r-xp 00000000 08:05 284176     /usr/lib/libxfce4util.so.4.1.1
b7d92000-b7d93000 r--p 0000c000 08:05 284176     /usr/lib/libxfce4util.so.4.1.1
b7d93000-b7d94000 rw-p 0000d000 08:05 284176     /usr/lib/libxfce4util.so.4.1.1
b7d94000-b7d95000 rw-p b7d94000 00:00 0 
b7d95000-b7dde000 r-xp 00000000 08:05 283980     /usr/lib/libxfcegui4.so.4.3.0
b7dde000-b7de0000 r--p 00048000 08:05 283980     /usr/lib/libxfcegui4.so.4.3.0
b7de0000-b7de1000 rw-p 0004a000 08:05 283980     /usr/lib/libxfcegui4.so.4.3.0
b7de1000-b7ecb000 r-xp 00000000 08:05 284265     /usr/lib/libX11.so.6.2.0
b7ecb000-b7ecc000 ---p 000ea000 08:05 284265     /usr/lib/libX11.so.6.2.0
b7ecc000-b7ecd000 r--p 000ea000 08:05 284265     /usr/lib/libX11.so.6.2.0
b7ecd000-b7ecf000 rw-p 000eb000 08:05 284265     /usr/lib/libX11.so.6.2.0
b7ecf000-b7ed0000 rw-p b7ecf000 00:00 0 
b7ed0000-b7ee5000 r-xp 00000000 08:05 285284     /usr/lib/libICE.so.6.3.0
b7ee5000-b7ee6000 rw-p 00014000 08:05 285284     /usr/lib/libICE.so.6.3.0
b7ee6000-b7ee9000 rw-p b7ee6000 00:00 0 
b7ee9000-b7ef0000 r-xp 00000000 08:05 284326     /usr/lib/libSM.so.6.0.0
b7ef0000-b7ef1000 r--p 00006000 08:05 284326     /usr/lib/libSM.so.6.0.0
b7ef1000-b7ef2000 rw-p 00007000 08:05 284326     /usr/lib/libSM.so.6.0.0
b7ef2000-b7ef5000 r-xp 00000000 08:05 283986     /usr/lib/libxfsm-4.6.so.0.0.0
b7ef5000-b7ef6000 r--p 00002000 08:05 283986     /usr/lib/libxfsm-4.6.so.0.0.0
b7ef6000-b7ef7000 rw-p 00003000 08:05 283986     /usr/lib/libxfsm-4.6.so.0.0.0
b7ef7000-b7ef8000 r--p 00000000 08:05 325524     /usr/lib/locale/en_US.utf8/LC_MONETARY
b7ef8000-b7ef9000 r--p 00000000 08:05 325747     /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7ef9000-b7efa000 r--p 00000000 08:05 325770     /usr/lib/locale/en_US.utf8/LC_PAPER
b7efa000-b7efb000 r--p 00000000 08:05 325794     /usr/lib/locale/en_US.utf8/LC_NAME
b7efb000-b7efc000 r--p 00000000 08:05 325525     /usr/lib/locale/en_US.utf8/LC_ADDRESS
b7efc000-b7efd000 r--p 00000000 08:05 325526     /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b7efd000-b7efe000 r--p 00000000 08:05 325527     /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b7efe000-b7f05000 r--s 00000000 08:05 300260     /usr/lib/gconv/gconv-modules.cache
b7f05000-b7f06000 r--p 00000000 08:05 325528     /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7f06000-b7f08000 rw-p b7f06000 00:00 0 
b7f08000-b7f09000 r-xp b7f08000 00:00 0          [vdso]
b7f09000-b7f25000 r-xp 00000000 08:05 487301     /lib/ld-2.9.so
b7f25000-b7f26000 r--p 0001b000 08:05 487301     /lib/ld-2.9.so
b7f26000-b7f27000 rw-p 0001c000 08:05 487301     /lib/ld-2.9.so
bfc11000-bfc26000 rw-p bffeb000 00:00 0          [stack]

Now, I really don't know what this means. Could anybody help me interpret this? Or better yet fix the problem? Thank you very much.

---

