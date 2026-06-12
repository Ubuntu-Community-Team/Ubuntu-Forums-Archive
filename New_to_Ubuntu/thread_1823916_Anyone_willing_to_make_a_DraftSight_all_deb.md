---
title: "Anyone willing to make a DraftSight all deb"
date: 2011-08-12
forum: New to Ubuntu
---

### Post by TheManno1 on 2011-08-12
It is a suprise it hasn't been done before.I can't install it.

family@ubuntu:~$ sudo dpkg -i --force-architecture DraftSight.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
dpkg: regarding DraftSight.deb containing dassault-systemes-draftsight:i386, pre-dependency problem:
 dassault-systemes-draftsight:i386 pre-depends on libexpat1 (>= 2.0.1-4)
dpkg: error processing DraftSight.deb (--install):
 pre-dependency problem - not installing dassault-systemes-draftsight:i386
Errors were encountered while processing:
 DraftSight.deb

---

### Post by LowSky on 2011-08-13
HUH? should work fine? libexpat1 is version 2..1-7ubuntu3 in 11.04

```
sudo dpkg --force-architecture -i DraftSight.deb
```

---

### Post by mosquitogang201 on 2011-08-13
Make sure you have libexpat1 installed. Dpkg doesn't automatically pull dependencies like apt-get does.

"sudo apt-get install libexpat1"

If you have that installed, issue

"sudo dpkg -i --force-architecture --force-depends DraftSight.deb"

This will get the package installed. Then if you have trouble running the program we can try to figure it out. I was missing a dependency or two but it runs fine for me without them.

---

