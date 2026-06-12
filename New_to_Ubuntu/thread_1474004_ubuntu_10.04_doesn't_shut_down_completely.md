---
title: "ubuntu 10.04 doesn't shut down completely"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by yamame on 2010-05-05
;) Please help me!  I installed Ubuntu 10.04 onto my wrap-top. But it didn't shut down after clean installing.  it stopped at ubutu logo and stay the same. doesn't shut down the screen.  Why?  I don't know how to fix it.  
 MY PC is Sotec DN 7010, with core 2 duo 1.66 GHz, 1GB memory, 80GB HDD.  Besides not shutting down, it works normally.  I checked the vallue of iso file before installing, and it's correct.  

 Anyone who knows how to fix,  please tell me about that.  

 Great thanks for reading.  ):P

---

### Post by spiky001 on 2010-05-05
you can use terminal to shutdown

```
sudo halt
```
```
sudo reboot
```

saying that there are alot of problems with this if you search the forums you will find lots of threads on it I dont know if they have found a fix, but those codes will help you turn off or reboot the system

---

### Post by yamame on 2010-05-05
Thanks a lot, Spiky001   I've already tried to do that.  means from console " sudo halt".  But the result isn't changed at all.  i hear the sound of HDD shutting down and then the display remains the same state with Ubuntu logo. Only the display never shuts down.  I love Ubuntu and have used it since version 6.x but this case never happened before.  so I don't know why at all.     Does anyone has had the same experience?  How did you fix it?  Could you tell me, please.

---

### Post by ranch hand on 2010-05-05
This is caused by the switch to plymouth.  You can get a patch for mountall from a ppa that will allow you to remove plymouth but this is not going to help this problem which is caused by libplymouth2.

You need libplymouth2.

You need to file a bug on this or find one that you can join;
```

ubuntu-bug libplymouth2

```
You will need an account with Launchpad which is easy to set up when you are auto connected to them using the code above.

That code will collect the needed information to transmit to LP.

10.04 is a great OS.  It is too bad that it is saddled with Plymouth.  I hope the devs get it straightened out.  They have done more in a short time than the Fedora devs have done since Fedora started using plymouth (not sure exactly when but it has been a while).

Plymouth works on a majority of hardware most of the time.  There is a large plurality of users, however, for which it just will not work.

Personally, I think that we will see plymouth never work correctly.  I think the basic code is just too flawed for it to work.  I am hoping that we see a reversion to xsplash and the related libs for booting up and shutting down.

The only way that will happen is if folks file bug reports.  The bug reports will, eventually, either get the problems fixed or plymouth dumped.

---

### Post by yamame on 2010-05-05
Great thanks for your kind advice, thanks for that, I could apport the bug to the Ubuntu Authorities.    I also joined Launchpad.  I appreciate you so much.  ):P

I wil wait for bug repaired.  Take care!!!!!!!!!! :p

---

### Post by DrKenobi on 2010-05-06
This also affects me, I also report the bug.

---

### Post by ranch hand on 2010-05-06
Bug reporting is how things get fixed.  Thank you very much.

I like to test the releases in development and 10.04 was a lot of fun.  We, of coarse, do not represent all the hardware out there.  Some bugs do not get fixed in time either but the system seems to work pretty well.

The squeaking wheel gets the grease.

I hope the devs do get this fixed.  What I find troubling is that all my test OS' are on one drive.  I had several variations of 10.04 on that drive.   Some upgraded (9.04>9.10>10.04 and 9.10>10.04) and some clean installs.  None of them, all on the same hardware, act the same.

The clean installs are definitely better but there is still variation.

---

### Post by phpmonkey on 2010-05-28
I've been having a similar issue on my twinhead twinmate e10 and found the following bug report:

[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/576204](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/576204)

This solution worked for me:

> 
sudo gedit /etc/default/grub

change : GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to : GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi=force"

sudo update-grub


---

### Post by LowSky on 2010-05-28
I'm having the same issue. I can't believe my computer is behaving like a machine from 1992. I shouldn't have to hold the power button to turn it off.

I tried the grub fix and doesn't work for me. I'm still having to hold the power button, like I did when I used Windows 3.11 and 95.

NOT COOL

---

### Post by solid000 on 2010-06-18
I too am having this problem in kubuntu 10.04.  Whenever I try to shutdown (via the menu icons or the console), the laptop instead reboots.  It is actually going all the way to the bios and then coming back up.  I tried the grub config above and that made no difference.

