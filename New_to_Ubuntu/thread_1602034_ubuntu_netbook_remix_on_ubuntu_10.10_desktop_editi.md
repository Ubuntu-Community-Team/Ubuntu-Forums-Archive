---
title: "ubuntu netbook remix on ubuntu 10.10 desktop edition?"
date: 2010-10-20
forum: New to Ubuntu
---

### Post by ornothaloapq on 2010-10-20
on version 10.04 there was a thing i could download from the synaptic package manager that let me boot into the ubuntu desktop version or the netbook version. does that still exist on 10.10 and if so, what is it called?

---

### Post by bigsmitty64 on 2010-10-20
With 10.10, I went into synaptic, i searched "ubuntu-netbook"  and marked for installation, and appllied, log out and back in, and your good to go. You will have the options you mentioned. I hope this is what you were looking for!

---

### Post by ornothaloapq on 2010-10-21
i just installed the selected packages but when i go into netbook mode, parts of the screen show up slanted. most of the screen looks fine but if i click on the shutdown, restart menu or try to switch workspaces with keyboard commands it shows up in a slanted menu. also "docky" shows up completely slanted

---

### Post by sikander3786 on 2010-10-21
> **ornothaloapq said:**
> i just installed the selected packages but when i go into netbook mode, parts of the screen show up slanted. most of the screen looks fine but if i click on the shutdown, restart menu or try to switch workspaces with keyboard commands it shows up in a slanted menu. also "docky" shows up completely slanted
I think the new netbook is 3d. You will need to enable the proprietary graphics drivers, if any. You can install them from the default Gnome session.

---

### Post by ornothaloapq on 2010-10-21
i have a the driver already installed. ive installed and uninstalled the netbook packages a few times now and it hasnt fixed it.

---

### Post by Escape311 on 2010-11-28
I'm having these exact issues. Not even running netbook. ATI Radeon graphics. Once it installs the drivers and I reboot, all of my menus are slanted.

---

### Post by spencerlewis520 on 2010-12-22
I'm having the slanted issue myself, and when opening any type of display property manager the screen flashes and everything moves downward. but as signing into the Ubuntu forums the problem mysteriously vanished... it seemed to start after installing the ati graphics drivers.... interesting. i assume after a restart the problem will persist. i will report back here with results :]

---

### Post by spencerlewis520 on 2010-12-22
after reboot the problem has returned
sorry for double post.

---

