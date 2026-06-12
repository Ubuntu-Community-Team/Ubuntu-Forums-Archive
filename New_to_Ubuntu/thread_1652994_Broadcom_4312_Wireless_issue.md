---
title: "Broadcom 4312 Wireless issue"
date: 2010-12-26
forum: New to Ubuntu
---

### Post by alanzee on 2010-12-26
Hi all, I'm new to Linux. I am using a Broadcom 4312 card, and I can't seem to get wireless internet access at home.
[This]("http://ubuntuforums.org/showthread.php?t=1604868") post seems quite relevant, except that I have no idea what it means or what I should do. I've messed around with various settings to no avail (I'm especially free to do that since I don't have persistent Linux.)
Any help is appreciated - thanks in advance! :D

In case you need further information:
I am booting Ubuntu Netbook Remix 10.10 from a USB drive. I have not actually installed it yet since I would like to sort out some wireless issues beforehand.

I have a tablet, a HP Pavilion Entertainment PC tx2500.

```
**lspci:**
Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet Controller (rev 02)

Also, r8169 Gigabit Ethernet driver 2.3LK-NAP driver

**lsusb:**
Bus 007 Device 003: ID 056a:0093 Wacom Co., Ltd TPC93
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader

**ifconfig:**
etho0	Link encap: Ethernet  HWaddr 00:1e:68:b4:f3:52
	UP BROADCAST MULTICAST  MTU:1500  Metric:1
	RX packets:0 errors:0 dropped:0 overruns:0 frame:0
	TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
	collisions:0 txqueuelen:1000
	RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
	Interrupt:43 Base address:0x6000

**iwconfig:**
eth0	no wireless extensions

**dmesg:**
[...]
b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[...]
r8169 0000:09:00.0: eth0: link down
ADDRCONF(NETDEV UP): etho0: link is not ready
phy0: Selected rate control algorithm 'minstrel'
Registered led device: b43-phy0::tx
Registered led device: b43-phy0::rx
Registered led device: b43-phy0::radio
Broadcom 43xx driver loaded [ Features: pL, Firmware-ID; FW13 ]
[...]
b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
b43-phy0 ERROR: Firmware file "b43-open/ucode15/fw" not found
b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[...]
b43-pci-bridge 0000:08:00.0: PCI INT A disabled

**sudo lshw -C network:**
PCI (sysfs)

**iwlist scan:**
lo	Interface doesn't support scanning

eth0	Interface doesn't support scanning

**lsb_release -d:**
Description:	Ubuntu 10.10

**uname -mr:**
2.6.35-22-generic i686

 * Reconfiguring network interfaces... [OK]
```

---

### Post by Sef on 2010-12-26
Read this [sticky]("http://ubuntuforums.org/showthread.php?t=1604868").

---

### Post by mikewhatever on 2010-12-26
BCM 4312 and other Broadcom cards require proprietary drivers to work. You can only install the drivers after installing Ubuntu. There is a Driver utility under System->Administration just for that. Now, BCM 4312 has two drivers to choose from, b43 and STA, go for the recommended one.

---

### Post by halj32 on 2010-12-26
> **mikewhatever said:**
> BCM 4312 and other Broadcom cards require proprietary drivers to work. You can only install the drivers after installing Ubuntu. There is a Driver utility under System->Administration just for that. Now, BCM 4312 has two drivers to choose from, b43 and STA, go for the recommended one.

use the sta drivers, Ive never had any problem with them.
re b43 Ive never been able to get this driver to work. 
ndiswrapper works well but a bit fiddly at first

goodluck

---

### Post by alanzee on 2010-12-26
> **Sef said:**
> Read this [sticky]("http://ubuntuforums.org/showthread.php?t=1604868").

Yes, I mentioned in my post that I did, but as I'm entirely new to linux/ubuntu I'm having difficulty following the advice.

I tried
System > Administration > Synaptic Package Manager > Search:  firmware-b43-lpphy-installer > Click Mark > Click install >  Close,
and it worked without errors, but my wireless is still down.

From the "Additional Drivers" program, I tried installing "Broadcom STA wireless driver", but it gave the same error ("SystemError: installArchives() failed")
Also, program ubiquity failed simueltaneously

> **mikewhatever said:**
> BCM 4312 and other Broadcom cards require proprietary drivers to work. You can only install the drivers after installing Ubuntu. There is a Driver utility under System->Administration just for that. Now, BCM 4312 has two drivers to choose from, b43 and STA, go for the recommended one.

