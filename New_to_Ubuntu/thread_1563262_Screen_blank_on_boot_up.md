---
title: "Screen blank on boot up"
date: 2010-08-28
forum: New to Ubuntu
---

### Post by PierreRobiquet on 2010-08-28
Hello,

I've been using Ubuntu for some time now and everything is working excellently, although not a huge problem I've noticed that on boot up the Ubuntu Plymouth purple screen no longer displays and instead just shows a black screen however apart from this the system boots perfectly. Is there an easy way to get this back?

Thanks for your help,

---

### Post by Rubi1200 on 2010-08-29
What graphics card do you have installed?

---

### Post by diablo75 on 2010-08-29
I'm gonna jump in here and see what happens.  I have the same problem, and I know it's related to me having an nVidia card (instead of an ATI).  I'm half inclined to hack a config file to get things reverted back to the way they were before 10.04, but also half inclined to just wait it out until better support rolls out.

---

### Post by Silent Warrior on 2010-08-29
Awaiting information on what card(s) is/are involved, I'll chime in with the possibility to add nomodeset to the kernel boot-up command in Grub. (If you don't want to write it into any configuration file right away, you can enter it after pressing 'e' (I think) after selecting your kernel in Grub. Just append 'nomodeset' at the end, and go for broke.)

---

### Post by 1991sudarshan on 2010-08-29
> **ConcreteDonkey said:**
> Hello,

I've been using Ubuntu for some time now and everything is working excellently, although not a huge problem I've noticed that on boot up the Ubuntu Plymouth purple screen no longer displays and instead just shows a black screen however apart from this the system boots perfectly. Is there an easy way to get this back?

Thanks for your help,

Did you make any changes in the contents of the files in the root folder???

---

### Post by PierreRobiquet on 2010-08-29
I'm just using my Samsung NC10 so it's a Intel GMA 950, I haven't installed any restricted drivers or edited anything apart from /etc/fstab

---

### Post by Rubi1200 on 2010-08-29
The next time you boot the computer hold Shift to bring up the GRUB menu. Highlight the entry you want and then "e" to edit.

Find the line that ends like this ```
ro quiet splash
``` and remove quiet splash.

Then "Ctrl" + "x" to boot.

If there are any error messages of significance, you should see them here.

Also check the logs with ```
dmesg | less
``` to see if anything shows there.

---

### Post by PierreRobiquet on 2010-08-29
Thanks for your help everyone,

Just to add further information, the purple Ubuntu screen displays perfectly upon shutdown with no issue although I'm still having the issue of it not displaying at boot.

When removing the quiet splash I cannot see any obvious error messages, and when running dmesg I cannot see any errors that stand out to me apart from it telling me I should update my BIOS. I've included the log in case there is something I've missed (sorry for zipping it, but the plain text file was over the limit).

---

### Post by varunendra on 2010-08-29
Have you tried uninstalling and then reinstalling plymouth via synaptic? If it is a problem due to improper dependencies, it may get fixed by this.

---

### Post by PierreRobiquet on 2010-08-29
> **varunendra said:**
> Have you tried uninstalling and then reinstalling plymouth via synaptic? If it is a problem due to improper dependencies, it may get fixed by this.