### Post by garvinrick4 on 2010-12-22
10.10 and up is the unity interface:
```
sudo apt-get install ubuntu-netbook
``````
sudo apt-get install unity
``````
rick@rick-laptop:~$ aptitude show ubuntu-netbook
Package: ubuntu-netbook                  
State: installed
Automatically installed: no
Version: 2.035
Priority: optional
Section: metapackages
Maintainer: Ubuntu Desktop Developers <ubuntu-desktop@lists.ubuntu.com>
Uncompressed Size: 61.4k
Depends: alacarte, alsa-base, alsa-utils, anacron, bc, ca-certificates,
         checkbox-gtk, consolekit, cups, cups-bsd, cups-client,
         cups-driver-gutenprint, dc, desktop-file-utils, doc-base, eog, evince,
         file-roller, foomatic-db-compressed-ppds, foomatic-filters, gcalctool,
         gconf-editor, gdm, gedit, genisoimage, ghostscript-x, gnome-about,
         gnome-applets, gnome-control-center, gnome-media, gnome-menus,
         gnome-nettool, gnome-panel, gnome-power-manager, gnome-session,
         gnome-session-canberra, gnome-system-monitor, gnome-system-tools,
         gnome-terminal, gnome-themes-selected, gnome-themes-ubuntu,
         gnome-utils, gstreamer0.10-alsa, gstreamer0.10-plugins-base-apps,
         gstreamer0.10-pulseaudio, gtk2-engines, gtk2-engines-pixbuf, gucharmap,
         humanity-icon-theme, indicator-applet-session, inputattach,
         language-selector, launchpad-integration, lftp, libgd2-xpm,
         libgnome2-perl, libpam-ck-connector, libsasl2-modules, libxp6,
         nautilus, nautilus-sendto, notify-osd, openprinting-ppds,
         plymouth-theme-ubuntu-logo, pnm2ppa, pulseaudio,
         pulseaudio-esound-compat, rarian-compat, screen,
         screensaver-default-images, seahorse, smbclient, software-center,
         software-properties-gtk, ssh-askpass-gnome, synaptic,
         system-config-printer-gnome, ttf-dejavu-core, ttf-freefont,
         ubuntu-artwork, ubuntu-extras-keyring, ubuntu-netbook-default-settings,
         ubuntu-sounds, unity, unzip, update-manager, update-notifier,
         wireless-tools, wpasupplicant, x-ttcidfont-conf, xdg-user-dirs,
         xdg-user-dirs-gtk, xkb-data, xorg, xscreensaver-data, xterm, yelp,
         zenity, zip
Recommends: acpi-support, aisleriot, app-install-data-partner, apport-gtk,
            avahi-autoipd, avahi-daemon, bluez, bluez-alsa, bluez-cups,
            bluez-gstreamer, branding-ubuntu, brltty, brltty-x11, cheese,
            computer-janitor-gtk, empathy, espeak, evolution,
            evolution-exchange, evolution-indicator, evolution-plugins,
            evolution-webcal, example-content, firefox, firefox-gnome-support,
            foo2zjs, gdm-guest-session, gnome-accessibility-themes,
            gnome-bluetooth, gnome-codec-install, gnome-disk-utility, gnome-mag,
            gnome-mahjongg, gnome-orca, gnome-screensaver, gnome-sudoku,
            gnome-user-guide, gvfs-fuse, gwibber, hplip, ibus, ibus-gtk,
            ibus-pinyin, ibus-pinyin-db-android, ibus-table, im-switch,
            indicator-appmenu, indicator-datetime, indicator-messages,
            jockey-gtk, kerneloops-daemon, laptop-detect, libnss-mdns,
            libpam-gnome-keyring, libunity-misc0, linux-headers-generic,
            min12xxw, mousetweaks, nautilus-share, network-manager-gnome,
            onboard, openoffice.org-calc, openoffice.org-gnome,
            openoffice.org-help-en-us, openoffice.org-impress,
            openoffice.org-style-human, openoffice.org-writer, pcmciautils,
            policykit-desktop-privileges, pulseaudio-module-bluetooth,
            pulseaudio-module-gconf, pulseaudio-module-x11, pxljr, quadrapassel,
            rhythmbox, rhythmbox-ubuntuone-music-store, shotwell, simple-scan,
            speech-dispatcher, splix, telepathy-idle, tomboy, totem,
            totem-mozilla, transmission-gtk, ttf-indic-fonts-core,
            ttf-kacst-one, ttf-khmeros-core, ttf-lao, ttf-liberation,
            ttf-punjabi-fonts, ttf-takao-pgothic, ttf-thai-tlwg,
            ttf-ubuntu-font-family, ttf-unfonts-core, ttf-wqy-microhei, ubufox,
            ubuntu-docs, ubuntuone-client-gnome, usb-creator-gtk,
            xcursor-themes, xdg-utils
Description: The Ubuntu Netbook system
 This package depends on all of the packages in the Ubuntu Netbook system 
 
 It is also used to help ensure proper upgrades, so it is recommended that it
 not be removed.

rick@rick-laptop:~$ 

```
```
rick@rick-laptop:~$ aptitude show unity
Package: unity                           
State: installed
Automatically installed: no
Version: 0.2.46-0ubuntu5
Priority: optional
Section: gnome
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 594k
Depends: libart-2.0-2 (>= 2.3.18), libatk1.0-0 (>= 1.29.3), libbamf0 (>=
         0.2.20), libbonobo2-0 (>= 2.15.0), libbonoboui2-0 (>= 2.15.1), libc6
         (>= 2.2.5), libcairo2 (>= 1.2.4), libclutk-0.3-0 (>= 0.3.6),
         libclutter-1.0-0 (>= 1.2.12-0ubuntu3) | libclutter-eglx-es20-1.0-0 (>=
         1.2.12-0ubuntu3) | libclutter-eglx-es11-1.0-0 (>= 1.2.12-0ubuntu3),
         libclutter-gtk-0.10-0 (>= 0.10.2), libdbus-1-3 (>= 1.0.2),
         libdbus-glib-1-2 (>= 0.78), libdbusmenu-glib1 (>= 0.3.12), libdee-1.0-0
         (>= 0.1.0), libfontconfig1 (>= 2.8.0), libfreetype6 (>= 2.2.1),
         libgconf2-4 (>= 2.31.1), libgdk-pixbuf2.0-0 (>= 2.21.6), libgee2 (>=
         0.5.2), libglib2.0-0 (>= 2.22.2-0ubuntu1wncksync3),
         libgnome-desktop-2-17 (>= 1:2.29.92), libgnome2-0 (>= 2.17.3),
         libgnomecanvas2-0 (>= 2.11.1), libgnomeui-0 (>= 2.22.0), libgnomevfs2-0
         (>= 1:2.17.90), libgtk2.0-0 (>= 2.18.0), libice6 (>= 1:1.0.0),
         libindicator1, libjson-glib-1.0-0, liborbit2 (>= 1:2.14.10),
         libpango1.0-0 (>= 1.14.0), libpng12-0 (>= 1.2.13-4), libpopt0 (>=
         1.16), libsm6, libstartup-notification0 (>= 0.10), libunique-1.0-0 (>=
         1.0.0), libunity-misc0 (>= 0.1.0), libunity0 (>= 0.2.30),
         libutouch-grail1 (>= 1.0.4), libwnck22 (>= 1:2.22), libx11-6,
         libxcb-atom1 (>= 0.3.6), libxcb-event1 (>= 0.3.6), libxcb-icccm1 (>=
         0.3.6), libxcb-property1 (>= 0.3.6), libxcb1, gconf2 (>= 2.28.1-2),
         mutter (>= 2.31.5), unity-asset-pool (>= 0.8.18)
Recommends: unity-place-applications, unity-place-files, indicator-appmenu,
            indicator-application, indicator-sound, indicator-datetime,
            indicator-messages, indicator-me, indicator-session,
            ubuntu-netbook-default-settings
Conflicts: netbook-launcher (< 1:2.1.18-0ubuntu2)
Replaces: netbook-launcher (< 1:2.1.18-0ubuntu2)
Provides: indicator-renderer, netbook-launcher
Description: Unity Interface for Ubuntu Netbook Edition
 Unity is a graphical interface designed for Ubuntu Netbook Edition
Homepage: https://launchpad.net/unity

  
```
## Can go from Desktop to Unity at login screen on bottom after clicking on login.