---

### Post by AlanB66 on 2010-07-14
phpmonkey,

Thanks! Solution posted in #8 worked for me, too.


Ooops, spoke too soon.
When I re-enabled my CIFS mounts in /etc/fstab, my shutdown is hanging again.

---

### Post by AlanB66 on 2010-07-15
I followed [these instructions]("http://ubuntuforums.org/showthread.php?p=8451352#post8451352") to the letter and it works. 

Caveat: Even though you will see the "*CIFS VFS: No response ...*" message, **_[COLOR="Red"]just wait [/COLOR]_**and it does shutdown/restart (whichever you chose) inside 3-5 minutes.

---

### Post by Inva on 2010-08-14
Hello, 

I have install ubuntu 10.04 inside windows7 and I have a problem. Ubuntu 10.04 doesn't shut-down completely. It freezes on shut down screen. I have tried to fix this problem using some of the advices you have given here, but it doesn't worked. Please, tell me what can I do because I don't want to use anytime the switch off button to switch off the screen.
My laptop is Dell INSPIRON 1750, dual core.

Best Regards.

---

### Post by amrypma on 2010-09-06
I've tried every thing in this thread so far and nothing seems to work. Has anyone got any more ideas?

-Summary of what follows below-
AAAAAAAAAAAARRRRRRRRRRRRRRRRRRRRRGGGGGGGGGGGGGGGGGGGG!
--

BEGIN WARNING

I've been banging my head against this all day and my frustration does show.

END WARNING

Here starts my rant.

I also have problems with shutting down. And while reading the bug report someone mentions removing the plymouth package. After all it only pretties up booting. How ever... Have you seen the *insane* amount of packages that are dependant on plymouth?!? I don't care one bit about how pretty my box boots and now I can't even remove a splash screen thingie? Seriously what went wrong? When did ubuntu become an apple clone?

