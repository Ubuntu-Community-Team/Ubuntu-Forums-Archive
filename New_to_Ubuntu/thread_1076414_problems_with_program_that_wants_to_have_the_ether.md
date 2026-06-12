---
title: "problems with program that wants to have the ethernet card ID"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by plutoslittleuser on 2009-02-21
hi,
I just installed the softWoRxExplorer (a Java application) from Appliedbioscience on my new computer but in order to use it I have to register. For this this nice program needs the ID from my ethernet card. But somehow it just shows an error message (error in getting ID).

can anyone show me the light at the end of my tunnel????

thank you

---

### Post by plutoslittleuser on 2009-02-21
maybe this helps. its what it tells me when I start the program:

Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb26077c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb2607891]
#2 /usr/lib/libX11.so.6(_XReply+0x254) [0xb1415494]
#3 /usr/local/softWoRxExplorer/jre/lib/i386/xawt/libmawt.so [0xb14edd3e]
#4 /usr/local/softWoRxExplorer/jre/lib/i386/xawt/libmawt.so [0xb14d7d47]
#5 /usr/local/softWoRxExplorer/jre/lib/i386/xawt/libmawt.so [0xb14d7ec3]
#6 /usr/local/softWoRxExplorer/jre/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x26) [0xb14d8106]
#7 [0xb2a44c4b]
#8 [0xb2a3eb3b]
#9 [0xb2a3eb3b]
#10 [0xb2a3c217]
#11 /usr/local/softWoRxExplorer/jre/lib/i386/client/libjvm.so [0xb77c3d8c]
#12 /usr/local/softWoRxExplorer/jre/lib/i386/client/libjvm.so [0xb78d7fd8]
#13 /usr/local/softWoRxExplorer/jre/lib/i386/client/libjvm.so [0xb77c3bbf]
#14 /usr/local/softWoRxExplorer/jre/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x32d) [0xb782134d]
#15 /usr/local/softWoRxExplorer/jre/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb75b72cd]
#16 [0xb2a444eb]
#17 [0xb2a3ea64]
#18 [0xb2a3c217]
#19 /usr/local/softWoRxExplorer/jre/lib/i386/client/libjvm.so [0xb77c3d8c]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb26077c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb260796e]
#2 /usr/lib/libX11.so.6 [0xb1414619]
#3 /usr/lib/libX11.so.6(XGetVisualInfo+0x26) [0xb140a666]
#4 /usr/local/softWoRxExplorer/jre/lib/i386/xawt/libmawt.so [0xb14d7089]
#5 /usr/local/softWoRxExplorer/jre/lib/i386/xawt/libmawt.so [0xb14d72d3]
#6 /usr/local/softWoRxExplorer/jre/lib/i386/xawt/libmawt.so [0xb14d7f71]
#7 /usr/local/softWoRxExplorer/jre/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x26) [0xb14d8106]
#8 [0xb2a44c4b]
#9 [0xb2a3eb3b]
#10 [0xb2a3eb3b]
#11 [0xb2a3c217]
#12 /usr/local/softWoRxExplorer/jre/lib/i386/client/libjvm.so [0xb77c3d8c]
#13 /usr/local/softWoRxExplorer/jre/lib/i386/client/libjvm.so [0xb78d7fd8]
#14 /usr/local/softWoRxExplorer/jre/lib/i386/client/libjvm.so [0xb77c3bbf]
#15 /usr/local/softWoRxExplorer/jre/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x32d) [0xb782134d]
#16 /usr/local/softWoRxExplorer/jre/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb75b72cd]
#17 [0xb2a444eb]
#18 [0xb2a3ea64]
#19 [0xb2a3c217]

---

### Post by txcrackers on 2009-02-21
It's using the bundled JRE and, as is many the case, it's not compatible with your system. You need to configure it to use the JRE that you can get via the software repositories.

---

### Post by plutoslittleuser on 2009-02-22
thanks for the answer,
sounds good (I think) but how do I do that????

why is it always the program that you need the most that creates these nice problems???

thanks

---

