---
title: "can't install chromium browser"
date: 2011-02-12
forum: New to Ubuntu
---

### Post by mortsemious on 2011-02-12
[FONT=Times New Roman][SIZE=2]i have been trying to install chrome browser using this tutorial
 [http://ubuntuguide.net/install-google-chrome-chromium-browser-in-ubuntu-10-10-maverick](http://ubuntuguide.net/install-google-chrome-chromium-browser-in-ubuntu-10-10-maverick)

i started with
[/SIZE][/FONT]```
kai@zebox:~$ sudo add-apt-repository ppa:chromium-daily/stable
```[FONT=Times New Roman][SIZE=2]put in my password
[/SIZE][/FONT]```
[sudo] password for kai: 
```[FONT=Times New Roman][SIZE=2]

and i received:
[/SIZE][/FONT]
```
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring  --secret-keyring /etc/apt/secring.gpg --trustdb-name  /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring  /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv  FBEF0D696DE1C72BA5A835FE5A9BF3BB4E5E17B5
gpg: requesting key 4E5E17B5 from hkp server keyserver.ubuntu.com
gpg: key 4E5E17B5: "Launchpad PPA for chromium-daily" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
kai@zebox:~$ sudo apt-get update
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") maverick Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick Release.gpg
Ign [http://ppa.launchpad.net/chromium-daily/stable/ubuntu/](http://ppa.launchpad.net/chromium-daily/stable/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/chromium-daily/stable/ubuntu/](http://ppa.launchpad.net/chromium-daily/stable/ubuntu/) maverick/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") maverick-updates Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Ign [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick Release.gpg                    
Ign [http://ppa.launchpad.net/chromium-daily-stable/ppa/ubuntu/](http://ppa.launchpad.net/chromium-daily-stable/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/chromium-daily-stable/ppa/ubuntu/](http://ppa.launchpad.net/chromium-daily-stable/ppa/ubuntu/) maverick/main Translation-en_US
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick Release                        
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") maverick Release                    
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security Release             
Ign [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick Release                        
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") maverick-updates Release            
Ign [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick/main Sources                   
Ign [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick/main i386 Packages                       
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick/main Sources                   
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick/main i386 Packages             
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") maverick/main Sources               
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security/main Sources
Ign [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick/main Sources
Ign [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick/main i386 Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") maverick/restricted Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") maverick/universe Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") maverick/multiverse Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") maverick/main i386 Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") maverick/restricted i386 Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") maverick/universe i386 Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security/restricted Sources  
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security/universe Sources    
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security/multiverse Sources  
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security/main i386 Packages  
Err [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick/main Sources                   
  404  Not Found
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") maverick/multiverse i386 Packages   
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") maverick-updates/main Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") maverick-updates/restricted Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") maverick-updates/universe Sources
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security/restricted i386 Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security/universe i386 Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") maverick-security/multiverse i386 Packages
Err [http://ppa.launchpad.net]("http://ppa.launchpad.net/") maverick/main i386 Packages
  404  Not Found
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") maverick-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") maverick-updates/main i386 Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") maverick-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") maverick-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") maverick-updates/multiverse i386 Packages
W: Failed to fetch  [http://ppa.launchpad.net/chromium-daily-stable/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/chromium-daily-stable/ppa/ubuntu/dists/maverick/main/source/Sources.gz)   404  Not Found

W: Failed to fetch  [http://ppa.launchpad.net/chromium-daily-stable/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/chromium-daily-stable/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)   404  Not Found 

E: Some index files failed to download, they have been ignored, or old ones used instead. 
```[FONT=Times New Roman][SIZE=2]

then i wrote[/SIZE][/FONT] [FONT=Times New Roman][SIZE=2]
[/SIZE][/FONT] ```
sudo apt-get install chromium-browser
```[FONT=Times New Roman][SIZE=2]
[/SIZE][/FONT][FONT=Times New Roman][SIZE=2]
[FONT=arial black][FONT=Times New Roman]and i get
[/FONT][/FONT][/SIZE][/FONT]
be installed
                           ```
Depends: python-oauth (>= 1.0~svn1092-0ubuntu2) but it is not going to be installed
 python-wnck : Depends: libatk1.0-0 (>= 1.29.3) but it is not going to be installed
               Depends: libc6 (>= 2.3.6-6~) but it is not going to be installed
               Depends: libfontconfig1 (>= 2.8.0) but it is not going to be installed
               Depends: libgdk-pixbuf2.0-0 (>= 2.21.6) but it is not going to be installed
               Depends: libglib2.0-0 (>= 2.16.0) but it is not going to be installed
               Depends: libgtk2.0-0 (>= 2.8.0) but it is not going to be installed
               Depends: libpango1.0-0 (>= 1.14.0) but it is not going to be installed
               Depends: libwnck22 (>= 1:2.22) but it is not going to be installed
               Depends: python (< 2.7) but it is not going to be installed
               Depends: python (>= 2.6) but it is not going to be installed
               Depends: python-support (>= 0.90.0) but it is not going to be installed
               Depends: python-gtk2 but it is not going to be installed
 python-zope.interface : Depends: python (< 2.7) but it is not going to be installed
                         Depends: python (>= 2.6) but it is not going to be installed
                         Depends: python-central (>= 0.6.11) but it is not going to be installed
                         Depends: libc6 (>= 2.3.6-6~) but it is not going to be installed
 sane-utils : Depends: adduser (>= 3.47) but it is not going to be installed
              Depends: libavahi-client3 (>= 0.6.16) but it is not going to be installed
              Depends: libavahi-common3 (>= 0.6.16) but it is not going to be installed
              Depends: libc6 (>= 2.4) but it is not going to be installed
              Depends: libieee1284-3 but it is not going to be installed
 seahorse : Depends: libatk1.0-0 (>= 1.29.3) but it is not going to be installed
            Depends: libavahi-client3 (>= 0.6.16) but it is not going to be installed
            Depends: libavahi-common3 (>= 0.6.16) but it is not going to be installed
            Depends: libavahi-glib1 (>= 0.6.16) but it is not going to be installed
            Depends: libc6 (>= 2.7) but it is not going to be installed
            Depends: libcryptui0 (>= 2.27.5) but it is not going to be installed
            Depends: libdbus-glib-1-2 (>= 0.88) but it is not going to be installed
            Depends: libgconf2-4 (>= 2.31.1) but it is not going to be installed
            Depends: libgcr0 (>= 2.26.0) but it is not going to be installed
            Depends: libgdk-pixbuf2.0-0 (>= 2.21.6) but it is not going to be installed
            Depends: libglib2.0-0 (>= 2.24.0) but it is not going to be installed
            Depends: libgnome-keyring0 (>= 2.25.5) but it is not going to be installed
            Depends: libgp11-0 (>= 2.29.4) but it is not going to be installed
            Depends: libgpgme11 (>= 1.2.0) but it is not going to be installed
            Depends: libgtk2.0-0 (>= 2.21.8) but it is not going to be installed
            Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not going to be installed
            Depends: libldap-2.4-2 (>= 2.4.7) but it is not going to be installed
            Depends: libnotify1 (>= 0.5.0) but it is not going to be installed
            Depends: libnotify1-gtk2.10
            Depends: gconf2 (>= 2.28.1-2) but it is not going to be installed
            Depends: gnupg (>= 1.4.7) but it is not going to be installed
            Recommends: openssh-client but it is not going to be installed
 shared-mime-info : Depends: libc6 (>= 2.3) but it is not going to be installed
                    Depends: libglib2.0-0 (>= 2.24.0) but it is not going to be installed
 shotwell : Depends: libatk1.0-0 (>= 1.29.3) but it is not going to be installed
            Depends: libc6 (>= 2.7) but it is not going to be installed
            Depends: libdbus-glib-1-2 (>= 0.78) but it is not going to be installed
            Depends: libexiv2-6 but it is not going to be installed
            Depends: libfontconfig1 (>= 2.8.0) but it is not going to be installed
            Depends: libgcc1 (>= 1:4.1.1) but it is not going to be installed
            Depends: libgconf2-4 (>= 2.31.1) but it is not going to be installed
            Depends: libgdk-pixbuf2.0-0 (>= 2.21.6) but it is not going to be installed
            Depends: libgee2 (>= 0.5.2) but it is not going to be installed
            Depends: libgexiv2-0 (>= 0.0.91) but it is not going to be installed
            Depends: libglib2.0-0 (>= 2.24.0) but it is not going to be installed
            Depends: libgphoto2-2 (>= 2.4.3) but it is not going to be installed
            Depends: libgphoto2-port0 (>= 2.4.3) but it is not going to be installed
            Depends: libgtk2.0-0 (>= 2.18.0) but it is not going to be installed
            Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not going to be installed
            Depends: libpango1.0-0 (>= 1.18.0) but it is not going to be installed
            Depends: libpng12-0 (>= 1.2.13-4) but it is not going to be installed
            Depends: libsqlite3-0 (>= 3.7.2) but it is not going to be installed
            Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
            Depends: libunique-1.0-0 (>= 1.0.0) but it is not going to be installed
            Depends: libwebkit-1.0-2 (>= 1.1.1) but it is not going to be installed
            Depends: librsvg2-common but it is not going to be installed
            Depends: dbus-x11 but it is not going to be installed
 sudo : Depends: libc6 (>= 2.8) but it is not going to be installed
        Depends: libpam-modules but it is not going to be installed
 system-config-printer-gnome : Depends: python (>= 2.5) but it is not going to be installed
                               Depends: python-support (>= 0.90.0) but it is not going to be installed
                               Depends: system-config-printer-common but it is not going to be installed
                               Depends: python-gtk2 but it is not going to be installed
                               Depends: python-glade2 but it is not going to be installed
                               Depends: python-notify but it is not going to be installed
                               Depends: python-gobject but it is not going to be installed
                               Depends: gnome-icon-theme but it is not going to be installed
                               Depends: python-libxml2 but it is not going to be installed
 tcl8.4 : Depends: libc6 (>= 2.7) but it is not going to be installed
 tcpd : Depends: libc6 (>= 2.4) but it is not going to be installed
        Depends: libwrap0 (>= 7.6-4~) but it is not going to be installed
 telnet : Depends: netbase but it is not going to be installed
          Depends: libc6 (>= 2.11) but it is not going to be installed
          Depends: libgcc1 (>= 1:4.1.1) but it is not going to be installed
          Depends: libncurses5 (>= 5.6+20071006-3) but it is not going to be installed
          Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 ubufox : Depends: xul-ext-ubufox but it is not going to be installed
 ubuntu-extras-keyring : Depends: apt but it is not going to be installed
                         Depends: gnupg but it is not going to be installed
 ubuntu-netbook : Depends: alacarte but it is not going to be installed
                  Depends: alsa-base but it is not going to be installed
                  Depends: alsa-utils but it is not going to be installed
                  Depends: anacron but it is not going to be installed
                  Depends: bc but it is not going to be installed
                  Depends: ca-certificates but it is not going to be installed
                  Depends: checkbox-gtk but it is not going to be installed
                  Depends: consolekit but it is not going to be installed
                  Depends: cups but it is not going to be installed
                  Depends: cups-bsd but it is not going to be installed
                  Depends: cups-client but it is not going to be installed
                  Depends: cups-driver-gutenprint but it is not going to be installed
                  Depends: dc but it is not going to be installed
                  Depends: doc-base but it is not going to be installed
                  Depends: evince but it is not going to be installed
                  Depends: file-roller but it is not going to be installed
                  Depends: foomatic-db-compressed-ppds but it is not going to be installed
                  Depends: foomatic-filters but it is not going to be installed
                  Depends: gcalctool but it is not going to be installed
                  Depends: gedit but it is not going to be installed
                  Depends: genisoimage but it is not going to be installed
                  Depends: ghostscript-x but it is not going to be installed
                  Depends: gnome-about but it is not going to be installed
                  Depends: gnome-applets but it is not going to be installed
                  Depends: gnome-control-center but it is not going to be installed
                  Depends: gnome-media but it is not going to be installed
                  Depends: gnome-menus but it is not going to be installed
                  Depends: gnome-nettool but it is not going to be installed
                  Depends: gnome-panel but it is not going to be installed
                  Depends: gnome-power-manager but it is not going to be installed
                  Depends: gnome-session but it is not going to be installed
                  Depends: gnome-session-canberra but it is not going to be installed
                  Depends: gnome-system-tools but it is not going to be installed
                  Depends: gnome-themes-ubuntu but it is not going to be installed
                  Depends: gnome-utils but it is not going to be installed
                  Depends: gstreamer0.10-alsa but it is not going to be installed
                  Depends: gstreamer0.10-pulseaudio but it is not going to be installed
                  Depends: gtk2-engines but it is not going to be installed
                  Depends: gtk2-engines-pixbuf but it is not going to be installed
                  Depends: gucharmap but it is not going to be installed
                  Depends: humanity-icon-theme but it is not going to be installed
                  Depends: indicator-applet-session but it is not going to be installed
                  Depends: inputattach but it is not going to be installed
                  Depends: launchpad-integration but it is not going to be installed
                  Depends: libgnome2-perl but it is not going to be installed
                  Depends: libpam-ck-connector but it is not going to be installed
                  Depends: libsasl2-modules but it is not going to be installed
                  Depends: libxp6 but it is not going to be installed
                  Depends: nautilus but it is not going to be installed
                  Depends: nautilus-sendto but it is not going to be installed
                  Depends: notify-osd but it is not going to be installed
                  Depends: plymouth-theme-ubuntu-logo but it is not going to be installed
                  Depends: pnm2ppa but it is not going to be installed
                  Depends: pulseaudio but it is not going to be installed
                  Depends: pulseaudio-esound-compat but it is not going to be installed
                  Depends: rarian-compat but it is not going to be installed
                  Depends: screen but it is not going to be installed
                  Depends: smbclient
                  Depends: software-center but it is not going to be installed
                  Depends: software-properties-gtk but it is not going to be installed
                  Depends: ssh-askpass-gnome but it is not going to be installed
                  Depends: synaptic but it is not going to be installed
                  Depends: ttf-dejavu-core but it is not going to be installed
                  Depends: ttf-freefont but it is not going to be installed
                  Depends: ubuntu-artwork but it is not going to be installed
                  Depends: ubuntu-sounds but it is not going to be installed
                  Depends: unzip but it is not going to be installed
                  Depends: update-manager but it is not going to be installed
                  Depends: update-notifier but it is not going to be installed
                  Depends: wireless-tools but it is not going to be installed
                  Depends: x-ttcidfont-conf but it is not going to be installed
                  Depends: xdg-user-dirs but it is not going to be installed
                  Depends: xkb-data but it is not going to be installed
                  Depends: xorg but it is not going to be installed
                  Depends: xterm but it is not going to be installed
                  Depends: yelp but it is not going to be installed
                  Depends: zenity but it is not going to be installed
                  Depends: zip but it is not going to be installed
                  Recommends: acpi-support but it is not going to be installed
                  Recommends: aisleriot but it is not going to be installed
                  Recommends: app-install-data-partner but it is not going to be installed
                  Recommends: apport-gtk but it is not going to be installed
                  Recommends: avahi-autoipd but it is not going to be installed
                  Recommends: avahi-daemon but it is not going to be installed
                  Recommends: bluez but it is not going to be installed
                  Recommends: bluez-alsa but it is not going to be installed
                  Recommends: bluez-cups but it is not going to be installed
                  Recommends: bluez-gstreamer but it is not going to be installed
                  Recommends: branding-ubuntu but it is not going to be installed
                  Recommends: brltty but it is not going to be installed
                  Recommends: brltty-x11 but it is not going to be installed
                  Recommends: cheese but it is not going to be installed
                  Recommends: computer-janitor-gtk but it is not going to be installed
                  Recommends: espeak but it is not going to be installed
                  Recommends: evolution but it is not going to be installed
                  Recommends: evolution-exchange but it is not going to be installed
                  Recommends: evolution-indicator but it is not going to be installed
                  Recommends: evolution-plugins but it is not going to be installed
                  Recommends: evolution-webcal but it is not going to be installed
                  Recommends: firefox but it is not going to be installed
                  Recommends: firefox-gnome-support but it is not going to be installed
                  Recommends: foo2zjs but it is not going to be installed
                  Recommends: gdm-guest-session but it is not going to be installed
                  Recommends: gnome-accessibility-themes but it is not going to be installed
                  Recommends: gnome-bluetooth but it is not going to be installed
                  Recommends: gnome-codec-install but it is not going to be installed
                  Recommends: gnome-disk-utility but it is not going to be installed
                  Recommends: gnome-mag but it is not going to be installed
                  Recommends: gnome-mahjongg but it is not going to be installed
                  Recommends: gnome-orca but it is not going to be installed
                  Recommends: gnome-screensaver but it is not going to be installed
                  Recommends: gnome-sudoku but it is not going to be installed
                  Recommends: gvfs-fuse but it is not going to be installed
                  Recommends: gwibber but it is not going to be installed
                  Recommends: hplip but it is not going to be installed
                  Recommends: ibus but it is not going to be installed
                  Recommends: ibus-pinyin but it is not going to be installed
                  Recommends: ibus-pinyin-db-android but it is not going to be installed
                  Recommends: ibus-table but it is not going to be installed
                  Recommends: im-switch but it is not going to be installed
                  Recommends: indicator-appmenu but it is not going to be installed
                  Recommends: indicator-datetime but it is not going to be installed
                  Recommends: indicator-messages but it is not going to be installed
                  Recommends: jockey-gtk but it is not going to be installed
                  Recommends: kerneloops-daemon but it is not going to be installed
                  Recommends: libnss-mdns but it is not going to be installed
                  Recommends: libpam-gnome-keyring but it is not going to be installed
                  Recommends: libunity-misc0 but it is not going to be installed
                  Recommends: linux-headers-generic but it is not going to be installed
                  Recommends: min12xxw but it is not going to be installed
                  Recommends: mousetweaks but it is not going to be installed
                  Recommends: network-manager-gnome but it is not going to be installed
                  Recommends: onboard but it is not going to be installed
                  Recommends: openoffice.org-calc but it is not going to be installed
                  Recommends: openoffice.org-impress but it is not going to be installed
                  Recommends: openoffice.org-writer but it is not going to be installed
                  Recommends: pcmciautils but it is not going to be installed
                  Recommends: policykit-desktop-privileges but it is not going to be installed
                  Recommends: pulseaudio-module-bluetooth but it is not going to be installed
                  Recommends: pulseaudio-module-gconf but it is not going to be installed
                  Recommends: pxljr but it is not going to be installed
                  Recommends: quadrapassel but it is not going to be installed
                  Recommends: rhythmbox but it is not going to be installed
                  Recommends: rhythmbox-ubuntuone-music-store but it is not going to be installed
                  Recommends: simple-scan but it is not going to be installed
                  Recommends: speech-dispatcher but it is not going to be installed
                  Recommends: splix but it is not going to be installed
                  Recommends: telepathy-idle but it is not going to be installed
                  Recommends: tomboy
                  Recommends: totem but it is not going to be installed
                  Recommends: totem-mozilla but it is not going to be installed
                  Recommends: transmission-gtk but it is not going to be installed
                  Recommends: ttf-indic-fonts-core but it is not going to be installed
                  Recommends: ttf-kacst-one but it is not going to be installed
                  Recommends: ttf-khmeros-core but it is not going to be installed
                  Recommends: ttf-lao but it is not going to be installed
                  Recommends: ttf-liberation but it is not going to be installed
                  Recommends: ttf-punjabi-fonts but it is not going to be installed
                  Recommends: ttf-takao-pgothic but it is not going to be installed
                  Recommends: ttf-thai-tlwg but it is not going to be installed
                  Recommends: ttf-ubuntu-font-family but it is not going to be installed
                  Recommends: ttf-unfonts-core but it is not going to be installed
                  Recommends: ttf-wqy-microhei but it is not going to be installed
                  Recommends: ubuntu-docs but it is not going to be installed
                  Recommends: ubuntuone-client-gnome but it is not going to be installed
                  Recommends: usb-creator-gtk but it is not going to be installed
                  Recommends: xdg-utils but it is not going to be installed
 ubuntu-netbook-default-settings : PreDepends: dpkg (>= 1.15.7.2) but it is not going to be installed
 unity : Depends: libatk1.0-0 (>= 1.29.3) but it is not going to be installed
         Depends: libbamf0 (>= 0.2.20) but it is not going to be installed
         Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
         Depends: libc6 (>= 2.3.6-6~) but it is not going to be installed
         Depends: libclutk-0.3-0 (>= 0.3.6) but it is not going to be installed
         Depends: libclutter-gtk-0.10-0 (>= 0.10.2) but it is not going to be installed
         Depends: libdbus-glib-1-2 (>= 0.78) but it is not going to be installed
         Depends: libdee-1.0-0 (>= 0.1.0) but it is not going to be installed
         Depends: libfontconfig1 (>= 2.8.0) but it is not going to be installed
         Depends: libgconf2-4 (>= 2.31.1) but it is not going to be installed
         Depends: libgdk-pixbuf2.0-0 (>= 2.21.6) but it is not going to be installed
         Depends: libgee2 (>= 0.5.2) but it is not going to be installed
         Depends: libglib2.0-0 (>= 2.22.2-0ubuntu1wncksync3) but it is not going to be installed
         Depends: libgnome2-0 (>= 2.17.3) but it is not going to be installed
         Depends: libgnomecanvas2-0 (>= 2.11.1) but it is not going to be installed
         Depends: libgnomeui-0 (>= 2.22.0) but it is not going to be installed
         Depends: libgnomevfs2-0 (>= 1:2.17.90) but it is not going to be installed
         Depends: libgtk2.0-0 (>= 2.18.0) but it is not going to be installed
         Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
         Depends: libindicator1 but it is not going to be installed
         Depends: liborbit2 (>= 1:2.14.10) but it is not going to be installed
         Depends: libpango1.0-0 (>= 1.14.0) but it is not going to be installed
         Depends: libpng12-0 (>= 1.2.13-4) but it is not going to be installed
         Depends: libsm6 but it is not going to be installed
         Depends: libstartup-notification0 (>= 0.10) but it is not going to be installed
         Depends: libunique-1.0-0 (>= 1.0.0) but it is not going to be installed
         Depends: libunity-misc0 (>= 0.1.0) but it is not going to be installed
         Depends: libunity0 (>= 0.2.30) but it is not going to be installed
         Depends: libutouch-grail1 (>= 1.0.4) but it is not going to be installed
         Depends: libwnck22 (>= 1:2.22) but it is not going to be installed
         Depends: libx11-6 but it is not going to be installed
         Depends: libxcb-atom1 (>= 0.3.6) but it is not going to be installed
         Depends: libxcb-event1 (>= 0.3.6) but it is not going to be installed
         Depends: libxcb-icccm1 (>= 0.3.6) but it is not going to be installed
         Depends: libxcb-property1 (>= 0.3.6) but it is not going to be installed
         Depends: libxcb1 but it is not going to be installed
         Depends: gconf2 (>= 2.28.1-2) but it is not going to be installed
         Depends: mutter (>= 2.31.5) but it is not going to be installed
         Depends: unity-asset-pool (>= 0.8.18) but it is not going to be installed
         Recommends: unity-place-applications but it is not going to be installed
         Recommends: unity-place-files but it is not going to be installed
         Recommends: indicator-appmenu but it is not going to be installed
         Recommends: indicator-application but it is not going to be installed
         Recommends: indicator-sound but it is not going to be installed
         Recommends: indicator-datetime but it is not going to be installed
         Recommends: indicator-messages but it is not going to be installed
         Recommends: indicator-me but it is not going to be installed
         Recommends: indicator-session but it is not going to be installed
 update-inetd : Depends: libfile-copy-recursive-perl but it is not going to be installed
 ure : Depends: uno-libs3 (= 1.6.1+OOo3.2.1-7ubuntu1.1) but it is not going to be installed
       Depends: libc6 (>= 2.11) but it is not going to be installed
       Depends: libgcc1 (>= 1:4.1.1) but it is not going to be installed
       Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
       Depends: libstlport4.6ldbl but it is not going to be installed
 usb-creator-common : Depends: python but it is not going to be installed
                      Depends: python-support (>= 0.90.0) but it is not going to be installed
                      Depends: syslinux but it is not going to be installed
                      Depends: udisks (>= 1.0~) but it is not going to be installed
                      Depends: udisks (< 1.1) but it is not going to be installed
                      Depends: genisoimage but it is not going to be installed
                      Depends: mtools but it is not going to be installed
                      Depends: parted but it is not going to be installed
                      Depends: python-debian but it is not going to be installed
 whois : Depends: libc6 (>= 2.4) but it is not going to be installed
         Depends: libidn11 (>= 1.13) but it is not going to be installed
 wireless-crda : Depends: udev but it is not going to be installed
 wpasupplicant : Depends: libc6 (>= 2.4) but it is not going to be installed
                 Depends: libnl1 (>= 1.1) but it is not going to be installed
                 Depends: libpcsclite1 (>= 1.5.3) but it is not going to be installed
                 Depends: libreadline6 (>= 6.0) but it is not going to be installed
                 Depends: libssl0.9.8 (>= 0.9.8m-1) but it is not going to be installed
                 Depends: adduser but it is not going to be installed
 x11-xkb-utils : Depends: libc6 (>= 2.7) but it is not going to be installed
                 Depends: libx11-6 but it is not going to be installed
                 Depends: libxaw7 but it is not going to be installed
                 Depends: libxmu6 but it is not going to be installed
                 Depends: libxt6 but it is not going to be installed
                 PreDepends: x11-common (>= 1:7.0.0) but it is not going to be installed
 xdg-user-dirs-gtk : Depends: libc6 (>= 2.3.6-6~) but it is not going to be installed
                     Depends: libglib2.0-0 (>= 2.12.0) but it is not going to be installed
                     Depends: libgtk2.0-0 (>= 2.8.0) but it is not going to be installed
                     Depends: xdg-user-dirs but it is not going to be installed
 xfonts-mathml : Depends: xfonts-utils but it is not going to be installed
 xscreensaver-data : Depends: libc6 (>= 2.7) but it is not going to be installed
                     Depends: libgdk-pixbuf2.0-0 (>= 2.21.6) but it is not going to be installed
                     Depends: libglib2.0-0 (>= 2.12.0) but it is not going to be installed
                     Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
                     Depends: libsm6 but it is not going to be installed
                     Depends: libx11-6 but it is not going to be installed
                     Depends: libxext6 but it is not going to be installed
                     Depends: libxmu6 but it is not going to be installed
                     Depends: libxpm4 but it is not going to be installed
                     Depends: libxt6 but it is not going to be installed
 xserver-common : Depends: x11-common but it is not going to be installed
                  Depends: xkb-data but it is not going to be installed
                  Recommends: xfonts-base but it is not going to be installed
                  Recommends: xauth but it is not going to be installed
 xserver-xorg-input-vmmouse : Depends: libc6 (>= 2.7) but it is not going to be installed
                              Depends: xorg-input-abi-11.0
                              Depends: xserver-xorg-core (>= 2:1.8.99.904) but it is not going to be installed
                              Depends: xserver-xorg-input-mouse but it is not going to be installed
                              Depends: udev but it is not going to be installed
 xserver-xorg-video-apm : Depends: libc6 (>= 2.4) but it is not going to be installed
                          Depends: xorg-video-abi-8.0
                          Depends: xserver-xorg-core (>= 2:1.8.99.904) but it is not going to be installed
 xserver-xorg-video-sis : Depends: libc6 (>= 2.7) but it is not going to be installed
                          Depends: xorg-video-abi-8.0
                          Depends: xserver-xorg-core (>= 2:1.8.99.904) but it is not going to be installed
 xserver-xorg-video-voodoo : Depends: libc6 (>= 2.1.3) but it is not going to be installed
                             Depends: xorg-video-abi-8.0
                             Depends: xserver-xorg-core (>= 2:1.8.99.904) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

next i tried

> sudo apt-get -f install chromium-browserand i got
[QUOTE]
         Depends: libncurses5 (>= 5.6+20071006-3) but it is not going to be installed
 pulseaudio-module-x11 : Depends: libc6 (>= 2.4) but it is not going to be installed
                         Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
                         Depends: libpulse0 (= 1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21.1) but it is not going to be installed
                         Depends: libsm6 but it is not going to be installed
                         Depends: libx11-6 but it is not going to be installed
                         Depends: libx11-xcb1 but it is not going to be installed
                         Depends: libxcb-atom1 (>= 0.3.6) but it is not going to be installed
                         Depends: libxcb1 but it is not going to be installed
                         Depends: libxtst6 but it is not going to be installed
                         Depends: pulseaudio but it is not going to be installed
 pulseaudio-utils : Depends: libc6 (>= 2.4) but it is not going to be installed
                    Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
                    Depends: libpulse-browse0 (>= 0.9.8) but it is not going to be installed
                    Depends: libpulse0 (= 1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21.1) but it is not going to be installed
                    Depends: libsm6 but it is not going to be installed
                    Depends: libsndfile1 (>= 1.0.20) but it is not going to be installed
                    Depends: libx11-6 but it is not going to be installed
                    Depends: libx11-xcb1 but it is not going to be installed
                    Depends: libxcb-atom1 (>= 0.3.6) but it is not going to be installed
                    Depends: libxcb1 but it is not going to be installed
                    Depends: libxtst6 but it is not going to be installed
 python-aptdaemon : Depends: python (< 2.7) but it is not going to be installed
                    Depends: python (>= 2.6) but it is not going to be installed
                    Depends: python-central (>= 0.6.11) but it is not going to be installed
                    Depends: python-apt (>= 0.7.96.1ubuntu9) but it is not going to be installed
                    Depends: python-gobject but it is not going to be installed
                    Depends: python-software-properties but it is not going to be installed
                    Depends: policykit-1 but it is not going to be installed
                    Recommends: aptdaemon but it is not going to be installed
 python-dbus : Depends: libc6 (>= 2.4) but it is not going to be installed
               Depends: libdbus-glib-1-2 (>= 0.78) but it is not going to be installed
               Depends: libglib2.0-0 (>= 2.12.0) but it is not going to be installed
               Depends: python (< 2.7) but it is not going to be installed
               Depends: python (>= 2.6) but it is not going to be installed
               Depends: python-support (>= 0.90.0) but it is not going to be installed
               Recommends: python-gobject but it is not going to be installed or
                           python-gtk (< 2.10) but it is not installable
 python-gnome2 : Depends: python (< 2.7) but it is not going to be installed
                 Depends: python (>= 2.6) but it is not going to be installed
                 Depends: python-gnomecanvas but it is not going to be installed
                 Depends: python-gobject (>= 2.17.0) but it is not going to be installed
                 Depends: python-gtk2 (>= 2.10.3) but it is not going to be installed
                 Depends: python-pyorbit (>= 2.0.1-4) but it is not going to be installed
                 Depends: python-support (>= 0.90.0) but it is not going to be installed
                 Depends: python2.6-gnomecanvas
                 Depends: python2.6-gobject
                 Depends: python2.6-gtk2
                 Depends: python2.6-pyorbit
                 Depends: libatk1.0-0 (>= 1.29.3) but it is not going to be installed
                 Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
                 Depends: libc6 (>= 2.4) but it is not going to be installed
                 Depends: libfontconfig1 (>= 2.8.0) but it is not going to be installed
                 Depends: libgconf2-4 (>= 2.27.0) but it is not going to be installed
                 Depends: libglib2.0-0 (>= 2.24.0) but it is not going to be installed
                 Depends: libgnome2-0 (>= 2.17.3) but it is not going to be installed
                 Depends: libgnomecanvas2-0 (>= 2.11.1) but it is not going to be installed
                 Depends: libgnomeui-0 (>= 2.22.0) but it is not going to be installed
                 Depends: libgnomevfs2-0 (>= 1:2.17.90) but it is not going to be installed
                 Depends: libgtk2.0-0 (>= 2.8.0) but it is not going to be installed
                 Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
                 Depends: liborbit2 (>= 1:2.14.10) but it is not going to be installed
                 Depends: libpango1.0-0 (>= 1.14.0) but it is not going to be installed
                 Depends: libsm6 but it is not going to be installed
                 Depends: python-gconf (= 2.28.1-1ubuntu2) but it is not going to be installed
 python-gnomeapplet : Depends: libatk1.0-0 (>= 1.29.3) but it is not going to be installed
                      Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
                      Depends: libc6 (>= 2.3.6-6~) but it is not going to be installed
                      Depends: libfontconfig1 (>= 2.8.0) but it is not going to be installed
                      Depends: libgconf2-4 (>= 2.31.1) but it is not going to be installed
                      Depends: libgdk-pixbuf2.0-0 (>= 2.21.6) but it is not going to be installed
                      Depends: libglib2.0-0 (>= 2.24.0) but it is not going to be installed
                      Depends: libgnome2-0 (>= 2.17.3) but it is not going to be installed
                      Depends: libgnomecanvas2-0 (>= 2.11.1) but it is not going to be installed
                      Depends: libgnomeui-0 (>= 2.22.0) but it is not going to be installed
                      Depends: libgnomevfs2-0 (>= 1:2.17.90) but it is not going to be installed
                      Depends: libgtk2.0-0 (>= 2.8.0) but it is not going to be installed
                      Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
                      Depends: liborbit2 (>= 1:2.14.10) but it is not going to be installed
                      Depends: libpanel-applet2-0 (>= 2.26.0) but it is not going to be installed
                      Depends: libpango1.0-0 (>= 1.14.0) but it is not going to be installed
                      Depends: libsm6 but it is not going to be installed
                      Depends: python (< 2.7) but it is not going to be installed
                      Depends: python (>= 2.6) but it is not going to be installed
                      Depends: python-support (>= 0.90.0) but it is not going to be installed
                      Depends: python-pyorbit but it is not going to be installed
                      Depends: python-gtk2 but it is not going to be installed
 python-gtkspell : Depends: libatk1.0-0 (>= 1.29.3) but it is not going to be installed
                   Depends: libc6 (>= 2.3.6-6~) but it is not going to be installed
                   Depends: libfontconfig1 (>= 2.8.0) but it is not going to be installed
                   Depends: libglib2.0-0 (>= 2.16.0) but it is not going to be installed
                   Depends: libgtk2.0-0 (>= 2.8.0) but it is not going to be installed
                   Depends: libpango1.0-0 (>= 1.14.0) but it is not going to be installed
                   Depends: python (< 2.7) but it is not going to be installed
                   Depends: python (>= 2.6) but it is not going to be installed
                   Depends: python-support (>= 0.90.0) but it is not going to be installed
                   Depends: python-gtk2 but it is not going to be installed
 python-ibus : Depends: python (>= 2.5) but it is not going to be installed
               Depends: python-support (>= 0.90.0) but it is not going to be installed
               Depends: python-gtk2 but it is not going to be installed
               Depends: iso-codes but it is not going to be installed
 python-libproxy : Depends: python (>= 2.5) but it is not going to be installed
                   Depends: python-support (>= 0.90.0) but it is not going to be installed
                   Depends: libproxy0 (>= 0.3.1-1ubuntu1) but it is not going to be installed
 python-mako : Depends: python (>= 2.4) but it is not going to be installed
               Depends: python-support (>= 0.90.0) but it is not going to be installed
               Depends: python-markupsafe but it is not going to be installed
 python-minimal : Depends: python2.6-minimal (>= 2.6.6-1~) but it is not going to be installed
                  Depends: dpkg (>= 1.13.20) but it is not going to be installed
                  Recommends: python but it is not going to be installed
 python-papyon : Depends: python (>= 2.5) but it is not going to be installed
                 Depends: python-support (>= 0.90.0) but it is not going to be installed
                 Depends: python-gobject (>= 2.10) but it is not going to be installed
                 Depends: python-openssl (>= 0.6) but it is not going to be installed
                 Depends: python-gst0.10 but it is not going to be installed
                 Depends: python-farsight but it is not going to be installed
                 Depends: python-crypto but it is not going to be installed
 python-pkg-resources : Depends: python (>= 2.6) but it is not going to be installed
                        Depends: python (< 2.8) but it is not going to be installed
 python-twisted-bin : Depends: python2.6 but it is not going to be installed
                      Depends: python (>= 2.6) but it is not going to be installed
                      Depends: python (< 2.7) but it is not going to be installed
                      Depends: libc6 (>= 2.3.6-6~) but it is not going to be installed
 python-twisted-web : Depends: python2.6 but it is not going to be installed
                      Depends: python (>= 2.6.5-10~) but it is not going to be installed
                      Depends: python (< 2.7) but it is not going to be installed
                      Depends: python-twisted-core (>= 10.0) but it is not going to be installed
 python-ubuntuone-client : Depends: python (>= 2.5) but it is not going to be installed
                           Depends: python-support (>= 0.90.0) but it is not going to be installed
                           Depends: python-ubuntuone-storageprotocol (>= 1.3.2) but it is not going to be installed
                           Depends: python-xdg but it is not going to be installed
                           Depends: xdg-utils but it is not going to be installed
                           Depends: python-gnomekeyring but it is not going to be installed or
                                    python-gnome2-desktop but it is not installable or
                                    python-kde4 but it is not going to be installed
                           Depends: python-notify but it is not going to be installed
                           Depends: python-pyinotify but it is not going to be installed
                           Depends: python-twisted-names but it is not going to be installed
                           Depends: python-oauth (>= 1.0~svn1092-0ubuntu2) but it is not going to be installed
 python-wnck : Depends: libatk1.0-0 (>= 1.29.3) but it is not going to be installed
               Depends: libc6 (>= 2.3.6-6~) but it is not going to be installed
               Depends: libfontconfig1 (>= 2.8.0) but it is not going to be installed
               Depends: libgdk-pixbuf2.0-0 (>= 2.21.6) but it is not going to be installed
               Depends: libglib2.0-0 (>= 2.16.0) but it is not going to be installed
               Depends: libgtk2.0-0 (>= 2.8.0) but it is not going to be installed
               Depends: libpango1.0-0 (>= 1.14.0) but it is not going to be installed
               Depends: libwnck22 (>= 1:2.22) but it is not going to be installed
               Depends: python (< 2.7) but it is not going to be installed
               Depends: python (>= 2.6) but it is not going to be installed
               Depends: python-support (>= 0.90.0) but it is not going to be installed
               Depends: python-gtk2 but it is not going to be installed
 python-zope.interface : Depends: python (< 2.7) but it is not going to be installed
                         Depends: python (>= 2.6) but it is not going to be installed
                         Depends: python-central (>= 0.6.11) but it is not going to be installed
                         Depends: libc6 (>= 2.3.6-6~) but it is not going to be installed
 sane-utils : Depends: adduser (>= 3.47) but it is not going to be installed
              Depends: libavahi-client3 (>= 0.6.16) but it is not going to be installed
              Depends: libavahi-common3 (>= 0.6.16) but it is not going to be installed
              Depends: libc6 (>= 2.4) but it is not going to be installed
              Depends: libieee1284-3 but it is not going to be installed
 seahorse : Depends: libatk1.0-0 (>= 1.29.3) but it is not going to be installed
            Depends: libavahi-client3 (>= 0.6.16) but it is not going to be installed
            Depends: libavahi-common3 (>= 0.6.16) but it is not going to be installed
            Depends: libavahi-glib1 (>= 0.6.16) but it is not going to be installed
            Depends: libc6 (>= 2.7) but it is not going to be installed
            Depends: libcryptui0 (>= 2.27.5) but it is not going to be installed
            Depends: libdbus-glib-1-2 (>= 0.88) but it is not going to be installed
            Depends: libgconf2-4 (>= 2.31.1) but it is not going to be installed
            Depends: libgcr0 (>= 2.26.0) but it is not going to be installed
            Depends: libgdk-pixbuf2.0-0 (>= 2.21.6) but it is not going to be installed
            Depends: libglib2.0-0 (>= 2.24.0) but it is not going to be installed
            Depends: libgnome-keyring0 (>= 2.25.5) but it is not going to be installed
            Depends: libgp11-0 (>= 2.29.4) but it is not going to be installed
            Depends: libgpgme11 (>= 1.2.0) but it is not going to be installed
            Depends: libgtk2.0-0 (>= 2.21.8) but it is not going to be installed
            Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not going to be installed
            Depends: libldap-2.4-2 (>= 2.4.7) but it is not going to be installed
            Depends: libnotify1 (>= 0.5.0) but it is not going to be installed
            Depends: libnotify1-gtk2.10
            Depends: gconf2 (>= 2.28.1-2) but it is not going to be installed
            Depends: gnupg (>= 1.4.7) but it is not going to be installed
            Recommends: openssh-client but it is not going to be installed
 shared-mime-info : Depends: libc6 (>= 2.3) but it is not going to be installed
                    Depends: libglib2.0-0 (>= 2.24.0) but it is not going to be installed
 shotwell : Depends: libatk1.0-0 (>= 1.29.3) but it is not going to be installed
            Depends: libc6 (>= 2.7) but it is not going to be installed
            Depends: libdbus-glib-1-2 (>= 0.78) but it is not going to be installed
            Depends: libexiv2-6 but it is not going to be installed
            Depends: libfontconfig1 (>= 2.8.0) but it is not going to be installed
            Depends: libgcc1 (>= 1:4.1.1) but it is not going to be installed
            Depends: libgconf2-4 (>= 2.31.1) but it is not going to be installed
            Depends: libgdk-pixbuf2.0-0 (>= 2.21.6) but it is not going to be installed
            Depends: libgee2 (>= 0.5.2) but it is not going to be installed
            Depends: libgexiv2-0 (>= 0.0.91) but it is not going to be installed
            Depends: libglib2.0-0 (>= 2.24.0) but it is not going to be installed
            Depends: libgphoto2-2 (>= 2.4.3) but it is not going to be installed
            Depends: libgphoto2-port0 (>= 2.4.3) but it is not going to be installed
            Depends: libgtk2.0-0 (>= 2.18.0) but it is not going to be installed
            Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not going to be installed
            Depends: libpango1.0-0 (>= 1.18.0) but it is not going to be installed
            Depends: libpng12-0 (>= 1.2.13-4) but it is not going to be installed
            Depends: libsqlite3-0 (>= 3.7.2) but it is not going to be installed
            Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
            Depends: libunique-1.0-0 (>= 1.0.0) but it is not going to be installed
            Depends: libwebkit-1.0-2 (>= 1.1.1) but it is not going to be installed
            Depends: librsvg2-common but it is not going to be installed
            Depends: dbus-x11 but it is not going to be installed
 sudo : Depends: libc6 (>= 2.8) but it is not going to be installed
        Depends: libpam-modules but it is not going to be installed
 system-config-printer-gnome : Depends: python (>= 2.5) but it is not going to be installed
                               Depends: python-support (>= 0.90.0) but it is not going to be installed
                               Depends: system-config-printer-common but it is not going to be installed
                               Depends: python-gtk2 but it is not going to be installed
                               Depends: python-glade2 but it is not going to be installed
                               Depends: python-notify but it is not going to be installed
                               Depends: python-gobject but it is not going to be installed
                               Depends: gnome-icon-theme but it is not going to be installed
                               Depends: python-libxml2 but it is not going to be installed
 tcl8.4 : Depends: libc6 (>= 2.7) but it is not going to be installed
 tcpd : Depends: libc6 (>= 2.4) but it is not going to be installed
        Depends: libwrap0 (>= 7.6-4~) but it is not going to be installed
 telnet : Depends: netbase but it is not going to be installed
          Depends: libc6 (>= 2.11) but it is not going to be installed
          Depends: libgcc1 (>= 1:4.1.1) but it is not going to be installed
          Depends: libncurses5 (>= 5.6+20071006-3) but it is not going to be installed
          Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
 ubufox : Depends: xul-ext-ubufox but it is not going to be installed
 ubuntu-extras-keyring : Depends: apt but it is not going to be installed
                         Depends: gnupg but it is not going to be installed
 ubuntu-netbook : Depends: alacarte but it is not going to be installed
                  Depends: alsa-base but it is not going to be installed
                  Depends: alsa-utils but it is not going to be installed
                  Depends: anacron but it is not going to be installed
                  Depends: bc but it is not going to be installed
                  Depends: ca-certificates but it is not going to be installed
                  Depends: checkbox-gtk but it is not going to be installed
                  Depends: consolekit but it is not going to be installed
                  Depends: cups but it is not going to be installed
                  Depends: cups-bsd but it is not going to be installed
                  Depends: cups-client but it is not going to be installed
                  Depends: cups-driver-gutenprint but it is not going to be installed
                  Depends: dc but it is not going to be installed
                  Depends: doc-base but it is not going to be installed
                  Depends: evince but it is not going to be installed
                  Depends: file-roller but it is not going to be installed
                  Depends: foomatic-db-compressed-ppds but it is not going to be installed
                  Depends: foomatic-filters but it is not going to be installed
                  Depends: gcalctool but it is not going to be installed
                  Depends: gedit but it is not going to be installed
                  Depends: genisoimage but it is not going to be installed
                  Depends: ghostscript-x but it is not going to be installed
                  Depends: gnome-about but it is not going to be installed
                  Depends: gnome-applets but it is not going to be installed
                  Depends: gnome-control-center but it is not going to be installed
                  Depends: gnome-media but it is not going to be installed
                  Depends: gnome-menus but it is not going to be installed
                  Depends: gnome-nettool but it is not going to be installed
                  Depends: gnome-panel but it is not going to be installed
                  Depends: gnome-power-manager but it is not going to be installed
                  Depends: gnome-session but it is not going to be installed
                  Depends: gnome-session-canberra but it is not going to be installed
                  Depends: gnome-system-tools but it is not going to be installed
                  Depends: gnome-themes-ubuntu but it is not going to be installed
                  Depends: gnome-utils but it is not going to be installed
                  Depends: gstreamer0.10-alsa but it is not going to be installed
                  Depends: gstreamer0.10-pulseaudio but it is not going to be installed
                  Depends: gtk2-engines but it is not going to be installed
                  Depends: gtk2-engines-pixbuf but it is not going to be installed
                  Depends: gucharmap but it is not going to be installed
                  Depends: humanity-icon-theme but it is not going to be installed
                  Depends: indicator-applet-session but it is not going to be installed
                  Depends: inputattach but it is not going to be installed
                  Depends: launchpad-integration but it is not going to be installed
                  Depends: libgnome2-perl but it is not going to be installed
                  Depends: libpam-ck-connector but it is not going to be installed
                  Depends: libsasl2-modules but it is not going to be installed
                  Depends: libxp6 but it is not going to be installed
                  Depends: nautilus but it is not going to be installed
                  Depends: nautilus-sendto but it is not going to be installed
                  Depends: notify-osd but it is not going to be installed
                  Depends: plymouth-theme-ubuntu-logo but it is not going to be installed
                  Depends: pnm2ppa but it is not going to be installed
                  Depends: pulseaudio but it is not going to be installed
                  Depends: pulseaudio-esound-compat but it is not going to be installed
                  Depends: rarian-compat but it is not going to be installed
                  Depends: screen but it is not going to be installed
                  Depends: smbclient
                  Depends: software-center but it is not going to be installed
                  Depends: software-properties-gtk but it is not going to be installed
                  Depends: ssh-askpass-gnome but it is not going to be installed
                  Depends: synaptic but it is not going to be installed
                  Depends: ttf-dejavu-core but it is not going to be installed
                  Depends: ttf-freefont but it is not going to be installed
                  Depends: ubuntu-artwork but it is not going to be installed
                  Depends: ubuntu-sounds but it is not going to be installed
                  Depends: unzip but it is not going to be installed
                  Depends: update-manager but it is not going to be installed
                  Depends: update-notifier but it is not going to be installed
                  Depends: wireless-tools but it is not going to be installed
                  Depends: x-ttcidfont-conf but it is not going to be installed
                  Depends: xdg-user-dirs but it is not going to be installed
                  Depends: xkb-data but it is not going to be installed
                  Depends: xorg but it is not going to be installed
                  Depends: xterm but it is not going to be installed
                  Depends: yelp but it is not going to be installed
                  Depends: zenity but it is not going to be installed
                  Depends: zip but it is not going to be installed
                  Recommends: acpi-support but it is not going to be installed
                  Recommends: aisleriot but it is not going to be installed
                  Recommends: app-install-data-partner but it is not going to be installed
                  Recommends: apport-gtk but it is not going to be installed
                  Recommends: avahi-autoipd but it is not going to be installed
                  Recommends: avahi-daemon but it is not going to be installed
                  Recommends: bluez but it is not going to be installed
                  Recommends: bluez-alsa but it is not going to be installed
                  Recommends: bluez-cups but it is not going to be installed
                  Recommends: bluez-gstreamer but it is not going to be installed
                  Recommends: branding-ubuntu but it is not going to be installed
                  Recommends: brltty but it is not going to be installed
                  Recommends: brltty-x11 but it is not going to be installed
                  Recommends: cheese but it is not going to be installed
                  Recommends: computer-janitor-gtk but it is not going to be installed
                  Recommends: espeak but it is not going to be installed
                  Recommends: evolution but it is not going to be installed
                  Recommends: evolution-exchange but it is not going to be installed
                  Recommends: evolution-indicator but it is not going to be installed
                  Recommends: evolution-plugins but it is not going to be installed
                  Recommends: evolution-webcal but it is not going to be installed
                  Recommends: firefox but it is not going to be installed
                  Recommends: firefox-gnome-support but it is not going to be installed
                  Recommends: foo2zjs but it is not going to be installed
                  Recommends: gdm-guest-session but it is not going to be installed
                  Recommends: gnome-accessibility-themes but it is not going to be installed
                  Recommends: gnome-bluetooth but it is not going to be installed
                  Recommends: gnome-codec-install but it is not going to be installed
                  Recommends: gnome-disk-utility but it is not going to be installed
                  Recommends: gnome-mag but it is not going to be installed
                  Recommends: gnome-mahjongg but it is not going to be installed
                  Recommends: gnome-orca but it is not going to be installed
                  Recommends: gnome-screensaver but it is not going to be installed
                  Recommends: gnome-sudoku but it is not going to be installed
                  Recommends: gvfs-fuse but it is not going to be installed
                  Recommends: gwibber but it is not going to be installed
                  Recommends: hplip but it is not going to be installed
                  Recommends: ibus but it is not going to be installed
                  Recommends: ibus-pinyin but it is not going to be installed
                  Recommends: ibus-pinyin-db-android but it is not going to be installed
                  Recommends: ibus-table but it is not going to be installed
                  Recommends: im-switch but it is not going to be installed
                  Recommends: indicator-appmenu but it is not going to be installed
                  Recommends: indicator-datetime but it is not going to be installed
                  Recommends: indicator-messages but it is not going to be installed
                  Recommends: jockey-gtk but it is not going to be installed
                  Recommends: kerneloops-daemon but it is not going to be installed
                  Recommends: libnss-mdns but it is not going to be installed
                  Recommends: libpam-gnome-keyring but it is not going to be installed
                  Recommends: libunity-misc0 but it is not going to be installed
                  Recommends: linux-headers-generic but it is not going to be installed
                  Recommends: min12xxw but it is not going to be installed
                  Recommends: mousetweaks but it is not going to be installed
                  Recommends: network-manager-gnome but it is not going to be installed
                  Recommends: onboard but it is not going to be installed
                  Recommends: openoffice.org-calc but it is not going to be installed
                  Recommends: openoffice.org-impress but it is not going to be installed
                  Recommends: openoffice.org-writer but it is not going to be installed
                  Recommends: pcmciautils but it is not going to be installed
                  Recommends: policykit-desktop-privileges but it is not going to be installed
                  Recommends: pulseaudio-module-bluetooth but it is not going to be installed
                  Recommends: pulseaudio-module-gconf but it is not going to be installed
                  Recommends: pxljr but it is not going to be installed
                  Recommends: quadrapassel but it is not going to be installed
                  Recommends: rhythmbox but it is not going to be installed
                  Recommends: rhythmbox-ubuntuone-music-store but it is not going to be installed
                  Recommends: simple-scan but it is not going to be installed
                  Recommends: speech-dispatcher but it is not going to be installed
                  Recommends: splix but it is not going to be installed
                  Recommends: telepathy-idle but it is not going to be installed
                  Recommends: tomboy
                  Recommends: totem but it is not going to be installed
                  Recommends: totem-mozilla but it is not going to be installed
                  Recommends: transmission-gtk but it is not going to be installed
                  Recommends: ttf-indic-fonts-core but it is not going to be installed
                  Recommends: ttf-kacst-one but it is not going to be installed
                  Recommends: ttf-khmeros-core but it is not going to be installed
                  Recommends: ttf-lao but it is not going to be installed
                  Recommends: ttf-liberation but it is not going to be installed
                  Recommends: ttf-punjabi-fonts but it is not going to be installed
                  Recommends: ttf-takao-pgothic but it is not going to be installed
                  Recommends: ttf-thai-tlwg but it is not going to be installed
                  Recommends: ttf-ubuntu-font-family but it is not going to be installed
                  Recommends: ttf-unfonts-core but it is not going to be installed
                  Recommends: ttf-wqy-microhei but it is not going to be installed
                  Recommends: ubuntu-docs but it is not going to be installed
                  Recommends: ubuntuone-client-gnome but it is not going to be installed
                  Recommends: usb-creator-gtk but it is not going to be installed
                  Recommends: xdg-utils but it is not going to be installed
 ubuntu-netbook-default-settings : PreDepends: dpkg (>= 1.15.7.2) but it is not going to be installed
 unity : Depends: libatk1.0-0 (>= 1.29.3) but it is not going to be installed
         Depends: libbamf0 (>= 0.2.20) but it is not going to be installed
         Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
         Depends: libc6 (>= 2.3.6-6~) but it is not going to be installed
         Depends: libclutk-0.3-0 (>= 0.3.6) but it is not going to be installed
         Depends: libclutter-gtk-0.10-0 (>= 0.10.2) but it is not going to be installed
         Depends: libdbus-glib-1-2 (>= 0.78) but it is not going to be installed
         Depends: libdee-1.0-0 (>= 0.1.0) but it is not going to be installed
         Depends: libfontconfig1 (>= 2.8.0) but it is not going to be installed
         Depends: libgconf2-4 (>= 2.31.1) but it is not going to be installed
         Depends: libgdk-pixbuf2.0-0 (>= 2.21.6) but it is not going to be installed
         Depends: libgee2 (>= 0.5.2) but it is not going to be installed
         Depends: libglib2.0-0 (>= 2.22.2-0ubuntu1wncksync3) but it is not going to be installed
         Depends: libgnome2-0 (>= 2.17.3) but it is not going to be installed
         Depends: libgnomecanvas2-0 (>= 2.11.1) but it is not going to be installed
         Depends: libgnomeui-0 (>= 2.22.0) but it is not going to be installed
         Depends: libgnomevfs2-0 (>= 1:2.17.90) but it is not going to be installed
         Depends: libgtk2.0-0 (>= 2.18.0) but it is not going to be installed
         Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
         Depends: libindicator1 but it is not going to be installed
         Depends: liborbit2 (>= 1:2.14.10) but it is not going to be installed
         Depends: libpango1.0-0 (>= 1.14.0) but it is not going to be installed
         Depends: libpng12-0 (>= 1.2.13-4) but it is not going to be installed
         Depends: libsm6 but it is not going to be installed
         Depends: libstartup-notification0 (>= 0.10) but it is not going to be installed
         Depends: libunique-1.0-0 (>= 1.0.0) but it is not going to be installed
         Depends: libunity-misc0 (>= 0.1.0) but it is not going to be installed
         Depends: libunity0 (>= 0.2.30) but it is not going to be installed
         Depends: libutouch-grail1 (>= 1.0.4) but it is not going to be installed
         Depends: libwnck22 (>= 1:2.22) but it is not going to be installed
         Depends: libx11-6 but it is not going to be installed
         Depends: libxcb-atom1 (>= 0.3.6) but it is not going to be installed
         Depends: libxcb-event1 (>= 0.3.6) but it is not going to be installed
         Depends: libxcb-icccm1 (>= 0.3.6) but it is not going to be installed
         Depends: libxcb-property1 (>= 0.3.6) but it is not going to be installed
         Depends: libxcb1 but it is not going to be installed
         Depends: gconf2 (>= 2.28.1-2) but it is not going to be installed
         Depends: mutter (>= 2.31.5) but it is not going to be installed
         Depends: unity-asset-pool (>= 0.8.18) but it is not going to be installed
         Recommends: unity-place-applications but it is not going to be installed
         Recommends: unity-place-files but it is not going to be installed
         Recommends: indicator-appmenu but it is not going to be installed
         Recommends: indicator-application but it is not going to be installed
         Recommends: indicator-sound but it is not going to be installed
         Recommends: indicator-datetime but it is not going to be installed
         Recommends: indicator-messages but it is not going to be installed
         Recommends: indicator-me but it is not going to be installed
         Recommends: indicator-session but it is not going to be installed
 update-inetd : Depends: libfile-copy-recursive-perl but it is not going to be installed
 ure : Depends: uno-libs3 (= 1.6.1+OOo3.2.1-7ubuntu1.1) but it is not going to be installed
       Depends: libc6 (>= 2.11) but it is not going to be installed
       Depends: libgcc1 (>= 1:4.1.1) but it is not going to be installed
       Depends: libstdc++6 (>= 4.1.1) but it is not going to be installed
       Depends: libstlport4.6ldbl but it is not going to be installed
 usb-creator-common : Depends: python but it is not going to be installed
                      Depends: python-support (>= 0.90.0) but it is not going to be installed
                      Depends: syslinux but it is not going to be installed
                      Depends: udisks (>= 1.0~) but it is not going to be installed
                      Depends: udisks (< 1.1) but it is not going to be installed
                      Depends: genisoimage but it is not going to be installed
                      Depends: mtools but it is not going to be installed
                      Depends: parted but it is not going to be installed
                      Depends: python-debian but it is not going to be installed
 whois : Depends: libc6 (>= 2.4) but it is not going to be installed
         Depends: libidn11 (>= 1.13) but it is not going to be installed
 wireless-crda : Depends: udev but it is not going to be installed
 wpasupplicant : Depends: libc6 (>= 2.4) but it is not going to be installed
                 Depends: libnl1 (>= 1.1) but it is not going to be installed
                 Depends: libpcsclite1 (>= 1.5.3) but it is not going to be installed
                 Depends: libreadline6 (>= 6.0) but it is not going to be installed
                 Depends: libssl0.9.8 (>= 0.9.8m-1) but it is not going to be installed
                 Depends: adduser but it is not going to be installed
 x11-xkb-utils : Depends: libc6 (>= 2.7) but it is not going to be installed
                 Depends: libx11-6 but it is not going to be installed
                 Depends: libxaw7 but it is not going to be installed
                 Depends: libxmu6 but it is not going to be installed
                 Depends: libxt6 but it is not going to be installed
                 PreDepends: x11-common (>= 1:7.0.0) but it is not going to be installed
 xdg-user-dirs-gtk : Depends: libc6 (>= 2.3.6-6~) but it is not going to be installed
                     Depends: libglib2.0-0 (>= 2.12.0) but it is not going to be installed
                     Depends: libgtk2.0-0 (>= 2.8.0) but it is not going to be installed
                     Depends: xdg-user-dirs but it is not going to be installed
 xfonts-mathml : Depends: xfonts-utils but it is not going to be installed
 xscreensaver-data : Depends: libc6 (>= 2.7) but it is not going to be installed
                     Depends: libgdk-pixbuf2.0-0 (>= 2.21.6) but it is not going to be installed
                     Depends: libglib2.0-0 (>= 2.12.0) but it is not going to be installed
                     Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
                     Depends: libsm6 but it is not going to be installed
                     Depends: libx11-6 but it is not going to be installed
                     Depends: libxext6 but it is not going to be installed
                     Depends: libxmu6 but it is not going to be installed
                     Depends: libxpm4 but it is not going to be installed
                     Depends: libxt6 but it is not going to be installed
 xserver-common : Depends: x11-common but it is not going to be installed
                  Depends: xkb-data but it is not going to be installed
                  Recommends: xfonts-base but it is not going to be installed
                  Recommends: xauth but it is not going to be installed
 xserver-xorg-input-vmmouse : Depends: libc6 (>= 2.7) but it is not going to be installed
                              Depends: xorg-input-abi-11.0
                              Depends: xserver-xorg-core (>= 2:1.8.99.904) but it is not going to be installed
                              Depends: xserver-xorg-input-mouse but it is not going to be installed
                              Depends: udev but it is not going to be installed
 xserver-xorg-video-apm : Depends: libc6 (>= 2.4) but it is not going to be installed
                          Depends: xorg-video-abi-8.0
                          Depends: xserver-xorg-core (>= 2:1.8.99.904) but it is not going to be installed
 xserver-xorg-video-sis : Depends: libc6 (>= 2.7) but it is not going to be installed
                          Depends: xorg-video-abi-8.0
                          Depends: xserver-xorg-core (>= 2:1.8.99.904) but it is not going to be installed
 xserver-xorg-video-voodoo : Depends: libc6 (>= 2.1.3) but it is not going to be installed
                             Depends: xorg-video-abi-8.0
                             Depends: xserver-xorg-core (>= 2:1.8.99.904) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```[FONT=Times New Roman][SIZE=2][FONT=arial black][FONT=Times New Roman]

What should i do?[/FONT]     
[/FONT][/SIZE][/FONT]

---

### Post by linuxsyst on 2011-02-12
try to do this go here [http://www.google.com/chrome](http://www.google.com/chrome) download it and run it.

---

### Post by adeee on 2011-02-12
try to install it via Software center.

---

### Post by linuxsyst on 2011-02-12
you can also download the .deb file from the link above copy/move it to the desktop 
open terminal type (sudo -s) then (cd Desktop)becareful D with capital! then
(dpkg -i here write the name of the file.deb)
please say if this works or not
best wishes

---

### Post by linuxsyst on 2011-02-12
you can also download the .deb file from the link above copy/move it to the desktop 
open terminal type (sudo -s) then (cd Desktop)becareful D with capital! then
(dpkg -i here write the name of the file.deb)
please say if this works or not
best wishes

---

