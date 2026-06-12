---
title: "Vodafone connect driver"
date: 2008-05-31
forum: Networking &amp; Wireless
---

### Post by mikeocaiside on 2008-05-31
running ubuntu 8.04 on hard drive i386 32 bit IBM X23 THINK PAD, this is the message I get from twistd when I start the package.

 Your device "Huawei E660A" is not properly registered with the kernel. Vodafone Mobile Connect Card driver for Linux needs at least two serial ports to communicate with your Huawei E660A. The program includes a set of udev rules plus some binaries that make sure that your device is always recognised properly. If you've installed from source, then make sure to copy the relevant files in the contrib dir 

Can anybody help a linux newbie Thanks

here is the debug file!!

mike@mike-laptop:~$ /usr/bin/vodafone-mobile-connect-card-driver-for-linux-debug
2008/06/01 16:09 +0100 [-] Log opened.
2008/06/01 16:09 +0100 [-] twistd 2.5.0 (/usr/bin/python 2.5.2) starting up
2008/06/01 16:09 +0100 [-] reactor class: <class 'twisted.internet.gtk2reactor.Gtk2Reactor'>
2008/06/01 16:09 +0100 [-] Loading /opt/vmc/usr/share/vodafone-mobile-connect-card-driver-for-linux/gtk-tap.py...
2008/06/01 16:09 +0100 [-] Loaded.
2008/06/01 16:09 +0100 [-] Changing process name to VMCCdfL
2008/06/01 16:09 +0100 [-] Log opened.
2008/06/01 16:09 +0100 [-] twistd 2.5.0 (/home/mike/ 2.5.2) starting up
2008/06/01 16:09 +0100 [-] reactor class: <class 'twisted.internet.gtk2reactor.Gtk2Reactor'>
2008/06/01 16:09 +0100 [-] Loading /opt/vmc/usr/share/vodafone-mobile-connect-card-driver-for-linux/gtk-tap.py...
2008/06/01 16:09 +0100 [-] Loaded.
2008/06/01 16:09 +0100 [-] twisted.conch.manhole_ssh.ConchFactory starting on 2222
2008/06/01 16:09 +0100 [-] Starting factory <twisted.conch.manhole_ssh.ConchFactory instance at 0x8b7676c>
Fontconfig warning: "/etc/fonts/conf.d/53-monospace-lcd-filter.conf", line 17: invalid constant used : lcdfilterlegacy
2008/06/01 16:09 +0100 [-] /opt/vmc/lib/python/site-packages/Vodafone_Mobile_Connect_Card_driver_for_Linux-2.0.beta3-py2.5.egg/vmc/contrib/gtkmvc/view.py:119: gobject.Warning: Two different plugins tried to register 'BasicEngineFc'.
2008/06/01 16:09 +0100 [-] /opt/vmc/lib/python/site-packages/Vodafone_Mobile_Connect_Card_driver_for_Linux-2.0.beta3-py2.5.egg/vmc/contrib/gtkmvc/view.py:119: gobject.Warning: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed
2008/06/01 16:09 +0100 [-] /opt/vmc/lib/python/site-packages/Vodafone_Mobile_Connect_Card_driver_for_Linux-2.0.beta3-py2.5.egg/vmc/contrib/gtkmvc/view.py:119: pango.PangoWarning: Failed to load Pango module '/usr/lib/pango/1.6.0/modules/pango-basic-fc.so' for id 'BasicScriptEngineFc'
2008/06/01 16:09 +0100 [-] /opt/vmc/lib/python/site-packages/Vodafone_Mobile_Connect_Card_driver_for_Linux-2.0.beta3-py2.5.egg/vmc/contrib/gtkmvc/view.py:59: gobject.Warning: Two different plugins tried to register 'BasicEngineFc'.
2008/06/01 16:09 +0100 [-] /opt/vmc/lib/python/site-packages/Vodafone_Mobile_Connect_Card_driver_for_Linux-2.0.beta3-py2.5.egg/vmc/contrib/gtkmvc/view.py:59: gobject.Warning: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed
2008/06/01 16:09 +0100 [-] /opt/vmc/lib/python/site-packages/Vodafone_Mobile_Connect_Card_driver_for_Linux-2.0.beta3-py2.5.egg/vmc/gtk/views/dialogs.py:38: gobject.Warning: Two different plugins tried to register 'BasicEngineFc'.
2008/06/01 16:09 +0100 [-] /opt/vmc/lib/python/site-packages/Vodafone_Mobile_Connect_Card_driver_for_Linux-2.0.beta3-py2.5.egg/vmc/gtk/views/dialogs.py:38: gobject.Warning: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed
2008/06/01 16:10 +0100 [-] Shutting down...
2008/06/01 16:10 +0100 [-] (Port 2222 Closed)
2008/06/01 16:10 +0100 [-] Stopping factory <twisted.conch.manhole_ssh.ConchFactory instance at 0x8b7676c>
2008/06/01 16:10 +0100 [-] Server Shut Down.
mike@mike-laptop:~$

---

