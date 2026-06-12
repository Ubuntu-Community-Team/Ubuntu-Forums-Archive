---
title: "Where does Software Center install files?"
date: 2010-10-06
forum: New to Ubuntu
---

### Post by Swiftslide on 2010-10-06
Is it different for each application, or is there a Program-Files-esque folder where applications tend to be installed? I've installed Banshee music player and am trying to listen to some online radio, but can't find Banshee to open the PLS file with.
Any help would be much appreciated :)

---

### Post by sanderd17 on 2010-10-06
you mean you want to open a file, you right click, choose an application and bahnsee is not in the list?

Well, just type "bahnsee" in the custom command field, that should work.

If you want to know where an application is installed. You can always ask ubuntu
```

which XXX

```

With XXX the app name.

Normally they are in one of the directories of the PATH variable.

```

$PATH

```

---

### Post by CandidMan on 2010-10-06
On Ubuntu, a program like Banshee should in Applications>Sound & Video, located at the top left of the desktop

Just beat by sanderd17 :-)

---

### Post by oldos2er on 2010-10-06
I don't know about Software Center, but you can see this information in Synaptic Package Manager; right-click on an installed package, Properties, Installed Files. Or in terminal, **dpkg -L <package name>**

---

### Post by garvinrick4 on 2010-10-06
Is this what you are looking for?

```
rick@rick-laptop:~$ cd /usr/share
rick@rick-laptop:/usr/share$ ls
aclocal                      im-switch
acpi-support                 indicator-application
adduser                      indicators
adium                        info
alacarte                     initramfs-tools
alsa                         initrd-tools
alsa-base                    initscripts
app-install                  insserv
application-registry         iptables
applications                 java
apport                       javascript
apps                         javazi
apt                          jockey
aptitude                     kde4
apturl                       keyrings
apt-xapian-index             language-selector
aspell                       language-support
avahi                        launchpad-integration
awk                          lftp
backgrounds                  libgksu
baobab                       libgnomekbd
base-files                   libgphoto2
base-passwd                  libgweather
binfmts                      libindicator
binfmt-support               liblouis
branding                     libparse-debianchangelog-perl
brasero                      librarian
brltty                       libsensors4
bug                          libthai
byobu                        libubuntuone
ca-certificates              libvisual-plugins-0.4
ca-certificates-java         lintian
cairo-dock                   linux-sound-base
calendar                     locale
ccsm                         locale-langpack
checkbox                     locales
cheese                       man
cli-common                   man-db
clutk                        media-player-info
command-not-found            menu
common-licenses              metacity
compiz                       mibs
compizconfig                 midi
computerjanitor              mime
computer-janitor             mime-info
consolefonts                 misc
console-setup                mobile-broadband-provider-info
consoletrans                 mono
couchdb                      mono-1.0
cups                         mousetweaks
dbus-1                       mozilla
debconf                      mplayer
debhelper                    mutter
debianutils                  myspell
defoma                       nano
desktopcouch                 nautilus
desktop-directories          nautilus-sendto
dict                         nautilus-share
dictionaries-common          netpbm
directfb-1.2.10              NetworkManager
djvu                         nm-applet
doc                          notify-osd
doc-base                     nvidia-common
dotnet                       omf
dpkg                         omf-langpack
e2fsprogs                    onboard
emacs                        opencc
empathy                      openoffice
enchant                      orca
eog                          os-prober
espeak-data                  pam
evince                       pam-configs
evolution                    perl
evolution-data-server-2.30   perl5
evolution-exchange           pitivi
example-content              pixmaps
ffmpeg                       pkgconfig
file                         pnm2ppa
file-roller                  polkit-1
fonts                        popularity-contest
foo2hiperc                   ppd
foo2hp                       ppp
foo2lava                     pulseaudio
foo2oak                      purple
foo2qpdl                     pycentral-data
foo2slx                      pygtk
foo2xqx                      pyshared
foo2zjs                      pyshared-data
foomatic                     python
games                        python-apt
gcalctool                    python-support
gconf                        qt4
GConf                        rdesktop
gconf-editor                 readline
gcr0                         recovery-mode
gdb                          rhythmbox
gdebi                        rsyslog
gdict-1.0                    samba
gdm                          sane
gedit-2                      screen
GeoIP                        screen-resolution-extra
ghostscript                  seahorse
gir-1.0                      sgml
gksu                         sgml-base
glade3                       sgml-data
glib-2.0                     shotwell
gnome                        simple-ccsm
gnome-2.0                    simple-scan
gnome-about                  smplayer
gnome-applets                snmp
gnome-background-properties  software-center
gnome-bluetooth              software-properties
gnome-control-center         sounds
gnome-dictionary             speech-dispatcher
gnome-doc-utils              ssl-cert
gnome-games                  subtitleripper
gnome-games-common           synaptic
gnome-keyring                system-config-printer
gnome-mag                    system-tools-backends-2.0
gnome-media                  sysv-rc
gnome-menus                  tabset
gnome-nettool                tcltk
gnome-panel                  telepathy
gnome-power-manager          terminfo
gnome-screensaver            themes
gnome-screenshot             tomboy
gnome-session                totem
gnome-settings-daemon        transmission
gnome-sound-recorder         ubufox
gnome-sudoku                 ubuntu-artwork
gnome-system-tools           ubuntu-docs
gnome-terminal               ubuntuone
gnome-utils                  ubuntuone-client
gnome-vpn-properties         ubuntu-sso-client
gnupg                        ufw
groff                        unattended-upgrades
grub                         une
gst-python                   unity
gstreamer-0.10               update-manager
gstreamer-properties         update-notifier
gtk-doc                      usb-creator
gtk-engines                  vim
gtkhtml-3.14                 vinagre
gtksourceview-2.0            vinagre-1
guile                        vino
gutenprint                   vlc
gvfs                         vte
gwibber                      w3m
hal                          webkit-1.0
hplip                        X11
hunspell                     xfig
hwdata                       xine
i18n                         xml
ibus                         xml-core
ibus-pinyin                  xmodmap
ibus-table                   xscreensaver
icons                        xsessions
idl                          xul-ext
ifupdown                     yelp
ImageMagick-6.5.7            zeitgeist
ImageMagick-6.6.2            zenity
images                       zoneinfo
rick@rick-laptop:/usr/share$ 
```
dpkg -L <package name> 
does work very well for individual paths to package as stated before me.

---

### Post by garvinrick4 on 2010-10-06
Or is this want you want:
System/Preferences to Main Menu and you can choose from installed items what you want to show up under Applications.
 Or right click in the farthest upper left hand corner you can put your pointer and choose
edit menus and the same package as Main Menu will open and choose items to be under
Applications.

---

### Post by Swiftslide on 2010-10-06
Thanks for all the detailed ideas. Ended up finding it in one of the $PATH directories, as per sanderd17's advice. But thanks to all of you for the tips.

---