After reinstalling it the problem still remains and when attempting to run sudo apt-get remove plymouth I get this lovely horrifying message:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libopenal1 libatk1.0-dev debhelper libbabl-0.0-0 linux-headers-2.6.32-21
  libxcb-keysyms1 intltool-debian x11proto-kb-dev libglib2.0-dev
  libnet-ssleay-perl x11proto-xinerama-dev librsvg2-2.18-cil libgfortran3
  libmono-zeroconf1.0-cil libqt4-dbus x11proto-render-dev libgdata1.4-cil
  libnotify-bin po-debconf xbindkeys podsleuth libxdmcp-dev libsysfs-dev
  libdirectfb-extra libparted0 pidgin-data libpng12-dev libdvbpsi5 grub-pc
  libboo2.0.9-cil libfontconfig1-dev libmail-sendmail-perl guile-1.6-libs
  libvlc2 x11proto-core-dev gettext python-numpy
  linux-headers-2.6.32-21-generic winetricks vlc-nox cvs libqtcore4
  x11proto-randr-dev libtaglib2.0-cil libupnp3 libdbus-1-dev giblib1
  libwxbase2.8-0 libjpeg62-dev libqthreads-12 zlib1g-dev x11proto-input-dev
  streamer libfreetype6-dev libpthread-stubs0-dev ttf-symbol-replacement
  os-prober libdbus-glib-1-dev libiso9660-7 libpthread-stubs0 libqt4-xml
  wine1.2-gecko libblas3gf xawtv-plugins libqt4-network libgimp2.0
  liblapack3gf libexpat1-dev liblua5.1-0 libmpg123-0 filezilla-common
  html2text vlc-data libpixman-1-dev libtar winbind grub-common scrot
  libimlib2 gimp-data libvlccore2 libvcdinfo0 libguile-ltdl-1 libebml0
  python-keybinder libsys-hostname-long-perl libmatroska0 libmng1
  libnotify0.4-cil libnet-libidn-perl
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  acpi-support acpid adobe-flashplugin aisleriot alsa-base alsa-utils anacron
  apparmor apparmor-utils apport apport-gtk aptdaemon apturl at at-spi
  avahi-daemon avahi-utils banshee bluez bluez-cups brltty brltty-x11
  capplets-data checkbox checkbox-gtk compiz compiz-core
  compiz-fusion-plugins-main compiz-gnome compiz-plugins
  compizconfig-backend-gconf computer-janitor-gtk computertemp console-setup
  consolekit couchdb-bin cron cups cups-driver-gutenprint dbus dbus-x11
  desktopcouch dkms dmsetup dockbarx dockbarx-themes-extra e2fsprogs
  easy-slow-down-manager empathy-common eog erlang-base erlang-crypto
  erlang-inets erlang-mnesia erlang-public-key erlang-runtime-tools erlang-ssl
  erlang-syntax-tools erlang-xmerl evince evolution-data-server
  evolution-webcal file-roller filezilla firefox firefox-branding
  firefox-gnome-support foo2zjs foomatic-db foomatic-db-engine
  friendly-recovery ftp gbrainy gcalctool gconf-defaults-service gconf-editor
  gconf2 gconf2-common gdebi gdm gdm-guest-session gedit ghostscript-cups
  ghostscript-x gimp gksu gnome-about gnome-applets gnome-applets-data
  gnome-bluetooth gnome-codec-install gnome-control-center gnome-disk-utility
  gnome-exe-thumbnailer gnome-games-common gnome-keyring gnome-mag
  gnome-mahjongg gnome-media gnome-media-common gnome-nettool gnome-orca
  gnome-panel gnome-panel-data gnome-power-manager gnome-screensaver
  gnome-session gnome-session-bin gnome-session-canberra gnome-settings-daemon
  gnome-sudoku gnome-system-monitor gnome-system-tools gnome-terminal
  gnome-terminal-data gnome-user-guide gnome-user-share gnome-utils gnomine
  gsfonts-x11 gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-good
  gstreamer0.10-pulseaudio gucharmap gvfs gvfs-backends gvfs-bin gvfs-fuse hal
  hostname hplip ibus ibus-m17n ibus-table icoutils ifupdown imagemagick
  indicator-applet indicator-applet-session indicator-me indicator-session
  indicator-sound initramfs-tools initscripts irqbalance jockey-common
  jockey-gtk kbd language-selector lftp libasound2-plugins libatspi1.0-0
  libaudio2 libbonoboui2-0 libcairo2-dev libcamel1.2-14 libcanberra-pulse
  libcompizconfig0 libcouchdb-glib-1.0-2 libcryptui0
  libdesktopcouch-glib-1.0-2 libdirectfb-dev libebackend1.2-0 libebook1.2-9
  libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-11
  libedataserverui1.2-8 libegroupwise1.2-13 libexchange-storage1.2-3
  libgail-gnome-module libgconf2-4 libgconf2.0-cil libgdata6 libgdu0
  libgegl-0.0-0 libgksu2-0 libgnome-desktop-2-17 libgnome-media0
  libgnome-pilot2 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2-0
  libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnome2.24-cil
  libgnomedesktop2.20-cil libgnomekbd-common libgnomekbd4
  libgnomepanel2.24-cil libgnomeui-0 libgnomevfs2-0 libgnomevfs2-common
  libgnomevfs2-extra libgstfarsight0.10-0 libgtk2.0-dev libgtkhtml-editor0
  libgtkhtml3.14-19 libgweather-common libgweather1 libice-dev libice6
  libio-socket-ssl-perl liblpint-bonobo0 libm17n-0 libmagickcore2
  libmagickcore2-extra libmagickwand2 libmetacity-private0 libmjpegtools-1.9
  libnet-dbus-perl libnss-mdns liboobs-1-4 libpanel-applet2-0 libpango1.0-dev
  libpolkit-gtk-1-0 libpulse-browse0 libpulse-mainloop-glib0 libpulse0
  libpurple-dev libpurple0 libqtgui4 librpc-xml-perl libsdl-image1.2
  libsdl1.2debian libsdl1.2debian-pulseaudio libsm-dev libsm6
  libsoup-gnome2.4-1 libstartup-notification0 libtelepathy-farsight0
  libwebkit-1.0-2 libwebkit1.1-cil libwnck2.20-cil libwnck22 libwww-perl
  libwxgtk2.8-0 libx11-dev libxau-dev libxaw7 libxcb-render-util0-dev
  libxcb-render0-dev libxcb1-dev libxcomposite-dev libxcursor-dev
  libxdamage-dev libxext-dev libxfixes-dev libxft-dev libxi-dev
  libxinerama-dev libxklavier16 libxml-parser-perl libxml-sax-expat-perl
  libxml-twig-perl libxml-xpath-perl libxmu6 libxrandr-dev libxrender-dev
  libxres1 libxss1 libxt6 libxtst6 libxvmc1 libxxf86dga1 light-themes
  linux-generic linux-image-2.6.32-24-generic linux-image-generic
  linux-sound-base logrotate m17n-contrib m17n-db media-player-info metacity
  metacity-common module-init-tools mountall mousetweaks nautilus
  nautilus-data nautilus-sendto nautilus-sendto-empathy nautilus-share netbase
  network-manager network-manager-gnome network-manager-pptp
  network-manager-pptp-gnome notify-osd ntfs-3g ntfs-config ntpdate
  obex-data-server onboard openoffice.org-base-core openoffice.org-calc
  openoffice.org-core openoffice.org-draw openoffice.org-emailmerge
  openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us
  openoffice.org-impress openoffice.org-math openoffice.org-writer
  openprinting-ppds opera pcmciautils pidgin pidgin-dev pidgin-libnotify
  pidgin-ppa plymouth plymouth-label plymouth-theme-ubuntu-logo
  plymouth-theme-ubuntu-text plymouth-x11 pm-utils pm-utils-powersave-policy
  policykit-1 policykit-1-gnome powermgmt-base ppp pppconfig pppoeconf
  pptp-linux prey procps pulseaudio pulseaudio-esound-compat
  pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-x11
  pulseaudio-utils pxljr python-aptdaemon python-aptdaemon-gtk
  python-desktopcouch python-desktopcouch-records python-evolution
  python-farsight python-gconf python-gnome2 python-gnome2-desktop
  python-gnomeapplet python-gnomedesktop python-mediaprofiles python-metacity
  python-papyon python-pyatspi python-speechd python-uno python-virtkey
  python-webkit python-wnck quadrapassel rsyslog samsung-tools
  screen-resolution-extra screensaver-default-images seahorse simple-scan
  skype software-center software-properties-gtk speech-dispatcher splix
  system-config-printer-gnome system-tools-backends telepathy-butterfly
  telepathy-haze telepathy-salut telnet tomboy transmission-gtk tsclient
  ttf-mscorefonts-installer ubufox ubuntu-artwork ubuntu-desktop ubuntu-docs
  ubuntu-minimal ubuntu-standard ubuntu-system-service ubuntu-tweak
  ubuntu-wallpapers udev udisks ufw update-manager update-notifier upower
  upstart ureadahead usb-creator-common usb-creator-gtk util-linux vinagre
  vino vlc vlc-plugin-pulse wine wine1.2 wireless-crda x-ttcidfont-conf
  x11-apps x11-common x11-session-utils x11-utils x11-xfs-utils x11-xkb-utils
  x11-xserver-utils x11proto-composite-dev x11proto-damage-dev
  x11proto-fixes-dev x11proto-xext-dev xfonts-100dpi xfonts-75dpi xfonts-base
  xfonts-encodings xfonts-mathml xfonts-scalable xfonts-utils xinit xorg
  xscreensaver-data xscreensaver-gl xserver-common xserver-xorg
  xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-evdev
  xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-all
  xserver-xorg-video-apm xserver-xorg-video-ark xserver-xorg-video-ati
  xserver-xorg-video-chips xserver-xorg-video-cirrus xserver-xorg-video-fbdev
  xserver-xorg-video-geode xserver-xorg-video-i128 xserver-xorg-video-i740
  xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-nv
  xserver-xorg-video-openchrome xserver-xorg-video-r128
  xserver-xorg-video-radeon xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-tseng xserver-xorg-video-v4l xserver-xorg-video-vesa
  xserver-xorg-video-vmware xserver-xorg-video-voodoo xterm xtrans-dev
  xulrunner-1.9.2 yelp
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  e2fsprogs util-linux (due to e2fsprogs) hostname upstart (due to hostname)
0 upgraded, 0 newly installed, 476 to remove and 0 not upgraded.
After this operation, 1,564MB disk space will be freed.
You are about to do something potentially harmful
To continue type in the phrase &#8216;Yes, do as I say!&#8217;
 ?]

