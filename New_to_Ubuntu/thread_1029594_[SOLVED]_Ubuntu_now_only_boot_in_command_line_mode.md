---
title: "[SOLVED] Ubuntu now only boot in command line mode"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by Pierrot Lafouine on 2009-01-03
Hi,
When booting, Ubuntu logo appears as usual, progress bar goes up
to the 3/4, then graphic goes off, Ubuntu switch in command line
mode and display this error :

kinit: no resume image, doing normal boot...
Then it ask me for my login and password.
My login and password works fine.

Before this reboot, I was uninstalling python.  During
uninstall, I had many error message in a DialogBox, on
NetworkManager.
Are these two problems related ?
Are they catastrophic ?

Thanks

---

### Post by Pierrot Lafouine on 2009-01-03
How can I fix this ?
Do I need to be advanced Guru Expert to fix this ?
Thanks

---

### Post by unutbu on 2009-01-03
At the command line, type
```

sudo apt-get install python
```
Many parts of the Ubuntu system depend on python. It is not a good idea (i.e. not possible) to remove it from your system.

---

### Post by Pierrot Lafouine on 2009-01-03
Ok, I have installed Python
Same comnmand line boot

Whats next ?
Thanks

---

### Post by Pierrot Lafouine on 2009-01-03
Should Python have fixed the problem ?
Is it a bad sign it did fixed the problem ?
Anything I can do to fix this ?
Thanks

---

### Post by unutbu on 2009-01-03
When python is removed, all packages that depend on python are also removed. Perhaps other packages are missing as well. 

How about type 
```

dpkg --get-selections > ~/package-list
```
This will produce a file called package-list which contains all the packages you have installed on your system. 

If you post that list, I'll compare it with the list of packages that are installed by default on a fresh Intrepid install. Then I'll post back with all the packages you are missing.

If you are not using Intrepid, state which distro you are using and... hm, I'm not sure what I'll do, but I'll try to find the appropriate list.

Edit: If you are not using Intrepid, type
```

bzip2 -c /var/log/dpkg.log* > ~/dpkg.log.bz2
```
Then post dpkg.log.bz2

Also, do you have a USB thumb drive or some other way to transfer those files to the machine you are using to reach ubuntuforums? 

If you are having trouble copying the files to the drive using the command-line, post back with what kind of media you have available and we can help you mount it and copy files to it.

---

### Post by Pierrot Lafouine on 2009-01-03
hummm...how do I write this file to USB key ?
I usually used the port /dev/sdb with SD FLASH formated in EXT2 (not compatible with Windows)

How can I mount/transfer file to USB ?

---

### Post by unutbu on 2009-01-03
Type 
```

sudo mount /dev/sdb1 /mnt    # This mounts the first partition on sdb at /mnt
cp ~/package-list /mnt       # Copies package-list to /mnt
cp ~/dpkg.log.bz2 /mnt       
sudo umount /mnt             # Don't forget (like I did) to unmount it! :)


```

You'll need another machine which can read ext2 filesystem format.

If the mount command returns an error, then please post the error and the output of 
```

sudo fdisk -l
```
(where "-l" is minus lowercase L, not minus one).

---

### Post by Pierrot Lafouine on 2009-01-03
LOL, Looked likes I remove all gnome package...

