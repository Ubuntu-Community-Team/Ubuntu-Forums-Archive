---
title: "need help reinstalled critical files to 8.10"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by kmcavoy on 2009-03-13
I am new to Ubuntu 8.10 and have been trying to install python 3.0.  Had the brilliant (stupid)idea to uninstall python 2.5.2 with its subsequent library files.  Did realize that red in Synaptic Manager meant that other files utilize these file and uninstalled them.  Now I am at the black screen with login and tty1.  How to I correct this situation?  Thank you for your help!

---

### Post by firefly2442 on 2009-03-13
If you login and type:

```
sudo apt-get install python
```

Does this help?  I assume you have internet access on the machine?

---

### Post by kmcavoy on 2009-03-13
I tried that and get the following message: failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-defaults/python_2.5.2-1ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-defaults/python_2.5.2-1ubuntu1_all.deb) Could not resolve 'us.archive.ubuntu.com' E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

Any recommendations?

I did try the apt-get update and the --fix-missing to no avail.  This is what I get at the login screen:

kinit: name_to_dev_t(/dev/disk/by-uuid/f25a7431-3492-46b1-a43e-7eb43a5f8eb4) = dev(8,6)
kinit: trying to resume from /dev/disk/by-uuid/f25a7431-3492-46b1-a43e-7eb43a5f8eb4
kinit: No resume image, doing normal boot. . .
Ubuntu 8.10 kerry-laptop tty1
kerry-laptop login:

---

### Post by firefly2442 on 2009-03-14
Hmm, sounds like you don't have internet access up and running.  Do you have wired or wireless?

---

### Post by kmcavoy on 2009-03-14
I have wireless. Using dsl to network router.  How do I re-establish the connection?

---

### Post by Shazaam on 2009-03-14
You might need to plug in an ethernet cable between the modem and your pc to get internet access.
You can also add the Ubuntu livecd as a repo in System>Administration>Software Sources to install the default python.

---

### Post by adult swim on 2009-03-14
once you have internet connection, try ```
sudo apt-get install ubuntu-desktop
``` and see if it will round up all of the programs you have lost.  whenever i try to remove python here is the list of stuff it will remove if i uninstall it ```
The following packages will be REMOVED:
  alacarte alsa-utils apport apport-gtk apt-xapian-index apturl at-spi
  bluez-gnome bootchart brasero bzr bzrtools capplets-data checkbox
  checkbox-gtk command-not-found compiz compiz-fusion-plugins-extra
  compiz-fusion-plugins-main compiz-gnome compizconfig-settings-manager
  computer-janitor computer-janitor-gtk contact-lookup-applet deskbar-applet
  ekiga eog evince evolution evolution-data-server evolution-exchange
  evolution-indicator evolution-plugins evolution-webcal f-spot
  fast-user-switch-applet file-roller firefox-3.0-gnome-support
  firefox-gnome-support foomatic-db-hpijs fusion-icon gcalctool gconf-editor
  gconf2 gdebi gdebi-core gdm gdm-guest-session gedit gimp gksu gnome-about
  gnome-app-install gnome-applets gnome-applets-data gnome-codec-install
  gnome-control-center gnome-desktop-sharp2 gnome-doc-utils gnome-games
  gnome-games-data gnome-keyring gnome-media gnome-media-common gnome-menus
  gnome-mount gnome-netstatus-applet gnome-orca gnome-panel gnome-panel-data
  gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver
  gnome-session gnome-settings-daemon gnome-system-monitor gnome-system-tools
  gnome-terminal gnome-terminal-data gnome-user-guide gnome-utils
  gstreamer0.10-gnomevfs gstreamer0.10-plugins-good gucharmap hal-cups-utils
  hpijs hplip hplip-data indicator-applet indicator-messages jockey-common
  jockey-gtk language-selector language-selector-common launchpad-integration
  libbonoboui2-0 libgail-gnome-module libgconf2-dev libgksu2-0 libgnome-media0
  libgnome-vfs2.24-cil libgnome2-0 libgnome2-common libgnome2-perl
  libgnome2-vfs-perl libgnome2.24-cil libgnomekbd-common libgnomekbd3
  libgnomekbdui3 libgnomepanel2.24-cil libgnomeui-0 libgnomevfs2-0
  libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgtkhtml-editor0
  libgtkhtml3.14-19 libgtkhtml3.16-cil libgweather-common libgweather1
  liblpint-bonobo0 libmbca0 libmetacity0 libpanel-applet2-0 libpurple-bin
  librsvg2-bin lsb-release metacity metacity-common mousetweaks nautilus
  nautilus-cd-burner nautilus-data nautilus-sendto nautilus-share
  network-manager network-manager-gnome nvidia-common onboard
  openoffice.org-emailmerge openoffice.org-gnome pidgin pidgin-libnotify
  pidgin-otr policykit-gnome python python-apport python-apt python-beagle
  python-brlapi python-cairo python-central python-compizconfig python-crypto
  python-cups python-cupshelpers python-dbus python-debian python-fstab
  python-gconf python-gdata python-gdbm python-glade2 python-gmenu
  python-gnome2 python-gnome2-desktop python-gnomecanvas python-gnupginterface
  python-gobject python-gst0.10 python-gtk2 python-gtkhtml2
  python-gtksourceview2 python-imaging python-launchpad-bugs
  python-launchpad-integration python-libxml2 python-newt python-notify
  python-paramiko python-pkg-resources python-problem-report python-pyatspi
  python-pyorbit python-rdflib python-sexy python-smbc
  python-software-properties python-support python-uno python-usb
  python-virtkey python-vte python-xapian python-xdg python-xkit rhythmbox
  screen-profiles screen-resolution-extra seahorse seahorse-plugins
  software-properties-gtk system-config-printer-common
  system-config-printer-gnome tomboy totem totem-common totem-gstreamer
  totem-mozilla totem-plugins tsclient ubufox ubuntu-desktop ubuntu-docs
  ubuntu-minimal ubuntu-system-service ufw unattended-upgrades update-manager
  update-manager-core update-notifier update-notifier-common usb-creator
  vinagre vino virtualbox-ose xulrunner-1.9-gnome-support yelp
0 upgraded, 0 newly installed, 229 to remove and 0 not upgraded.

```

---

### Post by kmcavoy on 2009-03-14
ok, I am now hardwired to the router and got internet connection.  I re-installed python and now get the following message:

kinit: name_to_dev_t(/dev/disk/by-uuid/f25a7431-3492-46b1-a43e-7eb43a5f8eb4) = dev(8,6)
kinit: trying to resume from /dev/disk/by-uuid/f25a7431-3492-46b1-a43e-7eb43a5f8eb4
kinit: No resume image, doing normal boot. . .
Ubuntu 8.10 kerry-laptop tty1
kerry-laptop login: [  44.943633] CIFS VFS: cifs_mount failed w/return code = -6

thanks

---

### Post by kmcavoy on 2009-03-14
hey thanks guys.   Installing ubuntu desktop fixed the problem.  I learned a valuable lesson--don't uninstall red highlighted items and keep learning ubuntu basics!!

---

