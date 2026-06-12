---
title: "awn-manager"
date: 2010-03-15
forum: New to Ubuntu
---

### Post by Drenriza on 2010-03-15
Im trying to get awn manager started, but without luck.

:~$ sudo awn-manager
/usr/share/avant-window-navigator/awn-manager/awnPreferences.py:242: DeprecationWarning: raising a string exception is deprecated
  raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"
Traceback (most recent call last):
  File "/usr/bin/awn-manager", line 200, in <module>
    awnmanager = AwnManager()
  File "/usr/bin/awn-manager", line 101, in __init__
    self.prefManager = awnPreferences(self.wTree)
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 150, in __init__
    self.setup_chooser(APP_ACTIVE_PNG, self.wTree.get_widget("activefilechooser"))
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 242, in setup_chooser
    raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"

Key: /apps/avant-window-navigator/app/active_png isn't set.
Restarting AWN usually solves this issue

Run as root:
awn-manager
/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py:72: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
/usr/bin/awn-manager:72: Warning: invalid (NULL) pointer instance
  self.wTree = gtk.glade.XML(self.GLADE_PATH, domain=I18N_DOMAIN)
/usr/bin/awn-manager:72: Warning: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
  self.wTree = gtk.glade.XML(self.GLADE_PATH, domain=I18N_DOMAIN)
/usr/bin/awn-manager:72: GtkWarning: gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed
  self.wTree = gtk.glade.XML(self.GLADE_PATH, domain=I18N_DOMAIN)
/usr/bin/awn-manager:72: Warning: g_object_get: assertion `G_IS_OBJECT (object)' failed
  self.wTree = gtk.glade.XML(self.GLADE_PATH, domain=I18N_DOMAIN)
/usr/bin/awn-manager:72: GtkWarning: gdk_pango_context_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed
  self.wTree = gtk.glade.XML(self.GLADE_PATH, domain=I18N_DOMAIN)
/usr/bin/awn-manager:72: PangoWarning: pango_context_set_font_description: assertion `context != NULL' failed
  self.wTree = gtk.glade.XML(self.GLADE_PATH, domain=I18N_DOMAIN)
/usr/bin/awn-manager:72: PangoWarning: pango_context_set_base_dir: assertion `context != NULL' failed
  self.wTree = gtk.glade.XML(self.GLADE_PATH, domain=I18N_DOMAIN)
/usr/bin/awn-manager:72: PangoWarning: pango_context_set_language: assertion `context != NULL' failed
  self.wTree = gtk.glade.XML(self.GLADE_PATH, domain=I18N_DOMAIN)
/usr/bin/awn-manager:72: PangoWarning: pango_layout_new: assertion `context != NULL' failed
  self.wTree = gtk.glade.XML(self.GLADE_PATH, domain=I18N_DOMAIN)
/usr/bin/awn-manager:72: PangoWarning: pango_layout_set_text: assertion `layout != NULL' failed
  self.wTree = gtk.glade.XML(self.GLADE_PATH, domain=I18N_DOMAIN)
/usr/bin/awn-manager:72: PangoWarning: pango_layout_get_pixel_extents: assertion `PANGO_IS_LAYOUT (layout)' failed
  self.wTree = gtk.glade.XML(self.GLADE_PATH, domain=I18N_DOMAIN)
/usr/bin/awn-manager:72: Warning: g_object_unref: assertion `G_IS_OBJECT (object)' failed
  self.wTree = gtk.glade.XML(self.GLADE_PATH, domain=I18N_DOMAIN)
/usr/bin/awn-manager:72: GtkWarning: gtk_widget_set_size_request: assertion `height >= -1' failed
  self.wTree = gtk.glade.XML(self.GLADE_PATH, domain=I18N_DOMAIN)
/usr/bin/awn-manager:72: GtkWarning: gdk_pixbuf_new: assertion `height > 0' failed
  self.wTree = gtk.glade.XML(self.GLADE_PATH, domain=I18N_DOMAIN)
/usr/bin/awn-manager:72: PangoWarning: pango_context_list_families: assertion `context != NULL' failed
  self.wTree = gtk.glade.XML(self.GLADE_PATH, domain=I18N_DOMAIN)
/usr/bin/awn-manager:72: GtkWarning: gtk_icon_theme_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed
  self.wTree = gtk.glade.XML(self.GLADE_PATH, domain=I18N_DOMAIN)
/usr/bin/awn-manager:72: GtkWarning: gtk_icon_size_lookup_for_settings: assertion `GTK_IS_SETTINGS (settings)' failed
  self.wTree = gtk.glade.XML(self.GLADE_PATH, domain=I18N_DOMAIN)
/usr/bin/awn-manager:72: GtkWarning: Invalid icon size 1

  self.wTree = gtk.glade.XML(self.GLADE_PATH, domain=I18N_DOMAIN)
