---
title: "How can I get back to Gnome 2 from Gnome 3"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by nemodot on 2011-04-30
I'm using Ubuntu 11.04, deleted Unity and installed Gnome 3.0, I would like to get back to the earlier version of gnome, how can I do it?

---

### Post by kansasnoob on 2011-04-30
How did you install gnome3?

Both methods I know of clearly say it can't be undone:

[https://launchpad.net/~gnome3-team/+archive/gnome3](https://launchpad.net/~gnome3-team/+archive/gnome3)

> This package contains packages from GNOME3 and their dependencies so they can be used in Ubuntu 11.04 (Natty). This PPA is EXPERIMENTAL and MAY BREAK YOUR SYSTEM. There is no downgrade process.

[http://ugr.teampr0xy.net/install](http://ugr.teampr0xy.net/install)

> DO NOT install this on a production machine, THERE IS NO DOWNGRADE PATH. THIS HAS NO WARRANTY, AND IT COULD SERIOUSLY MESS THINGS UP.  

---

### Post by sinelaw on 2011-05-26
> **nemodot said:**
> I'm using Ubuntu 11.04, deleted Unity and installed Gnome 3.0, I would like to get back to the earlier version of gnome, how can I do it?

I was about to kill myself too. But I managed to do it.
```

sudo apt-get install gnome-session=2.32.1-0ubuntu20 gnome-session-bin=2.32.1-0ubuntu20 gnome-session-common=2.32.1-0ubuntu20  gdm=2.32.1-0ubuntu3 gnome-session-common=2.32.1-0ubuntu20 gnome-settings-daemon=2.32.1-0ubuntu13.1 eog=2.32.1-0ubuntu2 gnome-screensaver=2.30.2-0ubuntu2 gnome-menus=2.30.5-0ubuntu3 python-gmenu=2.30.5-0ubuntu3 nautilus=1:2.32.2.1-0ubuntu13 nautilus-data=1:2.32.2.1-0ubuntu13 libgnome-desktop-2-17 gnome-panel=1:2.32.1-0ubuntu6.5 libgnome-menu2 gnome-control-center=1:2.32.1-0ubuntu15


```

EDIT: Afterwards I discovered some things (like nautilus) were not working. So I did also:

```

sudo apt-get install gnome-nettool=2.32.0-0ubuntu1 gnome-terminal=2.32.1-0ubuntu3  gnome-system-log=2.32.0-0ubuntu5 gnome-utils-common=2.32.0-0ubuntu5  gnome-terminal-data=2.32.1-0ubuntu3 libnautilus-extension1=1:2.32.2.1-0ubuntu13
 sudo apt-get remove aisleriot apturl banshee banshee-extension-soundmenu banshee-extension-ubuntuonemusicstore brasero desktopcouch empathy  eog evince evolution-data-server gcalctool gconf-editor gdebi gedit gir1.2-gnomebluetooth-1.0 gir1.2-gtk-3.0  gir1.2-peas-1.0 gir1.2-rb-0.13 gir1.2-totem-1.0 gir1.2-webkit-3.0 gnome-accessibility-themes gnome-applets  gnome-codec-install gnome-control-center gnome-disk-utility gnome-games-common gnome-icon-theme gnome-icon-theme-symbolic  gnome-keyring gnome-mahjongg gnome-media gnome-panel gnome-power-manager gnome-screensaver gnome-sudoku  gnome-system-monitor gnome-system-tools gnome-themes-selected gnome-themes-ubuntu gnomine gtk3-engines gucharmap  human-theme humanity-icon-theme ibus-gtk indicator-applet indicator-applet-appmenu indicator-applet-complete  indicator-applet-session indicator-datetime libappindicator3-1 libavahi-ui-gtk3-0 libcanberra-gtk3-0  libcanberra-gtk3-module libclutter-gtk-1.0-0 libcryptui0a libdbusmenu-gtk3-3 libgail-3-0 libgcr-3-0 libgdu-gtk0  libgnome-control-center1 libgnome-media-profiles-3.0-0 libgtk-3-0 libgtk-3-bin libgtk-3-common libgtk-vnc-2.0-0  libgtkmm-3.0-1 libgtksourceview-3.0-0 libgucharmap-2-90-7 libgucharmap7 libgweather-3-0 libindicator3-3  liblaunchpad-integration-3.0-1 libmutter0 libpeas-1.0-0 libpolkit-gtk-1-0 librhythmbox-core4 libseed-gtk3-0  libsyncdaemon-1.0-1 libtotem0 libubuntuone-1.0-1 libubuntuone1.0-cil libunique-3.0-0 libvte-2.90-9 libwebkitgtk-3.0-0  libwnck-3-0 light-themes metacity mousetweaks mutter network-manager-gnome pitivi python-desktopcouch  python-desktopcouch-application python-ubuntuone python-ubuntuone-control-panel quadrapassel rhythmbox rhythmbox-plugins  rhythmbox-ubuntuone-music-store seahorse simple-scan software-center system-config-printer-gnome totem totem-mozilla  totem-plugins ubuntu-artwork ubuntu-desktop ubuntu-mono ubuntu-sso-client ubuntuone-client ubuntuone-client-gnome  ubuntuone-control-panel ubuntuone-control-panel-gtk unity unity-asset-pool vinagre vino zenity
sudo apt-get install aisleriot apturl banshee banshee-extension-soundmenu banshee-extension-ubuntuonemusicstore brasero desktopcouch empathy  eog evince evolution-data-server gcalctool gconf-editor gdebi gedit   gir1.2-peas-1.0  gir1.2-webkit-3.0 gnome-accessibility-themes gnome-applets  gnome-codec-install gnome-control-center gnome-disk-utility gnome-games-common gnome-icon-theme   gnome-keyring gnome-mahjongg gnome-media gnome-panel gnome-power-manager gnome-screensaver gnome-sudoku  gnome-system-monitor gnome-system-tools gnome-themes-selected gnome-themes-ubuntu gnomine  gucharmap  human-theme humanity-icon-theme ibus-gtk indicator-applet indicator-applet-appmenu indicator-applet-complete  indicator-applet-session indicator-datetime   libclutter-gtk-1.0-0  libgail-3-0  libgdu-gtk0    libpeas-1.0-0 libpolkit-gtk-1-0  libsyncdaemon-1.0-1  libubuntuone-1.0-1 libubuntuone1.0-cil  libvte-2.90-9  light-themes metacity mousetweaks mutter network-manager-gnome pitivi python-desktopcouch  python-desktopcouch-application python-ubuntuone python-ubuntuone-control-panel quadrapassel rhythmbox rhythmbox-plugins  rhythmbox-ubuntuone-music-store seahorse simple-scan software-center system-config-printer-gnome totem totem-mozilla  totem-plugins ubuntu-artwork ubuntu-desktop ubuntu-mono ubuntu-sso-client ubuntuone-client ubuntuone-client-gnome  ubuntuone-control-panel ubuntuone-control-panel-gtk unity unity-asset-pool vinagre vino zenity gstreamer0.10-plugins-good libgstfarsight0.10-0 libtelepathy-farsight0 libedata-cal1.2-10  evolution-data-server-common=2.32.2-0ubuntu2 gnome-keyring=2.92.92.is.2.32.1-0ubuntu2 libgnome-keyring0=2.*
sudo apt-get install ubuntu-desktop
sudo apt-get remove libgtk-3-0
sudo apt-get autoremove


```

Good luck!

---

### Post by chrisjbrough on 2011-07-24
> **sinelaw said:**
> I was about to kill myself too. But I managed to do it.
```

sudo apt-get install gnome-session=2.32.1-0ubuntu20 gnome-session-bin=2.32.1-0ubuntu20 gnome-session-common=2.32.1-0ubuntu20  gdm=2.32.1-0ubuntu3 gnome-session-common=2.32.1-0ubuntu20 gnome-settings-daemon=2.32.1-0ubuntu13.1 eog=2.32.1-0ubuntu2 gnome-screensaver=2.30.2-0ubuntu2 gnome-menus=2.30.5-0ubuntu3 python-gmenu=2.30.5-0ubuntu3 nautilus=1:2.32.2.1-0ubuntu13 nautilus-data=1:2.32.2.1-0ubuntu13 libgnome-desktop-2-17 gnome-panel=1:2.32.1-0ubuntu6.5 libgnome-menu2 gnome-control-center=1:2.32.1-0ubuntu15


```

EDIT: Afterwards I discovered some things (like nautilus) were not working. So I did also:

```

sudo apt-get install gnome-nettool=2.32.0-0ubuntu1 gnome-terminal=2.32.1-0ubuntu3  gnome-system-log=2.32.0-0ubuntu5 gnome-utils-common=2.32.0-0ubuntu5  gnome-terminal-data=2.32.1-0ubuntu3 libnautilus-extension1=1:2.32.2.1-0ubuntu13
 sudo apt-get remove aisleriot apturl banshee banshee-extension-soundmenu banshee-extension-ubuntuonemusicstore brasero desktopcouch empathy  eog evince evolution-data-server gcalctool gconf-editor gdebi gedit gir1.2-gnomebluetooth-1.0 gir1.2-gtk-3.0  gir1.2-peas-1.0 gir1.2-rb-0.13 gir1.2-totem-1.0 gir1.2-webkit-3.0 gnome-accessibility-themes gnome-applets  gnome-codec-install gnome-control-center gnome-disk-utility gnome-games-common gnome-icon-theme gnome-icon-theme-symbolic  gnome-keyring gnome-mahjongg gnome-media gnome-panel gnome-power-manager gnome-screensaver gnome-sudoku  gnome-system-monitor gnome-system-tools gnome-themes-selected gnome-themes-ubuntu gnomine gtk3-engines gucharmap  human-theme humanity-icon-theme ibus-gtk indicator-applet indicator-applet-appmenu indicator-applet-complete  indicator-applet-session indicator-datetime libappindicator3-1 libavahi-ui-gtk3-0 libcanberra-gtk3-0  libcanberra-gtk3-module libclutter-gtk-1.0-0 libcryptui0a libdbusmenu-gtk3-3 libgail-3-0 libgcr-3-0 libgdu-gtk0  libgnome-control-center1 libgnome-media-profiles-3.0-0 libgtk-3-0 libgtk-3-bin libgtk-3-common libgtk-vnc-2.0-0  libgtkmm-3.0-1 libgtksourceview-3.0-0 libgucharmap-2-90-7 libgucharmap7 libgweather-3-0 libindicator3-3  liblaunchpad-integration-3.0-1 libmutter0 libpeas-1.0-0 libpolkit-gtk-1-0 librhythmbox-core4 libseed-gtk3-0  libsyncdaemon-1.0-1 libtotem0 libubuntuone-1.0-1 libubuntuone1.0-cil libunique-3.0-0 libvte-2.90-9 libwebkitgtk-3.0-0  libwnck-3-0 light-themes metacity mousetweaks mutter network-manager-gnome pitivi python-desktopcouch  python-desktopcouch-application python-ubuntuone python-ubuntuone-control-panel quadrapassel rhythmbox rhythmbox-plugins  rhythmbox-ubuntuone-music-store seahorse simple-scan software-center system-config-printer-gnome totem totem-mozilla  totem-plugins ubuntu-artwork ubuntu-desktop ubuntu-mono ubuntu-sso-client ubuntuone-client ubuntuone-client-gnome  ubuntuone-control-panel ubuntuone-control-panel-gtk unity unity-asset-pool vinagre vino zenity
sudo apt-get install aisleriot apturl banshee banshee-extension-soundmenu banshee-extension-ubuntuonemusicstore brasero desktopcouch empathy  eog evince evolution-data-server gcalctool gconf-editor gdebi gedit   gir1.2-peas-1.0  gir1.2-webkit-3.0 gnome-accessibility-themes gnome-applets  gnome-codec-install gnome-control-center gnome-disk-utility gnome-games-common gnome-icon-theme   gnome-keyring gnome-mahjongg gnome-media gnome-panel gnome-power-manager gnome-screensaver gnome-sudoku  gnome-system-monitor gnome-system-tools gnome-themes-selected gnome-themes-ubuntu gnomine  gucharmap  human-theme humanity-icon-theme ibus-gtk indicator-applet indicator-applet-appmenu indicator-applet-complete  indicator-applet-session indicator-datetime   libclutter-gtk-1.0-0  libgail-3-0  libgdu-gtk0    libpeas-1.0-0 libpolkit-gtk-1-0  libsyncdaemon-1.0-1  libubuntuone-1.0-1 libubuntuone1.0-cil  libvte-2.90-9  light-themes metacity mousetweaks mutter network-manager-gnome pitivi python-desktopcouch  python-desktopcouch-application python-ubuntuone python-ubuntuone-control-panel quadrapassel rhythmbox rhythmbox-plugins  rhythmbox-ubuntuone-music-store seahorse simple-scan software-center system-config-printer-gnome totem totem-mozilla  totem-plugins ubuntu-artwork ubuntu-desktop ubuntu-mono ubuntu-sso-client ubuntuone-client ubuntuone-client-gnome  ubuntuone-control-panel ubuntuone-control-panel-gtk unity unity-asset-pool vinagre vino zenity gstreamer0.10-plugins-good libgstfarsight0.10-0 libtelepathy-farsight0 libedata-cal1.2-10  evolution-data-server-common=2.32.2-0ubuntu2 gnome-keyring=2.92.92.is.2.32.1-0ubuntu2 libgnome-keyring0=2.*
sudo apt-get install ubuntu-desktop
sudo apt-get remove libgtk-3-0
sudo apt-get autoremove


```

Good luck!

I tried the above. didnt work for me :( i tried booting in recovery mode > terminal w/ networking > typed in said code > no go :(

so i thought i'd have to reinstall ubuntu 11.04 with a fresh start. i was partially wrong and had a very pleasent surprise when i found out the installer for 11.04 can "upgrade 11.04 to 11.04" while keeping programs and documents in tact.

this gives me hope :)

hope it does for you too!

~Chris

---

### Post by sadaruwan12 on 2011-07-24
I did same thing and got my system scrambled use these and see if these work.

```
sudo apt-get remove libgtk-3-common
sudo apt-get install ppa-purge
sudo ppa-purge ppa:gnome3-team/gnome3
sudo apt-get install gnome-panel
```

And after removing GNOME3 and when you boot back into the system and you don't find you GUI then run the below commands.

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install ubuntu-desktop
```

Hope this helps.

If you wish to go back to unity then take a look at this [link]("http://www.fossapps.com/how-to-uninstall-gnome-3-and-reinstall-unity-in-ubuntu-11-04-2/")

---

