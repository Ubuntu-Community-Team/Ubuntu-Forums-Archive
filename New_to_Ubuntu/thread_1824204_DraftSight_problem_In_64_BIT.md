---
title: "DraftSight problem In 64 BIT"
date: 2011-08-13
forum: New to Ubuntu
---

### Post by TheManno1 on 2011-08-13
This Happens when I  sudo ./preinst

family@ubuntu:~/DraftSight/DEBIAN$ sudo ./preinst
access control disabled, clients can connect from any host
access control disabled, clients can connect from any host

(ShowLicence:27409): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(ShowLicence:27409): Gtk-WARNING **: Loading IM context type 'ibus' failed

** (ShowLicence:27409): WARNING **: Pixbuf theme: Cannot load pixmap file /usr/share/themes/Macbuntu/gtk-2.0/Scrollbars/vertical_trough.png: Unable to load image-loading module: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64


(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

** (ShowLicence:27409): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Macbuntu/gtk-2.0/Scrollbars/vertical_trough.png,
borders don't fit within the image

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

** (ShowLicence:27409): WARNING **: Pixbuf theme: Cannot load pixmap file /usr/share/themes/Macbuntu/gtk-2.0/Scrollbars/flow-vert.png: Unable to load image-loading module: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64


(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

** (ShowLicence:27409): WARNING **: Pixbuf theme: Cannot load pixmap file /usr/share/themes/Macbuntu/gtk-2.0/Scrollbars/slider_vertical.png: Unable to load image-loading module: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64


(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

** (ShowLicence:27409): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Macbuntu/gtk-2.0/Scrollbars/slider_vertical.png,
borders don't fit within the image

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

** (ShowLicence:27409): WARNING **: Pixbuf theme: Cannot load pixmap file /usr/share/themes/Macbuntu/gtk-2.0/Scrollbars/null.png: Unable to load image-loading module: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64


(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

** (ShowLicence:27409): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Macbuntu/gtk-2.0/Scrollbars/null.png,
borders don't fit within the image

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

** (ShowLicence:27409): WARNING **: Pixbuf theme: Cannot load pixmap file /usr/share/themes/Macbuntu/gtk-2.0/Scrollbars/scroll_arrow_up_prelight.png: Unable to load image-loading module: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64


(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

** (ShowLicence:27409): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Macbuntu/gtk-2.0/Scrollbars/null.png,
borders don't fit within the image

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

** (ShowLicence:27409): WARNING **: Pixbuf theme: Cannot load pixmap file /usr/share/themes/Macbuntu/gtk-2.0/Scrollbars/scroll_arrow_down.png: Unable to load image-loading module: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64


(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

** (ShowLicence:27409): WARNING **: Pixbuf theme: Cannot load pixmap file /usr/share/themes/Macbuntu/gtk-2.0/Buttons/button-normal.png: Unable to load image-loading module: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64


(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

** (ShowLicence:27409): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Macbuntu/gtk-2.0/Buttons/button-normal.png,
borders don't fit within the image

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

** (ShowLicence:27409): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Macbuntu/gtk-2.0/Buttons/button-normal.png,
borders don't fit within the image

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

** (ShowLicence:27409): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Macbuntu/gtk-2.0/Scrollbars/vertical_trough.png,
borders don't fit within the image

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

** (ShowLicence:27409): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Macbuntu/gtk-2.0/Scrollbars/slider_vertical.png,
borders don't fit within the image

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

** (ShowLicence:27409): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Macbuntu/gtk-2.0/Scrollbars/null.png,
borders don't fit within the image

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

** (ShowLicence:27409): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Macbuntu/gtk-2.0/Scrollbars/null.png,
borders don't fit within the image

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

** (ShowLicence:27409): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Macbuntu/gtk-2.0/Scrollbars/vertical_trough.png,
borders don't fit within the image

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

** (ShowLicence:27409): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Macbuntu/gtk-2.0/Scrollbars/slider_vertical.png,
borders don't fit within the image

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

** (ShowLicence:27409): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Macbuntu/gtk-2.0/Scrollbars/null.png,
borders don't fit within the image

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

** (ShowLicence:27409): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Macbuntu/gtk-2.0/Scrollbars/null.png,
borders don't fit within the image

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(ShowLicence:27409): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

---

### Post by LowSky on 2011-08-14
pixbuf need to be installed (probably the dev files or something omre than the basic installed version), and your theme doesn't work with the program, so that can easily be changed.

---