/usr/bin/awn-manager:72: GtkWarning: gtk_icon_theme_load_icon: assertion `GTK_IS_ICON_THEME (icon_theme)' failed
  self.wTree = gtk.glade.XML(self.GLADE_PATH, domain=I18N_DOMAIN)
Segmentation fault

EDIT:
When trying to run avant-window-navigator

i get this output.
(avant-window-navigator:6811): Gtk-WARNING **: cannot open display:

Versions
ii  awn-manager              0.2.1-0ubuntu2.2                          A manager for the preferences of avant-windo
ii  libawn0                  0.2.1-0ubuntu2.2                          library for avant-window-navigator

Reposatory
deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main

How can i restart the awn-manager? (have read that it doesnt help)
How can i fix the problem?

Thanks on advance.
Kind regards

---

### Post by Easy Limits on 2010-03-15
Did you try downloading Awn from the Software Center?

---

### Post by Drenriza on 2010-03-16
I cannot find awn-manager in the software center.

---

### Post by lotharmat on 2010-03-16
Check out below

---

### Post by Drenriza on 2010-03-16
Okey, i searched on the wrong thing.

I found the Avant WIndow Navigator. And it says that it is already installed, on the system.

---

### Post by overlord.gaurav on 2010-03-16
Why are you using sudo? Why not just awn-manager? 
Or simply avant-window-navigator ?
Run avant-window-navigator and then you can open the awn-manager from the dock.

---

### Post by lotharmat on 2010-03-16
> **Drenriza said:**
> Okey, i searched on the wrong thing.

I found the Avant WIndow Navigator. And it says that it is already installed, on the system.


Can you see it in the menus thus?

---

### Post by Drenriza on 2010-03-16
Nope. I cannot see avant window navigator

---

### Post by Drenriza on 2010-03-16
as a reply to overloard.

$ avant-window-navigator
Error: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.

---

### Post by overlord.gaurav on 2010-03-16
You need to make sure that visual effects are enabled.
Go to System->Preferences->Appearance->Visual Effects->Change it to anything other than none. And now try avant-window-navigator.
Hope this fixes your problem.

---

### Post by Drenriza on 2010-03-16
It says that disktop effects cannot be enabled.

Im running ubuntu in an vmware-workstation 7 with an 8600GT grafic card. Arnt that enough?

---

### Post by overlord.gaurav on 2010-03-16
I don't think I have the solution to your problem. Probably somebody else will have one. 
Anyway, I came across [this post]("http://communities.vmware.com/thread/169821") when I tried to Google your problem.
I hope somebody finds you a solution..

---

### Post by Drenriza on 2010-03-16
would it help anything to upgrade my ubuntu distribution?

---

### Post by lotharmat on 2010-03-16
What version of Ubuntu are you using?

My gut feeling is that the VMWare will not see the full capabilities of the graphics card though.

Can you try VirtualBox (Sun) - IIRC version 3 incorporates OpenGL and thus compositing *should* work!

---

### Post by overlord.gaurav on 2010-03-16
> **Drenriza said:**
> would it help anything to upgrade my ubuntu distribution?

As far as a few Google results are to be believed, I would also recommend you to try [VirutalBox]("http://www.virtualbox.org/") instead of VMWare.
The article [here]("http://www.dedoimedo.com/computers/virtualization-3d-support-virtualbox.html") suggests that VirtualBox officially supports 3D acceleration.
I hope AWN should work fine for you on VirtualBox.

---

### Post by Drenriza on 2010-03-16
I have used virtualbox before. The problem with virtual box is it capabilities to discover usb devices. VmWare works greath execpt for this minor thing.

---

### Post by lotharmat on 2010-03-16
Is dual-booting out of the question?

It seems that if you want AWN; you are using Ubuntu quite alot. To be honest a dual-boot system will be better than virtualization any day.

---

### Post by Drenriza on 2010-03-16
That is not an option. Because i use windows & ubuntu at the same time. 90% of my day.

---

### Post by lotharmat on 2010-03-16
Same here - but on two different machines!

Hmmm.

The choice between good USB functionality and Compiz....

I'd take the good USB.

Unless someone knows of any other dock app that doesn't need compositing.

cairo-dock; iirc has got a non openGL mode that may work well in your situation.

```
sudo apt-get install cairo-dock
```

---

### Post by overlord.gaurav on 2010-03-17
Drenriza, seems like I have a bad news for you.
You cannot enable 3d acceleration on VMWare with linux as guest.
Read the post [here]("http://communities.vmware.com/message/1419545").

---

### Post by Paqman on 2010-03-17
> **Drenriza said:**
> 
Im running ubuntu in an vmware-workstation 7 with an 8600GT grafic card. Arnt that enough?

Support for hardware graphics acceleration is in it's infancy in virtual machines. Your graphics card won't be getting used at all.

The non-Open Source version of [Virtualbox]("http://www.virtualbox.org/wiki/Downloads") has full USB support. Later versions of AWN also work without the screen being composited. If you're running Hardy that will mean connecting to the [AWN PPA]("https://launchpad.net/~awn-testing/+archive/ppa") to get an upgraded version.

---

### Post by Drenriza on 2010-03-18
Why can't i download the packages
avant-window-navigator-trunk  0.3.9.1.1~bzr638-1.10.04  
awn-extras-applets-trunk  0.3.9.1.1~bzr1217-1.10.04  

I can only see them, and the person who added them. But not download?

from [https://launchpad.net/~awn-testing/+archive/ppa](https://launchpad.net/~awn-testing/+archive/ppa) ?

---

### Post by Paqman on 2010-03-18
A PPA is basically a small private repository. Click on the "read about installing" link on that page to get instructions. Once you've added the PPA, you can get the packages through Synaptic or Software Centre like normal.

---

