---
title: "Nokia 5310 bluetooth pairing problem"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by r3bol on 2009-11-22
Hi, I'm using LinuxMint7 (Ubuntu 9.04) and I'm having some problems pairing my Nokia Xpressmusic 5310 with my PC - The error reads "Failed to pair" or something. 
Weird thing is, the phone displays that I'm paired with the PC, but I can't transfer any files. I've had no problems pairing other phones and other devices with Ubuntu in the past. It's just this model that affects me. Note, USB connection is not a problem. 

Is this an Ubuntu issue or a Nokia issue? Is there anything I could install/try?

Thanks.

---

### Post by frenchn00b on 2009-11-22
> **r3bol said:**
> Hi, I'm using LinuxMint7 (Ubuntu 9.04) and I'm having some problems pairing my Nokia Xpressmusic 5310 with my PC - The error reads "Failed to pair" or something. 
Weird thing is, the phone displays that I'm paired with the PC, but I can't transfer any files. I've had no problems pairing other phones and other devices with Ubuntu in the past. It's just this model that affects me. Note, USB connection is not a problem. 

Is this an Ubuntu issue or a Nokia issue? Is there anything I could install/try?

Thanks.



Have you installed gnome and the blue-manager things? 

here are the package I have installed
> ii  blueman                              1.21-1                     A Graphical bluetooth manager
ii  bluetooth                            4.42-2                     Bluetooth support
ii  bluez                                4.42-2                     Bluetooth tools and daemons
ii  bluez-alsa                           4.42-2                     Bluetooth ALSA support
ii  bluez-cups                           4.42-2                     Bluetooth printer driver for CUPS
rc  bluez-gnome                          0.27-1                     Bluetooth utilities for GNOME
ii  bluez-gstreamer                      4.42-2                     Bluetooth GStreamer support
ii  bluez-hcidump                        1.42-1+b1                  Analyses Bluetooth HCI packets
ii  bluez-utils                          4.42-2                     Transitional package
ii  gnome-bluetooth                      2.27.5-1                   GNOME Bluetooth tools
ii  kdebluetooth                         1.0~beta8-6+b1             KDE Bluetooth Framework
ii  libbluetooth3                        4.42-2                     Library to use the BlueZ Linux Bluetooth sta
ii  libgnome-bluetooth2                  2.27.5-1                   GNOME Bluetooth tools - support library
ii  libkbluetooth0                       1.0~beta8-6+b1             Bluetooth library for KDE
ii  libpam-blue                          0.9.0-2.3                  PAM module for local authenticaction with bl
ii  mplayer-skin-blue                    1.6-2                      blue skin for mplayer
ii  python-bluez                         0.17-1                     Python wrappers around BlueZ for rapid bluet
ii  blueman                              1.21-1                     A Graphical bluetooth manager
ii  bluetooth                            4.42-2                     Bluetooth support
ii  bluez                                4.42-2                     Bluetooth tools and daemons
ii  bluez-alsa                           4.42-2                     Bluetooth ALSA support
ii  bluez-cups                           4.42-2                     Bluetooth printer driver for CUPS
rc  bluez-gnome                          0.27-1                     Bluetooth utilities for GNOME
ii  bluez-gstreamer                      4.42-2                     Bluetooth GStreamer support
ii  bluez-hcidump                        1.42-1+b1                  Analyses Bluetooth HCI packets
ii  gnome-bluetooth                      2.27.5-1                   GNOME Bluetooth tools
ii  kdebluetooth                         1.0~beta8-6+b1             KDE Bluetooth Framework
ii  libbluetooth3                        4.42-2                     Library to use the BlueZ Linux Bluetooth sta
ii  libgnome-bluetooth2                  2.27.5-1                   GNOME Bluetooth tools - support library
ii  libkbluetooth0                       1.0~beta8-6+b1             Bluetooth library for KDE
ii  dbus                                 1.2.16-2                   simple interprocess messaging system
ii  dbus-x11                             1.2.16-2                   simple interprocess messaging system (X11 de
ii  libaudclient2                        2.1-1+b1                   audacious dbus remote control library
ii  libdbus-1-3                          1.2.16-2                   simple interprocess messaging system
ii  libdbus-glib-1-2                     0.82-2                     simple interprocess messaging system (GLib-b
ii  libdbus-qt-1-1c2                     0.62.git.20060814-2        simple interprocess messaging system (Qt-bas
ii  libeggdbus-1-0                       0.5-2                      D-Bus bindings for GObject
ii  libndesk-dbus-glib1.0-cil            0.4.1-2                    CLI implementation of D-Bus (GLib mainloop i
ii  libndesk-dbus1.0-cil                 0.6.0-3                    CLI implementation of D-Bus
ii  libnet-dbus-perl                     0.33.6-1+b1                Extension for the DBus bindings
ii  libpolkit-dbus2                      0.9-4                      library for accessing PolicyKit via D-Bus
ii  libqt4-dbus                          4:4.5.3-4                  Qt 4 D-Bus module
ii  python-dbus                          0.83.0-1                   simple interprocess messaging system (Python
ii  python-qt4-dbus                      4.6-1                      DBus Support for PyQt4
ii  python                               2.5.4-2                    An interactive high-level object-oriented la
ii  python-beagle                        0.3.9-1                    Python bindings for beagle
ii  python-bluez                         0.17-1                     Python wrappers around BlueZ for rapid bluet
ii  python-cairo                         1.8.6-1                    Python bindings for the Cairo vector graphic
ii  python-central                       0.6.12+nmu1                register and build utility for Python packag
ii  python-crypto                        2.0.1+dfsg1-4              cryptographic algorithms and protocols for P
ii  python-dbus                          0.83.0-1                   simple interprocess messaging system (Python
ii  python-gconf                         2.28.0-1                   Python bindings for the GConf configuration 
ii  python-gdata                         1.1.1-1                    Google Data Python client library
ii  python-gdbm                          2.5.2-1.1                  GNU dbm database support for Python
ii  python-glade2                        2.16.0-1                   GTK+ bindings: Glade support
ii  python-gmenu                         2.28.0-1                   an implementation of the freedesktop menu sp
ii  python-gnome2                        2.28.0-1                   Python bindings for the GNOME desktop enviro
ii  python-gnomeapplet                   2.26.0-1                   Python bindings for the GNOME panel applet l
ii  python-gnomedesktop                  2.26.0-1                   Python bindings for the GNOME desktop librar
ii  python-gnomekeyring                  2.26.0-1                   Python bindings for the GNOME keyring librar
ii  python-gobject                       2.20.0-1                   Python bindings for the GObject library
ii  python-gst0.10                       0.10.17-1                  generic media-playing framework (Python bind
ii  python-gtk2                          2.16.0-1                   Python bindings for the GTK+ widget set
ii  python-libxml2                       2.7.6.dfsg-1               Python bindings for the GNOME XML library
ii  python-minimal                       2.5.4-2                    A minimal subset of the Python language (def
ii  python-notify                        0.1.1-2+b1                 Python bindings for libnotify
ii  python-numpy                         1:1.3.0-3                  Numerical Python adds a fast array facility 
ii  python-paramiko                      1.7.4-0.1                  Make ssh v2 connections with python
ii  python-pkg-resources                 0.6.6-1                    Package Discovery and Resource Access using 
ii  python-pyorbit                       2.24.0-2                   A Python language binding for the ORBit2 COR
ii  python-qt4                           4.4.4-6                    Python bindings for Qt4
ii  python-qt4-common                    4.4.4-6                    Shared files for PyQt4
ii  python-qt4-dbus                      4.6-1                      DBus Support for PyQt4
ii  python-rdflib                        2.4.2-1                    RDF library containing an RDF triple store a
ii  python-reportbug                     4.8                        Python modules for interacting with bug trac
ii  python-sip4                          4.7.9-2                    Python/C++ bindings generator runtime librar
ii  python-support                       1.0.4                      automated rebuilding support for Python modu
rc  python-twisted-core                  8.2.0-3                    Event-based framework for internet applicati
ii  python-wnck                          2.26.0-1                   Python bindings for the WNCK library
ii  python-xdg                           0.17-0.1                   Python library to access freedesktop.org sta
ii  python2.5                            2.5.4-2                    An interactive high-level object-oriented la
ii  python2.5-minimal                    2.5.4-2                    A minimal subset of the Python language (ver
ii  libcairo-perl                        1.061-1                    Perl interface to the Cairo graphics library
ii  libcairo2                            1.8.8-2                    The Cairo 2D vector graphics library
ii  libcairo2-dev                        1.8.8-2                    Development files for the Cairo 2D graphics 
ii  libcairomm-1.0-1                     1.8.0-1                    C++ wrappers for Cairo (shared libraries)
ii  libcairomm-1.0-dev                   1.8.0-1                    C++ wrappers for Cairo (development files)
ii  libmono-cairo2.0-cil                 2.4.2.3+dfsg-2             Mono Cairo library (for CLI 2.0)
ii  libpixman-1-0                        0.16.2-1                   pixel-manipulation library for X and cairo
ii  libpixman-1-dev                      0.16.2-1                   pixel-manipulation library for X and cairo (
ii  python-cairo                         1.8.6-1                    Python bindings for the Cairo vector graphic
ii  libevent-1.4-2                       1.4.12-stable-1            An asynchronous event notification library
ii  libknotificationitem-1-1             4:4.3.2-1                  library for new way of handling system tray
ii  libnotify1                           0.4.5-1                    sends desktop notifications to a notificatio
ii  libstartup-notification0             0.10-1                     library for program launch feedback (shared 
ii  libzephyr4                           3.0~rc.2544-1              Project Athena's notification service - non-
ii  notification-daemon                  0.4.0-2                    a daemon that displays passive pop-up notifi
ii  specto                               0.2.2-3.1                  Unobtrusive update notification program

 
You need gnome and one or few of those packages

I forgot hte names: but the programs you have to run 
are 

blue something - installer
and 
blue something - manager
e.g. blue-manager

forget command line to pairing : it is not working
forget kbluetooh: it is not working either

---