root@blablabla; apt-get install gnome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libopenexr2c2a libarts1c2a libartsc0 texlive-base kdelibs-data libsmokeqt1
  texlive-common liblualib50 postgresql-client-8.2 texlive-base-bin ruby1.8
  libavahi-qt3-1 libsdl-ttf2.0-0 texlive-latex-base libsdl-mixer1.2
  postgresql-client-common libqt0-ruby1.8 liblua50 libruby1.8
  texlive-doc-base tex-common libsdl-image1.2 libsmpeg0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  abiword-common abiword-gnome alacarte bug-buddy capplets-data desktop-base
  dia-common dia-gnome dia-libs ekiga eog epiphany-browser esound evince
  evolution evolution-data-server fast-user-switch-applet file-roller
  gcalctool gconf-editor gdm-themes gedit gnome-about gnome-applets
  gnome-applets-data gnome-backgrounds gnome-control-center gnome-core
  gnome-cups-manager gnome-desktop-environment gnome-doc-utils gnome-games
  gnome-games-data gnome-games-extra-data gnome-keyring-manager gnome-media
  gnome-media-common gnome-menus gnome-mount gnome-netstatus-applet
  gnome-nettool gnome-office gnome-panel gnome-panel-data
  gnome-power-manager gnome-screensaver gnome-session gnome-system-monitor
  gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes-extras
  gnome-user-guide gnome-utils gnome-volume-manager gnumeric gnumeric-common
  gstreamer0.10-gnomevfs gstreamer0.10-plugins-good gtkhtml3.14 gucharmap
  inkscape launchpad-integration libbonoboui2-0 libcamel1.2-10 libebook1.2-9
  libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserverui1.2-8
  libeel2-2 libexchange-storage1.2-3 libgconf2.0-cil libgnome-desktop-2
  libgnome-media0 libgnome-menu2 libgnome-vfs2.0-cil
  libgnome-window-settings1 libgnome2-0 libgnome2-common libgnome2-perl
  libgnome2-vfs-perl libgnome2.0-cil libgnomecupsui1.0-1c2a
  libgnomekbd-common libgnomekbd1 libgnomekbdui1 libgnomeui-0 libgnomevfs2-0
  libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgoffice-0-4
  libgoffice-0-common libgpgme11 libgsf-gnome-1-114 libgtkhtml2.0-cil
  libgtkhtml3.14-19 libgtkhtml3.8-15 libgucharmap6 liblaunchpad-integration0
  liblpint-bonobo0 libmetacity0 libnautilus-extension1 libpanel-applet2-0
  libpth20 libtotem-plparser7 lsb-release metacity metacity-common nautilus
  nautilus-cd-burner nautilus-data notification-daemon planner python-cairo
  python-central python-gconf python-glade2 python-gmenu python-gnome2
  python-gnome2-desktop python-gnomecanvas python-gobject python-gtk2
  python-libxml2 python-numeric python-pygtksourceview python-support
  rhythmbox seahorse sound-juicer synaptic tomboy totem totem-gstreamer
  totem-mozilla vino yelp
Suggested packages:
  mozplugger unrar gnome-spell evolution-exchange evolution-dbg
  evolution-plugins-experimental evolution-data-server-dbg lha
  esound-clients gnome-audio gnome-hearts cryptsetup gnucash fortunes-mod
  gnome2-user-guide ntp gnumeric-doc gnumeric-plugins-extra libxml-xql-perl
  python-xml skencil gpgsm libgtkhtml3.14-dbg libgtkhtml3.8-dbg beagle
  python-gconf-dbg python-glade2-dbg python-gmenu-dbg
  python-gnome2-desktop-doc python-gnome2-desktop-dbg python-gnomecanvas-dbg
  python-gtk2-dbg python-libxml2-dbg python-numeric-tutorial
  python-numeric-ext python-numeric-dbg dwww tsclient
Recommended packages:
  abiword-help abiword-plugins-gnome gsfonts-x11 epiphany-extensions
  gnome-pilot-conduits evolution-plugins sharutils lzop rpm arj p7zip
  p7zip-full mkisofs ncompress unace deskbar-applet gnome-dbg dasher
  gnopernicus gok fam gnome-orca menu-xdg gthumb libwmf-bin pstoedit
  perlmagick python-numpy lsb gnome-app-install gda2-postgres python-louie
  deborphan ttf-dejavu