```

You can probably guess how I answered :P

---

### Post by Rubi1200 on 2010-08-29
Hopefully no!?! :confused: ;)

Can't remember where I saw it now, but one of the forum mods posted something about this; obviously, do NOT remove plymouth.

---

### Post by varunendra on 2010-08-29
> **ConcreteDonkey said:**
> After reinstalling it the problem still remains and when attempting to run sudo apt-get remove plymouth I get this lovely horrifying message:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libopenal1 libatk1.0-dev debhelper libbabl-0.0-0 linux-headers-2.6.32-21
  libxcb-keysyms1 intltool-debian x11proto-kb-dev libglib2.0-dev
  libnet-ssleay-perl x11proto-xinerama-dev librsvg2-2.18-cil libgfortran3
  libmono-zeroconf1.0-cil libqt4-dbus x11proto-render-dev libgdata1.4-cil
  libnotify-bin po-debconf xbindkeys podsleuth libxdmcp-dev libsysfs-dev
  libdirectfb-extra libparted0 pidgin-data libpng12-dev libdvbpsi5 grub-pc
  libboo2.0.9-cil libfontconfig1-dev libmail-sendmail-perl guile-1.6-libs
  libvlc2 x11proto-core-dev gettext python-numpy
  linux-headers-2.6.32-21-generic winetricks vlc-nox cvs libqtcore4
  x11proto-randr-dev libtaglib2.0-cil libupnp3 libdbus-1-dev giblib1
  libwxbase2.8-0 libjpeg62-dev libqthreads-12 zlib1g-dev x11proto-input-dev
  streamer libfreetype6-dev libpthread-stubs0-dev ttf-symbol-replacement
  os-prober libdbus-glib-1-dev libiso9660-7 libpthread-stubs0 libqt4-xml
  wine1.2-gecko libblas3gf xawtv-plugins libqt4-network libgimp2.0
  liblapack3gf libexpat1-dev liblua5.1-0 libmpg123-0 filezilla-common
  html2text vlc-data libpixman-1-dev libtar winbind grub-common scrot
  libimlib2 gimp-data libvlccore2 libvcdinfo0 libguile-ltdl-1 libebml0
  python-keybinder libsys-hostname-long-perl libmatroska0 libmng1
  libnotify0.4-cil libnet-libidn-perl
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  acpi-support acpid adobe-flashplugin aisleriot alsa-base alsa-utils anacron
  apparmor apparmor-utils apport apport-gtk aptdaemon apturl at at-spi
  avahi-daemon avahi-utils banshee bluez bluez-cups brltty brltty-x11
  capplets-data checkbox checkbox-gtk compiz compiz-core
  compiz-fusion-plugins-main compiz-gnome compiz-plugins
  compizconfig-backend-gconf computer-janitor-gtk computertemp console-setup
  consolekit couchdb-bin cron cups cups-driver-gutenprint dbus dbus-x11
  desktopcouch dkms dmsetup dockbarx dockbarx-themes-extra e2fsprogs
  easy-slow-down-manager empathy-common eog erlang-base erlang-crypto
  erlang-inets erlang-mnesia erlang-public-key erlang-runtime-tools erlang-ssl
  erlang-syntax-tools erlang-xmerl evince evolution-data-server
  evolution-webcal file-roller filezilla firefox firefox-branding
  firefox-gnome-support foo2zjs foomatic-db foomatic-db-engine
  friendly-recovery ftp gbrainy gcalctool gconf-defaults-service gconf-editor
  gconf2 gconf2-common gdebi gdm gdm-guest-session gedit ghostscript-cups
  ghostscript-x gimp gksu gnome-about gnome-applets gnome-applets-data
  gnome-bluetooth gnome-codec-install gnome-control-center gnome-disk-utility
  gnome-exe-thumbnailer gnome-games-common gnome-keyring gnome-mag
  gnome-mahjongg gnome-media gnome-media-common gnome-nettool gnome-orca
  gnome-panel gnome-panel-data gnome-power-manager gnome-screensaver
  gnome-session gnome-session-bin gnome-session-canberra gnome-settings-daemon
  gnome-sudoku gnome-system-monitor gnome-system-tools gnome-terminal
  gnome-terminal-data gnome-user-guide gnome-user-share gnome-utils gnomine
  gsfonts-x11 gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-good
  gstreamer0.10-pulseaudio gucharmap gvfs gvfs-backends gvfs-bin gvfs-fuse hal
  hostname hplip ibus ibus-m17n ibus-table icoutils ifupdown imagemagick
  indicator-applet indicator-applet-session indicator-me indicator-session
  indicator-sound initramfs-tools initscripts irqbalance jockey-common
  jockey-gtk kbd language-selector lftp libasound2-plugins libatspi1.0-0
  libaudio2 libbonoboui2-0 libcairo2-dev libcamel1.2-14 libcanberra-pulse
  libcompizconfig0 libcouchdb-glib-1.0-2 libcryptui0
  libdesktopcouch-glib-1.0-2 libdirectfb-dev libebackend1.2-0 libebook1.2-9
  libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-11
  libedataserverui1.2-8 libegroupwise1.2-13 libexchange-storage1.2-3
  libgail-gnome-module libgconf2-4 libgconf2.0-cil libgdata6 libgdu0
  libgegl-0.0-0 libgksu2-0 libgnome-desktop-2-17 libgnome-media0
  libgnome-pilot2 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2-0
  libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnome2.24-cil
  libgnomedesktop2.20-cil libgnomekbd-common libgnomekbd4
  libgnomepanel2.24-cil libgnomeui-0 libgnomevfs2-0 libgnomevfs2-common
  libgnomevfs2-extra libgstfarsight0.10-0 libgtk2.0-dev libgtkhtml-editor0
  libgtkhtml3.14-19 libgweather-common libgweather1 libice-dev libice6
  libio-socket-ssl-perl liblpint-bonobo0 libm17n-0 libmagickcore2
  libmagickcore2-extra libmagickwand2 libmetacity-private0 libmjpegtools-1.9
  libnet-dbus-perl libnss-mdns liboobs-1-4 libpanel-applet2-0 libpango1.0-dev
  libpolkit-gtk-1-0 libpulse-browse0 libpulse-mainloop-glib0 libpulse0
  libpurple-dev libpurple0 libqtgui4 librpc-xml-perl libsdl-image1.2
  libsdl1.2debian libsdl1.2debian-pulseaudio libsm-dev libsm6
  libsoup-gnome2.4-1 libstartup-notification0 libtelepathy-farsight0
  libwebkit-1.0-2 libwebkit1.1-cil libwnck2.20-cil libwnck22 libwww-perl
  libwxgtk2.8-0 libx11-dev libxau-dev libxaw7 libxcb-render-util0-dev
  libxcb-render0-dev libxcb1-dev libxcomposite-dev libxcursor-dev
  libxdamage-dev libxext-dev libxfixes-dev libxft-dev libxi-dev
  libxinerama-dev libxklavier16 libxml-parser-perl libxml-sax-expat-perl
  libxml-twig-perl libxml-xpath-perl libxmu6 libxrandr-dev libxrender-dev
  libxres1 libxss1 libxt6 libxtst6 libxvmc1 libxxf86dga1 light-themes
  linux-generic linux-image-2.6.32-24-generic linux-image-generic
  linux-sound-base logrotate m17n-contrib m17n-db media-player-info metacity
  metacity-common module-init-tools mountall mousetweaks nautilus
  nautilus-data nautilus-sendto nautilus-sendto-empathy nautilus-share netbase
  network-manager network-manager-gnome network-manager-pptp
  network-manager-pptp-gnome notify-osd ntfs-3g ntfs-config ntpdate
  obex-data-server onboard openoffice.org-base-core openoffice.org-calc
  openoffice.org-core openoffice.org-draw openoffice.org-emailmerge
  openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us
  openoffice.org-impress openoffice.org-math openoffice.org-writer
  openprinting-ppds opera pcmciautils pidgin pidgin-dev pidgin-libnotify
  pidgin-ppa plymouth plymouth-label plymouth-theme-ubuntu-logo
  plymouth-theme-ubuntu-text plymouth-x11 pm-utils pm-utils-powersave-policy
  policykit-1 policykit-1-gnome powermgmt-base ppp pppconfig pppoeconf
  pptp-linux prey procps pulseaudio pulseaudio-esound-compat
  pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-x11
  pulseaudio-utils pxljr python-aptdaemon python-aptdaemon-gtk
  python-desktopcouch python-desktopcouch-records python-evolution
  python-farsight python-gconf python-gnome2 python-gnome2-desktop
  python-gnomeapplet python-gnomedesktop python-mediaprofiles python-metacity
  python-papyon python-pyatspi python-speechd python-uno python-virtkey
  python-webkit python-wnck quadrapassel rsyslog samsung-tools
  screen-resolution-extra screensaver-default-images seahorse simple-scan
  skype software-center software-properties-gtk speech-dispatcher splix
  system-config-printer-gnome system-tools-backends telepathy-butterfly
  telepathy-haze telepathy-salut telnet tomboy transmission-gtk tsclient
  ttf-mscorefonts-installer ubufox ubuntu-artwork ubuntu-desktop ubuntu-docs
  ubuntu-minimal ubuntu-standard ubuntu-system-service ubuntu-tweak
  ubuntu-wallpapers udev udisks ufw update-manager update-notifier upower
  upstart ureadahead usb-creator-common usb-creator-gtk util-linux vinagre
  vino vlc vlc-plugin-pulse wine wine1.2 wireless-crda x-ttcidfont-conf
  x11-apps x11-common x11-session-utils x11-utils x11-xfs-utils x11-xkb-utils
  x11-xserver-utils x11proto-composite-dev x11proto-damage-dev
  x11proto-fixes-dev x11proto-xext-dev xfonts-100dpi xfonts-75dpi xfonts-base
  xfonts-encodings xfonts-mathml xfonts-scalable xfonts-utils xinit xorg
  xscreensaver-data xscreensaver-gl xserver-common xserver-xorg
  xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-evdev
  xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-all
  xserver-xorg-video-apm xserver-xorg-video-ark xserver-xorg-video-ati
  xserver-xorg-video-chips xserver-xorg-video-cirrus xserver-xorg-video-fbdev
  xserver-xorg-video-geode xserver-xorg-video-i128 xserver-xorg-video-i740
  xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-nv
  xserver-xorg-video-openchrome xserver-xorg-video-r128
  xserver-xorg-video-radeon xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-tseng xserver-xorg-video-v4l xserver-xorg-video-vesa
  xserver-xorg-video-vmware xserver-xorg-video-voodoo xterm xtrans-dev
  xulrunner-1.9.2 yelp
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  e2fsprogs util-linux (due to e2fsprogs) hostname upstart (due to hostname)
0 upgraded, 0 newly installed, 476 to remove and 0 not upgraded.
After this operation, 1,564MB disk space will be freed.
You are about to do something potentially harmful
To continue type in the phrase ‘Yes, do as I say!’
 ?]

```You can probably guess how I answered :P


:shock:
My sympathies.....!!:confused:

I never knew Lucid has so much sense of humor .... :lolflag:

---

### Post by PierreRobiquet on 2010-08-29
> **Rubi1200 said:**
> Hopefully no!?! :confused: ;)

Can't remember where I saw it now, but one of the forum mods posted something about this; obviously, do NOT remove plymouth.

> **varunendra said:**
> :shock:
My sympathies.....!!:confused:
I never knew Lucid has so much sense of humor .... :lolflag:

Don't worry about it, luckily apt is a very friendly fellow and warns about the dangers of removing certain applications. Is there a reason that removing Plymouth removes every application from my computer, is it potentially that they all list something which has Plymouth as a dependency?

---

