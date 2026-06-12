---
title: "Python module not working"
date: 2011-02-09
forum: New to Ubuntu
---

### Post by andyzammy on 2011-02-09
Hi,

I'm trying to write a python script that manipulates csv files, but something seems to have stopped working. I keep getting

```
Traceback (most recent call last):
  File "reader1.py", line 4, in <module>
    reader = csv.reader(ifile)
AttributeError: 'module' object has no attribute 'reader'
```

Now it looks like any csv attribute refuses to work.. how can i fix this? It's an quite urgent problem, any help would be appreaciated.

---

### Post by andyzammy on 2011-02-09
just tried reinstalling python via purge, got this in the terminal, something's badly messed up:

```
seahorse
seahorse-plugins
simple-ccsm
simple-scan
software-center
software-properties-gtk
software-properties-kde
swell-foop
system-config-printer-common
system-config-printer-gnome
system-config-printer-udev
telepathy-butterfly
telepathy-haze
texlive-extra-utils
tomboy
totem
totem-common
totem-gstreamer
totem-mozilla
totem-plugins
tovid
tracker-search-tool
tsclient
ubufox
ubuntu-artwork
ubuntu-desktop
ubuntu-docs
ubuntu-minimal
ubuntu-standard
ubuntu-system-service
ubuntu-wallpapers
ubuntuone-client
ubuntuone-client-gnome
ufw
unattended-upgrades
update-manager
update-manager-core
update-manager-kde
update-notifier
update-notifier-common
usb-creator
usb-creator-common
usb-creator-gtk
vegastrike-data
vegastrike-music
vinagre
vino
xchat
xchat-common
yelp

Install the following packages:
epdfview [0.1.7-2 (lucid)]
kdebase-bin [4:4.4.5-0ubuntu1 (lucid-updates)]
kdebase-data [4:4.4.5-0ubuntu1 (lucid-updates)]

Downgrade the following packages:
empathy-common [2.30.3-0ubuntu1 (lucid-updates, now) -> 2.30.0.1-0ubuntu3
(lucid)]

Leave the following dependencies unresolved:
apport-symptoms recommends apport
dkms recommends lsb-release
empathy-common recommends yelp
friendly-recovery recommends update-manager-core (>= 0.90.0)
indicator-messages recommends indicator-applet | indicator-renderer
kerneloops-daemon recommends apport
liblaunchpad-integration1 recommends launchpad-integration
obex-data-server recommends python
obex-data-server recommends python-dbus
obex-data-server recommends python-gobject
python-gnome2-doc recommends python-gnome2
python-minimal recommends python
texlive-pstricks recommends texlive-extra-utils
phonon-backend-gstreamer recommends gstreamer0.10-plugins-good
tracker recommends tracker-search-tool
ant recommends ant-gcj
ant-optional recommends ant-optional-gcj
gedit-common recommends gedit
gimp-data recommends gimp
gparted recommends gksu
kdebase-runtime recommends kubuntu-debug-installer
libgimp2.0 recommends gimp
libglib2.0-dev recommends python
libgnome-keyring0 recommends gnome-keyring
libgtk2.0-dev recommends python (>= 2.4)
libpam-gnome-keyring recommends gnome-keyring
openoffice.org-writer recommends openoffice.org-emailmerge
screen recommends byobu
synaptic recommends libgnome2-perl
synaptic recommends software-properties-gtk
synaptic recommends apt-xapian-index
nvidia-current recommends nvidia-settings
virtualbox-4.0 recommends python-central
Score is -49539

Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.
```

if it could help diagnose what's wrong with my mahcine, let me know how and i'll post the whole thing

---

### Post by Cheesehead on 2011-02-09
Nothing seems wrong with your machine output - that's what I would expect to see if I tried to purge Python (a most unwise idea).

Please post your file reader1.py
A data sample would also be helpful.

---