The following NEW packages will be installed:
  abiword-common abiword-gnome alacarte bug-buddy capplets-data desktop-base
  dia-common dia-gnome dia-libs ekiga eog epiphany-browser esound evince
  evolution evolution-data-server fast-user-switch-applet file-roller
  gcalctool gconf-editor gdm-themes gedit gnome gnome-about gnome-applets
  gnome-applets-data gnome-backgrounds gnome-control-center gnome-core
  gnome-cups-manager gnome-desktop-environment gnome-doc-utils gnome-games
  gnome-games-data gnome-games-extra-data gnome-keyring-manager gnome-media
  gnome-media-common gnome-menus gnome-mount gnome-netstatus-applet
  gnome-nettool gnome-office gnome-panel gnome-panel-data
  gnome-power-manager gnome-screensaver gnome-session gnome-system-monitor
  gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes-extras
  gnome-user-guide gnome-utils gnome-volume-manager gnumeric gnumeric-common
  gstreamer0.10-gnomevfs gstreamer0.10-plugins-good gtkhtml3.14 gucharmap
  inkscape launchpad-integration libbonoboui2-0 libcamel1.2-10 libebook1.2-9
  libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserverui1.2-8
  libeel2-2 libexchange-storage1.2-3 libgconf2.0-cil libgnome-desktop-2
  libgnome-media0 libgnome-menu2 libgnome-vfs2.0-cil
  libgnome-window-settings1 libgnome2-0 libgnome2-common libgnome2-perl
  libgnome2-vfs-perl libgnome2.0-cil libgnomecupsui1.0-1c2a
  libgnomekbd-common libgnomekbd1 libgnomekbdui1 libgnomeui-0 libgnomevfs2-0
  libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgoffice-0-4
  libgoffice-0-common libgpgme11 libgsf-gnome-1-114 libgtkhtml2.0-cil
  libgtkhtml3.14-19 libgtkhtml3.8-15 libgucharmap6 liblaunchpad-integration0
  liblpint-bonobo0 libmetacity0 libnautilus-extension1 libpanel-applet2-0
  libpth20 libtotem-plparser7 lsb-release metacity metacity-common nautilus
  nautilus-cd-burner nautilus-data notification-daemon planner python-cairo
  python-central python-gconf python-glade2 python-gmenu python-gnome2
  python-gnome2-desktop python-gnomecanvas python-gobject python-gtk2
  python-libxml2 python-numeric python-pygtksourceview python-support
  rhythmbox seahorse sound-juicer synaptic tomboy totem totem-gstreamer
  totem-mozilla vino yelp
0 upgraded, 140 newly installed, 0 to remove and 0 not upgraded.
Need to get 132MB/134MB of archives.
After unpacking, 562MB of additional disk space will be used.
Do you want to continue [Y/n]?

---

### Post by adult swim on 2009-01-03
have you tried installing the ubuntu-desktop package?  it may bring back some of the important stuff that was deleted.
```
sudo apt-get install ubuntu-desktop
```

edit: this is all of the stuff that would be removed if i deleted python, yikes! :)
```
  alacarte alsa-utils apport apport-gtk apt-xapian-index apturl at-spi
  bluez-cups bluez-gnome brasero capplets-data command-not-found compiz
  compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome
  compizconfig-settings-manager contact-lookup-applet cups
  cups-driver-gutenprint deskbar-applet ekiga eog evince evolution
  evolution-data-server evolution-exchange evolution-plugins evolution-webcal
  f-spot fast-user-switch-applet file-roller firefox-3.0-gnome-support
  firefox-gnome-support foomatic-db-hpijs gcalctool gconf-editor gconf2 gdebi
  gdebi-core gdm gdm-guest-session gedit gimp gksu gnome-about
  gnome-app-install gnome-applets gnome-applets-data gnome-control-center
  gnome-do gnome-do-plugins gnome-doc-utils gnome-games gnome-games-data
  gnome-keyring gnome-media gnome-media-common gnome-menus gnome-mount
  gnome-netstatus-applet gnome-orca gnome-panel gnome-panel-data gnome-pilot
  gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session
  gnome-settings-daemon gnome-spell gnome-system-monitor gnome-system-tools
  gnome-terminal gnome-terminal-data gnome-user-guide gnome-utils
  gstreamer0.10-gnomevfs gstreamer0.10-plugins-good gucharmap hal-cups-utils
  hpijs hplip hplip-data hwtest hwtest-gtk jockey-common jockey-gtk
  language-selector language-selector-common launchpad-integration
  libbonoboui2-0 libdeskbar-tracker libebook1.2-9 libecal1.2-7
  libedata-book1.2-2 libedata-cal1.2-6 libedataserverui1.2-8 libeel2-2
  libevolution3.0-cil libexchange-storage1.2-3 libgail-gnome-module libgksu2-0
  libgnome-desktop-2-7 libgnome-media0 libgnome-vfs2.0-cil libgnome2-0
  libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnome2.0-cil
  libgnomekbd-common libgnomekbd3 libgnomekbdui3 libgnomeui-0 libgnomevfs2-0
  libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgtkhtml-editor0
  libgtkhtml3.14-19 libgweather-common libgweather1 liblpint-bonobo0 libmbca0
  libmetacity0 libpanel-applet2-0 libpurple-bin lsb-release metacity
  metacity-common mousetweaks nautilus nautilus-cd-burner nautilus-data
  nautilus-sendto nautilus-share network-manager network-manager-gnome
  notification-daemon nvidia-common onboard openoffice.org-emailmerge
  openoffice.org-gnome openssl-blacklist pidgin pidgin-otr policykit-gnome
  python python-apport python-apt python-beagle python-brlapi python-cairo
  python-central python-compizconfig python-cups python-cupshelpers
  python-dbus python-debian python-gconf python-gdata python-gdbm
  python-glade2 python-gmenu python-gnome2 python-gnome2-desktop
  python-gnomecanvas python-gnupginterface python-gobject python-gst0.10
  python-gtk2 python-gtkhtml2 python-gtksourceview2 python-imaging
  python-launchpad-bugs python-launchpad-integration python-libxml2
  python-notify python-numeric python-numpy python-pkg-resources
  python-problem-report python-pyatspi python-pyorbit python-rdflib
  python-sexy python-software-properties python-support python-uno python-usb
  python-virtkey python-vte python-xapian python-xdg python-xkit rhythmbox
  screen-resolution-extra seahorse seahorse-plugins software-properties-gtk
  ssl-cert system-config-printer-common system-config-printer-gnome tomboy
  totem totem-common totem-gstreamer totem-mozilla totem-plugins
  tracker-search-tool tsclient ubufox ubuntu-desktop ubuntu-docs
  ubuntu-minimal ubuntu-system-service ufw unattended-upgrades update-manager
  update-manager-core update-notifier update-notifier-common usb-creator
  vinagre vino xnee xulrunner-1.9-gnome-support yelp

```

