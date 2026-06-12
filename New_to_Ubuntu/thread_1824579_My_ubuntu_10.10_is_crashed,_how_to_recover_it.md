---
title: "My ubuntu 10.10 is crashed, how to recover it?"
date: 2011-08-14
forum: New to Ubuntu
---

### Post by amityadav9314 on 2011-08-14
Hello!
I ran this command "sudo apt-get remove python" by mistake, not knowing the consequences, and it removed it everything
Please tell me how to restore it.
Terminal and synaptic package manager not working.
Is there really a way to restore it knowing that terminal and synaptic not working.
Please help me.

---

### Post by garvinrick4 on 2011-08-14
To get into a file system that is not bootable is done with "chroot" command.
Take a Live Cd (install CD using Try Ubuntu)
open a terminal (ctrl/alt/t)
Find your linux install sda#
```
sudo fdisk -l
``` (lower case L)
Now lets say it is sda5 for this example:
Make sure in Live Cd the internet is working (can use firefox on net)
Now copy and paste these:
```
sudo mount /dev/sda5 /mnt
``````
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done 
``````
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
``````
sudo chroot /mnt
```## Now you can install want you want not using sudo you are in root of sda5 then continue below to unmount before rebooting: (Can install packages, grub, 
or "dpkg --configure -a" to clean up dependencys or to start installing packages if
you stopped in the middle of upgrades anything you need to do really.)
```
exit
``````
for i in /dev/pts /dev /proc /sys; do sudo umount /mnt$i ; done
``````
sudo umount /mnt
``````
sudo reboot
```##Have never removed python before or read a Thread about it so if you "apt-get install python" will fix this problem is a mystery, let us know how it washes out.

---

### Post by amityadav9314 on 2011-08-14
Would this be a fresh install or would I be able to retain all my files?
I really need to retain them(some important one).
WIll it be like repair of Windows?

---

### Post by Wim Sturkenboom on 2011-08-14
To save your not-so-important (see my signature) data

[INDENT]Boot from live CD and have a usb-stck/external HD ready; after the boot insert it.

Mount your Ubuntu partition; if you had a separate partition for the home directories, mount that one (see earlier post; *_sudo mount /dev/sda5 /mnt_*).

Copy your files from /mnt to the usb-stick / external HD

Unmount the usb-stick / external HD (see earlier post; *_sudo umount /mnt_*)[/INDENT]

Why am I so cynical about the not-so-important data?
[INDENT]What would you have done if you had a serious physical disk crash? You might have been able to get it back partitally by using a professional service that charges you a hell of a lot of money for each MB that they recover.
Making backups would prevent this.

If a document that I'm working on is important for me, I always save it twice. Once on HD and once externally (e.g. usb-stick)[/INDENT]

Good luck in getting your system back up and running. Above post by garvinrick4 seems quite reliable

---

### Post by garvinrick4 on 2011-08-14
> Would this be a fresh install or would I be able to retain all my files?This is the install you have now?
Make sure you use your own sda# 
sda5 was an example you have to get yours for your linux install.
Post #4 makes all the sense in the World about keeping backups at all times.

---

### Post by amityadav9314 on 2011-08-14
output of 
sudo fdisk -l


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa3799e50

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          13        5100    40857600    7  HPFS/NTFS
/dev/sda2            5100        6974    15055872    7  HPFS/NTFS
/dev/sda3            6974       26165   154151937    f  W95 Ext'd (LBA)
/dev/sda4           26165       38914   102398976    7  HPFS/NTFS
/dev/sda5            6974       16603    77339266    7  HPFS/NTFS
/dev/sda6           16603       25770    73637888   83  Linux
/dev/sda7           25770       26165     3173376   82  Linux swap / Solaris

Disk /dev/sdb: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9aa4f4bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         490     3928032    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(488, 254, 63) logical=(489, 5, 27)
ubuntu@ubuntu:~$ 


Now please tell me my linux partition.
Is it /sda6?

---

### Post by amityadav9314 on 2011-08-14
I think it is /sda6
but when i tried this command:       sudo cp /etc/resolv.conf/mnt/etc/resolv.conf


i am getting this error.


ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf/mnt/etc/resolv.conf
cp: missing destination file operand after `/etc/resolv.conf/mnt/etc/resolv.conf'
Try `cp --help' for more information.
ubuntu@ubuntu:~$