# If you install the netbook edition from get-go you get both the netbook edition and the desktop edition:
# If you install the desktop edition from get-go you get only the desktop and must install ubuntu-desktop and unity.

---

### Post by sikander3786 on 2010-12-23
In addition to what *garvinrick4* said, please post the output of these commands.

```
cat /etc/X11/xorg.conf
```

Note, capital 'X' for X11.

```
glxinfo | grep vendor
```

---

### Post by spencerlewis520 on 2010-12-23
alright here all my outputs. right away i don't see anything outstanding but maybe a more trained eye will. :) 

Ubuntu-Netbook
 ```
spencer@ubuntu:~$ aptitude show ubuntu-netbook
Package: ubuntu-netbook           
State: installed
Automatically installed: no
Version: 2.035
Priority: optional
Section: metapackages
Maintainer: Ubuntu Desktop Developers <ubuntu-desktop@lists.ubuntu.com>
Uncompressed Size: 61.4k
Depends: alacarte, alsa-base, alsa-utils, anacron, bc, ca-certificates,
         checkbox-gtk, consolekit, cups, cups-bsd, cups-client,
         cups-driver-gutenprint, dc, desktop-file-utils, doc-base, eog, evince,
         file-roller, foomatic-db-compressed-ppds, foomatic-filters, gcalctool,
         gconf-editor, gdm, gedit, genisoimage, ghostscript-x, gnome-about,
         gnome-applets, gnome-control-center, gnome-media, gnome-menus,
         gnome-nettool, gnome-panel, gnome-power-manager, gnome-session,
         gnome-session-canberra, gnome-system-monitor, gnome-system-tools,
         gnome-terminal, gnome-themes-selected, gnome-themes-ubuntu,
         gnome-utils, gstreamer0.10-alsa, gstreamer0.10-plugins-base-apps,
         gstreamer0.10-pulseaudio, gtk2-engines, gtk2-engines-pixbuf, gucharmap,
         humanity-icon-theme, indicator-applet-session, inputattach,
         language-selector, launchpad-integration, lftp, libgd2-xpm,
         libgnome2-perl, libpam-ck-connector, libsasl2-modules, libxp6,
         nautilus, nautilus-sendto, notify-osd, openprinting-ppds,
         plymouth-theme-ubuntu-logo, pnm2ppa, pulseaudio,
         pulseaudio-esound-compat, rarian-compat, screen,
         screensaver-default-images, seahorse, smbclient, software-center,
         software-properties-gtk, ssh-askpass-gnome, synaptic,
         system-config-printer-gnome, ttf-dejavu-core, ttf-freefont,
         ubuntu-artwork, ubuntu-extras-keyring, ubuntu-netbook-default-settings,
         ubuntu-sounds, unity, unzip, update-manager, update-notifier,
         wireless-tools, wpasupplicant, x-ttcidfont-conf, xdg-user-dirs,
         xdg-user-dirs-gtk, xkb-data, xorg, xscreensaver-data, xterm, yelp,
         zenity, zip
Recommends: acpi-support, aisleriot, app-install-data-partner, apport-gtk,
            avahi-autoipd, avahi-daemon, bluez, bluez-alsa, bluez-cups,
            bluez-gstreamer, branding-ubuntu, brltty, brltty-x11, cheese,
            computer-janitor-gtk, empathy, espeak, evolution,
            evolution-exchange, evolution-indicator, evolution-plugins,
            evolution-webcal, example-content, firefox, firefox-gnome-support,
            foo2zjs, gdm-guest-session, gnome-accessibility-themes,
            gnome-bluetooth, gnome-codec-install, gnome-disk-utility, gnome-mag,
            gnome-mahjongg, gnome-orca, gnome-screensaver, gnome-sudoku,
            gnome-user-guide, gvfs-fuse, gwibber, hplip, ibus, ibus-gtk,
            ibus-pinyin, ibus-pinyin-db-android, ibus-table, im-switch,
            indicator-appmenu, indicator-datetime, indicator-messages,
            jockey-gtk, kerneloops-daemon, laptop-detect, libnss-mdns,
            libpam-gnome-keyring, libunity-misc0, linux-headers-generic,
            min12xxw, mousetweaks, nautilus-share, network-manager-gnome,
            onboard, openoffice.org-calc, openoffice.org-gnome,
            openoffice.org-help-en-us, openoffice.org-impress,
            openoffice.org-style-human, openoffice.org-writer, pcmciautils,
            policykit-desktop-privileges, pulseaudio-module-bluetooth,
            pulseaudio-module-gconf, pulseaudio-module-x11, pxljr, quadrapassel,
            rhythmbox, rhythmbox-ubuntuone-music-store, shotwell, simple-scan,
            speech-dispatcher, splix, telepathy-idle, tomboy, totem,
            totem-mozilla, transmission-gtk, ttf-indic-fonts-core,
            ttf-kacst-one, ttf-khmeros-core, ttf-lao, ttf-liberation,
            ttf-punjabi-fonts, ttf-takao-pgothic, ttf-thai-tlwg,
            ttf-ubuntu-font-family, ttf-unfonts-core, ttf-wqy-microhei, ubufox,
            ubuntu-docs, ubuntuone-client-gnome, usb-creator-gtk,
            xcursor-themes, xdg-utils
Description: The Ubuntu Netbook system
 This package depends on all of the packages in the Ubuntu Netbook system 
 
 It is also used to help ensure proper upgrades, so it is recommended that it
 not be removed.

```