---

### Post by Pierrot Lafouine on 2009-01-03
Yep, one command can make a lot of damages :
apt-get remove python

The problem for a newbie like me is I'm thinking windoz.
A software doesn't work anymore ?
Uninstall - re-install makes miracle with registry under Windoz

Python and Pygames were not working on Linux.  I removed both, to re-install it.  Wrong move...

Still downloading package (download is very slow)

---

### Post by unutbu on 2009-01-03
You know, Pierrot, if the number of packages you need to install are very large, perhaps it would be quicker to reinstall. On most machines a fresh install from the LiveCD only takes between 30 min--1 hour. Though on the other hand you would need to backup your data first if it is on the same partition as Ubuntu.

---

### Post by Pierrot Lafouine on 2009-01-03
> **unutbu said:**
> You know, Pierrot, if the number of packages you need to install are very large, perhaps it would be quicker to reinstall. On most machines a fresh install from the LiveCD only takes between 30 min--1 hour. Though on the other hand you would need to backup your data first if it is on the same partition as Ubuntu.

Yes I will do that,
But I goofed, and I want to learned the max from this, hummm, little oups
And honestly, I don't know how to backup stuff under Linux, and I
have important stuff on this machine.  It worth spending a day or 2
too restore it.

About the content of the file of package-list, I cannot put it in
the post, Windows is not able to read my USB key...  Can I have 
changed file system of the key when I mounted it on Ubuntu ?

---

### Post by unutbu on 2009-01-03
I just found a simpler way to post that information (no USB key involved).

At the command line type:
```

sudo apt-get install pastebinit
```
This is a very small package -- only 52 KiB.
```

pastebinit -i ~/package-list -b http://paste.ubuntu.com
```
This will send the package-list file to paste.ubuntu.com, a free pastebin. The url to the pastebin page will be returned.

Then all you have to do is post the url here.

PS. It is possible to reformat the USB key so that it contains a FAT or NTFS filesystem. Then both Linux and Windows would be able to read it. We could show you how to do that too at some point if you are interested.

---

### Post by adult swim on 2009-01-03
if i were you i would boot the live cd and  mount your flash drive like you did to transfer that file to it and backup everything you need from your ubuntu install.  if you go to [http://www.fs-driver.org/](http://www.fs-driver.org/) you can download something that will let windows see ext2 so you can pull your info off of your flash drive.

---

### Post by Pierrot Lafouine on 2009-01-03
ok
Display is working...
Not exactly same behavior as before, but I can manage from here
Thanks you guys, for your help.

---