I don't think that's true. I can install other proprietary drivers (such as the one from my modem) just fine booting from my usb.

> **halj32 said:**
> use the sta drivers, Ive never had any problem with them.
re b43 Ive never been able to get this driver to work. 
ndiswrapper works well but a bit fiddly at first

goodluck

*How* do I use the sta drivers?
I've also tried the following unsuccessfully (errors related to dpkg i think):

```
$ sudo apt-get --purge remove bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  bcmwl-kernel-source
0 upgraded, 0 newly installed, 1 to remove and 210 not upgraded.
2 not fully installed or removed.
After this operation, 2,597kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 123609 files and directories currently installed.)
Removing bcmwl-kernel-source ...
update-initramfs: deferring update (trigger activated)
/usr/sbin/update-initramfs: 15: cannot create /cdrom/casper/initrd.lz.new: Read-only file system
dpkg: error processing bcmwl-kernel-source (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)
``````
$ sudo apt-get install patch
Reading package lists... Done
Building dependency tree       
Reading state information... Done
patch is already the newest version.
The following packages will be REMOVED:
  bcmwl-kernel-source
0 upgraded, 0 newly installed, 1 to remove and 210 not upgraded.
2 not fully installed or removed.
After this operation, 2,597kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 123609 files and directories currently installed.)
Removing bcmwl-kernel-source ...
update-initramfs: deferring update (trigger activated)
/usr/sbin/update-initramfs: 15: cannot create /cdrom/casper/initrd.lz.new: Read-only file system
dpkg: error processing bcmwl-kernel-source (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)
``````
$ sudo apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcmwl-kernel-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 210 not upgraded.
2 not fully installed or removed.
Need to get 0B/896kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package bcmwl-kernel-source.
(Reading database ... 123610 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 5.60.48.36+bdcom-0ubuntu5 (using .../bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb) ...
Unpacking replacement bcmwl-kernel-source ...
Setting up initramfs-tools (0.98.1ubuntu6) ...
update-initramfs: deferring update (trigger activated)
/usr/sbin/update-initramfs: 15: cannot create /cdrom/casper/initrd.lz.new: Read-only file system
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu5) ...
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 2.6.35-22-generic
Building for architecture i686
Building initial module for 2.6.35-22-generic
Done.

wl.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.35-22-generic/updates/dkms/

depmod....

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
/usr/sbin/update-initramfs: 15: cannot create /cdrom/casper/initrd.lz.new: Read-only file system
dpkg: error processing bcmwl-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 initramfs-tools
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)
```Finally, I think I read somewhere to attempt uninstalling dpkg, so I tried that:
```
Reading package lists...
Building dependency tree...
Reading state information...
The following packages were automatically installed and are no longer required:
  libclucene0ldbl libsdl1.2debian libsdl1.2debian-alsa libts-0.0-0 libmodplug1
  libqca2 libegl1-mesa libegl1-mesa-drivers libilmbase6 ttf-dejavu-extra lynx
  oxygen-icon-theme libqt4-test libqt4-sql-mysql libqt4-dbus
  libboost-program-options1.42.0 libxcb-xv0 libkdecore5 mysql-client-core-5.1
  shared-desktop-ontologies libxcb-xfixes0 mysql-common libxine1-bin odbcinst
  virtuoso-minimal libqt4-xmlpatterns mysql-server-core-5.1 libdirectfb-1.2-9
  libgles2-mesa libqapt1 python-sip libhal1 libvirtodbc0 odbcinst1debian2
  libqtcore4 libgif4 libxcb-shape0 libopenexr6 docbook-xsl-doc-html
  libthreadweaver4 libhal-storage1 localechooser-data libqt4-sql libkimap4
  libstreamanalyzer0 libqt4-xml libkntlm4 libqt4-network ttf-dejavu libkmime4
  libmysqlclient16 smartdimmer libattica0 tsconf libakonadi-kabc4 libkjsapi4
  libstreams0 hal-info virtuoso-opensource-6.1-common libqt4-script libssh-4
  libreadline5 libiodbc2 libmpcdec6 libmng1 virtuoso-opensource-6.1-bin
  libxine1-console
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  debconf-english docbook-xsl-doc-html hal-info libakonadi-kabc4 libasound2
  libattica0 libboost-program-options1.42.0 libclucene0ldbl libdirectfb-1.2-9
  libegl1-mesa libegl1-mesa-drivers libgif4 libgles2-mesa libhal-storage1
  libhal1 libilmbase6 libiodbc2 libkdecore5 libkimap4 libkjsapi4 libkmime4
  libkntlm4 libmng1 libmodplug1 libmpcdec6 libmysqlclient16 libopenexr6
  libqapt1 libqca2 libqt4-dbus libqt4-network libqt4-script libqt4-sql
  libqt4-sql-mysql libqt4-test libqt4-xml libqt4-xmlpatterns libqtcore4
  libreadline5 libsdl1.2debian libsdl1.2debian-alsa libssh-4
  libstreamanalyzer0 libstreams0 libthreadweaver4 libts-0.0-0 libvirtodbc0
  libxcb-shape0 libxcb-xfixes0 libxcb-xv0 libxine1-bin libxine1-console lynx
  lynx-cur mysql-client-core-5.1 mysql-common mysql-server-core-5.1 odbcinst
  odbcinst1debian2 oxygen-icon-theme python python-minimal python-sip
  shared-desktop-ontologies smartdimmer tsconf ttf-dejavu ttf-dejavu-extra
  virtuoso-minimal virtuoso-opensource-6.1-bin virtuoso-opensource-6.1-common
Suggested packages:
  libqca2-plugin-cyrus-sasl libqca2-plugin-gnupg libqca2-plugin-ossl
  libqca2-plugin-pkcs11 libqt4-dev lynx-cur-wrapper python-doc python-tk
  python-profiler
The following packages will be REMOVED:
  acpi-support* acpid* aisleriot* alacarte* alsa-base* alsa-utils* anacron*
  apparmor* apparmor-utils* appmenu-gtk* apport* apport-gtk*
  apt-transport-https* apt-xapian-index* aptdaemon* apturl* apturl-common*
  aspell* aspell-en* at* at-spi* avahi-autoipd* avahi-daemon* avahi-utils*
  bamfdaemon* baobab* bash* bash-completion* bcmwl-kernel-source bind9-host*
  binfmt-support* bluez* bluez-cups* brltty* brltty-x11* btrfs-tools* byobu*
  ca-certificates* capplets-data* casper* checkbox* checkbox-gtk* cheese*
  cheese-common* cli-common* command-not-found* computer-janitor*
  computer-janitor-gtk* console-setup* consolekit* couchdb-bin* cron*
  cryptsetup* cups* cups-bsd* cups-client* cups-driver-gutenprint* dash* dbus*
  dbus-x11* debconf-i18n* defoma* desktopcouch* dhcp3-client*
  dictionaries-common* dmraid* dmsetup* dnsutils* doc-base* docbook-xml*
  ecryptfs-utils* empathy* eog* erlang-base* erlang-crypto* erlang-inets*
  erlang-mnesia* erlang-public-key* erlang-runtime-tools* erlang-ssl*
  erlang-syntax-tools* erlang-xmerl* evince* evolution* evolution-data-server*
  evolution-exchange* evolution-indicator* evolution-plugins*
  evolution-webcal* file-roller* firefox* firefox-branding*
  firefox-gnome-support* fontconfig* fontconfig-config* foo2zjs*
  foomatic-db-compressed-ppds* foomatic-db-engine* foomatic-filters*
  friendly-recovery* fuse-utils* gcalctool* gconf-defaults-service*
  gconf-editor* gconf2* gconf2-common* gdb* gdm* gedit* ghostscript*
  ghostscript-cups* ghostscript-x* gksu* gnome-about*
  gnome-accessibility-themes* gnome-applets* gnome-applets-data*
  gnome-bluetooth* gnome-codec-install* gnome-control-center*
  gnome-dictionary* gnome-disk-utility* gnome-doc-utils* gnome-games-common*
  gnome-icon-theme* gnome-keyring* gnome-mag* gnome-mahjongg* gnome-media*
  gnome-media-common* gnome-menus* gnome-nettool* gnome-orca* gnome-panel*
  gnome-panel-data* gnome-power-manager* gnome-screensaver* gnome-screenshot*
  gnome-search-tool* gnome-session* gnome-session-bin* gnome-session-canberra*
  gnome-settings-daemon* gnome-sudoku* gnome-system-log* gnome-system-monitor*
  gnome-system-tools* gnome-terminal* gnome-terminal-data*
  gnome-themes-selected* gnome-themes-ubuntu* gnome-user-guide* gnome-utils*
  gparted* grub-common* grub-pc* gstreamer0.10-alsa* gstreamer0.10-nice*
  gstreamer0.10-plugins-base-apps* gstreamer0.10-plugins-good*
  gstreamer0.10-pulseaudio* gstreamer0.10-x* gtk2-engines*
  gtk2-engines-murrine* gtk2-engines-pixbuf* gucharmap* gvfs* gvfs-backends*
  gvfs-fuse* gwibber* gwibber-service* hpijs* hplip* hplip-cups* hplip-data*
  humanity-icon-theme* hunspell-en-ca* hunspell-en-us* ibus* ibus-gtk*
  ibus-pinyin* ibus-table* indicator-applet* indicator-applet-session*
  indicator-application* indicator-appmenu* indicator-datetime* indicator-me*
  indicator-messages* indicator-session* indicator-sound* iputils-ping*
  irqbalance* jfsutils* jockey-common* jockey-gtk* kbd* kerneloops-daemon*
  language-pack-bn* language-pack-bn-base* language-pack-de*
  language-pack-de-base* language-pack-en* language-pack-en-base*
  language-pack-es* language-pack-es-base* language-pack-fr*
  language-pack-fr-base* language-pack-gnome-bn* language-pack-gnome-bn-base*
  language-pack-gnome-de* language-pack-gnome-de-base* language-pack-gnome-en*
  language-pack-gnome-en-base* language-pack-gnome-es*
  language-pack-gnome-es-base* language-pack-gnome-fr*
  language-pack-gnome-fr-base* language-pack-gnome-xh*
  language-pack-gnome-xh-base* language-pack-gnome-zh-hans*
  language-pack-gnome-zh-hans-base* language-pack-xh* language-pack-xh-base*
  language-pack-zh-hans* language-pack-zh-hans-base* language-selector*
  language-selector-common* language-support-en* language-support-writing-en*
  launchpad-integration* libapparmor-perl* libappindicator0.1-cil*
  libappindicator1* libart2.0-cil* libasound2-plugins* libatspi1.0-0*
  libavahi-ui0* libbamf0* libbind9-60* libbonoboui2-0* libbrasero-media1*
  libcairo-perl* libcairo2* libcairomm-1.0-1* libcamel1.2-14*
  libcanberra-gtk-module* libcanberra-gtk0* libcanberra-pulse*
  libcheese-gtk18* libclutk-0.3-0* libclutter-1.0-0* libclutter-gtk-0.10-0*
  libcrypt-passwdmd5-perl* libcryptui0* libcurl3* libcurl3-gnutls*
  libdbusmenu-gtk1* libdigest-sha1-perl* libdns66* libebackend1.2-0*
  libebook1.2-9* libecal1.2-7* libedata-book1.2-2* libedata-cal1.2-7*
  libedataserver1.2-13* libedataserverui1.2-8* libegroupwise1.2-13*
  libevdocument3* libevolution* libevview3* libfile-copy-recursive-perl*
  libfont-afm-perl* libfontconfig1* libfreezethaw-perl* libgail-common*
  libgail18* libgconf2-4* libgconf2.0-cil* libgcr0* libgd2-xpm* libgdata7*
  libgdict-1.0-6* libgdu-gtk0* libgdu0* libgksu2-0* libglade2-0*
  libglade2.0-cil* libgladeui-1-9* libglew1.5* libglib-perl* libglib2.0-cil*
  libgmime2.4-cil* libgnome-bluetooth8* libgnome-desktop-2-17*
  libgnome-media0* libgnome-vfs2.0-cil* libgnome-window-settings1*
  libgnome2-0* libgnome2-canvas-perl* libgnome2-common* libgnome2-perl*
  libgnome2-vfs-perl* libgnome2.24-cil* libgnomecanvas2-0* libgnomekbd-common*
  libgnomekbd4* libgnomepanel2.24-cil* libgnomeui-0* libgnomevfs2-0*
  libgnomevfs2-common* libgnomevfs2-extra* libgphoto2-2* libgpod-common*
  libgpod4* libgs8* libgstfarsight0.10-0* libgtk2-perl* libgtk2.0-0*
  libgtk2.0-bin* libgtk2.0-cil* libgtkhtml-editor0* libgtkhtml3.14-19*
  libgtkmm-2.4-1c2a* libgtksourceview2.0-0* libgtkspell0* libgucharmap7*
  libgupnp-1.0-3* libgupnp-igd-1.0-3* libgweather-common* libgweather1*
  libgwibber0* libhpmud0* libhtml-format-perl* libhtml-parser-perl*
  libhtml-tagset-perl* libhtml-tree-perl* libice6* libido-0.1-0*
  libimobiledevice1* libindicate-gtk2* libindicator1* libisccfg60*
  liblaunchpad-integration1* liblaunchpad-integration1.0-cil*
  liblocale-gettext-perl* libmagickcore3* libmagickwand3* libmailtools-perl*
  libmetacity-private0* libmldbm-perl* libmono-addins-gui0.2-cil*
  libmono-addins0.2-cil* libmono-cairo2.0-cil* libmutter-private0*
  libnautilus-extension1* libndesk-dbus-glib1.0-cil* libndesk-dbus1.0-cil*
  libnet-dbus-perl* libnice0* libnm-glib2* libnm-util1* libnotify1*
  libnss-mdns* liboobs-1-5* libpam-ck-connector* libpam-gnome-keyring*
  libpam-runtime* libpanel-applet2-0* libpango-perl* libpango1.0-0*
  libpango1.0-common* libpangomm-1.4-1* libpaper-utils* libpaper1*
  libparted0debian1* libperl5.10* libpolkit-gtk-1-0* libpoppler-glib5*
  libpoppler7* libpulse-browse0* libpulse-mainloop-glib0* libpulse0*
  libpurple-bin* libpurple0* libraptor1* librasqal2* librdf0* librpc-xml-perl*
  librsvg2-2* librsvg2-common* libsane* libsane-hpaio* libslp1* libsm6*
  libsnmp15* libsoup-gnome2.4-1* libspectre1* libstartup-notification0*
  libsyncdaemon-1.0-1* libtelepathy-farsight0* libterm-readkey-perl*
  libtext-charwidth-perl* libtext-iconv-perl* libtext-wrapi18n-perl*
  libtie-ixhash-perl* libtimedate-perl* libtotem-plparser17*
  libubuntuone-1.0-1* libunique-1.0-0* libunity-misc0* libunity0* liburi-perl*
  libutempter0* libuuid-perl* libvte9* libwebkit-1.0-2* libwnck22*
  libwww-perl* libxaw7* libxft2* libxklavier16* libxml-parser-perl*
  libxml-twig-perl* libxml-xpath-perl* libxmu6* libxres1* libxss1* libxt6*
  libxtst6* libxvmc1* libxxf86dga1* light-themes* linux-generic*
  linux-image-2.6.35-22-generic* linux-image-generic* linux-sound-base*
  lm-sensors* login* logrotate* lsb-release* lupin-casper* man-db*
  media-player-info* memtest86+* metacity* metacity-common* mlocate*
  mousetweaks* mutter* mutter-common* myspell-en-au* myspell-en-gb*
  myspell-en-za* nautilus* nautilus-data* nautilus-sendto*
  nautilus-sendto-empathy* nautilus-share* network-manager*
  network-manager-gnome* network-manager-pptp* network-manager-pptp-gnome*
  notify-osd* ntfs-3g* ntfsprogs* ntpdate* nvidia-common* obex-data-server*
  onboard* openoffice.org-base-core* openoffice.org-calc*
  openoffice.org-common* openoffice.org-core* openoffice.org-draw*
  openoffice.org-emailmerge* openoffice.org-gnome* openoffice.org-gtk*
  openoffice.org-help-en-us* openoffice.org-impress* openoffice.org-math*
  openoffice.org-style-human* openoffice.org-writer* openssh-client* openssl*
  parted* pcmciautils* perl* perl-modules* plymouth-label*
  plymouth-theme-ubuntu-logo* plymouth-theme-ubuntu-text* pm-utils* pnm2ppa*
  policykit-1* policykit-1-gnome* poppler-utils* popularity-contest* ppp*
  pppconfig* pppoeconf* pptp-linux* pulseaudio* pulseaudio-esound-compat*
  pulseaudio-module-bluetooth* pulseaudio-module-gconf* pulseaudio-module-x11*
  pulseaudio-utils* pxljr* python-appindicator* python-apport* python-apt*
  python-aptdaemon* python-aptdaemon-gtk* python-argparse* python-avahi*
  python-brlapi* python-cairo* python-configglue* python-couchdb*
  python-crypto* python-cups* python-cupshelpers* python-dbus* python-debian*
  python-desktopcouch-records* python-egenix-mxdatetime*
  python-egenix-mxtools* python-farsight* python-gconf* python-gdbm*
  python-glade2* python-gmenu* python-gnome2* python-gnomeapplet*
  python-gnomecanvas* python-gnomekeyring* python-gnupginterface*
  python-gobject* python-gobject-cairo* python-gst0.10* python-gtk2*
  python-gtksourceview2* python-gtkspell* python-httplib2* python-ibus*
  python-imaging* python-indicate* python-launchpad-integration*
  python-launchpadlib* python-lazr.restfulclient* python-lazr.uri*
  python-libproxy* python-libxml2* python-louis* python-mako*
  python-markupsafe* python-newt* python-notify* python-oauth* python-openssl*
  python-pam* python-papyon* python-pexpect* python-pkg-resources*
  python-problem-report* python-protobuf* python-pyatspi* python-pycurl*
  python-pyicu* python-pyinotify* python-pyorbit* python-rdflib*
  python-serial* python-simplejson* python-smbc* python-software-properties*
  python-speechd* python-telepathy* python-twisted-bin* python-twisted-core*
  python-twisted-names* python-twisted-web* python-ubuntuone*
  python-ubuntuone-client* python-ubuntuone-storageprotocol* python-uno*
  python-virtkey* python-vte* python-wadllib* python-webkit* python-wnck*
  python-xapian* python-xdg* python-xkit* python-zope.interface* quadrapassel*
  rarian-compat* reiserfsprogs* rhythmbox* rhythmbox-plugin-cdrecorder*
  rhythmbox-plugins* rhythmbox-ubuntuone-music-store* rsync* rsyslog* rtkit*
  samba-common* samba-common-bin* sane-utils* screen* screen-resolution-extra*
  screensaver-default-images* seahorse* sessioninstaller* sgml-base*
  sgml-data* shotwell* simple-scan* smbclient* software-center*
  software-properties-gtk* speech-dispatcher* splix* ssh-askpass-gnome*
  ssl-cert* synaptic* system-config-printer-common*
  system-config-printer-gnome* system-config-printer-udev*
  system-tools-backends* tcpdump* telepathy-butterfly* telepathy-gabble*
  telepathy-haze* telepathy-idle* telepathy-salut* tomboy* totem*
  totem-common* totem-mozilla* totem-plugins* transmission-gtk*
  ttf-ubuntu-font-family* ttf-unfonts-core* ubiquity* ubiquity-casper*
  ubiquity-frontend-gtk* ubufox* ubuntu-artwork* ubuntu-docs* ubuntu-minimal*
  ubuntu-mono* ubuntu-netbook* ubuntu-netbook-default-settings*
  ubuntu-sso-client* ubuntu-standard* ubuntu-system-service*
  ubuntu-wallpapers* ubuntuone-client* ubuntuone-client-gnome* ucf* udisks*
  ufw* unattended-upgrades* unity* unity-asset-pool* unity-place-applications*
  unity-place-files* uno-libs3* update-inetd* update-manager*
  update-manager-core* update-notifier* update-notifier-common* upower* ure*
  ureadahead* usb-creator-common* usb-creator-gtk* usb-modeswitch*
  usb-modeswitch-data* usbmuxd* user-setup* uuid-runtime* w3m* wamerican*
  wbritish* wget* wireless-crda* wpasupplicant* x-ttcidfont-conf* x11-apps*
  x11-common* x11-session-utils* x11-utils* x11-xfs-utils* x11-xkb-utils*
  x11-xserver-utils* xdg-user-dirs-gtk* xfonts-100dpi* xfonts-75dpi*
  xfonts-base* xfonts-encodings* xfonts-mathml* xfonts-scalable* xfonts-utils*
  xfsprogs* xinit* xml-core* xorg* xscreensaver-data* xscreensaver-gl*
  xserver-common* xserver-xorg* xserver-xorg-core* xserver-xorg-input-all*
  xserver-xorg-input-evdev* xserver-xorg-input-mouse*
  xserver-xorg-input-synaptics* xserver-xorg-input-vmmouse*
  xserver-xorg-input-wacom* xserver-xorg-video-all* xserver-xorg-video-apm*
  xserver-xorg-video-ark* xserver-xorg-video-ati* xserver-xorg-video-chips*
  xserver-xorg-video-cirrus* xserver-xorg-video-fbdev*
  xserver-xorg-video-geode* xserver-xorg-video-i128* xserver-xorg-video-i740*
  xserver-xorg-video-intel* xserver-xorg-video-mach64* xserver-xorg-video-mga*
  xserver-xorg-video-neomagic* xserver-xorg-video-nouveau*
  xserver-xorg-video-nv* xserver-xorg-video-openchrome*
  xserver-xorg-video-r128* xserver-xorg-video-radeon*
  xserver-xorg-video-rendition* xserver-xorg-video-s3*
  xserver-xorg-video-s3virge* xserver-xorg-video-savage*
  xserver-xorg-video-siliconmotion* xserver-xorg-video-sis*
  xserver-xorg-video-sisusb* xserver-xorg-video-tdfx*
  xserver-xorg-video-trident* xserver-xorg-video-tseng*
  xserver-xorg-video-vesa* xserver-xorg-video-vmware*
  xserver-xorg-video-voodoo* xterm* xul-ext-ubufox* xulrunner-1.9.2* yelp*
  zeitgeist* zeitgeist-core* zeitgeist-datahub* zeitgeist-fts-extension*
  zenity*
The following NEW packages will be installed:
  debconf-english docbook-xsl-doc-html hal-info libakonadi-kabc4 libattica0
  libboost-program-options1.42.0 libclucene0ldbl libdirectfb-1.2-9
  libegl1-mesa libegl1-mesa-drivers libgif4 libgles2-mesa libhal-storage1
  libhal1 libilmbase6 libiodbc2 libkdecore5 libkimap4 libkjsapi4 libkmime4
  libkntlm4 libmng1 libmodplug1 libmpcdec6 libmysqlclient16 libopenexr6
  libqapt1 libqca2 libqt4-dbus libqt4-network libqt4-script libqt4-sql
  libqt4-sql-mysql libqt4-test libqt4-xml libqt4-xmlpatterns libqtcore4
  libreadline5 libsdl1.2debian libsdl1.2debian-alsa libssh-4
  libstreamanalyzer0 libstreams0 libthreadweaver4 libts-0.0-0 libvirtodbc0
  libxcb-shape0 libxcb-xfixes0 libxcb-xv0 libxine1-bin libxine1-console lynx
  lynx-cur mysql-client-core-5.1 mysql-common mysql-server-core-5.1 odbcinst
  odbcinst1debian2 oxygen-icon-theme python-sip shared-desktop-ontologies
  smartdimmer tsconf ttf-dejavu ttf-dejavu-extra virtuoso-minimal
  virtuoso-opensource-6.1-bin virtuoso-opensource-6.1-common
The following packages will be upgraded:
  libasound2 python python-minimal
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  bash dash (due to bash) login libpam-runtime (due to login)
3 upgraded, 68 newly installed, 762 to remove and 61 not upgraded.
2 not fully installed or removed.
Need to get 47.2MB of archives.
After this operation, 1,364MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?] Abort.
```