### Post by TheManno1 on 2011-08-14
Doesn't seem to work.
```

family@ubuntu:~$ sudo dpkg -i --force-architecture --force-depends DraftSight.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
dpkg: regarding DraftSight.deb containing dassault-systemes-draftsight:i386, pre-dependency problem:
 dassault-systemes-draftsight:i386 pre-depends on libexpat1 (>= 2.0.1-4)
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding DraftSight.deb containing dassault-systemes-draftsight:i386, pre-dependency problem:
 dassault-systemes-draftsight:i386 pre-depends on libglib2.0-0 (>= 2.22.3-0)
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding DraftSight.deb containing dassault-systemes-draftsight:i386, pre-dependency problem:
 dassault-systemes-draftsight:i386 pre-depends on libpcre3 (>= 7.8-3)
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding DraftSight.deb containing dassault-systemes-draftsight:i386, pre-dependency problem:
 dassault-systemes-draftsight:i386 pre-depends on libselinux1 (>= 2.0.85-2)
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding DraftSight.deb containing dassault-systemes-draftsight:i386, pre-dependency problem:
 dassault-systemes-draftsight:i386 pre-depends on zlib1g (>= 1:1.2.3.3.dfsg-13)
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding DraftSight.deb containing dassault-systemes-draftsight:i386, pre-dependency problem:
 dassault-systemes-draftsight:i386 pre-depends on libc6 (>= 2.10.1-0)
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding DraftSight.deb containing dassault-systemes-draftsight:i386, pre-dependency problem:
 dassault-systemes-draftsight:i386 pre-depends on libx11-6 (>= 2:1.2.2-1)
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding DraftSight.deb containing dassault-systemes-draftsight:i386, pre-dependency problem:
 dassault-systemes-draftsight:i386 pre-depends on libxau6 (>= 1:1.0.4-2)
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding DraftSight.deb containing dassault-systemes-draftsight:i386, pre-dependency problem:
 dassault-systemes-draftsight:i386 pre-depends on libxcomposite1 (>= 1:0.4.0-4)
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding DraftSight.deb containing dassault-systemes-draftsight:i386, pre-dependency problem:
 dassault-systemes-draftsight:i386 pre-depends on libxcursor1 (>= 1:1.1.9-1build1)
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding DraftSight.deb containing dassault-systemes-draftsight:i386, pre-dependency problem:
 dassault-systemes-draftsight:i386 pre-depends on libxdamage1 (>= 1:1.1.1-4)
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding DraftSight.deb containing dassault-systemes-draftsight:i386, pre-dependency problem:
 dassault-systemes-draftsight:i386 pre-depends on libxdmcp6 (>= 1:1.0.2-3)
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding DraftSight.deb containing dassault-systemes-draftsight:i386, pre-dependency problem:
 dassault-systemes-draftsight:i386 pre-depends on libxext6 (>= 2:1.0.99.1-0)
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding DraftSight.deb containing dassault-systemes-draftsight:i386, pre-dependency problem:
 dassault-systemes-draftsight:i386 pre-depends on libxfixes3 (>= 1:4.0.3-2build1)
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding DraftSight.deb containing dassault-systemes-draftsight:i386, pre-dependency problem:
 dassault-systemes-draftsight:i386 pre-depends on libxi6 (>= 2:1.2.1-2)
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding DraftSight.deb containing dassault-systemes-draftsight:i386, pre-dependency problem:
 dassault-systemes-draftsight:i386 pre-depends on libxinerama1 (>= 2:1.0.3-2)
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding DraftSight.deb containing dassault-systemes-draftsight:i386, pre-dependency problem:
 dassault-systemes-draftsight:i386 pre-depends on libxrandr2 (>= 2:1.3.0-2)
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding DraftSight.deb containing dassault-systemes-draftsight:i386, pre-dependency problem:
 dassault-systemes-draftsight:i386 pre-depends on libxrender1 (>= 1:0.9.4-2)
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding DraftSight.deb containing dassault-systemes-draftsight:i386, pre-dependency problem:
 dassault-systemes-draftsight:i386 pre-depends on libatk1.0-0 (>= 1.28.0-0)
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding DraftSight.deb containing dassault-systemes-draftsight:i386, pre-dependency problem:
 dassault-systemes-draftsight:i386 pre-depends on libcairo2 (>= 1.8.8-2)
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding DraftSight.deb containing dassault-systemes-draftsight:i386, pre-dependency problem:
 dassault-systemes-draftsight:i386 pre-depends on libdirectfb-extra (>= 1.2.7-2)
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding DraftSight.deb containing dassault-systemes-draftsight:i386, pre-dependency problem:
 dassault-systemes-draftsight:i386 pre-depends on libfontconfig1 (>= 2.6.0-1)
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding DraftSight.deb containing dassault-systemes-draftsight:i386, pre-dependency problem:
 dassault-systemes-draftsight:i386 pre-depends on libfreetype6 (>= 2.3.9-5)
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding DraftSight.deb containing dassault-systemes-draftsight:i386, pre-dependency problem:
 dassault-systemes-draftsight:i386 pre-depends on libgtk2.0-0 (>= 2.18.3-1)
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding DraftSight.deb containing dassault-systemes-draftsight:i386, pre-dependency problem:
 dassault-systemes-draftsight:i386 pre-depends on libpango1.0-0 (>= 1.26.0-1)
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding DraftSight.deb containing dassault-systemes-draftsight:i386, pre-dependency problem:
 dassault-systemes-draftsight:i386 pre-depends on libpixman-1-0 (>= 0.14.0-1)
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding DraftSight.deb containing dassault-systemes-draftsight:i386, pre-dependency problem:
 dassault-systemes-draftsight:i386 pre-depends on libpng12-0 (>= 1.2.37-1)
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding DraftSight.deb containing dassault-systemes-draftsight:i386, pre-dependency problem:
 dassault-systemes-draftsight:i386 pre-depends on libxcb-render-util0 (>= 0.3.6-1)
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding DraftSight.deb containing dassault-systemes-draftsight:i386, pre-dependency problem:
 dassault-systemes-draftsight:i386 pre-depends on libxcb-render0 (>= 1.4-1)
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding DraftSight.deb containing dassault-systemes-draftsight:i386, pre-dependency problem:
 dassault-systemes-draftsight:i386 pre-depends on libxcb1 (>= 1.4-1)
dpkg: warning: ignoring pre-dependency problem!
(Reading database ... 200580 files and directories currently installed.)
Unpacking dassault-systemes-draftsight:i386 (from DraftSight.deb) ...
access control disabled, clients can connect from any host
access control disabled, clients can connect from any host

(ShowLicence:3627): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(ShowLicence:3627): Gtk-WARNING **: Loading IM context type 'ibus' failed

** (ShowLicence:3627): WARNING **: Pixbuf theme: Cannot load pixmap file /usr/share/themes/Macbuntu/gtk-2.0/Scrollbars/vertical_trough.png: Unable to load image-loading module: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64


(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

** (ShowLicence:3627): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Macbuntu/gtk-2.0/Scrollbars/vertical_trough.png,
borders don't fit within the image

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

** (ShowLicence:3627): WARNING **: Pixbuf theme: Cannot load pixmap file /usr/share/themes/Macbuntu/gtk-2.0/Scrollbars/flow-vert.png: Unable to load image-loading module: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64


(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

** (ShowLicence:3627): WARNING **: Pixbuf theme: Cannot load pixmap file /usr/share/themes/Macbuntu/gtk-2.0/Scrollbars/slider_vertical.png: Unable to load image-loading module: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64


(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

** (ShowLicence:3627): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Macbuntu/gtk-2.0/Scrollbars/slider_vertical.png,
borders don't fit within the image

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

** (ShowLicence:3627): WARNING **: Pixbuf theme: Cannot load pixmap file /usr/share/themes/Macbuntu/gtk-2.0/Scrollbars/null.png: Unable to load image-loading module: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64


(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

** (ShowLicence:3627): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Macbuntu/gtk-2.0/Scrollbars/null.png,
borders don't fit within the image

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

** (ShowLicence:3627): WARNING **: Pixbuf theme: Cannot load pixmap file /usr/share/themes/Macbuntu/gtk-2.0/Scrollbars/scroll_arrow_up_prelight.png: Unable to load image-loading module: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64


(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

** (ShowLicence:3627): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Macbuntu/gtk-2.0/Scrollbars/null.png,
borders don't fit within the image

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

** (ShowLicence:3627): WARNING **: Pixbuf theme: Cannot load pixmap file /usr/share/themes/Macbuntu/gtk-2.0/Scrollbars/scroll_arrow_down.png: Unable to load image-loading module: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64


(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

** (ShowLicence:3627): WARNING **: Pixbuf theme: Cannot load pixmap file /usr/share/themes/Macbuntu/gtk-2.0/Buttons/button-normal.png: Unable to load image-loading module: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64


(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

** (ShowLicence:3627): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Macbuntu/gtk-2.0/Buttons/button-normal.png,
borders don't fit within the image

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

** (ShowLicence:3627): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Macbuntu/gtk-2.0/Buttons/button-normal.png,
borders don't fit within the image

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

** (ShowLicence:3627): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Macbuntu/gtk-2.0/Scrollbars/vertical_trough.png,
borders don't fit within the image

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

** (ShowLicence:3627): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Macbuntu/gtk-2.0/Scrollbars/slider_vertical.png,
borders don't fit within the image

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

** (ShowLicence:3627): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Macbuntu/gtk-2.0/Scrollbars/null.png,
borders don't fit within the image

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

** (ShowLicence:3627): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Macbuntu/gtk-2.0/Scrollbars/null.png,
borders don't fit within the image

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

** (ShowLicence:3627): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Macbuntu/gtk-2.0/Scrollbars/vertical_trough.png,
borders don't fit within the image

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

** (ShowLicence:3627): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Macbuntu/gtk-2.0/Scrollbars/slider_vertical.png,
borders don't fit within the image

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

** (ShowLicence:3627): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Macbuntu/gtk-2.0/Scrollbars/null.png,
borders don't fit within the image

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

** (ShowLicence:3627): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Macbuntu/gtk-2.0/Scrollbars/null.png,
borders don't fit within the image

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

** (ShowLicence:3627): WARNING **: Pixbuf theme: Cannot load pixmap file /usr/share/themes/Macbuntu/gtk-2.0/Buttons/button-hover.png: Unable to load image-loading module: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64


(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

** (ShowLicence:3627): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Macbuntu/gtk-2.0/Buttons/button-hover.png,
borders don't fit within the image

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

** (ShowLicence:3627): WARNING **: Pixbuf theme: Cannot load pixmap file /usr/share/themes/Macbuntu/gtk-2.0/Buttons/button-push.png: Unable to load image-loading module: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64


(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

** (ShowLicence:3627): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Macbuntu/gtk-2.0/Buttons/button-push.png,
borders don't fit within the image

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

** (ShowLicence:3627): WARNING **: Pixbuf theme: Cannot load pixmap file /usr/share/themes/Macbuntu/gtk-2.0/Others/focus-trans.png: Unable to load image-loading module: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64


(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

** (ShowLicence:3627): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Macbuntu/gtk-2.0/Others/focus-trans.png,
borders don't fit within the image

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:3627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed
access control enabled, only authorized clients can connect
access control enabled, only authorized clients can connect
dpkg: dependency problems prevent configuration of dassault-systemes-draftsight:i386:
 dassault-systemes-draftsight:i386 depends on libexpat1 (>= 2.0.1-4).
 dassault-systemes-draftsight:i386 depends on libglib2.0-0 (>= 2.22.3-0).
 dassault-systemes-draftsight:i386 depends on libpcre3 (>= 7.8-3).
 dassault-systemes-draftsight:i386 depends on libselinux1 (>= 2.0.85-2).
 dassault-systemes-draftsight:i386 depends on zlib1g (>= 1:1.2.3.3.dfsg-13).
 dassault-systemes-draftsight:i386 depends on libc6 (>= 2.10.1-0).
 dassault-systemes-draftsight:i386 depends on libx11-6 (>= 2:1.2.2-1).
 dassault-systemes-draftsight:i386 depends on libxau6 (>= 1:1.0.4-2).
 dassault-systemes-draftsight:i386 depends on libxcomposite1 (>= 1:0.4.0-4).
 dassault-systemes-draftsight:i386 depends on libxcursor1 (>= 1:1.1.9-1build1).
 dassault-systemes-draftsight:i386 depends on libxdamage1 (>= 1:1.1.1-4).
 dassault-systemes-draftsight:i386 depends on libxdmcp6 (>= 1:1.0.2-3).
 dassault-systemes-draftsight:i386 depends on libxext6 (>= 2:1.0.99.1-0).
 dassault-systemes-draftsight:i386 depends on libxfixes3 (>= 1:4.0.3-2build1).
 dassault-systemes-draftsight:i386 depends on libxi6 (>= 2:1.2.1-2).
 dassault-systemes-draftsight:i386 depends on libxinerama1 (>= 2:1.0.3-2).
 dassault-systemes-draftsight:i386 depends on libxrandr2 (>= 2:1.3.0-2).
 dassault-systemes-draftsight:i386 depends on libxrender1 (>= 1:0.9.4-2).
 dassault-systemes-draftsight:i386 depends on libatk1.0-0 (>= 1.28.0-0).
 dassault-systemes-draftsight:i386 depends on libcairo2 (>= 1.8.8-2).
 dassault-systemes-draftsight:i386 depends on libdirectfb-extra (>= 1.2.7-2).
 dassault-systemes-draftsight:i386 depends on libfontconfig1 (>= 2.6.0-1).
 dassault-systemes-draftsight:i386 depends on libfreetype6 (>= 2.3.9-5).
 dassault-systemes-draftsight:i386 depends on libgtk2.0-0 (>= 2.18.3-1).
 dassault-systemes-draftsight:i386 depends on libpango1.0-0 (>= 1.26.0-1).
 dassault-systemes-draftsight:i386 depends on libpixman-1-0 (>= 0.14.0-1).
 dassault-systemes-draftsight:i386 depends on libpng12-0 (>= 1.2.37-1).
 dassault-systemes-draftsight:i386 depends on libxcb-render-util0 (>= 0.3.6-1).
 dassault-systemes-draftsight:i386 depends on libxcb-render0 (>= 1.4-1).
 dassault-systemes-draftsight:i386 depends on libxcb1 (>= 1.4-1).
 dassault-systemes-draftsight:i386 depends on libcomerr2 (>= 1.41.9-1).
 dassault-systemes-draftsight:i386 depends on libdbus-1-3 (>= 1.2.16-0).
 dassault-systemes-draftsight:i386 depends on libexpat1 (>= 2.0.1-4).
 dassault-systemes-draftsight:i386 depends on libgcc1 (>= 1:4.4.1-4).
 dassault-systemes-draftsight:i386 depends on libgcrypt11 (>= 1.4.4-2).
 dassault-systemes-draftsight:i386 depends on libglib2.0-0 (>= 2.22.3-0).
 dassault-systemes-draftsight:i386 depends on libgpg-error0 (>= 1.6-1).
 dassault-systemes-draftsight:i386 depends on libkeyutils1 (>= 1.2-10).
 dassault-systemes-draftsight:i386 depends on libpcre3 (>= 7.8-3).
 dassault-systemes-draftsight:i386 depends on libuuid1 (>= 2.16-1).
 dassault-systemes-draftsight:i386 depends on zlib1g (>= 1:1.2.3.3.dfsg-13).
 dassault-systemes-draftsight:i386 depends on libc6 (>= 2.10.1-0).
 dassault-systemes-draftsight:i386 depends on libgl1-mesa-glx (>= 7.6.0-1).
 dassault-systemes-draftsight:i386 depends on libglu1-mesa (>= 7.6.0-1).
 dassault-systemes-draftsight:i386 depends on libice6 (>= 2:1.0.5-1).
 dassault-systemes-draftsight:i386 depends on libsm6 (>= 2:1.1.0-2).
 dassault-systemes-draftsight:i386 depends on libx11-6 (>= 2:1.2.2-1).
 dassault-systemes-draftsight:i386 depends on libxau6 (>= 1:1.0.4-2).
 dassault-systemes-draftsight:i386 depends on libxdamage1 (>= 1:1.1.1-4).
 dassault-systemes-draftsight:i386 depends on libxdmcp6 (>= 1:1.0.2-3).
 dassault-systemes-draftsight:i386 depends on libxext6 (>= 2:1.0.99.1-0).
 dassault-systemes-draftsight:i386 depends on libxfixes3 (>= 1:4.0.3-2build1).
 dassault-systemes-draftsight:i386 depends on libxrender1 (>= 1:0.9.4-2).
 dassault-systemes-draftsight:i386 depends on libxt6 (>= 1:1.0.5-3).
 dassault-systemes-draftsight:i386 depends on libxxf86vm1 (>= 1:1.0.2-1).
 dassault-systemes-draftsight:i386 depends on libaudio2 (>= 1.9.2-1).
 dassault-systemes-draftsight:i386 depends on libavahi-client3 (>= 0.6.25-1).
 dassault-systemes-draftsight:i386 depends on libavahi-common3 (>= 0.6.25-1).
 dassault-systemes-draftsight:i386 depends on libcups2 (>= 1.4.1-5).
 dassault-systemes-draftsight:i386 depends on libdrm2 (>= 2.4.14-1).
 dassault-systemes-draftsight:i386 depends on libfontconfig1 (>= 2.6.0-1).
 dassault-systemes-draftsight:i386 depends on libgnutls26 (>= 2.8.3-2).
 dassault-systemes-draftsight:i386 depends on libgssapi-krb5-2 (>= 1.7dfsg~beta3-1).
 dassault-systemes-draftsight:i386 depends on libk5crypto3 (>= 1.7dfsg~beta3-1).
 dassault-systemes-draftsight:i386 depends on libkrb5-3 (>= 1.7dfsg~beta3-1).
 dassault-systemes-draftsight:i386 depends on libkrb5support0 (>= 1.7dfsg~beta3-1).
 dassault-systemes-draftsight:i386 depends on libstdc++6 (>= 4.4.1-4).
 dassault-systemes-draftsight:i386 depends on libtasn1-3 (>= 2.2-1).
 dassault-systemes-draftsight:i386 depends on libxcb1 (>= 1.4-1).
 dassault-systemes-draftsight:i386 depends on sendmail.
dpkg: error processing dassault-systemes-draftsight:i386 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dassault-systemes-draftsight:i386
family@ubuntu:~$
```

---

### Post by Elfy on 2011-08-14
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by TheManno1 on 2011-08-16
Wonder why it isn't working

---

### Post by TheManno1 on 2011-08-19
Help.

---

### Post by JC Cheloven on 2011-08-19
Hi, it seems that you're installing the linux version of draftsight (which is offered for 32 bits only) in a 64 bit system. It doesn't work "out of the box", but it's easy to get it working. Please see these threads:

[http://ubuntuforums.org/showthread.php?t=1718010](http://ubuntuforums.org/showthread.php?t=1718010)
[http://ubuntuforums.org/showthread.php?p=10555266](http://ubuntuforums.org/showthread.php?p=10555266)

If you understand spanish (not much to understand really), the procedure is summarized [here]("http://www.ggsalas.com.ar/instalar-draftsight-en-ubuntu-11-04-x64/") in a more concise way.

I got it working with that.

---

