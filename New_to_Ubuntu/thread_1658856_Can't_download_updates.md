---
title: "Can't download updates"
date: 2011-01-03
forum: New to Ubuntu
---

### Post by BilleeSugger on 2011-01-03
I have recently installed Ubuntu 10.10 but when I try to download updates or software it says can't download check you internet connection . I am online as I can browse the web.
Any help pls?

---

### Post by vivek.pandey on 2011-01-03
> **BilleeSugger said:**
> I have recently installed Ubuntu 10.10 but when I try to download updates or software it says can't download check you internet connection . I am online as I can browse the web.
Any help pls?

which metod have  u tried terminal (cui) or update manager?

---

### Post by karthick87 on 2011-01-03
Post the output of,

```
sudo apt-get update
```

---

### Post by BilleeSugger on 2011-01-03
Sorry but how do I do that?

---

### Post by karthick87 on 2011-01-03
Open terminal(Applications>>Accessories>>Terminal) and enter that command.Post the results here..

---

### Post by BilleeSugger on 2011-01-03
barry@ubuntu:~$ sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick Release.gpg
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/main Translation-en
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_GB
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_GB
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Hit [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates Release.gpg
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick/multiverse i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Reading package lists... Done
barry@ubuntu:~$

---

### Post by karthick87 on 2011-01-03
Also post the output of,

```
sudo apt-get upgrade
```

---

### Post by BilleeSugger on 2011-01-03
Thought that was what I did before , but................

barry@ubuntu:~$ sudo apt-get upgrade
[sudo] password for barry: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  cups evolution-plugins linux-generic-pae linux-headers-generic-pae
  linux-image-generic-pae
The following packages will be upgraded:
  alsa-utils app-install-data-partner apparmor apparmor-utils aptdaemon
  bind9-host compiz compiz-core compiz-gnome compiz-plugins cups-bsd
  cups-client cups-common dnsutils empathy empathy-common evolution
  evolution-common evolution-data-server evolution-data-server-common
  evolution-exchange firefox firefox-branding firefox-gnome-support gcalctool
  gconf-defaults-service gconf2 gconf2-common gdb gdm-guest-session
  gnome-keyring gnome-settings-daemon gnome-system-tools gvfs gvfs-backends
  gvfs-fuse gwibber gwibber-service hpijs hplip hplip-cups hplip-data
  humanity-icon-theme ibus ibus-gtk indicator-sound initscripts jockey-common
  jockey-gtk language-pack-en language-pack-gnome-en libapparmor-perl
  libapparmor1 libasound2 libbind9-60 libc-bin libc-dev-bin libc6 libc6-dev
  libcairo2 libcamel1.2-14 libcups2 libcupscgi1 libcupsdriver1 libcupsimage2
  libcupsmime1 libcupsppdc1 libdecoration0 libdns66 libdrm-intel1
  libdrm-nouveau1 libdrm-radeon1 libdrm2 libebackend1.2-0 libebook1.2-9
  libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-7 libedataserver1.2-13
  libedataserverui1.2-8 libegroupwise1.2-13 libevolution libfreetype6
  libgconf2-4 libgcr0 libgdata-google1.2-1 libgdata1.2-1 libgexiv2-0 libgp11-0
  libgpod-common libgpod4 libgssapi-krb5-2 libgudev-1.0-0 libgvfscommon0
  libhpmud0 libibus2 libisc60 libisccc60 libisccfg60 libk5crypto3 libkrb5-3
  libkrb5support0 libldap-2.4-2 liblwres60 libmagickcore3 libmagickwand3
  libnautilus-extension1 libnss3-1d libpam-gnome-keyring libpam-modules
  libpam-runtime libpam0g libplymouth2 libpoppler-glib5 libpoppler7
  libpulse-browse0 libpulse-mainloop-glib0 libpulse0 libpurple-bin libpurple0
  libsane-hpaio libsmbclient libsqlite3-0 libssl0.9.8 libsyncdaemon-1.0-1
  libudev0 libutouch-grail1 libvte-common libvte9 libwbclient0 libwebkit-1.0-2
  libwebkit-1.0-common libxml2 libxml2-utils light-themes
  linux-headers-2.6.35-22 linux-headers-2.6.35-23
  linux-headers-2.6.35-23-generic-pae linux-image-2.6.35-23-generic-pae
  linux-libc-dev nautilus nautilus-data nautilus-sendto-empathy nautilus-share
  openssl pitivi plymouth plymouth-label plymouth-theme-ubuntu-logo
  plymouth-theme-ubuntu-text poppler-utils pulseaudio pulseaudio-esound-compat
  pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-x11
  pulseaudio-utils python python-aptdaemon python-aptdaemon-gtk
  python-cupshelpers python-ibus python-libxml2 python-minimal python-papyon
  python-ubuntuone-client python-vte rhythmbox rhythmbox-plugin-cdrecorder
  rhythmbox-plugins rhythmbox-ubuntuone-music-store samba-common
  samba-common-bin simple-scan smbclient software-center
  system-config-printer-common system-config-printer-gnome
  system-config-printer-udev sysv-rc sysvinit-utils telepathy-haze tomboy
  tzdata ubufox ubuntu-docs ubuntu-sso-client ubuntuone-client
  ubuntuone-client-gnome udev update-inetd update-manager update-manager-core
  vino xdg-utils xserver-xorg-video-intel xul-ext-ubufox xulrunner-1.9.2
198 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
Need to get 0B/175MB of archives.
After this operation, 3,486kB of additional disk space will be used.
Do you want to continue [Y/n]?

---

### Post by karthick87 on 2011-01-03
It seems to be Oke..Then what's your problem?

---

### Post by nick_goodfate on 2011-01-03
> **karthick87 said:**
> It seems to be Oke..Then what's your problem?

i don't like this part

> The following packages have been kept back:
cups evolution-plugins linux-generic-pae linux-headers-generic-pae
linux-image-generic-pae

But i don't know the solution.

---

### Post by BilleeSugger on 2011-01-03
I tried to download updates at the start with update manage but it didn't work . Now it does[B]. 

Thanks for your time [/B]**karthick87**** **

---

### Post by karthick87 on 2011-01-03
You are welcome :)

---

