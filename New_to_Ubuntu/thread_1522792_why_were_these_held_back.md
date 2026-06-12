---
title: "why were these held back"
date: 2010-07-02
forum: New to Ubuntu
---

### Post by rburkartjo on 2010-07-02
i ran

sudo apt-get update && sudo apt-get upgrade

why did i get this message


Reading state information... Done
The following packages have been kept back:
  gyachi linux-generic linux-headers-generic linux-image-generic
  mozilla-plugin-vlc shotwell totem totem-mozilla totem-plugins vlc
  vlc-data vlc-nox vlc-plugin-pulse

note i could upgrade the following

The following packages will be upgraded:
  brasero brasero-common chromium-browser chromium-browser-inspector
  evince evolution-data-server evolution-data-server-common gnome-about
  gnome-desktop-data gnome-keyring gnome-panel gnome-panel-data
  libbrasero-media0 libcamel1.2-14 libebackend1.2-0 libebook1.2-9
  libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-11
  libedataserverui1.2-8 libegroupwise1.2-13 libevdocument2 libevview2
  libgcr0 libgdata-google1.2-1 libgdata1.2-1 libgnome-desktop-2-17
  libgnome-keyring0 libgnomekbd-common libgnomekbd4 libgp11-0
  libpam-gnome-keyring libpanel-applet2-0 libsoup-gnome2.4-1
  libsoup2.4-1 libusb-0.1-4 opera

is this normal
tks

---

### Post by tom.swartz07 on 2010-07-02
Thats because there are new installs to go with that upgrade. The new kernels almost always involve using Synaptic or the Update Manager to get installed.

Launch either of them and you'll see that they are released for update.

---

### Post by da burger on 2010-07-02
An alternative to using the GUI options if you really want a terminal command is ```
sudo apt-get dist-upgrade
``` but if you run that then make sure you read what is getting installed as there may be some stuff getting uninstalled as well.

---

### Post by bodhi.zazen on 2010-07-02
> **da burger said:**
> An alternative to using the GUI options if you really want a terminal command is ```
sudo apt-get dist-upgrade
``` but if you run that then make sure you read what is getting installed as there may be some stuff getting uninstalled as well.

This ^^

To add to that information, from the man page (under "upgrade") ...

[http://manpages.ubuntu.com/manpages/lucid/en/man8/apt-get.8.html](http://manpages.ubuntu.com/manpages/lucid/en/man8/apt-get.8.html)

> {clip}

under no circumstances are currently installed packages removed, or packages not already installed retrieved and installed. New versions of currently installed packages that cannot be upgraded without changing the install status of another package will be left at their current version.In this event, you may use apt-get dist-upgrade, but make sure you review and understand what is going to be removed (adding packages is IMO less critical, but is important if you are running a server as the added packages may have security implications).

---

### Post by philinux on 2010-07-02
Or.

sudo aptitude update && sudo aptitude safe-upgrade

---

### Post by rburkartjo on 2010-07-02
tks ya'll

---

### Post by -humanaut- on 2010-07-02
Sometimes apt will hold back upgrades that can potentially break something Kernel updates like to break my X because of my Nvidia card but last time I had upgrades held back I was using KDE SC 4.5 and I should of listened instead I fired up synaptic and upgraded it and the end result was me reinstalling Kubuntu lol

---