Unity
```
spencer@ubuntu:~$ aptitude show unity
Package: unity                    
State: installed
Automatically installed: no
Version: 0.2.46-0ubuntu5
Priority: optional
Section: gnome
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 496k
Depends: libart-2.0-2 (>= 2.3.18), libatk1.0-0 (>= 1.29.3), libbamf0 (>=
         0.2.20), libbonobo2-0 (>= 2.15.0), libbonoboui2-0 (>= 2.15.1), libc6
         (>= 2.3.6-6~), libcairo2 (>= 1.2.4), libclutk-0.3-0 (>= 0.3.6),
         libclutter-1.0-0 (>= 1.2.12-0ubuntu3) | libclutter-eglx-es20-1.0-0 (>=
         1.2.12-0ubuntu3) | libclutter-eglx-es11-1.0-0 (>= 1.2.12-0ubuntu3),
         libclutter-gtk-0.10-0 (>= 0.10.2), libdbus-1-3 (>= 1.0.2),
         libdbus-glib-1-2 (>= 0.78), libdbusmenu-glib1 (>= 0.3.12), libdee-1.0-0
         (>= 0.1.0), libfontconfig1 (>= 2.8.0), libfreetype6 (>= 2.2.1),
         libgconf2-4 (>= 2.31.1), libgdk-pixbuf2.0-0 (>= 2.21.6), libgee2 (>=
         0.5.2), libglib2.0-0 (>= 2.22.2-0ubuntu1wncksync3),
         libgnome-desktop-2-17 (>= 1:2.29.92), libgnome2-0 (>= 2.17.3),
         libgnomecanvas2-0 (>= 2.11.1), libgnomeui-0 (>= 2.22.0), libgnomevfs2-0
         (>= 1:2.17.90), libgtk2.0-0 (>= 2.18.0), libice6 (>= 1:1.0.0),
         libindicator1, libjson-glib-1.0-0, liborbit2 (>= 1:2.14.10),
         libpango1.0-0 (>= 1.14.0), libpng12-0 (>= 1.2.13-4), libpopt0 (>=
         1.16), libsm6, libstartup-notification0 (>= 0.10), libunique-1.0-0 (>=
         1.0.0), libunity-misc0 (>= 0.1.0), libunity0 (>= 0.2.30),
         libutouch-grail1 (>= 1.0.4), libwnck22 (>= 1:2.22), libx11-6,
         libxcb-atom1 (>= 0.3.6), libxcb-event1 (>= 0.3.6), libxcb-icccm1 (>=
         0.3.6), libxcb-property1 (>= 0.3.6), libxcb1, gconf2 (>= 2.28.1-2),
         mutter (>= 2.31.5), unity-asset-pool (>= 0.8.18)
Recommends: unity-place-applications, unity-place-files, indicator-appmenu,
            indicator-application, indicator-sound, indicator-datetime,
            indicator-messages, indicator-me, indicator-session,
            ubuntu-netbook-default-settings
Conflicts: netbook-launcher (< 1:2.1.18-0ubuntu2)
Replaces: netbook-launcher (< 1:2.1.18-0ubuntu2)
Provides: indicator-renderer, netbook-launcher
Description: Unity Interface for Ubuntu Netbook Edition
 Unity is a graphical interface designed for Ubuntu Netbook Edition
Homepage: https://launchpad.net/unity

```

