---
title: "Transmission closing."
date: 2009-02-20
forum: New to Ubuntu
---

### Post by nilsolaris on 2009-02-20
Up until today i have had no problems with transmission bittorrent client. But for some odd reason transmissin just keep closing itself out and 10-20 seconds of running.

After running it through the terminal i get:

*** glibc detected *** transmission: double free or corruption (fasttop): 0x0acb16f0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb77a2454]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb77a44b6]
/usr/lib/libcurl.so.4[0xb7a52214]
/usr/lib/libcurl.so.4[0xb7a49278]
/usr/lib/libcurl.so.4[0xb7a55ad0]
/usr/lib/libcurl.so.4[0xb7a683ed]
/usr/lib/libcurl.so.4(curl_multi_perform+0x59)[0xb7a68739]
transmission[0x809e04d]
transmission[0x809e1f8]
transmission[0x809e433]
/usr/lib/libcurl.so.4[0xb7a678df]
/usr/lib/libcurl.so.4(curl_multi_perform+0xde)[0xb7a687be]
transmission[0x809e04d]
transmission[0x809e1f8]
transmission[0x809e433]
/usr/lib/libcurl.so.4[0xb7a678df]
/usr/lib/libcurl.so.4(curl_multi_perform+0xde)[0xb7a687be]
transmission[0x809e04d]
transmission[0x809e1f8]
transmission[0x809e433]
/usr/lib/libcurl.so.4[0xb7a678df]
/usr/lib/libcurl.so.4(curl_multi_add_handle+0x1a5)[0xb7a69865]
transmission[0x809d9c1]
transmission(tr_runInEventThread+0x87)[0x809a27a]
transmission(tr_webRun+0xa3)[0x809e4f3]
transmission[0x8098f28]
transmission(tr_runInEventThread+0x87)[0x809a27a]
transmission[0x8098fac]
transmission(tr_trackerStart+0xb0)[0x809971c]
transmission[0x80949d5]
transmission[0x8099ac1]
transmission(event_base_loop+0x318)[0x80c0dc8]
transmission(event_loop+0x1a)[0x80c0f9a]
transmission(event_dispatch+0x12)[0x80c0fb2]
transmission[0x8099d0e]
transmission[0x8087717]
/lib/tls/i686/cmov/libpthread.so.0[0xb789750f]
/lib/tls/i686/cmov/libc.so.6(clone+0x5e)[0xb7814a0e]
======= Memory map: ========
08048000-080e1000 r-xp 00000000 08:05 19049176   /usr/bin/transmission
080e1000-080e2000 r--p 00098000 08:05 19049176   /usr/bin/transmission
080e2000-080e5000 rw-p 00099000 08:05 19049176   /usr/bin/transmission
080e5000-080ea000 rw-p 080e5000 00:00 0 
08601000-0ad87000 rw-p 08601000 00:00 0          [heap]
b5c00000-b5c21000 rw-p b5c00000 00:00 0 
b5c21000-b5d00000 ---p b5c21000 00:00 0 
b5de9000-b5e49000 rw-s 00000000 00:09 6586384    /SYSV00000000 (deleted)
b5e49000-b5f7e000 r-xp 00000000 08:05 19046645   /usr/lib/libxml2.so.2.6.32
b5f7e000-b5f7f000 ---p 00135000 08:05 19046645   /usr/lib/libxml2.so.2.6.32
b5f7f000-b5f83000 r--p 00135000 08:05 19046645   /usr/lib/libxml2.so.2.6.32
b5f83000-b5f84000 rw-p 00139000 08:05 19046645   /usr/lib/libxml2.so.2.6.32
b5f84000-b5f85000 rw-p b5f84000 00:00 0 
b5f85000-b5fb6000 r-xp 00000000 08:05 19047927   /usr/lib/libcroco-0.6.so.3.0.1
b5fb6000-b5fb9000 rw-p 00030000 08:05 19047927   /usr/lib/libcroco-0.6.so.3.0.1
b5fb9000-b5fe9000 r-xp 00000000 08:05 19047155   /usr/lib/libgsf-1.so.114.0.8
b5fe9000-b5feb000 r--p 0002f000 08:05 19047155   /usr/lib/libgsf-1.so.114.0.8
b5feb000-b5fec000 rw-p 00031000 08:05 19047155   /usr/lib/libgsf-1.so.114.0.8
b5fec000-b5fed000 rw-p b5fec000 00:00 0 
b5fed000-b604d000 rw-s 00000000 00:09 6553615    /SYSV00000000 (deleted)
b604d000-b6151000 rw-p b604d000 00:00 0 
b6151000-b61da000 r--p 00000000 08:05 19161259   /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b61da000-b61f2000 r-xp 00000000 08:05 123112     /usr/lib/gio/modules/libgvfsdbus.so
b61f2000-b61f3000 r--p 00017000 08:05 123112     /usr/lib/gio/modules/libgvfsdbus.so
b61f3000-b61f4000 rw-p 00018000 08:05 123112     /usr/lib/gio/modules/libgvfsdbus.so
b61f4000-b6201000 r-xp 00000000 08:05 19046421   /usr/lib/libgvfscommon.so.0.0.0
b6201000-b6202000 r--p 0000d000 08:05 19046421   /usr/lib/libgvfscommon.so.0.0.0
b6202000-b6203000 rw-p 0000e000 08:05 19046421   /usr/lib/libgvfscommon.so.0.0.0
b6224000-b6231000 r-xp 00000000 08:05 18262113   /lib/libgcc_s.so.1
b6231000-b6232000 r--p 0000c000 08:05 18262113   /lib/libgcc_s.so.1
b6232000-b6233000 rw-p 0000d000 08:05 18262113   /lib/libgcc_s.so.1
b6233000-b6264000 r-xp 00000000 08:05 19046549   /usr/lib/librsvg-2.so.2.22.3
b6264000-b6265000 r--p 00030000 08:05 19046549   /usr/lib/librsvg-2.so.2.22.3
b6265000-b6266000 rw-p 00031000 08:05 19046549   /usr/lib/librsvg-2.so.2.22.3
b6266000-b6268000 r-xp 00000000 08:05 18284642   /lib/tls/i686/cmov/libutil-2.8.90.so
b6268000-b6269000 r--p 00001000 08:05 18284642   /lib/tls/i686/cmov/libutil-2.8.90.so
b6269000-b626a000 rw-p 00002000 08:05 18284642   /lib/tls/i686/cmov/libutil-2.8.90.so
b626e000-b627d000 r-xp 00000000 08:05 18260530   /lib/libbz2.so.1.0.4
b627d000-b627e000 r--p 0000f000 08:05 18260530   /lib/libbz2.so.1.0.4
b627e000-b627f000 rw-p 00010000 08:05 18260530   /lib/libbz2.so.1.0.4
b628f000-b6290000 r-xp 00000000 08:05 19079527   /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b6290000-b6291000 r--p 00000000 08:05 19079527   /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b6291000-b6292000 rw-p 00001000 08:05 19079527   /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b6292000-b6296000 r-xp 00000000 08:05 19080644   /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b6296000-b6297000 r--p 00003000 08:05 19080644   /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b6297000-b6298000 rw-p 00004000 08:05 19080644   /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b6298000-b62af000 r--s 00000000 08:05 19112774   /usr/share/mime/mime.cache
b62af000-b63b3000 rw-p b62af000 00:00 0 
b63b3000-b6448000 r--p 00000000 08:05 19161258   /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b6448000-b644a000 r-xp 00000000 08:05 19095567   /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b644a000-b644b000 r--p 00001000 08:05 19095567   /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b644b000-b644c000 rw-p 00002000 08:05 19095567   /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b644c000-b6452000 r--s 00000000 08:05 18334914   /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b6452000-b6455000 r--s 00000000 08:05 18333752   /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b6455000-b6457000 r--s 00000000 08:05 18334911   /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
b6457000-b645a000 r--s 00000000 08:05 18334909   /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b645a000-b6461000 r--s 00000000 08:05 18334908   /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b6461000-b6464000 r--s 00000000 08:05 18334907   /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b6464000-b646c000 r--s 00000000 08:05 18334906   /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b646c000-b6477000 r--s 00000000 08:05 18334915   /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b6477000-b6479000 r--s 00000000 08:05 18334903   /var/cache/fontconfig/2c5ba8142dffc8bf0377700342b8ca1a-x86.cache-2
b6479000-b647c000 r--s 00000000 08:05 18334902   /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b647c000-b6483000 r--s 00000000 08:05 18333760   /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b6483000-b6487000 r-xp 00000000 08:05 18284593   /lib/tls/i686/cmov/libnss_dns-2.8.90.so
b6487000-b6488000 r--p 00003000 08:05 18284593   /lib/tls/i686/cmov/libnss_dns-2.8.90.so
b6488000-b6489000 rw-p 00004000 08:05 18284593   /lib/tls/i686/cmov/libnss_dns-2.8.90.so
b6489000-b648b000 r-xp 00000000 08:05 18260063   /lib/libnss_mdns4_minimal.so.2
b648b000-b648c000 rw-p 00001000 08:05 18260063   /lib/libnss_mdns4_minimal.so.2
b648c000-b648d000 ---p b648c000 00:00 0 
b648d000-b6c8d000 rw-p b648d000 00:00 0 
b6c8d000-b6e73000 r--p 00000000 08:05 19211967   /usr/share/icons/hicolor/icon-theme.cache
b6e73000-b6e9a000 r-xp 00000000 08:05 19079412   /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b6e9a000-b6e9b000 r--p 00026000 08:05 19079412   /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b6e9b000-b6e9c000 rw-p 00027000 08:05 19079412   /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b6e9c000-b6ea6000 r-xp 00000000 08:05 18284594   /lib/tls/i686/cmov/libnss_files-2.8.90.so
b6ea6000-b6ea7000 r--p 00009000 08:05 18284594   /lib/tls/i686/cmov/libnss_files-2.8.90.so
b6ea7000-b6ea8000 rw-p 0000a000 08:05 18284594   /lib/tls/i686/cmov/libnss_files-2.8.90.so
b6ea8000-b6eb1000 r-xp 00000000 08:05 18284596   /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b6eb1000-b6eb2000 r--p 00008000 08:05 18284596   /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b6eb2000-b6eb3000 rw-p 00009000 08:05 18284596   /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b6eb3000-b6eba000 r-xp 00000000 08:05 18284592   /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b6eba000-b6ebb000 r--p 00006000 08:05 18284592   /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b6ebb000-b6ebc000 rw-p 00007000 08:05 18284592   /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b6ebd000-b6ebe000 r--s 00000000 08:05 18334910   /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b6ebe000-b6ebf000 r--s 00000000 08:05 18334904   /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b6ebf000-b6ec5000 r--s 00000000 08:05 18333754   /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b6ec5000-b6ecc000 r--s 00000000 08:05 18334182   /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b6ecc000-b6ecd000 r--p 00000000 08:05 141433     /usr/share/locale/en_CA/LC_MESSAGES/transmission.mo
b6ecd000-b6f0c000 r--p 00000000 08:05 19080395   /usr/lib/locale/en_CA.utf8/LC_CTYPE
b6f0c000-b6f0d000 r--p 00000000 08:05 19080103   /usr/lib/locale/en_CA.utf8/LC_NUMERIC
b6f0d000-b6fee000 r--p 00000000 08:05 19080416   /usr/lib/locale/en_CA.utf8/LC_COLLATE
b6fee000-b6ff2000 rw-p b6fee000 00:00 0 
b6ff2000-b6ff5000 r-xp 00000000 08:05 18260036   /lib/libgpg-error.so.0.3.0
b6ff5000-b6ff6000 rw-p 00002000 08:05 18260036   /lib/libgpg-error.so.0.3.0
b6ff6000-b6ffa000 r-xp 00000000 08:05 19046651   /usr/lib/libXdmcp.so.6.0.0
b6ffa000-b6ffb000 rw-p 00003000 08:05 19046651   /usr/lib/libXdmcp.so.6.0.0
b6ffb000-b6ffd000 r-xAborted




any help on fixing this please?


also now getting "Segmentation fault"

---

### Post by donkyhotay on 2009-02-20
No idea on what specifically is causing this problem. A few troubleshooting tips to narrow this down would be to close all torrents (don't just stop them but remove them from the list) and see if it still crashes to confirm it's not just something wierd in one of your torrents.

---

### Post by RomeReactor on 2009-02-20
Hi. The error you posted is also discussed [here]("http://ubuntuforums.org/showthread.php?p=6202877"). If you're using a version lower than 1.40, [try upgrading it]("http://forum.transmissionbt.com/viewtopic.php?f=13&t=5604").

EDIT: As you're running Gutsy, I don't now if adding the repository will work for you.

---

