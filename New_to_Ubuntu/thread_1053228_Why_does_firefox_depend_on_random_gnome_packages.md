---
title: "Why does firefox depend on random gnome packages?"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by talonstriker on 2009-01-28
I just finished uninstalling gnome after installing the latest KDE.  During the uninstallation firefox was removed as well (including some java apps).  Now I'm trying to reinstall firefox and I notice that I depends on a plethora of gnome libraries...do I really need them?  How can I install firefox without gnome?

```

rdeva@sinusoidal:~$ sudo apt-get install firefox 
Reading package lists... Done                    
Building dependency tree                         
Reading state information... Done                
The following packages were automatically installed and are no longer required:
  libk3b3 libflac++6 k3b-data                                                  
Use 'apt-get autoremove' to remove them.                                       
The following extra packages will be installed:                                
  apturl docbook-xml firefox-3.0 firefox-3.0-branding gamin gconf2             
  gconf2-common gksu gnome-app-install gnome-icon-theme gnome-keyring          
  gnome-mime-data gnome-mount libavahi-glib1 libbonobo2-0 libbonobo2-common    
  libbonoboui2-0 libbonoboui2-common libcairo-perl libgamin0 libgconf2-4       
  libgksu2-0 libglade2-0 libglib-perl libgnome-keyring0 libgnome2-0            
  libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl     
  libgnomecanvas2-0 libgnomecanvas2-common libgnomeui-0 libgnomeui-common      
  libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-extra libgp11-0 libgtk2-perl 
  libgtkhtml2-0 libgtop2-7 libgtop2-common libidl0 liblaunchpad-integration1
  libnotify1 liborbit2 libpam-gnome-keyring libpolkit-gnome0 librsvg2-common
  libscrollkeeper0 libsexy2 libstartup-notification0 libvte-common libvte9
  libwnck-common libwnck22 libxres1 notification-daemon policykit-gnome
  python-cairo python-gconf python-glade2 python-gst0.10 python-gtk2
  python-gtkhtml2 python-launchpad-integration python-numeric python-pyorbit
  python-sexy python-vte scrollkeeper sgml-data software-properties-gtk
  synaptic ubufox xulrunner-1.9

```

edit: NVM, got it working with aptitude.

---

### Post by carfield on 2009-08-31
Yes, I also have that wondering.... for Firefox 3.5 . If we comparing it with Firefox 3.0, none of Gnome package are required, that is especially look like a waste for XFCE user

---

### Post by pedro3005 on 2009-08-31
Uh, this will install firefox 3.0. To get 3.5 you do:
```

sudo apt-get install firefox-3.5

```
See if that will require packages.

---

### Post by carfield on 2009-08-31
> **pedro3005 said:**
> Uh, this will install firefox 3.0. To get 3.5 you do:
```

sudo apt-get install firefox-3.5

```
See if that will require packages.

It will, but I don't want to install so many dependence, in fact, I just spend time on move from GNOME to XFCE because of that

---

### Post by t0p on 2009-08-31
> **carfield said:**
> It will, but I don't want to install so many dependence, in fact, I just spend time on move from GNOME to XFCE because of that

Unfortunately, firefox needs the dependencies it needs.  Firefox is a rather bloated browser.  If you're that short on disk space, you'd better use a different browser. Though if you're *that* short on disk space, maybe you shouldn't be running a gui at all?

---

### Post by XCan on 2009-08-31
I think carfield is more concerned about performance. Loading all the gnome and Kstuff onto xfce will kind of nullify the eventual performance gain.

---

### Post by t0p on 2009-08-31
> **XCan said:**
> I think carfield is more concerned about performance. Loading all the gnome and Kstuff onto xfce will kind of nullify the eventual performance gain.

I don't agree that it will "nullify the eventual performance gain".  Just running thunar instead of nautilus will improve performance.  But of course using a bloated browser like firefox *will* affect performance to some degree.  If performance is such an issue, don't use firefox.  There are more lightweight browsers available - epiphany for instance.

Firefox is not the be-all and end-all of web browsers.  It is featureful, but you don't get all those features without bloat.  If you want to run an app like firefox, you have to accept it will affect performance to some degree.

---

### Post by XCan on 2009-08-31
Indeed, but I was referring to the eventual performance gains as those obtained intrinsically. Simply changing the default programs in gnome to those of xfce will most likely still not give as lightweight system as using xfce by itself without loading on all the libs. Although I admit, the difference is not too big to begin with.

---

### Post by CatKiller on 2009-08-31
You can tell your package manager not to install suggested packages, you know. In particular, you can tell it not to install firefox-gnome-support, which, as the name suggests, brings in a whole load of Gnome stuff.

---

### Post by carfield on 2009-08-31
> **CatKiller said:**
> You can tell your package manager not to install suggested packages, you know. In particular, you can tell it not to install firefox-gnome-support, which, as the name suggests, brings in a whole load of Gnome stuff.

How can i tell? I am just using synatic and doesn't aware that option.

---

### Post by jpeddicord on 2009-08-31
> **carfield said:**
> How can i tell? I am just using synatic and doesn't aware that option.

Settings > Preferences; uncheck "Consider recommended packages as dependencies."

This was the default behavior (no recommends) up until last year if I remember right.

---

### Post by carfield on 2009-09-01
> **jacobmp92 said:**
> Settings > Preferences; uncheck "Consider recommended packages as dependencies."

This was the default behavior (no recommends) up until last year if I remember right.

Right, and uncheck that work better for me, not sure how the other think.

For me it really doesn't do that for performance, I just don't like to have so many file and are not going to use

---

