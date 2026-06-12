---
title: "Dependency problems"
date: 2010-07-04
forum: New to Ubuntu
---

### Post by bokgeneraal on 2010-07-04
Hi there
Every time I install a new program I get the following error message in synaptic :
E: kdebase-runtime: subprocess installed post-installation script returned error exit status 2
E: amarok: dependency problems - leaving unconfigured
E: blinken: dependency problems - leaving unconfigured
E: k9copy: dependency problems - leaving unconfigured
E: kaffeine: dependency problems - leaving unconfigured
E: kalgebra: dependency problems - leaving unconfigured
E: kalzium: dependency problems - leaving unconfigured
E: kanagram: dependency problems - leaving unconfigured
E: kbruch: dependency problems - leaving unconfigured
E: kdebase-bin: dependency problems - leaving unconfigured
E: kdebase-runtime-bin-kde4: dependency problems - leaving unconfigured
E: kdebase-workspace-kgreet-plugins: dependency problems - leaving unconfigured
E: libkcddb4: dependency problems - leaving unconfigured
E: kdemultimedia-kio-plugins: dependency problems - leaving unconfigured
E: khangman: dependency problems - leaving unconfigured
E: khelpcenter4: dependency problems - leaving unconfigured
E: kig: dependency problems - leaving unconfigured
E: kmplot: dependency problems - leaving unconfigured
E: krosspython: dependency problems - leaving unconfigured
E: kstars: dependency problems - leaving unconfigured
E: ktouch: dependency problems - leaving unconfigured
E: libkdegames5: dependency problems - leaving unconfigured
E: ktuberling: dependency problems - leaving unconfigured
E: kturtle: dependency problems - leaving unconfigured
E: kwordquiz: dependency problems - leaving unconfigured
E: marble: dependency problems - leaving unconfigured
E: parley: dependency problems - leaving unconfigured
E: plasma-widget-playwolf: dependency problems - leaving unconfigured
E: sabily-gdm-themes: subprocess installed post-installation script returned error exit status 2
E: step: dependency problems - leaving unconfigured
E: ubuntu-edu-preschool: dependency problems - leaving unconfigured
E: ubuntu-edu-primary: dependency problems - leaving unconfigured
E: ubuntu-edu-secondary: dependency problems - leaving unconfigured
E: ubuntu-edu-tertiary: dependency problems - leaving unconfigured
E: ubuntume-gdm-themes: dependency problems - leaving unconfigured
E: ubuntustudio-gdm-theme: subprocess installed post-installation script returned error exit status 2
E: umbrello: dependency problems - leaving unconfigured
E: kolourpaint4: dependency problems - leaving unconfigured
E: polkit-kde-1: dependency problems - leaving unconfigured

Sorry about the bloated post anyone know what causes this. ;)

---

### Post by Leppie on 2010-07-04
try the following:
```
sudo apt-get -f install
```

---

### Post by wojox on 2010-07-04
If that don't work try:

```
sudo dpkg --force all --remove
```

---