---

### Post by sandyd on 2010-12-26
installing the STA drivers on a non-persistant/live session will not work, becuase the filesystem is

a) readonly

b) you need to restart for the sta drivers to work.

---

### Post by hugmenot on 2010-12-26
> **sandyd said:**
> installing the STA drivers on a non-persistant/live session will not work, becuase the filesystem is

a) readonly

b) you need to restart for the sta drivers to work.

Yes, it can work because

a) there is a writable file system overlay
b) all it requires is unloading the unwanted driver module and 
   loading the wanted driver module. No idea what those are.

---

### Post by sandyd on 2010-12-26
> **hugmenot said:**
> Yes, it can work because

a) there is a writable file system overlay
the op doesnt have one.
```
/usr/sbin/update-initramfs: 15: cannot create /cdrom/casper/initrd.lz.new: Read-only file system.

```
b) all it requires is unloading the unwanted driver module and 
   loading the wanted driver module. No idea what those are.
.

---

### Post by hugmenot on 2010-12-26
> **sandyd said:**
> .

Well, the boot loader is read-only. But the rest of the file system is writable. How else would you be able to install ****?

---

### Post by alanzee on 2010-12-26
...

Considering that the installer asks for internet before the full install, I think that it should be possible to get internet in a usb boot.

Any suggestions on what else to try? I'm not having much luck.

---