---

### Post by garvinrick4 on 2011-08-14
You are right sda6 is correct:
Try it again I left out a space in that piece of code, sorry.

---

### Post by amityadav9314 on 2011-08-14
ok i have crossed that command and upto root.

this is the error I am getting...


root@ubuntu:/# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-docky casper unity-asset-pool libmono-getoptions2.0-cil libfolks0 libgio-cil libdmraid1.0.0.rc16 python-renderpm libatk1.0-doc libzeitgeist-gio
  libglib2.0-doc libxcb-icccm1 python-paramiko libdiscover2 librsvg2-2.18-cil libdesktop-agnostic-cfg-gconf unity-2d-launcher libpango1.0-doc
  libmono-zeroconf1.0-cil python-pyicu kdelibs-data libgdata1.4-cil libtagc0 libmono-simd2.0-cil gnome-session-common libgkeyfile1.0-cil evince-common
  libxcb-property1 ubiquity-frontend-debconf liblualib50 python-awn python-lxml python-reportlab-accel libedata-cal1.2-7 ubiquity libdebian-installer4
  squashfs-tools xresprobe discover zeitgeist libqtdee2 user-setup zeitgeist-core ubiquity-casper python-configobj cryptsetup reiserfsprogs
  python-beautifulsoup libcompfaceg1 rdate libfolks-telepathy0 python-gnomedesktop libdesktop-agnostic-vfs-gio python-xklavier devhelp-common
  libclutk-0.3-0 python-compizconfig bogl-bterm libdesktop-agnostic-fdo-glib libavahi-qt3-1 libtaglib2.0-cil sessioninstaller libtelepathy-logger1
  python-desktop-agnostic libgtk2.0-doc avant-window-navigator-data zeitgeist-fts-extension libdee-1.0-0 localechooser-data libappindicator0.1-cil
  libwmf-bin libxml2-dev unity-2d-spread telepathy-logger python-dateutil libwnck2.20-cil libmagick++3 indicator-datetime libkarma0 python-uniconvertor
  libgudev1.0-cil python-gweather libxml++2.6-2 ubiquity-ubuntu-artwork zeitgeist-datahub libcheese-gtk18 libindicate0.1-cil libutouch-geis1
  libdebconfclient0 libkeybinder0 pmount discover-data libunity-misc0 dmraid liblua50 awn-applets-common python-xlib perlmagick libzeitgeist-1.0-0
  libsubtitleeditor0 python-reportlab libesmtp5 libglademm-2.4-1c2a python-keybinder unity-2d-places libnotify0.4-cil libgnomedesktop2.20-cil python-gtop
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
98 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up gconf2 (2.31.91-0ubuntu3.1) ...
/var/lib/dpkg/info/gconf2.postinst: 52: gconf-schemas: not found
dpkg: error processing gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of gnome-applets-data:
 gnome-applets-data depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-applets-data (--configure):
 dependency problems - leaving unconfigured
