---
title: "help!!"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by ejlal on 2009-06-24
i was basically trying to upgrade pidgin manually,so i got the .debs but i faced dependency issues, which lead to installing dependencies manually too >>>>>> 
i got  notification message says:'error:broken count>0'
so i went to synpatic and i found that the packages are:
libperl5.8
perl
 
those packages were among the one's i installed,so what to do:confused:
dont bother telling me that i messed  up  the blah blah blah of the blah blah or what so ever kind of things, wont understand it any way beside am new to ubuntu /linux so.
am using ubuntu hardy which is preinstalled in toshiba nb100-11r

thanks

---

### Post by ejlal on 2009-06-24
am clueless,so should i remove those packages or reinstall it synoptic  manager,if i removed it will i still find my older version and wont that messes my system even more????!!!!

---

### Post by ejlal on 2009-06-24
anybody?!!

---

### Post by scrooge_74 on 2009-06-24
What are you trying to accomplish? Update so you can connect to YAhoo Messenger?

If the answer is yes check this link:  [http://www.pidgin.im/download/ubuntu/](http://www.pidgin.im/download/ubuntu/)

Go to synaptic and remove any packages you are having problems, then update system and start over using the link above.

---

### Post by ejlal on 2009-06-24
> **scrooge_74 said:**
> 

Go to synaptic and remove any packages you are having problems, then update system and start over using the link above.

but those packages will affect many other beside i got unsolved updating problems.
so if i removed it will i be able to restore my older versions (perl -libperl). 
are those any important ,sorry for the noob question:(

---

### Post by ejlal on 2009-06-24
ejlal@TOSHIBA:~$ sudo apt-get check
[sudo] password for ejlal: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run &#8216;apt-get -f install&#8217; to correct these.
The following packages have unmet dependencies.
  libperl5.8: Depends: perl-base (= 5.8.8-12) but 5.8.8-12ubuntu0.4 is installed
  perl: Depends: perl-base (= 5.8.8-12) but 5.8.8-12ubuntu0.4 is installed
E: Unmet dependencies. Try using -f.

---

### Post by ejlal on 2009-06-24
ejlal@TOSHIBA:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following packages were automatically installed and are no longer required:
  xserver-xorg libedit2 gstreamer0.10-alsa evolution-common mesa-utils xserver-xorg-video-rendition libmono2.0-cil
  libartsc0 python-gst0.10 xsltproc libmono-security1.0-cil libopenal0a xserver-xorg-input-evdev libcompizconfig0
  xserver-xorg-video-newport libarchive1 libmono-data-tds2.0-cil libpth20 libparted1.7-1 libgphoto2-port0
  xserver-xorg-video-s3virge gnome-desktop-data xfonts-scalable libmono0 libmono-system-data2.0-cil libgtop2-common
  libsensors3 xserver-xorg-video-all pkg-config libxine1-x xserver-xorg-video-apm libcaca0 xserver-xorg-video-ark
  libglib2.0-cil libiec61883-0 xserver-xorg-video-ati libdjvulibre15 libmono-sharpzip0.84-cil guidance-backends
  python-software-properties libgnome-mag2 xserver-xorg-video-tdfx libgnomeui-common iso-codes ubuntu-gdm-themes
  network-manager iputils-tracepath xserver-xorg-video-trident xserver-xorg-video-glint sqlite mplayer-skins
  libgconf2.0-cil dnsutils mdetect libsilc-1.1-2 xserver-xorg-video-fbdev xserver-xorg-input-wacom update-manager-core
  cupsddk libgnome-media0 libart-2.0-2 app-install-data libmono-system-web1.0-cil libsane unzip gnome-cards-data
  libglew1.5 libwpg-0.1-1 xserver-xorg-video-v4l libmono-corlib1.0-cil python-gdata xserver-xorg-video-mga libnm-util0
  python-libxml2 libdecoration0 liblircclient0 libxcb-xv0 libopenexr2ldbl python-numeric xserver-xorg-input-mouse
  libieee1284-3 xserver-xorg-video-nsc libart2.0-cil libbonoboui2-common libspeex1 libapm1 libpisock9 libcamel1.2-11 xauth
  compizconfig-backend-gconf update-notifier-common libtrackerclient0 xserver-xorg-video-vesa libggzmod4 python-apt
  xserver-xorg-video-siliconmotion libsqlite0 groff-base ubuntu-wallpapers whois xserver-xorg-video-tga
  xserver-xorg-video-sis libsgutils1 python-pyorbit gdebi-core totem-common libx11-xcb1 python-gconf libedata-cal1.2-6
  xserver-xorg-video-vga libxine1-bin xserver-xorg-video-via apport xserver-xorg-video-s3 gnome-media-common
  libgnome-menu2 xserver-xorg-video-nv libgadu3 libgd2-noxpm libgphoto2-2 xserver-xorg-core mono-common libwavpack1
  libsnack2 xserver-xorg-video-tseng libcdio7 libelfg0 openssh-client libeel2-data jockey-common xfonts-75dpi
  guile-1.6-libs libgnomekbd-common gedit-common libalut0 libhesiod0 xserver-xorg-video-savage libdmx1 libzltext
  libgnome-pilot2 libxevie1 libglibmm-2.4-1c2a python-launchpad-bugs xbitmaps dhcdbd libenca0 gnome-about libcdio-cdda0
  libgnomeprint2.2-data libxine1-ffmpeg libmono-system1.0-cil libgtksourceview2.0-common python-imaging libkpathsea4
  xserver-xorg-input-all libmono-security2.0-cil gdb python-compizconfig xfonts-base libavc1394-0 libggi2 libzlcore
  libegroupwise1.2-13 libgii1 python-brlapi python-xdg mono-gac libnm-glib0 libgutenprint2 unattended-upgrades libggz2
  libxcb-shape0 libgsf-1-common gnome-doc-utils libcroco3 libgweather-common libecal1.2-7 xserver-xorg-video-vmware
  librarian0 libaa1 libmono1.0-cil xserver-xorg-input-kbd libgdata1.2-1 libgtksourceview-common tcltls
  system-config-printer-common python-gnupginterface localechooser-data libmono-data-tds1.0-cil libmono-sqlite2.0-cil
  mono-jit human-icon-theme python-problem-report libqthreads-12 libbluetooth2 gnome-games-data libgdata-google1.2-1
  libmono-system-data1.0-cil libmono-system-web2.0-cil libgii1-target-x xdg-utils xinit iputils-arping libebook1.2-9 tcl
  libgnomecanvas2-common libshout3 libdvdnav4 libmono-sharpzip2.84-cil libmono-corlib2.0-cil libedata-book1.2-2
  evolution-data-server ufw xfonts-100dpi libxss1 libfakekey0 libgnome-speech7 tcl8.4 tcl8.5 libedataserver1.2-9
  cupsddk-drivers libjasper1 libgtop2-7 xserver-xorg-video-i128 xserver-xorg-video-neomagic mono-runtime
  xserver-xorg-video-chips xserver-xorg-video-voodoo libcdio-paranoia0 libxvmc1 zip python-gdbm python-cups libnl1
  dmz-cursor-theme language-selector-common libtag1c2a libxklavier12 gnome-terminal-data libmeanwhile1 libsnmp-base
  xserver-xorg-video-i740 xserver-xorg-video-i810 libgpgme11 man-db libggzcore9 libmodplug0c2 libzephyr3
  xserver-xorg-video-cyrix libxml2-utils gvfs xserver-xorg-video-dummy x11-xkb-utils gvfs-backends libvisual-0.4-0
  python-apport sqlite3 gstreamer0.10-gnomevfs compiz-core xserver-xorg-input-synaptics evolution-data-server-common
  libaudio2 libgnome-vfs2.0-cil libxcb-shm0 gstreamer0.10-plugins-base desktop-file-utils libvte-common libguile-ltdl-1
  xserver-xorg-video-sisusb iptables liblame0 libscrollkeeper0 gstreamer0.10-tools xserver-xorg-video-imstt libmng1
  libcucul0 libmono-system2.0-cil libgnomeprintui2.2-common libgsf-1-114 libxkbfile1 xserver-xorg-video-cirrus
  xserver-xorg-video-intel libgnomecups1.0-1 libpisync1 hplip-data libxine1-console hwtest libosso1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  adobe-flashplugin adobereader-enu alacarte amsn apport-gtk at-spi brltty-x11 bug-buddy capplets-data cheese cli-common
  cmotech-qtmodem compiz compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins
  compizconfig-settings-manager contact-lookup-applet cups-pdf cupsys cupsys-driver-gutenprint defoma desktop-switcher
  displayconfig-gtk doc-base docbook-xml eog evince evolution evolution-plugins evolution-webcal f-spot
  fast-user-switch-applet fbreader file-roller firefox firefox-3.0 firefox-3.0-gnome-support firefox-gnome-support
  flashplugin-nonfree fontconfig fontconfig-config foomatic-db-engine foomatic-db-hpijs foomatic-filters frozen-bubble
  fusion-icon gcalctool gconf-editor gdebi gdm gedit ghostscript ghostscript-x gimp-help-en gksu
  gnome-accessibility-themes gnome-app-install gnome-applets gnome-applets-data gnome-control-center gnome-games
  gnome-icon-theme gnome-keyring gnome-mag gnome-media gnome-menus gnome-mount gnome-netstatus-applet gnome-nettool
  gnome-orca gnome-panel gnome-panel-data gnome-power-manager gnome-screensaver gnome-session gnome-settings-daemon
  gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal gnome-themes gnome-user-guide gnome-utils
  gnome-volume-manager go-home-applet gparted gsfonts gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good
  gstreamer0.10-x gtk2-engines gtk2-engines-murrine gtk2-engines-pixbuf gtk2-engines-ubuntulooks gtkhtml3.14 gucharmap
  gufw hal-cups-utils hpijs hplip human-netbook-theme human-theme hwtest-gtk icedtea-gcjwebplugin jockey-gtk
  language-installer language-selector language-support-ar language-support-en language-support-fonts-ar
  language-support-input-ar language-support-translations-en language-support-writing-en libatspi1.0-0 libbonoboui2-0
  libcairo-perl libcairo2 libcairomm-1.0-1 libclutter-0.6-0 libedataserverui1.2-8 libeel2-2 libexchange-storage1.2-3
  libflickrnet2.1.5-cil libfontconfig1 libgail-common libgail-gnome-module libgail18 libgksu2-0 libglade2-0
  libglade2.0-cil libglib-perl libgnome-desktop-2 libgnome-window-settings-dev libgnome-window-settings1
  libgnome2-canvas-perl libgnome2-perl libgnome2-vfs-perl libgnome2.0-cil libgnomecanvas2-0 libgnomekbd2 libgnomekbdui2
  libgnomeprint2.2-0 libgnomeprintui2.2-0 libgnomeui-0 libgpod-common libgpod3 libgraphviz4 libgs8 libgtk2-perl
  libgtk2.0-0 libgtk2.0-bin libgtk2.0-cil libgtkglext1 libgtkhtml2-0 libgtkhtml3.14-19 libgtkhtml3.16-cil
  libgtkmm-2.4-1c2a libgtksourceview1.0-0 libgtksourceview2.0-0 libgtkspell0 libgucharmap6 libgweather1 libhildon-1-0
  libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl liblaunchpad-integration1 liblpint-bonobo0 libmagick10
  libmetacity0 libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo1.0-cil libmono-cairo2.0-cil libnautilus-burn4
  libnautilus-extension1 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libnet-dbus-perl libnotify1 libnss-mdns
  liboobs-1-4 libpanel-applet2-0 libpango1.0-0 libpango1.0-common libperl5.8 libpolkit-gnome0 libpoppler-glib2 libpoppler2
  libqt3-mt librsvg2-2 librsvg2-common libsdl-pango1 libsdl-perl libsexy2 libsnmp15 libtotem-plparser10 liburi-perl
  libvte9 libwmf0.2-7 libwnck22 libwww-perl libxft2 libxine1 libxine1-misc-plugins libxine1-plugins libxml-parser-perl
  libxml-twig-perl libzlui-gtk libzlui-maemo maximus metacity metacity-common mousetweaks mozilla-mplayer mplayer nautilus
  nautilus-data nautilus-sendto nautilus-share network-manager-gnome notification-daemon oem-config oem-config-gtk onboard
  openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-help-en-gb
  openoffice.org-help-en-us openoffice.org-impress openoffice.org-java-common openoffice.org-l10n-en-gb
  openoffice.org-l10n-en-za openoffice.org-style-human openoffice.org-thesaurus-en-au openoffice.org-thesaurus-en-us
  openoffice.org-writer perl perl-modules pnm2ppa policykit-gnome poppler-utils python-cairo python-glade2 python-gmenu
  python-gnome2 python-gnome2-desktop python-gnomecanvas python-gtk2 python-gtkglext1 python-gtkhtml2
  python-gtksourceview2 python-launchpad-integration python-notify python-pyatspi python-sexy python-uno python-virtkey
  python-vte rhythmbox rss-glx scim scim-bridge-agent scim-bridge-client-gtk scim-gtk2-immodule scim-modules-table
  scim-tables-additional screensaver-default-images scrollkeeper seahorse sgml-base sgml-data software-properties-gtk
  ssh-askpass-gnome synaptic system-config-printer-gnome system-tools-backends tangerine-icon-theme
  thunderbird-locale-en-gb tk8.5 totem-gstreamer totem-mozilla totem-plugins totem-xine ttf-arabeyes ttf-arphic-uming
  ttf-bitstream-vera ttf-dejavu ttf-dejavu-core ttf-dejavu-extra ttf-farsiweb ttf-freefont ttf-indic-fonts-core ttf-kacst
  ttf-kochi-gothic ttf-kochi-mincho ttf-lao ttf-malayalam-fonts ttf-sil-scheherazade ttf-thai-tlwg ttf-unfonts-core
  ubuntu-artwork ubuntu-docs ubuntu-netbook-remix ume-config-netbook ume-launcher update-manager update-notifier vino
  webfav window-picker-applet x-ttcidfont-conf x11-apps x11-utils xbase-clients xdg-user-dirs-gtk xml-core xorg
  xscreensaver-data xscreensaver-gl xterm xulrunner-1.9 xulrunner-1.9-gnome-support xutils yelp zenity
0 upgraded, 0 newly installed, 330 to remove and 0 not upgraded.
After this operation, 1234MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

---

### Post by Viva on 2009-06-24
You should also install the latest libraries for pidgin. Remove pidgin if it allows you to and add the repositories from [https://launchpad.net/~pidgin-developers/+archive/ppa](https://launchpad.net/~pidgin-developers/+archive/ppa)

---

### Post by ejlal on 2009-06-24
but this will remove 330 pachages!!!!!!

---

### Post by Viva on 2009-06-24
Yes, I've just noticed:(

---

### Post by ejlal on 2009-06-24
> **Viva said:**
> Yes, I've just noticed:(
so?? remove/keep  what shall i do??:confused:

---

### Post by ejlal on 2009-06-24
btw i have zero interest in Pidgin/yahoo/msn/chatting/my friends now

---

### Post by carml on 2009-06-24
If I were you I'd try to reboot and choose the Recovery option->Try to fix broken packages; to do so you need a wired lan connection,because your system will check all the packages.
A wired lan connection is also known as Ethernet or Eth0 under System->Administration->Network.

---

### Post by snowpine on 2009-06-24
'sudo apt-get install pidgin' or you can install it using Add/Remove Programs or Synaptic Package Manager.

This is the safe way to install Pidgin that will avoid dependency problems or otherwise break your system.

---

### Post by emeraldgirl08 on 2009-06-24
I've received that "broken count>0" before. It's been awhile and maybe someone here can confirm. I used commands listed in the [Comprehensive Multimedia & Video Howto.]("http://ubuntuforums.org/showthread.php?t=766683")

```
sudo rm /var/lib/apt/lists/partial/*

sudo apt-get update
```

The explanation given in the Multimedia thread is:

> If you're certain that you have the necessary repositories enabled, then you may have a currupt apt list due to an interrupted "apt-get update", which would then make the package manager think certain packages don't exist on the server.

I'm somewhat of a NOOB also but the command seems like it may work.

---

### Post by ejlal on 2009-06-24
any other option carmal ? coz i dont have any interent connection other than my usb modem,and can i use mu recovery cd? though my laptop doesnt have cd player

---

### Post by ejlal on 2009-06-24
> **emeraldgirl08 said:**
> I've received that "broken count>0" before. It's been awhile and maybe someone here can confirm. I used commands listed in the [Comprehensive Multimedia & Video Howto.]("http://ubuntuforums.org/showthread.php?t=766683")

```
sudo rm /var/lib/apt/lists/partial/*

sudo apt-get update
```
 please confirm!!

---

### Post by carml on 2009-06-24
Yes, ```
sudo apt-get update && sudo apt-get upgrade
```,this hopefully should check also your package list.
There a way to fix the packages,but I don't remember exactly it and I don't know if it works for many packages. :confused:

---

### Post by ejlal on 2009-06-24
> **carml said:**
> Yes, ```
sudo apt-get update && sudo apt-get upgrade
```,this hopefully should check also your package list.
  this didnt help:(

---

### Post by carml on 2009-06-24
Did you try what emeradgirl8 suggested?

---

### Post by ejlal on 2009-06-24
no, am waiting for confirmation

---

### Post by carml on 2009-06-24
I think I can confirm it :). I had a look at the suggested page and looked the path on my pc.

---

### Post by ejlal on 2009-06-24
sudo rm /var/lib/apt/lists/partial/* &sudo apt-get update
Didnt help the error still here:(

---

### Post by ejlal on 2009-06-24
would u rocemmend i reinstall the broken packages just to see what will happen?!

---

### Post by emeraldgirl08 on 2009-06-24
You've restarted the console after running those commands right? And did you try issuing the command again? There is a suggestion on the thread that states 

> Note: You may have to perform "sudo apt-get update" twice after recovering from any of the errors below.

Wow. If that doesn't work I'm not sure what to tell ya. Hope you get this fixed soon!

---

### Post by emeraldgirl08 on 2009-06-24
> **ejlal said:**
> would u rocemmend i reinstall the broken packages just to see what will happen?!

Try this. You're going to replace the * with the broken file name. I think you said Perl and libperl5.8 right? 

```

sudo rm /var/lib/dpkg/info/filename*
```

next.

```
sudo apt-get update
```

> This doesn't mean the package has been removed, just the pre/post-install scripts, md5sums, and file lists related to it. You should reinstall the package - even if you plan to remove it, as those deleted and currupted files related to it will be replaced with non-currupted ones.

Hope it works!

*crosses fingers for ya*

---

### Post by Ayuthia on 2009-06-24
What .deb packages did you install?  Would one of them happen to be perl-base?

Can you go into the Terminal and post the results of:
```
tail -100 /var/log/dpkg.log
```
This will show the last few items that were installed through dpkg.  It might just be a matter of going back to the previous version of perl-base.

My guess is that those packages that are going to be removed are because they are dependent on perl.  Since perl is broken, it thinks that they need to be removed.

---

### Post by ejlal on 2009-06-24
> **emeraldgirl08 said:**
> Try this. You're going to replace the * with the broken file name. I think you said Perl and libperl5.8 right? 

```

sudo rm /var/lib/dpkg/info/filename*
```next.

```
sudo apt-get update
```

Hope it works!

*crosses fingers for ya*
i get no such file or directory!

---

### Post by carml on 2009-06-24
Just change "filename" with the name of the package you want to perform that command :)

---

### Post by ejlal on 2009-06-24
> **Ayuthia said:**
> What .deb packages did you install?  Would one of them happen to be perl-base?

Can you go into the Terminal and post the results of:
```
tail -100 /var/log/dpkg.log
``` 
ejlal@TOSHIBA:~$ tail -100 /var/log/dpkg.log
2009-06-24 13:23:13 status unpacked libdbus-glib-1-2 0.74-2
2009-06-24 13:23:13 status half-installed libdbus-glib-1-2 0.74-2
2009-06-24 13:23:13 status half-installed libdbus-glib-1-2 0.74-2
2009-06-24 13:23:13 status unpacked libdbus-glib-1-2 0.74-2
2009-06-24 13:23:13 status unpacked libdbus-glib-1-2 0.74-2
2009-06-24 13:23:14 startup packages configure
2009-06-24 13:23:14 configure libdbus-glib-1-2 0.74-2 0.74-2
2009-06-24 13:23:14 status unpacked libdbus-glib-1-2 0.74-2
2009-06-24 13:23:14 status half-configured libdbus-glib-1-2 0.74-2
2009-06-24 13:23:14 status installed libdbus-glib-1-2 0.74-2
2009-06-24 13:23:14 status triggers-pending libc6 2.7-10ubuntu3
2009-06-24 13:23:14 trigproc libc6 2.7-10ubuntu3 2.7-10ubuntu3
2009-06-24 13:23:14 status half-configured libc6 2.7-10ubuntu3
2009-06-24 13:23:14 status installed libc6 2.7-10ubuntu3
2009-06-24 13:36:09 startup archives unpack
2009-06-24 13:36:18 upgrade libpurple-bin 1:2.5.7-1~getdeb1 1:2.5.7-1ubuntu1~pidgin3.8.04.1
2009-06-24 13:36:18 status half-configured libpurple-bin 1:2.5.7-1~getdeb1
2009-06-24 13:36:18 status unpacked libpurple-bin 1:2.5.7-1~getdeb1
2009-06-24 13:36:18 status half-installed libpurple-bin 1:2.5.7-1~getdeb1
2009-06-24 13:36:18 status half-installed libpurple-bin 1:2.5.7-1~getdeb1
2009-06-24 13:36:18 status unpacked libpurple-bin 1:2.5.7-1ubuntu1~pidgin3.8.04.1
2009-06-24 13:36:18 status unpacked libpurple-bin 1:2.5.7-1ubuntu1~pidgin3.8.04.1
2009-06-24 13:36:18 upgrade pidgin-data 1:2.5.7-1~getdeb1 1:2.5.7-1ubuntu1~pidgin3.8.04.1
2009-06-24 13:36:18 status half-configured pidgin-data 1:2.5.7-1~getdeb1
2009-06-24 13:36:18 status unpacked pidgin-data 1:2.5.7-1~getdeb1
2009-06-24 13:36:18 status half-installed pidgin-data 1:2.5.7-1~getdeb1
2009-06-24 13:36:25 status half-installed pidgin-data 1:2.5.7-1~getdeb1
2009-06-24 13:36:29 status unpacked pidgin-data 1:2.5.7-1ubuntu1~pidgin3.8.04.1
2009-06-24 13:36:30 status unpacked pidgin-data 1:2.5.7-1ubuntu1~pidgin3.8.04.1
2009-06-24 13:36:31 startup packages configure
2009-06-24 13:36:31 configure libpurple-bin 1:2.5.7-1ubuntu1~pidgin3.8.04.1 1:2.5.7-1ubuntu1~pidgin3.8.04.1
2009-06-24 13:36:31 status unpacked libpurple-bin 1:2.5.7-1ubuntu1~pidgin3.8.04.1
2009-06-24 13:36:32 status half-configured libpurple-bin 1:2.5.7-1ubuntu1~pidgin3.8.04.1
2009-06-24 13:36:32 status installed libpurple-bin 1:2.5.7-1ubuntu1~pidgin3.8.04.1
2009-06-24 13:36:32 configure pidgin-data 1:2.5.7-1ubuntu1~pidgin3.8.04.1 1:2.5.7-1ubuntu1~pidgin3.8.04.1
2009-06-24 13:36:32 status unpacked pidgin-data 1:2.5.7-1ubuntu1~pidgin3.8.04.1
2009-06-24 13:36:32 status unpacked pidgin-data 1:2.5.7-1ubuntu1~pidgin3.8.04.1
2009-06-24 13:36:32 status half-configured pidgin-data 1:2.5.7-1ubuntu1~pidgin3.8.04.1
2009-06-24 13:36:32 status installed pidgin-data 1:2.5.7-1ubuntu1~pidgin3.8.04.1
2009-06-24 13:37:24 startup archives install
2009-06-24 13:37:28 upgrade libdbus-glib-1-2 0.74-2 0.74-2
2009-06-24 13:37:28 status half-configured libdbus-glib-1-2 0.74-2
2009-06-24 13:37:28 status unpacked libdbus-glib-1-2 0.74-2
2009-06-24 13:37:28 status half-installed libdbus-glib-1-2 0.74-2
2009-06-24 13:37:28 status half-installed libdbus-glib-1-2 0.74-2
2009-06-24 13:37:28 status unpacked libdbus-glib-1-2 0.74-2
2009-06-24 13:37:28 status unpacked libdbus-glib-1-2 0.74-2
2009-06-24 13:37:28 configure libdbus-glib-1-2 0.74-2 0.74-2
2009-06-24 13:37:28 status unpacked libdbus-glib-1-2 0.74-2
2009-06-24 13:37:28 status half-configured libdbus-glib-1-2 0.74-2
2009-06-24 13:37:28 status installed libdbus-glib-1-2 0.74-2
2009-06-24 13:37:28 status triggers-pending libc6 2.7-10ubuntu3
2009-06-24 13:37:28 trigproc libc6 2.7-10ubuntu3 2.7-10ubuntu3
2009-06-24 13:37:28 status half-configured libc6 2.7-10ubuntu3
2009-06-24 13:37:29 status installed libc6 2.7-10ubuntu3
2009-06-24 13:39:03 startup archives unpack
2009-06-24 13:39:03 upgrade libdbus-glib-1-2 0.74-2 0.74-2
2009-06-24 13:39:03 status half-configured libdbus-glib-1-2 0.74-2
2009-06-24 13:39:03 status unpacked libdbus-glib-1-2 0.74-2
2009-06-24 13:39:03 status half-installed libdbus-glib-1-2 0.74-2
2009-06-24 13:39:03 status half-installed libdbus-glib-1-2 0.74-2
2009-06-24 13:39:03 status unpacked libdbus-glib-1-2 0.74-2
2009-06-24 13:39:03 status unpacked libdbus-glib-1-2 0.74-2
2009-06-24 13:39:04 startup packages configure
2009-06-24 13:39:04 configure libdbus-glib-1-2 0.74-2 0.74-2
2009-06-24 13:39:04 status unpacked libdbus-glib-1-2 0.74-2
2009-06-24 13:39:04 status half-configured libdbus-glib-1-2 0.74-2
2009-06-24 13:39:04 status installed libdbus-glib-1-2 0.74-2
2009-06-24 13:39:04 status triggers-pending libc6 2.7-10ubuntu3
2009-06-24 13:39:04 trigproc libc6 2.7-10ubuntu3 2.7-10ubuntu3
2009-06-24 13:39:04 status half-configured libc6 2.7-10ubuntu3
2009-06-24 13:39:04 status installed libc6 2.7-10ubuntu3
2009-06-24 14:26:40 startup archives install
2009-06-24 14:26:52 upgrade libdbus-glib-1-2 0.74-2 0.74-2
2009-06-24 14:26:52 status half-configured libdbus-glib-1-2 0.74-2
2009-06-24 14:26:52 status unpacked libdbus-glib-1-2 0.74-2
2009-06-24 14:26:52 status half-installed libdbus-glib-1-2 0.74-2
2009-06-24 14:26:52 status half-installed libdbus-glib-1-2 0.74-2
2009-06-24 14:26:52 status unpacked libdbus-glib-1-2 0.74-2
2009-06-24 14:26:52 status unpacked libdbus-glib-1-2 0.74-2
2009-06-24 14:26:52 configure libdbus-glib-1-2 0.74-2 0.74-2
2009-06-24 14:26:52 status unpacked libdbus-glib-1-2 0.74-2
2009-06-24 14:26:52 status half-configured libdbus-glib-1-2 0.74-2
2009-06-24 14:26:52 status installed libdbus-glib-1-2 0.74-2
2009-06-24 14:26:52 status triggers-pending libc6 2.7-10ubuntu3
2009-06-24 14:26:52 trigproc libc6 2.7-10ubuntu3 2.7-10ubuntu3
2009-06-24 14:26:52 status half-configured libc6 2.7-10ubuntu3
2009-06-24 14:26:52 status installed libc6 2.7-10ubuntu3
2009-06-24 14:39:33 startup archives install
2009-06-24 14:39:44 upgrade perl-base 5.8.8-12 5.8.8-12ubuntu0.4
2009-06-24 14:39:44 status half-configured perl-base 5.8.8-12
2009-06-24 14:39:44 status unpacked perl-base 5.8.8-12
2009-06-24 14:39:44 status half-installed perl-base 5.8.8-12
2009-06-24 14:39:44 status half-installed perl-base 5.8.8-12
2009-06-24 14:39:45 status unpacked perl-base 5.8.8-12ubuntu0.4
2009-06-24 14:39:45 status unpacked perl-base 5.8.8-12ubuntu0.4
2009-06-24 14:39:45 configure perl-base 5.8.8-12ubuntu0.4 5.8.8-12ubuntu0.4
2009-06-24 14:39:45 status unpacked perl-base 5.8.8-12ubuntu0.4
2009-06-24 14:39:45 status half-configured perl-base 5.8.8-12ubuntu0.4
2009-06-24 14:39:45 status installed perl-base 5.8.8-12ubuntu0.4
ejlal@TOSHIBA:~$

---

### Post by ejlal on 2009-06-24
> **carml said:**
> Just change "filename" with the name of the package you want to perform that command :)
i know ,i changed it & even tried it with filenameperl:D

---

### Post by Ayuthia on 2009-06-24
> **ejlal said:**
> 2009-06-24 14:39:33 startup archives install
2009-06-24 14:39:44 upgrade perl-base 5.8.8-12 5.8.8-12ubuntu0.4
2009-06-24 14:39:44 status half-configured perl-base 5.8.8-12
2009-06-24 14:39:44 status unpacked perl-base 5.8.8-12
2009-06-24 14:39:44 status half-installed perl-base 5.8.8-12
2009-06-24 14:39:44 status half-installed perl-base 5.8.8-12
2009-06-24 14:39:45 status unpacked perl-base 5.8.8-12ubuntu0.4
2009-06-24 14:39:45 status unpacked perl-base 5.8.8-12ubuntu0.4
2009-06-24 14:39:45 configure perl-base 5.8.8-12ubuntu0.4 5.8.8-12ubuntu0.4
2009-06-24 14:39:45 status unpacked perl-base 5.8.8-12ubuntu0.4
2009-06-24 14:39:45 status half-configured perl-base 5.8.8-12ubuntu0.4
2009-06-24 14:39:45 status installed perl-base 5.8.8-12ubuntu0.4
ejlal@TOSHIBA:~$
It does look like perl-base was recently installed.  Do you recall if you did this manually (via dpkg -i)?

We can check the archives to see if we have an older version of this package:
```
ls /var/cache/apt/archives/perl-base*
```

If there is still a 5.8.8-12 version still out there, we might just be able to install it.

---

### Post by ejlal on 2009-06-24
ejlal@TOSHIBA:~$ ls /var/cache/apt/archives/perl-base*
ls: cannot access /var/cache/apt/archives/perl-base*: No such file or directory

there is perl-base 5.8.8-12ubuntu0.4 already installed i found it by searching synaptic

---

### Post by Ayuthia on 2009-06-24
I just checked packages.ubuntu.com and noticed that perl-base should be at 5.8.8-12ubuntu0.4 which is where yours is at.

Can you tell us what .deb packages you were installing?  It would be helpful to have the links on where you downloaded them.  It might help us see what packages were installed that is causing the problem.

---

### Post by Ayuthia on 2009-06-24
Can you also post the results of:
```
dpkg -l libperl
dpkg -l perl
```I want to see the version numbers of those packages.  Those packages might need to be changed if the version numbers are different than what the current updates are supposed to be.

---

### Post by ejlal on 2009-06-24
[http://garr.dl.sourceforge.net/sourceforge/pidgin/pidgin-2.5.7.tar.bz2](http://garr.dl.sourceforge.net/sourceforge/pidgin/pidgin-2.5.7.tar.bz2)
[http://darkstar.ist.utl.pt/getdeb/ubuntu/jaunty/pi/pidgin_2.5.7-1~getdeb1_amd64.deb](http://darkstar.ist.utl.pt/getdeb/ubuntu/jaunty/pi/pidgin_2.5.7-1~getdeb1_amd64.deb)
[http://darkstar.ist.utl.pt/getdeb/ubuntu/jaunty/pi/pidgin_2.5.7-1~getdeb1_i386.deb](http://darkstar.ist.utl.pt/getdeb/ubuntu/jaunty/pi/pidgin_2.5.7-1~getdeb1_i386.deb)
[http://darkstar.ist.utl.pt/getdeb/ubuntu/jaunty/li/libpurple-bin_2.5.7-1~getdeb1_all.deb](http://darkstar.ist.utl.pt/getdeb/ubuntu/jaunty/li/libpurple-bin_2.5.7-1~getdeb1_all.deb)
[http://darkstar.ist.utl.pt/getdeb/ubuntu/jaunty/li/libpurple0_2.5.7-1~getdeb1_i386.deb](http://darkstar.ist.utl.pt/getdeb/ubuntu/jaunty/li/libpurple0_2.5.7-1~getdeb1_i386.deb)
[http://darkstar.ist.utl.pt/getdeb/ubuntu/jaunty/pi/pidgin-data_2.5.7-1~getdeb1_all.deb](http://darkstar.ist.utl.pt/getdeb/ubuntu/jaunty/pi/pidgin-data_2.5.7-1~getdeb1_all.deb)
[http://darkstar.ist.utl.pt/getdeb/ubuntu/jaunty/pi/pidgin_2.5.7-1~getdeb1_i386.deb](http://darkstar.ist.utl.pt/getdeb/ubuntu/jaunty/pi/pidgin_2.5.7-1~getdeb1_i386.deb)
[http://news.softpedia.com/images/extra/LINUX/small/pidgin_key](http://news.softpedia.com/images/extra/LINUX/small/pidgin_key)
[http://mirrors.kernel.org/ubuntu/pool/main/d/dbus-glib/libdbus-glib-1-2_0.74-2_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/d/dbus-glib/libdbus-glib-1-2_0.74-2_i386.deb)
[http://cz.archive.ubuntu.com/ubuntu/pool/main/d/dbus-glib/libdbus-glib-1-2_0.74-2_i386.deb](http://cz.archive.ubuntu.com/ubuntu/pool/main/d/dbus-glib/libdbus-glib-1-2_0.74-2_i386.deb)
[http://launchpadlibrarian.net/8744058/libdbus-glib-1-2_0.74-1_lpia.deb](http://launchpadlibrarian.net/8744058/libdbus-glib-1-2_0.74-1_lpia.deb)
[http://launchpadlibrarian.net/13424330/libdbus-glib-1-2_0.74-2_lpia.deb](http://launchpadlibrarian.net/13424330/libdbus-glib-1-2_0.74-2_lpia.deb)
[http://launchpadlibrarian.net/24329633/pidgin_2.5.2-0ubuntu1%7Ehardy2_lpia.deb](http://launchpadlibrarian.net/24329633/pidgin_2.5.2-0ubuntu1%7Ehardy2_lpia.deb)
[http://launchpadlibrarian.net/24329633/pidgin_2.5.2-0ubuntu1%7Ehardy2_lpia.deb](http://launchpadlibrarian.net/24329633/pidgin_2.5.2-0ubuntu1%7Ehardy2_lpia.deb)
[http://launchpadlibrarian.net/21247901/perl_5.8.8-12ubuntu0.4_lpia.deb](http://launchpadlibrarian.net/21247901/perl_5.8.8-12ubuntu0.4_lpia.deb)
[http://launchpadlibrarian.net/21247900/perl-base_5.8.8-12ubuntu0.4_lpia.deb](http://launchpadlibrarian.net/21247900/perl-base_5.8.8-12ubuntu0.4_lpia.deb)


those were my last downloads i can see that i downloaded some jaunty packages while am using ubuntu hardy,i cant remeber which one's i installed

---

### Post by ejlal on 2009-06-24
ejlal@TOSHIBA:~$ dpkg -l libperl5.8
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                      Version                   Description
+++-=========================-========================
ii  libperl5.8                5.8.8-12                  Shared Perl library
ejlal@TOSHIBA:~$ dpkg -l perl
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                      Version                   Description
+++-=========================-========================
ejlal@TOSHIBA:~$

---

### Post by ejlal on 2009-06-24
i noticed there is an option to fix broken packages in synaptic,do u recommend using it?!!

---

### Post by ejlal on 2009-06-24
> **ejlal said:**
> i noticed there is an option to fix broken packages in synaptic,do u recommend using it?!!
anybody?!!

---

### Post by ejlal on 2009-06-24
> **ejlal said:**
> ejlal@TOSHIBA:~$ sudo apt-get check
[sudo] password for ejlal: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
  libperl5.8: Depends: perl-base (= 5.8.8-12) but 5.8.8-12ubuntu0.4 is installed
  perl: Depends: perl-base (= 5.8.8-12) but 5.8.8-12ubuntu0.4 is installed
E: Unmet dependencies. Try using -f.
am being over cautious here. i know its kinda too late but, i learn as i go.
am thinking ; regarding to the above quotation i understand i have unmet dependencies.....my question is ;would it help if i downloaded the missing packages manually?

---

### Post by scrooge_74 on 2009-06-24
First: breath take it easy, we reply when we have time (or in my case came online).

If you have broken dependencies you could follow the system advice and do a:

sudo apt-get -f install

Second: You need to bring yourself to understand that installing things in Linux is not like in Windowds that you need to hunt down stuff online to download to then install things. In synaptic you will find 99.9% of stuff you need and it will take care of the dependencies by itself no need to download things by yourself.

The only times you need to go outside of Synaptic to download and install something is when you need to use some application that is not supported by Debian/Ubuntu because is new or is a very specific task you need to accomplish.

So again stick to Synaptic, read the help pages in help.ubuntu.com so you can get a better grasp of the system.

Your problems are not new is just another case of comming from a Windows world (I had your problem at one time also), in fact I would go out looking for stuff in google only to find out that there was a package in synaptic for it.

---

### Post by ejlal on 2009-06-24
u will probably hate me,but i have got to ask this: if i follow the system advice the 
sudo apt-get -f install, 
the system asks to remove 330 packages!!! wont that wipe program i got??? how will i be able to get it back?

---

### Post by scrooge_74 on 2009-06-24
lol what exactly you tried to do? Did you tried to remove a package and is trying to do remove Ubuntu or gnome?

See if you can retrace your steps inside synaptic and un-mark all the changes you have mark.

You are going to make me read back all the stuff people posted

---

### Post by Chalfont on 2009-06-24
Hi Ej
I am also using the Ubuntu netbook remix and having terrible time trying to get some sound out of my browser.

Interesting though the previous poster was just saying that everything is available, I have had to run loads of commands to load stuff which wasn't available, so maybe the netbook version doesn't have all this software available that the Linux gurus are all saying is available, you have to add it all manually.

So far I am really strugling with this, sounds like you are too!

---

### Post by scrooge_74 on 2009-06-24
> **Chalfont said:**
> Hi Ej
I am also using the Ubuntu netbook remix and having terrible time trying to get some sound out of my browser.

Interesting though the previous poster was just saying that everything is available, I have had to run loads of commands to load stuff which wasn't available, so maybe the netbook version doesn't have all this software available that the Linux gurus are all saying is available, you have to add it all manually.

So far I am really strugling with this, sounds like you are too!

That would mean you need to add repositories not add stuff manually.

[https://help.ubuntu.com/9.04/add-applications/C/adding-repos.html](https://help.ubuntu.com/9.04/add-applications/C/adding-repos.html)


ejlal, I think by trying to remove pidgin it is trying to remove the entire Gnome desktop

---

### Post by ejlal on 2009-06-24
> **scrooge_74 said:**
> lol what exactly you tried to do? Did you tried to remove a package and is trying to do remove Ubuntu or gnome?

See if you can retrace your steps inside synaptic and un-mark all the changes you have mark.

You are going to make me read back all the stuff people posted
  plzzzzzzzzzzzzzzzzzzzzzz do read all the post:( ths was a very very very long day!

---

### Post by ejlal on 2009-06-24
> **Chalfont said:**
> 
So far I am really strugling with this, sounds like you are too!
i could use some company :)

---

### Post by scrooge_74 on 2009-06-24
From what I read, try to unmark all the changes in synaptic first and then try to update the system again. Then you will try to upgrade stuff, but always from inside synaptic

There still a few other things you can do from the command line like deleting downloaded packages, but I rather you dont get to do that.


By the way I see you post to often like every other minute dont giving people time to read your stuff. You could get an infraction from the Admins or at least a verbal warning about it

---

### Post by ejlal on 2009-06-24
> **scrooge_74 said:**
> 
ejlal, I think by trying to remove pidgin it is trying to remove the entire Gnome desktop
yeah  i know very stupid.:D

---

### Post by Ayuthia on 2009-06-24
Ok.  It looks like libperl is supposed to be at 5.8.8-12ubuntu0.4 and your dpkg -l result shows 5.8.8-12.  It does not look like you have perl installed yet either.  Let's first see if we can find the right package that you will need to install.  The current available package is this one:
[http://security.ubuntu.com/ubuntu/pool/main/p/perl/libperl5.8_5.8.8-12ubuntu0.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/perl/libperl5.8_5.8.8-12ubuntu0.4_i386.deb)

However, we might want to check and see if there were other packages installed in the past.  Can you post the results of the following:
```
cat /var/log/dpkg.log|grep perl
```This will return all the packages installed that contain the word perl.  This will help us see if perl was ever installed or not and if any other versions of libperl were installed.

My thought is that we will try to install the package from the above link by doing:
```
sudo dpkg -i libperl5.8_5.8.8-12ubuntu0.4_i386.deb
```but we should check and see what has been done to all the perl packages first.

---

### Post by snowpine on 2009-06-24
Part of your problem appears to be that you are mixing i386, amd64, and lpia packages. These are three different architectures; you can't mix and match. The command 'uname -a' will tell you which kernel you are using, so you can choose the correct packages for your architecture.

That being said, at this stage in the game, you should not be downloading random packages from the internet. Install applications from the ubuntu repositories (using the command line, add/remove programs, or synaptic) and you will automatically get the correct, tested, trusted package.

---

### Post by Ayuthia on 2009-06-24
> **ejlal said:**
> yeah  i know very stupid.:D

I am not for sure if it is because you are removing pidgin or if it is because the perl packages are broken so it is going to remove all the packages that are dependent on those perl packages.  In theory, those packages won't work because the perl package is broken.  However, the version that is currently out there is most likely ok for them but the rules in the system say that they are not.

---

### Post by ejlal on 2009-06-24
ejlal@TOSHIBA:~$ cat /var/log/dpkg.log|grep perl
2008-08-29 17:18:42 install perl-base <none> 5.8.8-12
2008-08-29 17:18:42 status half-installed perl-base 5.8.8-12
2008-08-29 17:18:42 status unpacked perl-base 5.8.8-12
2008-08-29 17:18:42 status unpacked perl-base 5.8.8-12
2008-08-29 17:18:42 configure perl-base 5.8.8-12 5.8.8-12
2008-08-29 17:18:42 status unpacked perl-base 5.8.8-12
2008-08-29 17:18:42 status half-configured perl-base 5.8.8-12
2008-08-29 17:18:42 status installed perl-base 5.8.8-12
2008-08-29 17:18:45 install liblocale-gettext-perl <none> 1.05-2ubuntu1
2008-08-29 17:18:45 status half-installed liblocale-gettext-perl 1.05-2ubuntu1
2008-08-29 17:18:45 status unpacked liblocale-gettext-perl 1.05-2ubuntu1
2008-08-29 17:18:45 status unpacked liblocale-gettext-perl 1.05-2ubuntu1
2008-08-29 17:18:46 install libtext-charwidth-perl <none> 0.04-4build1
2008-08-29 17:18:46 status half-installed libtext-charwidth-perl 0.04-4build1
2008-08-29 17:18:46 status unpacked libtext-charwidth-perl 0.04-4build1
2008-08-29 17:18:46 status unpacked libtext-charwidth-perl 0.04-4build1
2008-08-29 17:18:46 install libtext-iconv-perl <none> 1.4-3
2008-08-29 17:18:46 status half-installed libtext-iconv-perl 1.4-3
2008-08-29 17:18:46 status unpacked libtext-iconv-perl 1.4-3
2008-08-29 17:18:46 status unpacked libtext-iconv-perl 1.4-3
2008-08-29 17:18:46 install libtext-wrapi18n-perl <none> 0.06-5
2008-08-29 17:18:46 status half-installed libtext-wrapi18n-perl 0.06-5
2008-08-29 17:18:46 status unpacked libtext-wrapi18n-perl 0.06-5
2008-08-29 17:18:46 status unpacked libtext-wrapi18n-perl 0.06-5
2008-08-29 17:18:47 upgrade perl-base 5.8.8-12 5.8.8-12
2008-08-29 17:18:47 status half-configured perl-base 5.8.8-12
2008-08-29 17:18:47 status unpacked perl-base 5.8.8-12
2008-08-29 17:18:47 status half-installed perl-base 5.8.8-12
2008-08-29 17:18:47 status half-installed perl-base 5.8.8-12
2008-08-29 17:18:47 status unpacked perl-base 5.8.8-12
2008-08-29 17:18:47 status unpacked perl-base 5.8.8-12
2008-08-29 17:18:48 configure perl-base 5.8.8-12 5.8.8-12
2008-08-29 17:18:48 status unpacked perl-base 5.8.8-12
2008-08-29 17:18:48 status half-configured perl-base 5.8.8-12
2008-08-29 17:18:48 status installed perl-base 5.8.8-12
2008-08-29 17:18:48 configure libtext-iconv-perl 1.4-3 1.4-3
2008-08-29 17:18:48 status unpacked libtext-iconv-perl 1.4-3
2008-08-29 17:18:48 status half-configured libtext-iconv-perl 1.4-3
2008-08-29 17:18:48 status installed libtext-iconv-perl 1.4-3
2008-08-29 17:18:49 configure liblocale-gettext-perl 1.05-2ubuntu1 1.05-2ubuntu1
2008-08-29 17:18:49 status unpacked liblocale-gettext-perl 1.05-2ubuntu1
2008-08-29 17:18:49 status half-configured liblocale-gettext-perl 1.05-2ubuntu1
2008-08-29 17:18:49 status installed liblocale-gettext-perl 1.05-2ubuntu1
2008-08-29 17:18:49 configure libtext-charwidth-perl 0.04-4build1 0.04-4build1
2008-08-29 17:18:49 status unpacked libtext-charwidth-perl 0.04-4build1
2008-08-29 17:18:49 status half-configured libtext-charwidth-perl 0.04-4build1
2008-08-29 17:18:49 status installed libtext-charwidth-perl 0.04-4build1
2008-08-29 17:18:49 configure libtext-wrapi18n-perl 0.06-5 0.06-5
2008-08-29 17:18:49 status unpacked libtext-wrapi18n-perl 0.06-5
2008-08-29 17:18:49 status half-configured libtext-wrapi18n-perl 0.06-5
2008-08-29 17:18:49 status installed libtext-wrapi18n-perl 0.06-5
2008-08-29 17:20:20 install perl-modules <none> 5.8.8-12
2008-08-29 17:20:20 status half-installed perl-modules 5.8.8-12
2008-08-29 17:20:20 status unpacked perl-modules 5.8.8-12
2008-08-29 17:20:20 status unpacked perl-modules 5.8.8-12
2008-08-29 17:20:20 install perl <none> 5.8.8-12
2008-08-29 17:20:20 status half-installed perl 5.8.8-12
2008-08-29 17:20:20 status unpacked perl 5.8.8-12
2008-08-29 17:20:20 status unpacked perl 5.8.8-12
2008-08-29 17:20:26 configure perl-modules 5.8.8-12 5.8.8-12
2008-08-29 17:20:26 status unpacked perl-modules 5.8.8-12
2008-08-29 17:20:26 status unpacked perl-modules 5.8.8-12
2008-08-29 17:20:26 status half-configured perl-modules 5.8.8-12
2008-08-29 17:20:26 status installed perl-modules 5.8.8-12
2008-08-29 17:20:26 configure perl 5.8.8-12 5.8.8-12
2008-08-29 17:20:26 status unpacked perl 5.8.8-12
2008-08-29 17:20:26 status half-configured perl 5.8.8-12
2008-08-29 17:20:26 status installed perl 5.8.8-12
2008-08-29 17:20:49 install liburi-perl <none> 1.35.dfsg.1-1
2008-08-29 17:20:49 status half-installed liburi-perl 1.35.dfsg.1-1
2008-08-29 17:20:49 status unpacked liburi-perl 1.35.dfsg.1-1
2008-08-29 17:20:49 status unpacked liburi-perl 1.35.dfsg.1-1
2008-08-29 17:20:49 install libhtml-tagset-perl <none> 3.10-2
2008-08-29 17:20:49 status half-installed libhtml-tagset-perl 3.10-2
2008-08-29 17:20:49 status unpacked libhtml-tagset-perl 3.10-2
2008-08-29 17:20:49 status unpacked libhtml-tagset-perl 3.10-2
2008-08-29 17:20:49 install libhtml-parser-perl <none> 3.56-1
2008-08-29 17:20:49 status half-installed libhtml-parser-perl 3.56-1
2008-08-29 17:20:49 status unpacked libhtml-parser-perl 3.56-1
2008-08-29 17:20:49 status unpacked libhtml-parser-perl 3.56-1
2008-08-29 17:20:49 install libhtml-tree-perl <none> 3.23-1
2008-08-29 17:20:49 status half-installed libhtml-tree-perl 3.23-1
2008-08-29 17:20:49 status unpacked libhtml-tree-perl 3.23-1
2008-08-29 17:20:49 status unpacked libhtml-tree-perl 3.23-1
2008-08-29 17:20:49 install libwww-perl <none> 5.808-1
2008-08-29 17:20:49 status half-installed libwww-perl 5.808-1
2008-08-29 17:20:49 status unpacked libwww-perl 5.808-1
2008-08-29 17:20:49 status unpacked libwww-perl 5.808-1
2008-08-29 17:20:49 install libxml-parser-perl <none> 2.34-4.3
2008-08-29 17:20:49 status half-installed libxml-parser-perl 2.34-4.3
2008-08-29 17:20:49 status unpacked libxml-parser-perl 2.34-4.3
2008-08-29 17:20:49 status unpacked libxml-parser-perl 2.34-4.3
2008-08-29 17:20:49 install libxml-twig-perl <none> 1:3.32-1
2008-08-29 17:20:49 status half-installed libxml-twig-perl 1:3.32-1
2008-08-29 17:20:49 status unpacked libxml-twig-perl 1:3.32-1
2008-08-29 17:20:49 status unpacked libxml-twig-perl 1:3.32-1
2008-08-29 17:20:49 install libnet-dbus-perl <none> 0.33.5-1
2008-08-29 17:20:49 status half-installed libnet-dbus-perl 0.33.5-1
2008-08-29 17:20:49 status unpacked libnet-dbus-perl 0.33.5-1
2008-08-29 17:20:49 status unpacked libnet-dbus-perl 0.33.5-1
2008-08-29 17:20:51 install libperl5.8 <none> 5.8.8-12
2008-08-29 17:20:51 status half-installed libperl5.8 5.8.8-12
2008-08-29 17:20:51 status unpacked libperl5.8 5.8.8-12
2008-08-29 17:20:51 status unpacked libperl5.8 5.8.8-12
2008-08-29 17:22:43 install libcairo-perl <none> 1.043-1
2008-08-29 17:22:43 status half-installed libcairo-perl 1.043-1
2008-08-29 17:22:43 status unpacked libcairo-perl 1.043-1
2008-08-29 17:22:43 status unpacked libcairo-perl 1.043-1
2008-08-29 17:22:43 install libglib-perl <none> 1:1.161-1
2008-08-29 17:22:43 status half-installed libglib-perl 1:1.161-1
2008-08-29 17:22:43 status unpacked libglib-perl 1:1.161-1
2008-08-29 17:22:43 status unpacked libglib-perl 1:1.161-1
2008-08-29 17:22:43 install libgtk2-perl <none> 1:1.161-1
2008-08-29 17:22:43 status half-installed libgtk2-perl 1:1.161-1
2008-08-29 17:22:43 status unpacked libgtk2-perl 1:1.161-1
2008-08-29 17:22:43 status unpacked libgtk2-perl 1:1.161-1
2008-08-29 17:22:43 install libgnome2-canvas-perl <none> 1.002-1+b1ubuntu1
2008-08-29 17:22:43 status half-installed libgnome2-canvas-perl 1.002-1+b1ubuntu1
2008-08-29 17:22:44 status unpacked libgnome2-canvas-perl 1.002-1+b1ubuntu1
2008-08-29 17:22:44 status unpacked libgnome2-canvas-perl 1.002-1+b1ubuntu1
2008-08-29 17:22:44 install libgnome2-vfs-perl <none> 1.080-1
2008-08-29 17:22:44 status half-installed libgnome2-vfs-perl 1.080-1
2008-08-29 17:22:44 status unpacked libgnome2-vfs-perl 1.080-1
2008-08-29 17:22:44 status unpacked libgnome2-vfs-perl 1.080-1
2008-08-29 17:22:44 install libgnome2-perl <none> 1.040-1
2008-08-29 17:22:44 status half-installed libgnome2-perl 1.040-1
2008-08-29 17:22:44 status unpacked libgnome2-perl 1.040-1
2008-08-29 17:22:44 status unpacked libgnome2-perl 1.040-1
2008-08-29 17:29:22 configure liburi-perl 1.35.dfsg.1-1 1.35.dfsg.1-1
2008-08-29 17:29:22 status unpacked liburi-perl 1.35.dfsg.1-1
2008-08-29 17:29:22 status half-configured liburi-perl 1.35.dfsg.1-1
2008-08-29 17:29:22 status installed liburi-perl 1.35.dfsg.1-1
2008-08-29 17:29:22 configure libhtml-tagset-perl 3.10-2 3.10-2
2008-08-29 17:29:22 status unpacked libhtml-tagset-perl 3.10-2
2008-08-29 17:29:22 status half-configured libhtml-tagset-perl 3.10-2
2008-08-29 17:29:22 status installed libhtml-tagset-perl 3.10-2
2008-08-29 17:29:22 configure libhtml-parser-perl 3.56-1 3.56-1
2008-08-29 17:29:22 status unpacked libhtml-parser-perl 3.56-1
2008-08-29 17:29:22 status half-configured libhtml-parser-perl 3.56-1
2008-08-29 17:29:22 status installed libhtml-parser-perl 3.56-1
2008-08-29 17:29:22 configure libhtml-tree-perl 3.23-1 3.23-1
2008-08-29 17:29:22 status unpacked libhtml-tree-perl 3.23-1
2008-08-29 17:29:22 status half-configured libhtml-tree-perl 3.23-1
2008-08-29 17:29:22 status installed libhtml-tree-perl 3.23-1
2008-08-29 17:29:22 configure libwww-perl 5.808-1 5.808-1
2008-08-29 17:29:22 status unpacked libwww-perl 5.808-1
2008-08-29 17:29:22 status half-configured libwww-perl 5.808-1
2008-08-29 17:29:22 status installed libwww-perl 5.808-1
2008-08-29 17:29:22 configure libxml-parser-perl 2.34-4.3 2.34-4.3
2008-08-29 17:29:22 status unpacked libxml-parser-perl 2.34-4.3
2008-08-29 17:29:22 status half-configured libxml-parser-perl 2.34-4.3
2008-08-29 17:29:22 status installed libxml-parser-perl 2.34-4.3
2008-08-29 17:29:22 configure libxml-twig-perl 1:3.32-1 1:3.32-1
2008-08-29 17:29:22 status unpacked libxml-twig-perl 1:3.32-1
2008-08-29 17:29:22 status half-configured libxml-twig-perl 1:3.32-1
2008-08-29 17:29:22 status installed libxml-twig-perl 1:3.32-1
2008-08-29 17:29:22 configure libnet-dbus-perl 0.33.5-1 0.33.5-1
2008-08-29 17:29:22 status unpacked libnet-dbus-perl 0.33.5-1
2008-08-29 17:29:22 status half-configured libnet-dbus-perl 0.33.5-1
2008-08-29 17:29:22 status installed libnet-dbus-perl 0.33.5-1
2008-08-29 17:29:23 configure libperl5.8 5.8.8-12 5.8.8-12
2008-08-29 17:29:23 status unpacked libperl5.8 5.8.8-12
2008-08-29 17:29:23 status half-configured libperl5.8 5.8.8-12
2008-08-29 17:29:23 status installed libperl5.8 5.8.8-12
2008-08-29 17:32:33 configure libcairo-perl 1.043-1 1.043-1
2008-08-29 17:32:33 status unpacked libcairo-perl 1.043-1
2008-08-29 17:32:33 status half-configured libcairo-perl 1.043-1
2008-08-29 17:32:33 status installed libcairo-perl 1.043-1
2008-08-29 17:32:34 configure libglib-perl 1:1.161-1 1:1.161-1
2008-08-29 17:32:34 status unpacked libglib-perl 1:1.161-1
2008-08-29 17:32:34 status half-configured libglib-perl 1:1.161-1
2008-08-29 17:32:34 status installed libglib-perl 1:1.161-1
2008-08-29 17:32:34 configure libgtk2-perl 1:1.161-1 1:1.161-1
2008-08-29 17:32:34 status unpacked libgtk2-perl 1:1.161-1
2008-08-29 17:32:34 status half-configured libgtk2-perl 1:1.161-1
2008-08-29 17:32:34 status installed libgtk2-perl 1:1.161-1
2008-08-29 17:32:34 configure libgnome2-canvas-perl 1.002-1+b1ubuntu1 1.002-1+b1ubuntu1
2008-08-29 17:32:34 status unpacked libgnome2-canvas-perl 1.002-1+b1ubuntu1
2008-08-29 17:32:34 status half-configured libgnome2-canvas-perl 1.002-1+b1ubuntu1
2008-08-29 17:32:34 status installed libgnome2-canvas-perl 1.002-1+b1ubuntu1
2008-08-29 17:37:18 configure libgnome2-vfs-perl 1.080-1 1.080-1
2008-08-29 17:37:18 status unpacked libgnome2-vfs-perl 1.080-1
2008-08-29 17:37:18 status half-configured libgnome2-vfs-perl 1.080-1
2008-08-29 17:37:18 status installed libgnome2-vfs-perl 1.080-1
2008-08-29 17:37:18 configure libgnome2-perl 1.040-1 1.040-1
2008-08-29 17:37:18 status unpacked libgnome2-perl 1.040-1
2008-08-29 17:37:18 status half-configured libgnome2-perl 1.040-1
2008-08-29 17:37:18 status installed libgnome2-perl 1.040-1
2009-06-19 02:46:45 install libsdl-perl <none> 1.20.3dfsg-2.1
2009-06-19 02:46:45 status half-installed libsdl-perl 1.20.3dfsg-2.1
2009-06-19 02:46:45 status unpacked libsdl-perl 1.20.3dfsg-2.1
2009-06-19 02:46:45 status unpacked libsdl-perl 1.20.3dfsg-2.1
2009-06-19 02:46:50 configure libsdl-perl 1.20.3dfsg-2.1 1.20.3dfsg-2.1
2009-06-19 02:46:50 status unpacked libsdl-perl 1.20.3dfsg-2.1
2009-06-19 02:46:50 status half-configured libsdl-perl 1.20.3dfsg-2.1
2009-06-19 02:46:50 status installed libsdl-perl 1.20.3dfsg-2.1
2009-06-24 14:39:44 upgrade perl-base 5.8.8-12 5.8.8-12ubuntu0.4
2009-06-24 14:39:44 status half-configured perl-base 5.8.8-12
2009-06-24 14:39:44 status unpacked perl-base 5.8.8-12
2009-06-24 14:39:44 status half-installed perl-base 5.8.8-12
2009-06-24 14:39:44 status half-installed perl-base 5.8.8-12
2009-06-24 14:39:45 status unpacked perl-base 5.8.8-12ubuntu0.4
2009-06-24 14:39:45 status unpacked perl-base 5.8.8-12ubuntu0.4
2009-06-24 14:39:45 configure perl-base 5.8.8-12ubuntu0.4 5.8.8-12ubuntu0.4
2009-06-24 14:39:45 status unpacked perl-base 5.8.8-12ubuntu0.4
2009-06-24 14:39:45 status half-configured perl-base 5.8.8-12ubuntu0.4
2009-06-24 14:39:45 status installed perl-base 5.8.8-12ubuntu0.4
ejlal@TOSHIBA:~$

---

### Post by Ayuthia on 2009-06-24
> **ejlal said:**
> ejlal@TOSHIBA:~$ cat /var/log/dpkg.log|grep perl
2008-08-29 17:18:42 install perl-base <none> 5.8.8-12
2008-08-29 17:18:42 status half-installed perl-base 5.8.8-12
2008-08-29 17:18:42 status unpacked perl-base 5.8.8-12
2008-08-29 17:18:42 status unpacked perl-base 5.8.8-12
2008-08-29 17:18:42 configure perl-base 5.8.8-12 5.8.8-12
2008-08-29 17:18:42 status unpacked perl-base 5.8.8-12
2008-08-29 17:18:42 status half-configured perl-base 5.8.8-12
2008-08-29 17:18:42 status installed perl-base 5.8.8-12
2008-08-29 17:18:47 upgrade perl-base 5.8.8-12 5.8.8-12
2008-08-29 17:18:47 status half-configured perl-base 5.8.8-12
2008-08-29 17:18:47 status unpacked perl-base 5.8.8-12
2008-08-29 17:18:47 status half-installed perl-base 5.8.8-12
2008-08-29 17:18:47 status half-installed perl-base 5.8.8-12
2008-08-29 17:18:47 status unpacked perl-base 5.8.8-12
2008-08-29 17:18:47 status unpacked perl-base 5.8.8-12
2008-08-29 17:18:48 configure perl-base 5.8.8-12 5.8.8-12
2008-08-29 17:18:48 status unpacked perl-base 5.8.8-12
2008-08-29 17:18:48 status half-configured perl-base 5.8.8-12
2008-08-29 17:18:48 status installed perl-base 5.8.8-12
2008-08-29 17:20:20 install perl-modules <none> 5.8.8-12
2008-08-29 17:20:20 status half-installed perl-modules 5.8.8-12
2008-08-29 17:20:20 status unpacked perl-modules 5.8.8-12
2008-08-29 17:20:20 status unpacked perl-modules 5.8.8-12
2008-08-29 17:20:20 install perl <none> 5.8.8-12
2008-08-29 17:20:20 status half-installed perl 5.8.8-12
2008-08-29 17:20:20 status unpacked perl 5.8.8-12
2008-08-29 17:20:20 status unpacked perl 5.8.8-12
2008-08-29 17:20:26 configure perl-modules 5.8.8-12 5.8.8-12
2008-08-29 17:20:26 status unpacked perl-modules 5.8.8-12
2008-08-29 17:20:26 status unpacked perl-modules 5.8.8-12
2008-08-29 17:20:26 status half-configured perl-modules 5.8.8-12
2008-08-29 17:20:26 status installed perl-modules 5.8.8-12
2008-08-29 17:20:26 configure perl 5.8.8-12 5.8.8-12
2008-08-29 17:20:26 status unpacked perl 5.8.8-12
2008-08-29 17:20:26 status half-configured perl 5.8.8-12
2008-08-29 17:20:26 status installed perl 5.8.8-12
2008-08-29 17:20:51 install libperl5.8 <none> 5.8.8-12
2008-08-29 17:20:51 status half-installed libperl5.8 5.8.8-12
2008-08-29 17:20:51 status unpacked libperl5.8 5.8.8-12
2008-08-29 17:20:51 status unpacked libperl5.8 5.8.8-12
2008-08-29 17:29:23 configure libperl5.8 5.8.8-12 5.8.8-12
2008-08-29 17:29:23 status unpacked libperl5.8 5.8.8-12
2008-08-29 17:29:23 status half-configured libperl5.8 5.8.8-12
2008-08-29 17:29:23 status installed libperl5.8 5.8.8-12
2009-06-24 14:39:44 upgrade perl-base 5.8.8-12 5.8.8-12ubuntu0.4
2009-06-24 14:39:44 status half-configured perl-base 5.8.8-12
2009-06-24 14:39:44 status unpacked perl-base 5.8.8-12
2009-06-24 14:39:44 status half-installed perl-base 5.8.8-12
2009-06-24 14:39:44 status half-installed perl-base 5.8.8-12
2009-06-24 14:39:45 status unpacked perl-base 5.8.8-12ubuntu0.4
2009-06-24 14:39:45 status unpacked perl-base 5.8.8-12ubuntu0.4
2009-06-24 14:39:45 configure perl-base 5.8.8-12ubuntu0.4 5.8.8-12ubuntu0.4
2009-06-24 14:39:45 status unpacked perl-base 5.8.8-12ubuntu0.4
2009-06-24 14:39:45 status half-configured perl-base 5.8.8-12ubuntu0.4
2009-06-24 14:39:45 status installed perl-base 5.8.8-12ubuntu0.4
ejlal@TOSHIBA:~$

Here is the history of the perl-base/libperl/perl packages that is in the log.  The options look like you can either downgrade perl-base back down to 5.8.8-12 or you can upgrade libperl and perl to 5.8.8-12ubuntu0.4.

If you try to go to 5.8.8-12ubuntu0.4, it looks like the packages can be found here:
[http://security.ubuntu.com/ubuntu/pool/main/p/perl/perl_5.8.8-12ubuntu0.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/perl/perl_5.8.8-12ubuntu0.4_i386.deb)

[http://security.ubuntu.com/ubuntu/pool/main/p/perl/libperl5.8_5.8.8-12ubuntu0.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/perl/libperl5.8_5.8.8-12ubuntu0.4_i386.deb)

If you are able to find perl-base 5.8.8-12, you might be better off just because it looks like you might have installed that originally.

If you are going to upgrade, you might need to do the sudo dpkg -i instead of using aptitude/apt-get/synaptic.

---

### Post by scrooge_74 on 2009-06-24
He really needs to downgrade back to begining and stop ramdomly downloading packages which is the base of his problems. He needs to stick with synaptic and not download more things by hand.

I'm about to suggest he just goes ahead with the force install and if he cant run gnome when he is back he should just do a sudo apt-get remove ubuntu-desktop and latter a sudo apt-get install ubuntu-desktop.

Maybe that will end his broken dependencies and let him start a new (or just install from scratch)

---

### Post by ejlal on 2009-06-25
> **Ayuthia said:**
> The options look like you can either downgrade perl-base back down to 5.8.8-12 or you can upgrade libperl and perl to 5.8.8-12ubuntu0.4.
If you are going to upgrade, you might need to do the sudo dpkg -i instead of using aptitude/apt-get/synaptic.

thank u sooooooooooooooo much Ayuthia 
i upgraded  perl and libperl to 5.8.812-ubuntu0.4 using sudo dpkg -i there was dependency error with libperl ( i dont know how) but there was some updates in update manager  once iinstalled those it fanished.
now i dont have any errors or broken pachages.

thank u guys for the responses.

---

### Post by pablobm on 2009-06-25
> What are you trying to accomplish? Update so you can connect to YAhoo Messenger?

If the answer is yes check this link: [http://www.pidgin.im/download/ubuntu/](http://www.pidgin.im/download/ubuntu/)

That helped me to get my yahoo in pidging up and running again.  But smtgh is bugging me. Now, every time I update my sources I get the following message: 

> GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3F2A5EE4B796B6FE

I tried

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \ 67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8
```

and I also imported the [[COLOR="Blue"]_key_[/COLOR]]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x7FB8BEE0A1F196A8") on software sources from the gui.  I got this key from [[COLOR="Blue"]_launchpad.net_[/COLOR]]("https://launchpad.net/~pidgin-developers/+archive/ppa")

I am still getting the error. What I am doing wrong?

---

