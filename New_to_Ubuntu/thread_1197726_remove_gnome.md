---
title: "remove gnome?"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by Duke Togo on 2009-06-26
hi
I have gradually downgraded my ubuntu windows manager experience due to greater knowledge of the terminal and less gui reliance in a drive for a quicker system
having settled on fluxbox, what is the easiest way to remove gnome?
p.s. I googled this question (google is my friend) but the answers were kind of confusing, not really satisfactory or recommending going through synaptic and finding all gnome references, so any ideas?

---

### Post by Tyke91 on 2009-06-26
```

sudo apt-get remove alacarte app-install-data-partner binfmt-support brltty brltty-x11 capplets-data checkbox checkbox-gtk cli-common compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins compiz-wrapper compizconfig-backend-gconf computer-janitor computer-janitor-gtk contact-lookup-applet dcraw ekiga eog evolution evolution-common evolution-data-server evolution-data-server-common evolution-documentation-en evolution-exchange evolution-indicator evolution-plugins evolution-webcal example-content f-spot fast-user-switch-applet firefox-gnome-support gconf-editor gdm-guest-session gedit gedit-common gnome-about gnome-applets gnome-applets-data gnome-codec-install gnome-control-center gnome-menus gnome-nettool gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-session gnome-session-canberra gnome-settings-daemon gnome-terminal gnome-terminal-data gnome-themes-selected gnome-themes-ubuntu gnome-utils gstreamer0.10-plugins-base-apps gstreamer0.10-pulseaudio gstreamer0.10-schroedinger gstreamer0.10-tools gvfs-fuse human-icon-theme human-theme indicator-applet indicator-messages libart2.24-cil libasound2-plugins libcolamd-3.2.0 libcompizconfig0 libdecoration0 libebackend1.2-0 libedata-book1.2-2 libedata-cal1.2-6 libedataserverui1.2-8 libegroupwise1.2-13 libexchange-storage1.2-3 libexempi3 libflickrnet2.1.5-cil libgconf2.24-cil libgdata-google1.2-1 libgdata1.2-1 libgdict-1.0-6 libgdiplus libgif4 libglade2.0-cil libglib2.0-cil libglitz-glx1 libglitz1 libgmime-2.0-2a libgmime2.2a-cil libgnome-keyring1.0-cil libgnome-pilot2 libgnome-vfs2.24-cil libgnome-window-settings1 libgnome2.24-cil libgnomepanel2.24-cil libgnomevfs2-bin libgpod-common libgpod4 libgsm1 libgtk2.0-cil libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml3.14-19 libhyphen0 libicu38 libindicate1 liblpint-bonobo0 libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo2.0-cil libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-data2.0-cil libmono-getoptions2.0-cil libmono-i18n2.0-cil libmono-posix2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil libmono-system-web2.0-cil libmono-system2.0-cil libmono0 libmono2.0-cil libmtp8 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libneon27 libopal3.6.1 libpisock9 libpisync1 libprotobuf3 libpt2.6.1 libpt2.6.1-plugins-alsa libpt2.6.1-plugins-v4l2 libpulsecore9 libsamplerate0 libschroedinger-1.0-0 libsgutils1 libspeexdsp1 libsqlite0 libstlport4.6ldbl libunique-1.0-0 libwmf0.2-7-gtk libwps-0.1-1 lp-solve mesa-utils metacity mono-2.0-gac mono-2.0-runtime mono-common mono-gac mono-jit mono-runtime mousetweaks mtools nautilus nautilus-data nautilus-sendto nautilus-share notify-osd openoffice.org-base-core openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-emailmerge openoffice.org-gnome openoffice.org-gtk openoffice.org-impress openoffice.org-math openoffice.org-style-human openoffice.org-writer pidgin-libnotify pkg-config pulseaudio pulseaudio-esound-compat pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-x11 python-fstab python-gmenu python-gtksourceview2 python-uno rdesktop rhythmbox screen-resolution-extra sg3-utils syslinux tangerine-icon-theme tomboy tsclient ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-gdm-themes ubuntu-sounds ubuntu-system-service ubuntu-wallpapers uno-libs3 ure usb-creator usplash-theme-ubuntu vino whois xdg-user-dirs-gtk 
```that'l nuke all of your gnome stuff from the ubuntu-desktop meta package. notice that things like open office are on that list, so you might want to run through and take everything you want to keep OFF of the list before you run it.

PS: As a fluxbox user, welcome ^_^

---

### Post by Duke Togo on 2009-06-26
thanks for the welcome and the OO heads up, as thats useful for my college work
cheers
I will implement that in the morning as its getting kinda late here and I don`t want any cock ups......
thanks again:D

---

### Post by Bölvaður on 2009-06-26
there are some programs on the list you might want to keep.

also. install Awesome or some other tiling window manager. It is good for cli + gui hybrid people.

---

