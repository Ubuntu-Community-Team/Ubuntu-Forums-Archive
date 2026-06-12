---
title: "Google Earth crashes since upgrade from 10.04 to 10.10"
date: 2010-11-14
forum: New to Ubuntu
---

### Post by Domie on 2010-11-14
This is the crash log:

Major Version 5
Minor Version 2
Build Number 0001
Build Date Sep  1 2010
Build Time 11:25:42
OS Type 3
OS Major Version 2
OS Minor Version 6
OS Build Version 35
OS Patch Version 0
Crash Signal 11
Crash Time 1289769483
Up Time 2,69897

Stacktrace from glibc:
./libgoogleearth_free.so(+0xd090b)[0x56b90b]
[0xd69400]
/usr/lib/libgdk_pixbuf-2.0.so.0(gdk_pixbuf_from_pixdata+0x13f)[0x52eabaf]
/usr/lib/libgdk_pixbuf-2.0.so.0(gdk_pixbuf_new_from_inline+0x63)[0x52eae73]
/usr/lib/flashplugin-installer/libflashplayer.so(+0x4d5e5)[0x5c4b5e5]
/usr/lib/flashplugin-installer/libflashplayer.so(+0x4c03e)[0x5c4a03e]
/usr/lib/flashplugin-installer/libflashplayer.so(NP_Initialize+0x1ae)[0x5c4e67e]
./libQtWebKit.so.4(+0x747b22)[0x1d6fb22]
./libQtWebKit.so.4(+0x747c0c)[0x1d6fc0c]
./libQtWebKit.so.4(+0x6062ff)[0x1c2e2ff]
./libQtWebKit.so.4(+0x604516)[0x1c2c516]
./libQtWebKit.so.4(+0x60476a)[0x1c2c76a]
./libQtWebKit.so.4(+0x712beb)[0x1d3abeb]
./libQtWebKit.so.4(+0x5b1595)[0x1bd9595]
./libQtWebKit.so.4(+0x5a185c)[0x1bc985c]
./libQtWebKit.so.4(+0x5b1981)[0x1bd9981]
./libQtWebKit.so.4(+0x5b199a)[0x1bd999a]
./libQtWebKit.so.4(+0xaa2c4b)[0x20cac4b]
./libQtWebKit.so.4(+0x16ad57)[0x1792d57]
./libQtWebKit.so.4(+0x1749d5)[0x179c9d5]
./libQtWebKit.so.4(+0x183282)[0x17ab282]
./libQtWebKit.so.4(+0x1bc22d)[0x17e422d]
./libQtWebKit.so.4(+0x29ac5d)[0x18c2c5d]
./libQtWebKit.so.4(+0x2a9410)[0x18d1410]
./libQtWebKit.so.4(+0x2a9f72)[0x18d1f72]
./libQtWebKit.so.4(+0x2b7fea)[0x18dffea]
./libQtWebKit.so.4(+0x4be45a)[0x1ae645a]
./libQtWebKit.so.4(+0x4bf243)[0x1ae7243]
./libQtWebKit.so.4(+0x4c0449)[0x1ae8449]
./libQtWebKit.so.4(+0x4c2a75)[0x1aeaa75]
./libQtWebKit.so.4(+0x4c36b8)[0x1aeb6b8]
./libQtWebKit.so.4(+0x4c6773)[0x1aee773]
./libQtWebKit.so.4(+0x501706)[0x1b29706]
./libQtWebKit.so.4(+0x5017fb)[0x1b297fb]
./libQtWebKit.so.4(+0x539f0b)[0x1b61f0b]
./libQtWebKit.so.4(+0x54c290)[0x1b74290]
./libQtWebKit.so.4(+0x547cc3)[0x1b6fcc3]
./libQtWebKit.so.4(+0x6fd155)[0x1d25155]
./libQtWebKit.so.4(+0x6fd83e)[0x1d2583e]
./libQtCore.so.4(_ZN11QMetaObject8metacallEP7QObjectNS_4CallEiPPv+0x3f)[0x8065a7]
./libQtCore.so.4(_ZN14QMetaCallEvent13placeMetaCallEP7QObject+0x24)[0x80e5ec]
./libQtCore.so.4(_ZN7QObject5eventEP6QEvent+0x185)[0x80f03d]
./libQtGui.so.4(_ZN19QApplicationPrivate13notify_helperEP7QObjectP6QEvent+0xa0)[0xea8e20]
./libQtGui.so.4(_ZN12QApplication6notifyEP7QObjectP6QEvent+0x22e)[0xeb2962]
./libQtCore.so.4(_ZN16QCoreApplication14notifyInternalEP7QObjectP6QEvent+0x70)[0x800d50]
./libQtCore.so.4(_ZN23QCoreApplicationPrivate16sendPostedEventsEP7QObjectiP11QThreadData+0x22d)[0x801989]
./libQtCore.so.4(_ZN20QEventDispatcherUNIX13processEventsE6QFlagsIN10QEventLoop17ProcessEventsFlagEE+0x37)[0x82694b]
./libQtGui.so.4(+0x1d3ca4)[0xf3dca4]
./libQtCore.so.4(_ZN10QEventLoop13processEventsE6QFlagsINS_17ProcessEventsFlagEE+0x47)[0x7fffbf]
./libQtCore.so.4(_ZN10QEventLoop4execE6QFlagsINS_17ProcessEventsFlagEE+0xff)[0x800223]
./libQtCore.so.4(_ZN16QCoreApplication4execEv+0x9d)[0x801c05]
./libQtGui.so.4(_ZN12QApplication4execEv+0x25)[0xea87a1]
./libgoogleearth_free.so(_ZN5earth6client11Application3runEv+0x4bc)[0x576b0c]
./libgoogleearth_free.so(earthmain+0x27d)[0x56ad3d]
./googleearth-bin(_init+0x12e)[0x80486d2]
/lib/libc.so.6(__libc_start_main+0xe7)[0x2c6ce7]
./googleearth-bin(_init+0x9d)[0x8048641]

-------------
Any ideas?

---