Look at it!
apt-get remove -s plymouth
```

Reading package lists...
Building dependency tree...
Reading state information...
The following packages were automatically installed and are no longer required:
<snip>
Removed the list of packages that can be removed afterwards
</snip>
The following packages will be REMOVED
  acpi-support acpid agave aisleriot alsa-base alsa-utils anacron apache2
  apache2-mpm-prefork apache2.2-common apmd apparmor apparmor-utils apport
  apport-gtk apport-hooks-medibuntu aptdaemon apturl arduino asymptote at
  at-spi audacity avahi-daemon avahi-utils backstep bb beneath-a-steel-sky
  bins blcr-dkms bluetooth bluez bluez-cups brasero brasero-common brltty
  brltty-x11 bsd-mailx capplets-data checkbox checkbox-gtk chromium-browser
  chromium-browser-inspector chromium-codecs-ffmpeg cm-super cm-super-minimal
  cm-super-x11 compiz compiz-core compiz-fusion-plugins-extra
  compiz-fusion-plugins-main compiz-gnome compiz-plugins
  compizconfig-backend-gconf computer-janitor-gtk console-setup consolekit
  context couchdb-bin cron csound csound-gui csound-utils cups
  cups-driver-gutenprint dblatex dbus dbus-x11 default-jdk default-jre
  desktopcouch dict dict-devil dict-easton dict-elements dict-foldoc
  dict-gcide dict-hitchcock dict-jargon dict-stardic dict-vera dict-wn dictd
  dkms dmsetup dolphin drapes dssi-example-plugins dvipng e2fsprogs eclipse
  eclipse-jdt eclipse-pde eclipse-platform eclipse-plugin-cvs eclipse-rcp
  ekiga electricsheep empathy empathy-common enblend enfuse eog erlang-base
  erlang-crypto erlang-inets erlang-mnesia erlang-public-key
  erlang-runtime-tools erlang-ssl erlang-syntax-tools erlang-xmerl evince
  evolution evolution-couchdb evolution-data-server evolution-exchange
  evolution-indicator evolution-plugins evolution-webcal exim4 exim4-base
  exim4-daemon-light f-spot feynmf ffado-dbus-server ffado-mixer-qt4
  ffado-tools file-roller firefox firefox-branding firefox-gnome-support
  flashplugin-installer fluidsynth fluidsynth-dssi fontforge fontmatrix
  foo2zjs foomatic-db foomatic-db-engine fragmaster freecad freqtweak
  friendly-recovery ftp gcalctool gcdmaster gcj-4.4-jdk gcj-4.4-jre
  gcj-4.4-source gcj-jre gconf-defaults-service gconf-editor gconf2
  gconf2-common gdebi gdebi-kde gdm gdm-guest-session gedit genpo
  ghostscript-cups ghostscript-x gimp gimp-gap gimp-plugin-registry gimp-ufraw
  gir1.0-gconf-2.0 gksu glchess glines gnect gnibbles gnobots2 gnome-about
  gnome-applets gnome-applets-data gnome-bluetooth gnome-codec-install
  gnome-control-center gnome-disk-utility gnome-games gnome-games-common
  gnome-keyring gnome-mag gnome-mahjongg gnome-media gnome-media-common
  gnome-mplayer gnome-netstatus-applet gnome-nettool gnome-network-admin
  gnome-orca gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits
  gnome-power-manager gnome-raw-thumbnailer gnome-session gnome-session-bin
  gnome-settings-daemon gnome-sudoku gnome-system-monitor gnome-system-tools
  gnome-terminal gnome-terminal-data gnome-user-guide gnome-user-guide-en
  gnome-user-guide-nl gnome-user-share gnome-utils gnomine gnotravex gnotski
  gnuplot gnuplot-x11 gok googleearth groff gsfonts-x11
  gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gtali gtick gucharmap
  gvfs gvfs-backends gvfs-bin gwibber gwibber-service hal hostname hplip hugin
  hugin-tools hydrogen iagno ibus ibus-m17n ibus-table icedtea6-plugin
  icoutils ifupdown imagemagick indicator-applet indicator-applet-session
  indicator-me indicator-session initramfs-tools initscripts inkscape
  install-package irqbalance jack-rack jack-tools jackbeat jockey-common
  jockey-gtk kate kbd kbibtex kdebase-bin kdebase-runtime kdelibs-bin
  kdelibs4c2a kdelibs5 kdepimlibs5 kdesudo kfind kile konqueror
  konqueror-nsplugins konsole kpackagekit kubuntu-debug-installer labyrinth
  language-selector latex-beamer latex-cjk-all latex-cjk-chinese
  latex-cjk-common latex-cjk-japanese latex-cjk-japanese-wadalab
  latex-cjk-korean latex-cjk-thai latex-cjk-xcjk latex-sanskrit latex-xcolor
  latex2html latexmk lftp libaccess-bridge-java libaccess-bridge-java-jni
  libapache2-mod-fastcgi libapache2-mod-php5 libasound2-plugins libatspi1.0-0
  libaudio2 libavahi-qt3-1 libbonoboui2-0 libbrasero-media0 libcamel1.2-14
  libcoin60 libcomedi0 libcompizconfig0 libcouchdb-glib-1.0-2 libcryptui0
  libcsound64-5.2 libdbusmenu-qt2 libdesktopcouch-glib-1.0-2 libebackend1.2-0
  libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6
  libedataserver1.2-11 libedataserverui1.2-8 libegroupwise1.2-13
  libequinox-osgi-java libexchange-storage1.2-3 libfluidsynth1 libgcj10-awt
  libgcj10-dev libgconf2-4 libgconf2.0-cil libgconfmm-2.6-1c2 libgdata6
  libgdraw4 libgdu0 libggi-target-x libggi2 libgksu2-0 libglew1.5
  libgnome-desktop-2-17 libgnome-media0 libgnome-pilot2 libgnome-speech7
  libgnome-vfs2.0-cil libgnome-vfsmm-2.6-1c2a libgnome-window-settings1
  libgnome2-0 libgnome2-common libgnome2-perl libgnome2-vfs-perl
  libgnome2.24-cil libgnomekbd-common libgnomekbd4 libgnomemm-2.6-1c2
  libgnomepanel2.24-cil libgnomeui-0 libgnomeuimm-2.6-1c2a libgnomevfs2-0
  libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgstfarsight0.10-0
  libgtkglext1 libgtkhtml-editor0 libgtkhtml3.14-19 libgweather-common
  libgweather1 libice-dev libice6 libkonq5 libkonqsidebarplugin4
  liblpint-bonobo0 libm17n-0 libmagick++2 libmagickcore2 libmagickcore2-extra
  libmagickwand2 libmetacity-private0 libnet-dbus-perl libnss-mdns liboobs-1-4
  libpanel-applet2-0 libphonon4 libplasma3 libplot2c2 libpolkit-gtk-1-0
  libpolkit-qt-1-0 libpstoedit0c2a libpulse-browse0 libpulse-mainloop-glib0
  libpulse0 libpurple0 libqt3-mt libqt4-designer libqt4-help libqt4-opengl
  libqt4-qt3support libqt4-scripttools libqt4-svg libqt4-webkit libqtgui4
  librpc-xml-perl librxtx-java libseed0 libsm-dev libsm6 libsoqt4-20
  libsoup-gnome2.4-1 libstartup-notification0 libtelepathy-farsight0 libvtk5.2
  libwebkit-1.0-2 libwnck22 libwww-perl libwxgtk2.8-0 libx11-dev libxau-dev
  libxaw7 libxcb1-dev libxine1 libxine1-misc-plugins libxine1-x libxklavier16
  libxml-dom-perl libxml-grove-perl libxml-handler-yawriter-perl
  libxml-parser-perl libxml-perl libxml-sax-expat-perl libxml-twig-perl
  libxml-xpath-perl libxml-xql-perl libxmu6 libxres1 libxss1 libxt-dev libxt6
  libxtst6 libxvmc1 libxxf86dga1 lightsoff lilypond lilypond-data linux
  linux-backports-modules-alsa-2.6.32-24-generic
  linux-backports-modules-alsa-lucid-generic linux-generic linux-image
  linux-image-2.6.32-22-generic linux-image-2.6.32-23-generic
  linux-image-2.6.32-24-generic linux-image-generic linux-sound-base lmms
  lmodern logrotate m17n-contrib m17n-db media-player-info mediawiki
  mediawiki-extensions mediawiki-math metacity metacity-common mixxx
  module-init-tools mountall mousetweaks mplayer mplayer-fonts mplayer-gui
  mscore muse musescore musixlyr musixtex musixtex-slurps mysql-navigator
  mysql-query-browser mysql-server mysql-server-5.1 nautilus nautilus-data
  nautilus-image-converter nautilus-sendto nautilus-sendto-empathy
  nautilus-share netbase network-manager network-manager-gnome
  network-manager-pptp network-manager-pptp-gnome notify-osd ntfs-3g ntp
  ntpdate nvidia-185-kernel-source nvidia-185-libvdpau nvidia-185-libvdpau-dev
  nvidia-current nvidia-current-dev nvidia-glx-185 nvidia-glx-185-dev
  nvidia-kernel-common nvidia-settings obex-data-server onboard openjdk-6-jdk
  openjdk-6-jre openoffice.org openoffice.org-base openoffice.org-base-core
  openoffice.org-calc openoffice.org-core openoffice.org-draw
  openoffice.org-emailmerge openoffice.org-filter-binfilter
  openoffice.org-filter-mobiledev openoffice.org-impress
  openoffice.org-java-common openoffice.org-math openoffice.org-officebean
  openoffice.org-report-builder-bin openoffice.org-style-galaxy
  openoffice.org-writer openprinting-ppds openssh-server oss-compat packagekit
  pcmciautils perlmagick pgf phonon phonon-backend-xine php-openid php5 pidgin
  pidgin-libnotify pidgin-otr plasma-scriptengine-javascript plymouth
  plymouth-theme-ubuntu-text pm-utils policykit policykit-1 policykit-1-gnome
  polkit-kde-1 pornview powermgmt-base ppp pppconfig pppoeconf pptp-linux
  privoxy procps prosper pstoedit pulseaudio-utils puredata pxljr
  python-aptdaemon python-aptdaemon-gtk python-desktopcouch
  python-desktopcouch-records python-evolution python-farsight python-gconf
  python-gnome2 python-gnome2-desktop python-gnomeapplet python-gnomedesktop
  python-gtkglext1 python-imaging-tk python-kde4 python-mediaprofiles
  python-metacity python-papyon python-pivy python-pyatspi python-qt4
  python-qt4-gl python-speechd python-tk python-uno python-virtkey
  python-webkit python-wnck qamix qcad qjackctl qsynth quadrapassel redshift
  rhythmbox rhythmbox-plugin-cdrecorder rhythmbox-plugins rss-glx rsyslog
  rtirq-init sailcut sat4j screen-resolution-extra screensaver-default-images
  scribus scummvm seahorse seahorse-plugins seed sensors-applet skype
  software-center software-properties-gtk software-properties-kde sooperlooper
  sound-juicer soundconverter speech-dispatcher splix squid ssh stopmotion
  subtitleeditor swell-foop system-config-printer-gnome system-tools-backends
  t1-cyrillic t1-oldslavic t1-teams telepathy-butterfly telepathy-haze
  telepathy-salut telnet terminatorx tex-gyre tex4ht tex4ht-common texlive
  texlive-base texlive-bibtex-extra texlive-binaries texlive-extra-utils
  texlive-font-utils texlive-fonts-extra texlive-fonts-recommended
  texlive-formats-extra texlive-full texlive-games texlive-generic-extra
  texlive-generic-recommended texlive-humanities texlive-lang-african
  texlive-lang-arabic texlive-lang-armenian texlive-lang-croatian
  texlive-lang-cyrillic texlive-lang-czechslovak texlive-lang-danish
  texlive-lang-dutch texlive-lang-finnish texlive-lang-french
  texlive-lang-german texlive-lang-greek texlive-lang-hebrew
  texlive-lang-hungarian texlive-lang-indic texlive-lang-italian
  texlive-lang-latin texlive-lang-latvian texlive-lang-lithuanian
  texlive-lang-mongolian texlive-lang-norwegian texlive-lang-other
  texlive-lang-polish texlive-lang-portuguese texlive-lang-spanish
  texlive-lang-swedish texlive-lang-tibetan texlive-lang-ukenglish
  texlive-lang-vietnamese texlive-latex-base texlive-latex-extra
  texlive-latex-recommended texlive-latex3 texlive-luatex texlive-math-extra
  texlive-metapost texlive-music texlive-omega texlive-pictures
  texlive-plain-extra texlive-pstricks texlive-publishers texlive-science
  texlive-xetex thailatex thunderbird thunderbird-locale-en-gb timidity
  timidity-daemon tipa tk8.5 tomboy totem totem-common totem-mozilla
  totem-plugins transmission-gtk tsclient ttf-mscorefonts-installer ubufox
  ubuntu-docs ubuntu-minimal ubuntu-standard ubuntu-system-service
  ubuntu-wallpapers ubuntuone-client-gnome ubuntustudio-audio-plugins
  ubuntustudio-font-meta udev udisks ufw update-manager update-manager-kde
  update-notifier upower upstart ureadahead usb-creator-common usb-creator-gtk
  util-linux vinagre vino vlc vlc-plugin-pulse wireless-crda wmnet wterm
  x-ttcidfont-conf x11-apps x11-common x11-session-utils x11-utils
  x11-xfs-utils x11-xkb-utils x11-xserver-utils xaw3dg xbase-clients
  xfonts-100dpi xfonts-75dpi xfonts-base xfonts-encodings xfonts-kapl
  xfonts-mathml xfonts-naga10 xfonts-scalable xfonts-terminus
  xfonts-terminus-dos xfonts-terminus-oblique xfonts-thai-nectec
  xfonts-thai-poonlap xfonts-thai-vor xfonts-utils xinit xorg xscreensaver
  xscreensaver-data xscreensaver-data-extra xscreensaver-gl
  xscreensaver-gl-extra xserver-common xserver-xorg xserver-xorg-core
  xserver-xorg-input-all xserver-xorg-input-evdev xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom xserver-xorg-video-apm xserver-xorg-video-ark
  xserver-xorg-video-ati xserver-xorg-video-chips xserver-xorg-video-cirrus
  xserver-xorg-video-fbdev xserver-xorg-video-geode xserver-xorg-video-i128
  xserver-xorg-video-i740 xserver-xorg-video-intel xserver-xorg-video-mach64
  xserver-xorg-video-mga xserver-xorg-video-neomagic
  xserver-xorg-video-openchrome xserver-xorg-video-r128
  xserver-xorg-video-radeon xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-tseng xserver-xorg-video-v4l xserver-xorg-video-vesa
  xserver-xorg-video-vmware xserver-xorg-video-voodoo xsnow xterm xtrans-dev
  xulrunner-1.9.2 xvkbd yakuake yeahconsole yelp z88
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  e2fsprogs util-linux (due to e2fsprogs) hostname upstart (due to hostname)
0 upgraded, 0 newly installed, 812 to remove and 0 not upgraded.

```

Could somebody please explain what a boot prettifier has to do with mediawiki,kernel modules, texlive, audacity and aislerot solitair?

Please somebody... A boot splash shouldn't this vital to linux.

---

### Post by Moorbilt on 2010-09-23
.

---