Setting up update-manager-core (1:0.142.23) ...
No apport report written because the error message indicates its a followup error from a previous failure.
/var/lib/dpkg/info/update-manager-core.postinst: 10: pycentral: not found
dpkg: error processing update-manager-core (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up python-gmenu (2.30.4-0ubuntu1) ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
/var/lib/dpkg/info/python-gmenu.postinst: 1: /usr/share/gnome-menus/update-gnome-menus-cache: not found
/var/lib/dpkg/info/python-gmenu.postinst: 25: update-python-modules: not found
dpkg: error processing python-gmenu (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of gnome-menus:
 gnome-menus depends on python-gmenu (= 2.30.4-0ubuntu1); however:
  Package python-gmenu is not configured yet.
dpkg: error processing gnome-menus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of alacarte:
 alacarte depends on python-gmenu (>= 2.27.92); however:
  Package python-gmenu is not configured yet.
 alacarte depends on gnome-menus (>= 2.27.92); however:
  Package gnome-menus is not configured yet.
dpkg: error processing alacarte (--configure):
 dependency problems - leaving unconfigured
Setting up python-debian (0.1.16ubuntu1) ...
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
/var/lib/dpkg/info/python-debian.postinst: 6: update-python-modules: not found
dpkg: error processing python-debian (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of apt-xapian-index:
 apt-xapian-index depends on python-debian (>= 0.1.14); however:
  Package python-debian is not configured yet.
dpkg: error processing apt-xapian-index (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of at-spi:
 at-spi depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing at-spi (--configure):
 dependency problems - leaving unconfigured
Setting up bicyclerepair (0.9-6) ...
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
/var/lib/dpkg/info/bicyclerepair.postinst: 10: pycentral: not found
dpkg: error processing bicyclerepair (--configure):
 subprocess installed post-installation script returned error exit status 127
No apport report written because MaxReports is reached already
Setting up python-argparse (1.1-1) ...
/var/lib/dpkg/info/python-argparse.postinst: 6: update-python-modules: not found
dpkg: error processing python-argparse (--configure):
 subprocess installed post-installation script returned error exit status 127
No apport report written because MaxReports is reached alreadydpkg: dependency problems prevent configuration of computer-janitor:
 computer-janitor depends on update-manager-core (>= 1:0.98.1); however:
  Package update-manager-core is not configured yet.
 computer-janitor depends on python-argparse (>= 1.1); however:
  Package python-argparse is not configured yet.

dpkg: error processing computer-janitor (--configure):
 dependency problems - leaving unconfigured
Setting up crebs (0.9.8.5-0ppa1) ...
No apport report written because MaxReports is reached already
/var/lib/dpkg/info/crebs.postinst: 6: update-python-modules: not found
dpkg: error processing crebs (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of devhelp-common:
 devhelp-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
No apport report written because MaxReports is reached already
dpkg: error processing devhelp-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomevfs2-common:
 libgnomevfs2-common depends on gconf2 (>= 2.28.1); however:
  Package gconf2 is not configured yet.
No apport report written because MaxReports is reached already
dpkg: error processing libgnomevfs2-common (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of libgnomevfs2-0:
 libgnomevfs2-0 depends on libgnomevfs2-common (>= 1:2.24); however:
  Package libgnomevfs2-common is not configured yet.
 libgnomevfs2-0 depends on libgnomevfs2-common (<< 1:2.25); however:
  Package libgnomevfs2-common is not configured yet.
dpkg: error processing libgnomevfs2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome-vfs2.0-cil:
 libgnome-vfs2.0-cil depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnome-vfs2.0-cil (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of libgnome2-common:
 libgnome2-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing libgnome2-common (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of libgnome2-0:
 libgnome2-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 libgnome2-0 depends on libgnome2-common (>= 2.32); however:
  Package libgnome2-common is not configured yet.
 libgnome2-0 depends on libgnome2-common (<< 2.33); however:
  Package libgnome2-common is not configured yet.
dpkg: error processing libgnome2-0 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached alreadydpkg: dependency problems prevent configuration of libbonoboui2-0:
 libbonoboui2-0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.

dpkg: error processing libbonoboui2-0 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of libgnomeui-0:
 libgnomeui-0 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libgnomeui-0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libgnomeui-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnomeui-0 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of libgnome2.24-cil:
 libgnome2.24-cil depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libgnome2.24-cil depends on libgnome-vfs2.0-cil (>= 2.24.0); however:
  Package libgnome-vfs2.0-cil is not configured yet.
 libgnome2.24-cil depends on libgnomeui-0 (>= 2.22.0); however:
  Package libgnomeui-0 is not configured yet.
dpkg: error processing libgnome2.24-cil (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached alreadydpkg: dependency problems prevent configuration of libpanel-applet2-0:
 libpanel-applet2-0 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libpanel-applet2-0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.

dpkg: error processing libpanel-applet2-0 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached alreadydpkg: dependency problems prevent configuration of libgnomepanel2.24-cil:
 libgnomepanel2.24-cil depends on libpanel-applet2-0 (>= 2.26.0); however:
  Package libpanel-applet2-0 is not configured yet.
 libgnomepanel2.24-cil depends on libgnome2.24-cil (>= 2.24.0); however:
  Package libgnome2.24-cil is not configured yet.

dpkg: error processing libgnomepanel2.24-cil (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of drapes:
 drapes depends on libgnome-vfs2.0-cil (>= 2.24.0); however:
  Package libgnome-vfs2.0-cil is not configured yet.
 drapes depends on libgnome2.24-cil (>= 2.24.0); however:
  Package libgnome2.24-cil is not configured yet.
 drapes depends on libgnomepanel2.24-cil (>= 2.26.0); however:
  Package libgnomepanel2.24-cil is not configured yet.
 drapes depends on gconf2 (>= 2.10.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing drapes (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of eric:
 eric depends on bicyclerepair (>= 0.9-4.1); however:
  Package bicyclerepair is not configured yet.
No apport report written because MaxReports is reached already
dpkg: error processing eric (--configure):
 dependency problems - leaving unconfigured
Setting up gazpacho (0.7.2-2ubuntu1) ...
No apport report written because MaxReports is reached already
/var/lib/dpkg/info/gazpacho.postinst: 11: update-python-modules: not found
dpkg: error processing gazpacho (--configure):
 subprocess installed post-installation script returned error exit status 127
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of gedit:
 gedit depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gedit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gedit-plugins:
 gedit-plugins depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
 gedit-plugins depends on gedit (>= 2.29.3); however:
  Package gedit is not configured yet.
dpkg: error processing gedit-plugins (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
Setting up gimp (2.6.10-1ubuntu3.3) ...
No apport report written because MaxReports is reached already
/var/lib/dpkg/info/gimp.postinst: 11: update-python-modules: not found
dpkg: error processing gimp (--configure):
 subprocess installed post-installation script returned error exit status 127
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of libgksu2-0:
 libgksu2-0 depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing libgksu2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gksu:
 gksu depends on libgksu2-0 (>= 2.0.8); however:
  Package libgksu2-0 is not configured yet.
dpkg: error processing gksu (--configure):
 dependency problems - leaving unconfigured
Setting up gnome-doc-utils (0.20.1-1ubuntu1) ...
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
/var/lib/dpkg/info/gnome-doc-utils.postinst: 6: update-python-modules: not found
dpkg: error processing gnome-doc-utils (--configure):
 subprocess installed post-installation script returned error exit status 127
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of gnome-media-common:
 gnome-media-common depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-media-common (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of libgnome-media0:
 libgnome-media0 depends on gnome-media-common (>= 2.31); however:
  Package gnome-media-common is not configured yet.
 libgnome-media0 depends on gnome-media-common (<< 2.32); however:
  Package gnome-media-common is not configured yet.
dpkg: error processing libgnome-media0 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of gstreamer0.10-plugins-good:
 gstreamer0.10-plugins-good depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing gstreamer0.10-plugins-good (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-media:
 gnome-media depends on libgnome-media0; however:
  Package libgnome-media0 is not configured yet.
 gnome-media depends on gnome-media-common (>= 2.31); however:
  Package gnome-media-common is not configured yet.
 gnome-media depends on gnome-media-common (<< 2.32); however:
  Package gnome-media-common is not configured yet.
 gnome-media depends on gstreamer0.10-plugins-good; however:
  Package gstreamer0.10-plugins-good is not configured yet.
dpkg: error processing gnome-media (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnome2:
 python-gnome2 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 python-gnome2 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 python-gnome2 depends on libgnomeui-0 (>= 2.22.0); however:
  Package libgnomeui-0 is not configured yet.
 python-gnome2 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing python-gnome2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-pyatspi:
 python-pyatspi depends on at-spi (>= 1.31.91-0ubuntu1); however:
  Package at-spi is not configured yet.
 python-pyatspi depends on at-spi (<< 1.31.91-0ubuntu1.1~); however:
  Package at-spi is not configured yet.
 python-pyatspi depends on python-gnome2; however:
  Package python-gnome2 is not configured yet.
dpkg: error processing python-pyatspi (--configure):
 dependency problems - leaving unconfigured
Setting up python-brlapi (4.2-3ubuntu1) ...
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
/var/lib/dpkg/info/python-brlapi.postinst: 8: update-python-modules: not found
dpkg: error processing python-brlapi (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of gnome-orca:
 gnome-orca depends on python-pyatspi (>= 1.22.0) | python-pyatspi2; however:
  Package python-pyatspi is not configured yet.
  Package python-pyatspi2 is not installed.
 gnome-orca depends on python-gnome2 (>= 2.6.2); however:
  Package python-gnome2 is not configured yet.
 gnome-orca depends on python-brlapi; however:
  Package python-brlapi is not configured yet.
dpkg: error processing gnome-orca (--configure):
 dependency problems - leaving unconfigured
Setting up gnome-sudoku (1:2.32.0-0ubuntu1) ...
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
/var/lib/dpkg/info/gnome-sudoku.postinst: 11: update-python-modules: not found
dpkg: error processing gnome-sudoku (--configure):
 subprocess installed post-installation script returned error exit status 127
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of yelp:
 yelp depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
 yelp depends on gnome-doc-utils (>= 0.17.2); however:
  Package gnome-doc-utils is not configured yet.
dpkg: error processing yelp (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-user-guide:
 gnome-user-guide depends on yelp; however:
  Package yelp is not configured yet.
dpkg: error processing gnome-user-guide (--configure):
 dependency problems - leaving unconfigured
Setting up googlecl (0.9.8-1) ...
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
/var/lib/dpkg/info/googlecl.postinst: 6: update-python-modules: not found
dpkg: error processing googlecl (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up gtk-recordmydesktop (0.3.8-3ubuntu1) ...
No apport report written because MaxReports is reached already
/var/lib/dpkg/info/gtk-recordmydesktop.postinst: 11: update-python-modules: not found
dpkg: error processing gtk-recordmydesktop (--configure):
 subprocess installed post-installation script returned error exit status 127
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of gufw:
 gufw depends on python-gnome2; however:
  Package python-gnome2 is not configured yet.
dpkg: error processing gufw (--configure):
 dependency problems - leaving unconfigured
Setting up hplip (3.10.6-1ubuntu10.2) ...
No apport report written because MaxReports is reached already
Creating/updating hplip user account...
/var/lib/dpkg/info/hplip.postinst: 120: update-python-modules: not found
dpkg: error processing hplip (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of ibus:
 ibus depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing ibus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ibus-pinyin:
 ibus-pinyin depends on ibus (>= 1.2.99); however:
  Package ibus is not configured yet.
dpkg: error processing ibus-pinyin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ibus-table:
 ibus-table depends on ibus (>= 1.2); however:
  Package ibus is not configured yet.
dpkg: error processing ibus-table (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
Processing triggers for menu ...
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 gconf2
 gnome-applets-data
 update-manager-core
 python-gmenu
 gnome-menus
 alacarte
 python-debian
 apt-xapian-index
 at-spi
 bicyclerepair
 python-argparse
 computer-janitor
 crebs
 devhelp-common
 libgnomevfs2-common
 libgnomevfs2-0
 libgnome-vfs2.0-cil
 libgnome2-common
 libgnome2-0
 libbonoboui2-0
 libgnomeui-0
 libgnome2.24-cil
 libpanel-applet2-0
 libgnomepanel2.24-cil
 drapes
 eric
 gazpacho
 gedit
 gedit-plugins
 gimp
 libgksu2-0
 gksu
 gnome-doc-utils
 gnome-media-common
 libgnome-media0
 gstreamer0.10-plugins-good
 gnome-media
 python-gnome2
 python-pyatspi
 python-brlapi
 gnome-orca
 gnome-sudoku
 yelp
 gnome-user-guide
 googlecl
 gtk-recordmydesktop
 gufw
 hplip
 ibus
 ibus-pinyin
 ibus-table
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/#

---

### Post by garvinrick4 on 2011-08-14
That is because you removed python by accident in your original post.
So install it and see if it works out. As I said never removed python before it is essential
so lets see what she does when we install it again. One at a time let each one finish.
```
apt-get install python
```
```
dpkg --configure -a
```
```
apt-get update && apt-get upgrade
```
```
dpkg --configure -a
```

---

### Post by amityadav9314 on 2011-08-14
Okay everything is done correctly
But after EXIT command when I run this:-     for i in /dev/pts /dev /proc /sys; do sudo umount /mnt$i ; done
I am getting error....


root@ubuntu:/# exit
exit
There are stopped jobs.
root@ubuntu:/# for i in /dev/pts /dev /proc /sys; do sudo umount /mnt$i ; done
umount: /mnt/dev/pts: not found
umount: /mnt/dev: not found
umount: /mnt/proc: not found
umount: /mnt/sys: not found
root@ubuntu:/#

---

### Post by garvinrick4 on 2011-08-14
When you run from the same root:
dpkg --configure -a
It is suppose to give you nothing no response did it.
Did it run the update and upgrade ok, did it install python Ok?

Telling you there are stopped jobs I believe.
Run the
dpkg --configure -a 
again, what does it do? Could fix the stopped jobs.

## The exit command takes it out of root so you can umount.

---

### Post by garvinrick4 on 2011-08-14
My session is done for this evening and will be back online in 9 or 10 hrs hope you reboot
and can boot into your Ubuntu install. If not tell what I asked, if you are all Ok now let us know please.

---

### Post by amityadav9314 on 2011-08-14
AT this time I am Installing many things manually from synaptic by opening the synaptic manager by typing "synaptic" in the root terminal. I still can not exit it. I am getting same error I will tell you for sure everything I will do.Thank you for all your valuable help.

---

### Post by garvinrick4 on 2011-08-14
I got to believe right now you are just in root of Live Cd and not in chroot of sda6. Sooner or later you have
to reboot and see if install is at a bootable point. Do not know quite where you are really. If bootable, install
from inside your install and not chroot from live cd now. I know this is hard for you to understand when you are new to linux. 
Just from now on watch what you remove!!! Will be around and hope things work out for you.

---

### Post by amityadav9314 on 2011-08-14
> **garvinrick4 said:**
> I got to believe right now you are just in root of Live Cd and not in chroot of sda6..

I think I am in chroot of sda6 as i can open the synaptic from the chroot and it open as a windows other than the synaptic of liveCD.

---

### Post by amityadav9314 on 2011-08-14
> **garvinrick4 said:**
> If bootable, install
from inside your install and not chroot from live cd now. I know this is hard for you to understand when you are new to linux. 


One thing i really do not understand that after changing to chroot to sda6 , I am doing all those thing in my main linux install drive, i.e. sda6?
 I am really a newbie in LINUX

---

### Post by amityadav9314 on 2011-08-14
Okay now lastly I successful exit the command and unmounted but now another weird problem is occurring while booting the system.

It says:-


1:- [12.697771] /build/buildd/linux-2.6.32/drivers.hid/usbhid/hid-core.c: usb_submit_urb(center) failed.
(That is the error which comes at the very starting of booting screen.

2:-Then a window appears which says:---UBUNTU IS RUNNING IN LOW GRAPHICS MODE
YOUR SCREEN, GRAPHICS CARD, AND INPUT DEVICE SETTINGS COULD NOT BE DETECTED CORRECTLY, YOU WILL NEED TO CONFIGURE THIS YOURSELF.


3:-after that another windows pop up saying, "stand by one minute while the display starts.


But it never starts, The boot screen exists  forever...:(

---

### Post by amityadav9314 on 2011-08-15
Yippee......
Hey man thanks for all your help.
I rebooted successfully.
I think this command has helped me....
sudo apt-get install ubuntu-desktop

---

### Post by kroq-gar78 on 2011-08-15
Yay!

If everything is all and well, please mark your thread as "Solved" by going to "Thread Tools" in the top-left corner of the top post on the forum and select "Mark this thread as solved" or something along those lines.

Glad to see that your problem is solved.

P.S. When you chroot'd, you were doing stuff on your drive/installation, NOT the live CD.

---

### Post by amityadav9314 on 2011-08-15
> **kroq-gar78 said:**
> Yay!

If everything is all and well, please mark your thread as "Solved" by going to "Thread Tools" in the top-left corner of the top post on the forum and select "Mark this thread as solved" or something along those lines.

Glad to see that your problem is solved.

P.S. When you chroot'd, you were doing stuff on your drive/installation, NOT the live CD.

Okay I am going to mark it as a Solved.
Yeah today I learned that when we chroot, we work on our linux installation drive.
Thanks again to every one.....:)

---

### Post by amityadav9314 on 2011-08-15
> **garvinrick4 said:**
> I got to believe right now you are just in root of Live Cd and not in chroot of sda6. Sooner or later you have
to reboot and see if install is at a bootable point. Do not know quite where you are really. If bootable, install
from inside your install and not chroot from live cd now. I know this is hard for you to understand when you are new to linux. 
Just from now on watch what you remove!!! Will be around and hope things work out for you.

Hey Garvinrick4, I solved it ,
I solved that very big problem but another problem has occured, now i lost the windows option from the boot menu.
I will probably search the internet to get it back.


Thank you very very much for your valuable help. I love to see you reply to this.

---

