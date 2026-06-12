---
title: "How to install Totem without all the gnome stuff?"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by sylvainrb on 2009-09-09
Hi,

I have openbox as a window manager and would like to install Totem but when i type: ```
sudo aptitude install totem
``` it asks me to install ~300MB of gnome stuff so I was wondering if there was away to just get Totem.

I could get the .deb file with ```
sudo aptitude download totem
``` but how can I get the right dependencies?

The reason is I want to play some flash videos from the internet (the ones located in /tmp) but some won't play in vlc. But I know they'll play with Totem since its the one I use in my other ubuntu machine (using gnome!)

Thanks!

---

### Post by PurposeOfReason on 2009-09-09
[http://www.linuxfromscratch.org/blfs/view/svn/gnome/totem.html](http://www.linuxfromscratch.org/blfs/view/svn/gnome/totem.html) 

**           Totem Dependencies         **

         **           Required         **

                    [GNOME Icon Theme-2.26.0]("http://www.linuxfromscratch.org/blfs/view/svn/gnome/gnome-icon-theme.html"), [GNOME           Desktop-2.26.3]("http://www.linuxfromscratch.org/blfs/view/svn/gnome/gnome-desktop.html"), [ISO           Codes-3.5]("http://www.linuxfromscratch.org/blfs/view/svn/general/iso-codes.html"), and [GStreamer Good           Plug-ins-0.10.11]("http://www.linuxfromscratch.org/blfs/view/svn/multimedia/gst-plugins-good.html") (default back-end) or [xine           Libraries-1.1.15]("http://www.linuxfromscratch.org/blfs/view/svn/multimedia/xine-lib.html") (secondary back-end)         
                    If you anticipate using Totem to           play DVDs, you should use the Xine           Libraries backend by passing --enable-xine to the **configure** script as the the           GStreamer backend does not work           properly. If you elect to use the default GStreamer backend anyway, ensure you built           GStreamer Good Plugins with           GConf support or the **configure** script will fail.         
         **           Optional         **

                    [intltool-0.40.6]("http://www.linuxfromscratch.org/blfs/view/svn/general/intltool.html"), [Nautilus-2.26.3]("http://www.linuxfromscratch.org/blfs/view/svn/gnome/nautilus.html"),           [HAL-0.5.12]("http://www.linuxfromscratch.org/blfs/view/svn/general/hal.html"), [SeaMonkey-1.1.9]("http://www.linuxfromscratch.org/blfs/view/svn/xsoft/seamonkey.html") or [Firefox-3.5.2]("http://www.linuxfromscratch.org/blfs/view/svn/xsoft/firefox.html") (to           build the browser plug-in), [libirman]("http://www.evation.com/libirman/libirman.html"),           [LIRC]("http://www.lirc.org/"), [Gromit]("http://www.home.unix-ag.org/simon/gromit/")           (required for the telestrator mode), and [NvTv Simple]("http://sourceforge.net/projects/nv-tv-out/")         
                    Note: [libdvdcss-1.2.10]("http://www.linuxfromscratch.org/blfs/view/svn/multimedia/libdvdcss.html") is a run-time requirement           if you wish to play encrypted DVDs         
                    User Notes: [http://wiki.linuxfromscratch.org/blfs/wiki/totem](http://wiki.linuxfromscratch.org/blfs/wiki/totem)

---

### Post by eyeyoubin on 2009-09-09
you could always just get VLC. it works pretty well and comes with codecs.

---

### Post by sylvainrb on 2009-09-09
> **eyeyoubin said:**
> you could always just get VLC. it works pretty well and comes with codecs.

I have vlc but some video won't play. It starts but I have no image nor sound. Do you know if I need anymore packages or codecs?

---

### Post by sylvainrb on 2009-09-09
> **PurposeOfReason said:**
> [http://www.linuxfromscratch.org/blfs/view/svn/gnome/totem.html](http://www.linuxfromscratch.org/blfs/view/svn/gnome/totem.html) 

**           Totem Dependencies         **

         **           Required         **

                    [GNOME Icon Theme-2.26.0]("http://www.linuxfromscratch.org/blfs/view/svn/gnome/gnome-icon-theme.html"), [GNOME           Desktop-2.26.3]("http://www.linuxfromscratch.org/blfs/view/svn/gnome/gnome-desktop.html"), [ISO           Codes-3.5]("http://www.linuxfromscratch.org/blfs/view/svn/general/iso-codes.html"), and [GStreamer Good           Plug-ins-0.10.11]("http://www.linuxfromscratch.org/blfs/view/svn/multimedia/gst-plugins-good.html") (default back-end) or [xine           Libraries-1.1.15]("http://www.linuxfromscratch.org/blfs/view/svn/multimedia/xine-lib.html") (secondary back-end)         
                    If you anticipate using Totem to           play DVDs, you should use the Xine           Libraries backend by passing --enable-xine to the **configure** script as the the           GStreamer backend does not work           properly. If you elect to use the default GStreamer backend anyway, ensure you built           GStreamer Good Plugins with           GConf support or the **configure** script will fail.         
         **           Optional         **

                    [intltool-0.40.6]("http://www.linuxfromscratch.org/blfs/view/svn/general/intltool.html"), [Nautilus-2.26.3]("http://www.linuxfromscratch.org/blfs/view/svn/gnome/nautilus.html"),           [HAL-0.5.12]("http://www.linuxfromscratch.org/blfs/view/svn/general/hal.html"), [SeaMonkey-1.1.9]("http://www.linuxfromscratch.org/blfs/view/svn/xsoft/seamonkey.html") or [Firefox-3.5.2]("http://www.linuxfromscratch.org/blfs/view/svn/xsoft/firefox.html") (to           build the browser plug-in), [libirman]("http://www.evation.com/libirman/libirman.html"),           [LIRC]("http://www.lirc.org/"), [Gromit]("http://www.home.unix-ag.org/simon/gromit/")           (required for the telestrator mode), and [NvTv Simple]("http://sourceforge.net/projects/nv-tv-out/")         
                    Note: [libdvdcss-1.2.10]("http://www.linuxfromscratch.org/blfs/view/svn/multimedia/libdvdcss.html") is a run-time requirement           if you wish to play encrypted DVDs         
                    User Notes: [http://wiki.linuxfromscratch.org/blfs/wiki/totem](http://wiki.linuxfromscratch.org/blfs/wiki/totem)

Thanks! I guess I won't be using Totem. I don't want to install the Gnome desktop...

---