Now this Xorg.conf is when i have the ATI driver turned OFF, where the computer will actually function.
(one note, i normally wouldn't have a Xorg.conf file unless i had created one to get my trackpad to work. could this be a cause of the graphics??[Doubt it])
```
spencer@ubuntu:~$ cat /etc/X11/xorg.conf
Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizScrollDelta" "0"
Option "ShmConfig" "true"
EndSection

```


and here is after installing the Proprietary drivers. things are now buggy. 
```

spencer@ubuntu:~$ cat /etc/X11/xorg.conf

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "InputDevice"
	Identifier "Synaptics Touchpad"
	Driver "synaptics"
	Option "SendCoreEvents" "true"
	Option "Device" "/dev/psaux"
	Option "Protocol" "auto-dev"
	Option "HorizScrollDelta" "0"
	Option "ShmConfig" "true"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"fglrx"
EndSection


```

server glx vendor string 
without "ATI/AMD proprietary FGLRX graphics driver" installed
```
spencer@ubuntu:~$ glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: Mesa Project and SGI
OpenGL vendor string: Advanced Micro Devices, Inc.

```

with the above drivers installed.
```
spencer@ubuntu:~$ glxinfo | grep vendor
server glx vendor string: ATI
client glx vendor string: ATI
OpenGL vendor string: ATI Technologies Inc.
```

If there is anything else that you need me to output i'd be glad to do it! i really want this bug fixed!! :)

---

### Post by garvinrick4 on 2010-12-23
Looks like a Video card driver issue. I will bump it for you. See if someone can chime
in that can help. Should have driver issue in Title so a video driver guy will see or
sikander 3786 is still around to look at code he wanted you to run.

---

### Post by sikander3786 on 2010-12-23
Try reconfiguring your graphics. Modern X deals directly with the graphics stuff so it really doesn't need an xorg.conf. Press Ctrl + Alt + F1 and login to the tty1.

```
sudo service gdm stop
```

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Reboot!

```
sudo shutdown -r now
```

Let us know if there is any improvement ;-)

---

### Post by spencerlewis520 on 2010-12-24
yeah getting people more tuned into the video card scene might help lol 
i love how supportive this community is!(it actually makes troubleshooting enjoyable) :D thank you!!!!

ill try reconfiguring and post back in a bit!



isnt changing my Xorg.conf to Xorg.conf.old going to fubar my trackpad aswell?? im gonna have to pick my poison huh... atleast temporaraly! but its all in the name of getting this working for others! :D

---

### Post by spencerlewis520 on 2010-12-24
so when doing the sudo service gdm stop the screen flashes uncontrollably and is quite unfavorable. lol
after doing the rest of the steps after a reboot and using the tty1 things are still the same, but i now have a funky trackpad! :P

---

### Post by sikander3786 on 2010-12-24
OK. Restore your original xorg.conf.

```
sudo mv /etc/X11/xorg.conf.old /etc/X11/xorg.conf
```

That should bring your trackpad back into shape.

And, as suggested earlier, start a new thread with a graphics or such title.

Good Luck!

---

