---
title: "problems installing openMotif"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by stephendlynch on 2010-05-25
hello!

I'm running into troubles installing openMotif.   So far my efforts have all been to build from source - if there is a pre-built binary available for ubuntu 10.04 (x86_64) it's not obvious to me which it is.  

But make is having problems with XmStrDefs.c in lib/Xm/ (within the source code tree): 

XmStrDefs.c:1371: warning: excess elements in scalar initializer
XmStrDefs.c:1371: warning: (near initialization for ‘_XmStrings’)

The above messages come up many times each for several lines in XmStrDefs.c 

finally make quits: 
XmStrDefs.c:18: error: declaration for parameter ‘_XmStrings’ but no such parameter
XmStrDefs.c:1733: error: expected ‘{’ at end of input
make[3]: *** [XmStrDefs.lo] Error 1
make[3]: Leaving directory `/usr/local/src/openmotif-2.3.3/lib/Xm'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/usr/local/src/openmotif-2.3.3/lib/Xm'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/local/src/openmotif-2.3.3/lib'
make: *** [all-recursive] Error 1

I'm not sure if I'm still missing some include file or package that openMotif still requires or what. 
previously i had tried to build openMotif-2.2.3, and thought that maybe the newer version would be better suited for Ubuntu (was previously running SUSE), but the same thing happens for openMotif-2.3.3.  

ANY guidance would be GREATLY appreciated!  

THANKS! 

-sdl

---

### Post by gmargo on 2010-05-25
Open Motif v2.2.3 from the 10.04 Lucid repository:

```

$ apt-cache search "open motif"
libmotif-dev - Open Motif - development files
libmotif3 - Open Motif - shared libraries
motif-clients - Open Motif - X11 clients (mwm, xmbind)

$ apt-cache show `apt-cache search "open motif" | awk '{print $1}'` | egrep "^Package:|^Version:"
Package: libmotif-dev
Version: 2.2.3-4
Package: libmotif3
Version: 2.2.3-4
Package: motif-clients
Version: 2.2.3-4

```

---

### Post by stephendlynch on 2010-05-25
wow.  thank you.   i feel pretty silly, but that doesn't matter because i'm happily on my way. 

thanks again.   have a good one.

-sdl

---

### Post by janniklindquist on 2010-07-23
When I try to install OpenMotif (sudo aptitude install libxaw6 libmotif3), I am told that a lot of packages will be uninstalled. Is it safe to uninstall these packages? How can I install OpenMotif without uninstalling them? The packages are:

akonadi-server{u} kdebase-workspace-bin{u} kdebase-workspace-data{u} 
  kdebase-workspace-kgreet-plugins{u} kdepim-runtime{u} ksysguardd{u} 
  libkephal4{u} libkfontinst4{u} libkscreensaver5{u} libksgrd4{u} 
  libkworkspace4{u} libplasma-applet-system-monitor4{u} 
  libplasma-geolocation-interface4{u} libplasmaclock4{u} 
  libplasmagenericshell4{u} libprocesscore4{u} libprocessui4{u} 
  libqimageblitz4{u} libqt3-mt{u} libsolidcontrol4{u} 
  libsolidcontrolifaces4{u} libtaskmanager4{u} libweather-ion4{u} 
  linux-backports-modules-wireless-2.6.32-22-generic{u} 
  mysql-client-core-5.1{u} mysql-server-core-5.1{u} 
  plasma-dataengines-workspace{u} plasma-widgets-workspace{u} 

tia,
Jannik

---

### Post by gmargo on 2010-07-24
> **janniklindquist said:**
> When I try to install OpenMotif (sudo aptitude install libxaw6 libmotif3), I am told that a lot of packages will be uninstalled. Is it safe to uninstall these packages? How can I install OpenMotif without uninstalling them? 

Those packages are unrelated to motif.  They are uninstalling for another reason.  You can these this theory by attempting to install yet another package that is clearly unrelated.  Try to install the **units** package (assuming it's not installed already) and see if you get the same message.

I suspect that just recently you removed something that caused kubuntu-desktop to get uninstalled.  One easy but tedious way to get around this is to explicitly install each of those packages - which changes their internal status from "automatically installed" to "manually installed". Hence they will not try to uninstall automatically.

Another possibility is that you have recently decided to ditch kde (since those are all kde-related packages) but it's not fully uninstalled.

---

