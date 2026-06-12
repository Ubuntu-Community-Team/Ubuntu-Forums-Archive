---
title: "Cannot change system appearance properties."
date: 2009-01-25
forum: New to Ubuntu
---

### Post by prolapse on 2009-01-25
I am running Ubuntu 8.04, I haven't really made any recent changes to this system hardware wise, nor have I changed any settings or anything that I can think of that would cause this.  When I go to System > Preferences > Appearance nothing happens.  If I right click on my desktop and go to Change Desktop Background nothing happens.  Finally if I run 'gnome-appearance-properties' in a terminal I get the following error...

>  gnome-appearance-properties: error while loading shared libraries: t&#65533;&#65533;<$&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;$&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;D=: cannot open shared object file: No such file or directory

Does anyone have any suggestions as to what I could do to fix this? As far as I can tell everything else is working as it should. Thanks a lot! :)

---

### Post by snova on 2009-01-25
Post its shared library dependencies:

```
ldd /usr/bin/gnome-appearance-properties
```

---

### Post by prolapse on 2009-01-25
> **snova said:**
> Post its shared library dependencies:

```
ldd /usr/bin/gnome-appearance-properties
```

ok here you go:

```
	linux-gate.so.1 =>  (0xb7ee8000)
	libgnome-window-settings.so.1 => /usr/lib/libgnome-window-settings.so.1 (0xb7ed0000)
	libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0xb7ec7000)
	t&#65533;&#65533;<$&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;$&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;D= => not found
	&#65533;`&#65533;&#65533;&#65533; => not found
	&#65533;&#65533; => not found
	&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;U&#65533;&#65533;WVS1&#1731;&#65533;
                                         &#65533;&#65533;$&#65533;z => not found
	&#65533;&#1787;&#65533;&#65533;&#65533;S&#65533;&#65533;u&#65533;&#65533;D => not found
	libgnomeui-2.so.0 => /usr/lib/libgnomeui-2.so.0 (0xb7e3d000)
	libgnomevfs-2.so.0 => /usr/lib/libgnomevfs-2.so.0 (0xb7de4000)
	libgnome-2.so.0 => /usr/lib/libgnome-2.so.0 (0xb7dcf000)
	libgconf-2.so.4 => /usr/lib/libgconf-2.so.4 (0xb7d9f000)
	libgthread-2.0.so.0 => /usr/lib/libgthread-2.0.so.0 (0xb7d9a000)
	libXft.so.2 => /usr/lib/libXft.so.2 (0xb7d88000)
	libmetacity-private.so.0 => /usr/lib/libmetacity-private.so.0 (0xb7d5f000)
	libgtk-x11-2.0.so.0 => /usr/lib/libgtk-x11-2.0.so.0 (0xb79e8000)
	libgdk-x11-2.0.so.0 => /usr/lib/libgdk-x11-2.0.so.0 (0xb7964000)
	libgdk_pixbuf-2.0.so.0 => /usr/lib/libgdk_pixbuf-2.0.so.0 (0xb794c000)
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7927000)
	libpango-1.0.so.0 => /usr/lib/libpango-1.0.so.0 (0xb78e9000)
	libcairo.so.2 => /usr/lib/libcairo.so.2 (0xb7887000)
	libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0xb785d000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0xb7776000)
	libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0xb773a000)
	libglib-2.0.so.0 => /usr/lib/libglib-2.0.so.0 (0xb7689000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7670000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7521000)
	libXcomposite.so.1 => /usr/lib/libXcomposite.so.1 (0xb751e000)
	libgio-2.0.so.0 => /usr/lib/libgio-2.0.so.0 (0xb74bd000)
	libglade-2.0.so.0 => /usr/lib/libglade-2.0.so.0 (0xb74a5000)
	libxml2.so.2 => /usr/lib/libxml2.so.2 (0xb7385000)
	libgnome-desktop-2.so.2 => /usr/lib/libgnome-desktop-2.so.2 (0xb7362000)
	libstartup-notification-1.so.0 => /usr/lib/libstartup-notification-1.so.0 (0xb7359000)
	libgnome-menu.so.2 => /usr/lib/libgnome-menu.so.2 (0xb7344000)
	libpanel-applet-2.so.0 => /usr/lib/libpanel-applet-2.so.0 (0xb7336000)
	libbonoboui-2.so.0 => /usr/lib/libbonoboui-2.so.0 (0xb72d8000)
	libgnomecanvas-2.so.0 => /usr/lib/libgnomecanvas-2.so.0 (0xb72a7000)
	libpopt.so.0 => /lib/libpopt.so.0 (0xb729f000)
	libart_lgpl_2.so.2 => /usr/lib/libart_lgpl_2.so.2 (0xb7289000)
	libatk-1.0.so.0 => /usr/lib/libatk-1.0.so.0 (0xb726f000)
	libpangocairo-1.0.so.0 => /usr/lib/libpangocairo-1.0.so.0 (0xb7266000)
	libbonobo-2.so.0 => /usr/lib/libbonobo-2.so.0 (0xb720b000)
	libbonobo-activation.so.4 => /usr/lib/libbonobo-activation.so.4 (0xb71f6000)
	libgmodule-2.0.so.0 => /usr/lib/libgmodule-2.0.so.0 (0xb71f2000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb71ee000)
	libORBit-2.so.0 => /usr/lib/libORBit-2.so.0 (0xb719c000)
	librt.so.1 => /lib/tls/i686/cmov/librt.so.1 (0xb7193000)
	libSM.so.6 => /usr/lib/libSM.so.6 (0xb718a000)
	libICE.so.6 => /usr/lib/libICE.so.6 (0xb7172000)
	libXrender.so.1 => /usr/lib/libXrender.so.1 (0xb716a000)
	libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0xb7165000)
	libgnome-keyring.so.0 => /usr/lib/libgnome-keyring.so.0 (0xb7155000)
	libdbus-glib-1.so.2 => /usr/lib/libdbus-glib-1.so.2 (0xb713a000)
	libdbus-1.so.3 => /usr/lib/libdbus-1.so.3 (0xb7103000)
	libgnutls.so.13 => /usr/lib/libgnutls.so.13 (0xb708d000)
	libavahi-glib.so.1 => /usr/lib/libavahi-glib.so.1 (0xb708a000)
	libavahi-common.so.3 => /usr/lib/libavahi-common.so.3 (0xb707f000)
	libavahi-client.so.3 => /usr/lib/libavahi-client.so.3 (0xb7070000)
	libresolv.so.2 => /lib/tls/i686/cmov/libresolv.so.2 (0xb705c000)
	libutil.so.1 => /lib/tls/i686/cmov/libutil.so.1 (0xb7058000)
	libesd.so.0 => /usr/lib/libesd.so.0 (0xb704e000)
	libaudiofile.so.0 => /usr/lib/libaudiofile.so.0 (0xb7029000)
	libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0xb6fbc000)
	libz.so.1 => /usr/lib/libz.so.1 (0xb6fa7000)
	libXdamage.so.1 => /usr/lib/libXdamage.so.1 (0xb6fa3000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0xb6f95000)
	libXinerama.so.1 => /usr/lib/libXinerama.so.1 (0xb6f92000)
	libXi.so.6 => /usr/lib/libXi.so.6 (0xb6f8a000)
	libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0xb6f84000)
	/lib/ld-linux.so.2 (0xb7ee9000)
	libpng12.so.0 => /usr/lib/libpng12.so.0 (0xb6f60000)
	libpixman-1.so.0 => /usr/lib/libpixman-1.so.0 (0xb6f37000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb6e44000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb6e39000)
	libexpat.so.1 => /usr/lib/libexpat.so.1 (0xb6e18000)
	libxcb-xlib.so.0 => /usr/lib/libxcb-xlib.so.0 (0xb6e15000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0xb6dfd000)
	libpcre.so.3 => /usr/lib/libpcre.so.3 (0xb6dd6000)
	libselinux.so.1 => /lib/libselinux.so.1 (0xb6dbd000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0xb6db9000)
	libgailutil.so.18 => /usr/lib/libgailutil.so.18 (0xb6db2000)
	libpangoft2-1.0.so.0 => /usr/lib/libpangoft2-1.0.so.0 (0xb6d8b000)
	libORBitCosNaming-2.so.0 => /usr/lib/libORBitCosNaming-2.so.0 (0xb6d86000)
	libnsl.so.1 => /lib/tls/i686/cmov/libnsl.so.1 (0xb6d6d000)
	libtasn1.so.3 => /usr/lib/libtasn1.so.3 (0xb6d5d000)
	libgcrypt.so.11 => /lib/libgcrypt.so.11 (0xb6d10000)
	libasound.so.2 => /usr/lib/libasound.so.2 (0xb6c4d000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb6c47000)
	libgpg-error.so.0 => /lib/libgpg-error.so.0 (0xb6c43000)

```

---

### Post by prolapse on 2009-01-26
This is strange I have never encountered this before, I especially do not understand what the deal is with the non-displayable characters. :?

---

### Post by theozzlives on 2009-01-26
from a Windows point of view, I'd say something was corrupt on your hard drive... try fsck

---

### Post by prolapse on 2009-01-26
Also when I run the same command on my desktop that is running ubuntu 8.04 as well I get the same output except for the part that is garbled on the computer with the issue appears as follows...

```
        libdbus-glib-1.so.2 => /usr/lib/libdbus-glib-1.so.2 (0xb7f8b000)
        libgio-2.0.so.0 => /usr/lib/libgio-2.0.so.0 (0xb7f2a000)
        libglade-2.0.so.0 => /usr/lib/libglade-2.0.so.0 (0xb7f12000)
        libxml2.so.2 => /usr/lib/libxml2.so.2 (0xb7df1000)
        libgnome-desktop-2.so.2 => /usr/lib/libgnome-desktop-2.so.2 (0xb7dcf000)
```

my guess would be that these libraries are corrupt or something on this computer but I'm still relatively new to linux in general so I could be on the wrong track.

---

