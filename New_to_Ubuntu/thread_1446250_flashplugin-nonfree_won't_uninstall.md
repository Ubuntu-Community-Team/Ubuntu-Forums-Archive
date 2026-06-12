---
title: "flashplugin-nonfree won't uninstall"
date: 2010-04-03
forum: New to Ubuntu
---

### Post by Masterion on 2010-04-03
When trying to install other packages and the such, it's telling me that this package can't uninstall, or, on occasions, it won't be upgraded. What should I do?

---

### Post by garvinrick4 on 2010-04-03
> **Masterion said:**
> When trying to install other packages and the such, it's telling me that this package can't uninstall, or, on occasions, it won't be upgraded. What should I do?
Explain just a little better, do you want to install, or upgrade or purge packages?

---

### Post by Masterion on 2010-04-03
I want to just get rid of it altogether. However, when trying to do this, the following message appears:

E: flashplugin-nonfree: subprocess installed pre-removal script returned error exit status 2

---

### Post by NightwishFan on 2010-04-03
Try:
```
sudo aptitude purge flashplugin-nonfree
```

---

### Post by Masterion on 2010-04-03
Okay, I did that, and this shows up:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
The following packages will be REMOVED:
  flashplugin-nonfree{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 4 not upgraded.
Need to get 0B of archives. After unpacking 164kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 139209 files and directories currently installed.)
Removing flashplugin-nonfree ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing flashplugin-nonfree (--purge):
 subprocess installed pre-removal script returned error exit status 2
postinst called with argument `abort-remove'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

```Did it work?

---

### Post by sandyd on 2010-04-03
> **Masterion said:**
> Okay, I did that, and this shows up:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
The following packages will be REMOVED:
  flashplugin-nonfree{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 4 not upgraded.
Need to get 0B of archives. After unpacking 164kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 139209 files and directories currently installed.)
Removing flashplugin-nonfree ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing flashplugin-nonfree (--purge):
 subprocess installed pre-removal script returned error exit status 2
postinst called with argument `abort-remove'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

```Did it work?
no.
try
```

sudo dpkg --purge --force all iceape-flashplugin
sudo dpkg --purge --force all flashplugin-nonfree
```

---

### Post by Masterion on 2010-04-03
sudo dpkg --purge --force all iceape-flashplugin returns the following:

```
dpkg: warning: ignoring request to remove iceape-flashplugin which isn't installed.

```sudo dpkg --purge --force all flashplugin-nonfree returns the following:

```
(Reading database ... 139209 files and directories currently installed.)
Removing flashplugin-nonfree ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing flashplugin-nonfree (--purge):
 subprocess installed pre-removal script returned error exit status 2
postinst called with argument `abort-remove'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree
```

---

### Post by sandyd on 2010-04-03
> **Masterion said:**
> sudo dpkg --purge --force all iceape-flashplugin returns the following:

```
dpkg: warning: ignoring request to remove iceape-flashplugin which isn't installed.

```sudo dpkg --purge --force all flashplugin-nonfree returns the following:

```
(Reading database ... 139209 files and directories currently installed.)
Removing flashplugin-nonfree ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing flashplugin-nonfree (--purge):
 subprocess installed pre-removal script returned error exit status 2
postinst called with argument `abort-remove'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree
```
can you do
```

ls /var/lib/dpkg/info

```
and list the output here?
thanks

---

### Post by NoaHall on 2010-04-03
Try this -```
 wget http://launchpadlibrarian.net/29383483/flash.patch -O- | sudo patch /var/lib/dpkg/info/flashplugin-installer.prerm && sudo dpkg --purge --force all flashplugin-nonfree
```

---

### Post by theozzlives on 2010-04-03
All I've ever done is:
```
sudo apt-get install ubuntu-restricted-extras
```
Flash and java works just fine.

---

### Post by Masterion on 2010-04-03
@carlee: It's a long code, but, here it is:

```
ttf-unfonts-core.list
ttf-unfonts-core.md5sums
ttf-unfonts-core.postinst
ttf-unfonts-core.prerm
ttf-vlgothic.conffiles
ttf-vlgothic.list
ttf-vlgothic.md5sums
ttf-vlgothic.postinst
ttf-vlgothic.prerm
ttf-wqy-zenhei.conffiles
ttf-wqy-zenhei.list
ttf-wqy-zenhei.md5sums
ttf-wqy-zenhei.postinst
ttf-wqy-zenhei.prerm
tzdata.config
tzdata.list
tzdata.md5sums
tzdata.postinst
tzdata.postrm
tzdata.templates
ubufox.conffiles
ubufox.list
ubufox.md5sums
ubufox.preinst
ubuntu-artwork.list
ubuntu-artwork.md5sums
ubuntu-artwork.postinst
ubuntu-artwork.postrm
ubuntu-desktop.list
ubuntu-desktop.md5sums
ubuntu-docs.list
ubuntu-docs.md5sums
ubuntu-docs.postinst
ubuntu-docs.prerm
ubuntu-keyring.list
ubuntu-keyring.postinst
ubuntu-minimal.list
ubuntu-minimal.md5sums
ubuntuone-client-gnome.list
ubuntuone-client-gnome.md5sums
ubuntuone-client.list
ubuntuone-client.md5sums
ubuntu-sounds.list
ubuntu-sounds.md5sums
ubuntu-standard.list
ubuntu-standard.md5sums
ubuntu-system-service.conffiles
ubuntu-system-service.list
ubuntu-system-service.md5sums
ubuntu-system-service.postinst
ubuntu-system-service.preinst
ubuntu-system-service.prerm
ubuntu-wallpapers.list
ubuntu-wallpapers.md5sums
ubuntu-wallpapers.postinst
ubuntu-wallpapers.postrm
ubuntu-xsplash-artwork.list
ubuntu-xsplash-artwork.md5sums
ucf.conffiles
ucf.list
ucf.md5sums
ucf.postinst
ucf.postrm
ucf.preinst
ucf.templates
udev.conffiles
udev.list
udev.md5sums
udev.postinst
udev.postrm
udev.preinst
ufw.conffiles
ufw.config
ufw.list
ufw.md5sums
ufw.postinst
ufw.postrm
ufw.preinst
ufw.prerm
ufw.templates
ufw.triggers
unattended-upgrades.conffiles
unattended-upgrades.config
unattended-upgrades.list
unattended-upgrades.md5sums
unattended-upgrades.postinst
unattended-upgrades.postrm
unattended-upgrades.templates
uno-libs3.list
uno-libs3.md5sums
uno-libs3.postinst
uno-libs3.postrm
uno-libs3.shlibs
unzip.list
unzip.md5sums
update-inetd.list
update-inetd.postinst
update-inetd.postrm
update-inetd.templates
update-manager-core.conffiles
update-manager-core.list
update-manager-core.md5sums
update-manager-core.postinst
update-manager-core.preinst
update-manager-core.prerm
update-manager.list
update-manager.md5sums
update-manager.postinst
update-manager.preinst
update-manager.prerm
update-notifier-common.conffiles
update-notifier-common.list
update-notifier-common.md5sums
update-notifier-common.postinst
update-notifier.conffiles
update-notifier.list
update-notifier.md5sums
update-notifier.postinst
update-notifier.postrm
update-notifier.preinst
update-notifier.prerm
upstart.conffiles
upstart.list
upstart.md5sums
upstart.postinst
upstart.postrm
upstart.preinst
ureadahead.conffiles
ureadahead.list
ureadahead.md5sums
ureadahead.postinst
ureadahead.postrm
ureadahead.triggers
ure.list
ure.md5sums
ure.shlibs
usb-creator-common.conffiles
usb-creator-common.list
usb-creator-common.md5sums
usb-creator-common.postinst
usb-creator-common.preinst
usb-creator-common.prerm
usb-creator-gtk.list
usb-creator-gtk.md5sums
usb-creator-gtk.postinst
usb-creator-gtk.preinst
usb-creator-gtk.prerm
usbutils.list
usbutils.md5sums
usplash.conffiles
usplash.list
usplash.md5sums
usplash.postinst
usplash.postrm
usplash.preinst
usplash-theme-ubuntu.list
usplash-theme-ubuntu.md5sums
usplash-theme-ubuntu.postinst
usplash-theme-ubuntu.postrm
util-linux.conffiles
util-linux.list
util-linux.md5sums
util-linux.postinst
util-linux.postrm
util-linux.preinst
util-linux.prerm
uuid-runtime.list
uuid-runtime.md5sums
uuid-runtime.postinst
uuid-runtime.postrm
uuid-runtime.prerm
vbetool.list
vbetool.md5sums
vim-common.conffiles
vim-common.list
vim-common.md5sums
vim-common.postinst
vim-common.postrm
vim-common.preinst
vim-tiny.conffiles
vim-tiny.list
vim-tiny.md5sums
vim-tiny.postinst
vim-tiny.prerm
vinagre.list
vinagre.md5sums
vinagre.postinst
vinagre.postrm
vinagre.prerm
vino.conffiles
vino.list
vino.md5sums
vino.postinst
vino.prerm
w3m.conffiles
w3m.list
w3m.md5sums
w3m.postinst
w3m.postrm
w3m.prerm
wamerican.config
wamerican.list
wamerican.md5sums
wamerican.postinst
wamerican.postrm
wamerican.templates
wbritish.config
wbritish.list
wbritish.md5sums
wbritish.postinst
wbritish.postrm
wbritish.templates
wget.conffiles
wget.list
wget.md5sums
whiptail.list
whiptail.md5sums
whois.list
whois.md5sums
wireless-crda.list
wireless-crda.md5sums
wireless-tools.conffiles
wireless-tools.list
wireless-tools.md5sums
wodim.conffiles
wodim.list
wodim.md5sums
wodim.postinst
wodim.postrm
wodim.preinst
wpasupplicant.conffiles
wpasupplicant.list
wpasupplicant.md5sums
wpasupplicant.postinst
wpasupplicant.postrm
x11-apps.conffiles
x11-apps.list
x11-apps.md5sums
x11-apps.postinst
x11-apps.postrm
x11-apps.preinst
x11-common.conffiles
x11-common.config
x11-common.list
x11-common.md5sums
x11-common.postinst
x11-common.postrm
x11-common.preinst
x11-common.prerm
x11-common.templates
x11-session-utils.conffiles
x11-session-utils.list
x11-session-utils.md5sums
x11-utils.conffiles
x11-utils.list
x11-utils.md5sums
x11-utils.postinst
x11-utils.postrm
x11-xfs-utils.list
x11-xfs-utils.md5sums
x11-xkb-utils.list
x11-xkb-utils.md5sums
x11-xserver-utils.conffiles
x11-xserver-utils.list
x11-xserver-utils.md5sums
x11-xserver-utils.postinst
x11-xserver-utils.postrm
xauth.list
xauth.md5sums
xbitmaps.list
xbitmaps.md5sums
xchat-common.list
xchat-common.md5sums
xchat-common.postinst
xchat-common.prerm
xchat.list
xchat.md5sums
xchat.postinst
xchat.postrm
xcursor-themes.conffiles
xcursor-themes.list
xcursor-themes.md5sums
xcursor-themes.postinst
xcursor-themes.prerm
xdg-user-dirs.conffiles
xdg-user-dirs-gtk.conffiles
xdg-user-dirs-gtk.list
xdg-user-dirs-gtk.md5sums
xdg-user-dirs.list
xdg-user-dirs.md5sums
xdg-utils.list
xdg-utils.md5sums
xdg-utils.postinst
xdg-utils.prerm
xfonts-100dpi.conffiles
xfonts-100dpi.list
xfonts-100dpi.md5sums
xfonts-100dpi.postinst
xfonts-100dpi.postrm
xfonts-100dpi.preinst
xfonts-75dpi.conffiles
xfonts-75dpi.list
xfonts-75dpi.md5sums
xfonts-75dpi.postinst
xfonts-75dpi.postrm
xfonts-75dpi.preinst
xfonts-base.conffiles
xfonts-base.list
xfonts-base.md5sums
xfonts-base.postinst
xfonts-base.postrm
xfonts-base.preinst
xfonts-encodings.list
xfonts-encodings.md5sums
xfonts-mathml.conffiles
xfonts-mathml.list
xfonts-mathml.md5sums
xfonts-mathml.postinst
xfonts-mathml.prerm
xfonts-scalable.conffiles
xfonts-scalable.list
xfonts-scalable.md5sums
xfonts-scalable.postinst
xfonts-scalable.postrm
xfonts-utils.list
xfonts-utils.md5sums
xfonts-utils.postinst
xinit.conffiles
xinit.list
xinit.md5sums
xinput.list
xinput.md5sums
xkb-data.conffiles
xkb-data.list
xkb-data.md5sums
xml-core.list
xml-core.md5sums
xml-core.postinst
xml-core.postrm
xml-core.preinst
xml-core.prerm
xorg-docs-core.list
xorg-docs-core.md5sums
xorg-driver-fglrx.conffiles
xorg-driver-fglrx.list
xorg-driver-fglrx.md5sums
xorg-driver-fglrx.postinst
xorg-driver-fglrx.postrm
xorg-driver-fglrx.preinst
xorg-driver-fglrx.shlibs
xorg.list
xorg.preinst
xsane-common.list
xsane-common.md5sums
xsane.list
xsane.md5sums
xsane.postinst
xsane.postrm
xscreensaver-data.conffiles
xscreensaver-data.list
xscreensaver-data.md5sums
xscreensaver-data.postinst
xscreensaver-data.postrm
xscreensaver-gl.conffiles
xscreensaver-gl.list
xscreensaver-gl.md5sums
xscreensaver-gl.postinst
xscreensaver-gl.postrm
xserver-common.list
xserver-common.md5sums
xserver-xorg-core.conffiles
xserver-xorg-core.list
xserver-xorg-core.md5sums
xserver-xorg-core.postinst
xserver-xorg-core.postrm
xserver-xorg-core.preinst
xserver-xorg-input-all.list
xserver-xorg-input-all.preinst
xserver-xorg-input-evdev.list
xserver-xorg-input-evdev.md5sums
xserver-xorg-input-mouse.list
xserver-xorg-input-mouse.md5sums
xserver-xorg-input-synaptics.list
xserver-xorg-input-synaptics.md5sums
xserver-xorg-input-vmmouse.list
xserver-xorg-input-vmmouse.md5sums
xserver-xorg-input-wacom.list
xserver-xorg-input-wacom.md5sums
xserver-xorg-input-wacom.postinst
xserver-xorg-input-wacom.preinst
xserver-xorg.list
xserver-xorg.md5sums
xserver-xorg.postinst
xserver-xorg.postrm
xserver-xorg.preinst
xserver-xorg.prerm
xserver-xorg-video-all.list
xserver-xorg-video-all.preinst
xserver-xorg-video-apm.list
xserver-xorg-video-apm.md5sums
xserver-xorg-video-ark.list
xserver-xorg-video-ark.md5sums
xserver-xorg-video-ati.list
xserver-xorg-video-ati.md5sums
xserver-xorg-video-chips.list
xserver-xorg-video-chips.md5sums
xserver-xorg-video-cirrus.list
xserver-xorg-video-cirrus.md5sums
xserver-xorg-video-fbdev.list
xserver-xorg-video-fbdev.md5sums
xserver-xorg-video-geode.list
xserver-xorg-video-geode.md5sums
xserver-xorg-video-i128.list
xserver-xorg-video-i128.md5sums
xserver-xorg-video-i740.list
xserver-xorg-video-i740.md5sums
xserver-xorg-video-intel.list
xserver-xorg-video-intel.md5sums
xserver-xorg-video-intel.postinst
xserver-xorg-video-intel.postrm
xserver-xorg-video-intel.shlibs
xserver-xorg-video-mach64.list
xserver-xorg-video-mach64.md5sums
xserver-xorg-video-mga.list
xserver-xorg-video-mga.md5sums
xserver-xorg-video-neomagic.list
xserver-xorg-video-neomagic.md5sums
xserver-xorg-video-nv.list
xserver-xorg-video-nv.md5sums
xserver-xorg-video-openchrome.list
xserver-xorg-video-openchrome.md5sums
xserver-xorg-video-openchrome.postinst
xserver-xorg-video-openchrome.postrm
xserver-xorg-video-openchrome.shlibs
xserver-xorg-video-r128.list
xserver-xorg-video-r128.md5sums
xserver-xorg-video-radeon.list
xserver-xorg-video-radeon.md5sums
xserver-xorg-video-rendition.list
xserver-xorg-video-rendition.md5sums
xserver-xorg-video-s3.list
xserver-xorg-video-s3.md5sums
xserver-xorg-video-s3virge.list
xserver-xorg-video-s3virge.md5sums
xserver-xorg-video-savage.list
xserver-xorg-video-savage.md5sums
xserver-xorg-video-siliconmotion.list
xserver-xorg-video-siliconmotion.md5sums
xserver-xorg-video-sis.list
xserver-xorg-video-sis.md5sums
xserver-xorg-video-sisusb.list
xserver-xorg-video-sisusb.md5sums
xserver-xorg-video-tdfx.list
xserver-xorg-video-tdfx.md5sums
xserver-xorg-video-trident.list
xserver-xorg-video-trident.md5sums
xserver-xorg-video-tseng.list
xserver-xorg-video-tseng.md5sums
xserver-xorg-video-v4l.list
xserver-xorg-video-v4l.md5sums
xserver-xorg-video-vesa.list
xserver-xorg-video-vesa.md5sums
xserver-xorg-video-vmware.list
xserver-xorg-video-vmware.md5sums
xserver-xorg-video-voodoo.list
xserver-xorg-video-voodoo.md5sums
xsltproc.list
xsltproc.md5sums
xsplash.conffiles
xsplash.list
xsplash.md5sums
xterm.conffiles
xterm.list
xterm.md5sums
xterm.postinst
xterm.postrm
xterm.preinst
xterm.prerm
x-ttcidfont-conf.conffiles
x-ttcidfont-conf.config
x-ttcidfont-conf.list
x-ttcidfont-conf.md5sums
x-ttcidfont-conf.postinst
x-ttcidfont-conf.postrm
x-ttcidfont-conf.prerm
x-ttcidfont-conf.templates
xulrunner-1.9.1.conffiles
xulrunner-1.9.1-gnome-support.list
xulrunner-1.9.1-gnome-support.md5sums
xulrunner-1.9.1-gnome-support.postinst
xulrunner-1.9.1.list
xulrunner-1.9.1.md5sums
xulrunner-1.9.1.postinst
xulrunner-1.9.1.postrm
xulrunner-1.9.1.preinst
xulrunner-1.9.1.prerm
yelp.list
yelp.md5sums
yelp.postinst
yelp.postrm
yelp.prerm
zenity.list
zenity.md5sums
zip.list
zip.md5sums
zlib1g.list
zlib1g.md5sums
zlib1g.postinst
zlib1g.postrm
zlib1g.shlibs
zlib1g.symbols

```

---

### Post by Masterion on 2010-04-03
@theozzlives: That returns this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libfreebob0 libpostproc-extra-51 libtwolame0 libwildmidi0 libxvidcore4
  libsoundtouch1c2 libdca0 libopenjpeg2 libopenspc0 libass3 libamrnb3
  libavutil-extra-49 libamrwb3 libenca0 libcelt0 freepats libswscale-extra-0
  libdvdnav4 libdvdread4 libkate1 libcdaudio1 libmimic0 libsidplay1 libid3tag0
  apport-hooks-medibuntu libdirac0c2a libmodplug0c2 libmpcdec3 libmpeg2-4
  libmms0 libiptcdata0 libfaac0 libfaad0 liba52-0.7.4
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  apport-hooks-medibuntu cabextract flashplugin-installer freepats
  gstreamer0.10-pitfdll gstreamer0.10-plugins-ugly-multiverse liba52-0.7.4
  libamrnb3 libamrwb3 libass3 libavutil-extra-49 libcdaudio1 libcelt0 libdca0
  libdirac0c2a libdvdnav4 libdvdread4 libenca0 libfaac0 libfaad0 libfreebob0
  libid3tag0 libiptcdata0 libkate1 libmimic0 libmms0 libmodplug0c2 libmp3lame0
  libmp4v2-0 libmpcdec3 libmpeg2-4 libopenjpeg2 libopenspc0
  libpostproc-extra-51 libsidplay1 libsoundtouch1c2 libswscale-extra-0
  libtwolame0 libwildmidi0 libx264-67 libxvidcore4 ttf-mscorefonts-installer
  unrar w32codecs
Suggested packages:
  xulrunner-1.9 konqueror-nsplugins msttcorefonts ttf-bitstream-vera
  ttf-dejavu ttf-xfree86-nonfree xfs libdvdcss2 debhelper build-essential
  sidplay-base xsidplay mplayer
Recommended packages:
  ttf-liberation gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad
  gstreamer0.10-plugins-bad-multiverse gstreamer0.10-ffmpeg libavcodec52
  libavformat52 libpostproc51 libswscale0
The following packages will be REMOVED:
  flashplugin-nonfree
The following NEW packages will be installed:
  apport-hooks-medibuntu cabextract flashplugin-installer freepats
  gstreamer0.10-pitfdll gstreamer0.10-plugins-ugly-multiverse liba52-0.7.4
  libamrnb3 libamrwb3 libass3 libavutil-extra-49 libcdaudio1 libcelt0 libdca0
  libdirac0c2a libdvdnav4 libdvdread4 libenca0 libfaac0 libfaad0 libfreebob0
  libid3tag0 libiptcdata0 libkate1 libmimic0 libmms0 libmodplug0c2 libmp3lame0
  libmp4v2-0 libmpcdec3 libmpeg2-4 libopenjpeg2 libopenspc0
  libpostproc-extra-51 libsidplay1 libsoundtouch1c2 libswscale-extra-0
  libtwolame0 libwildmidi0 libx264-67 libxvidcore4 ttf-mscorefonts-installer
  ubuntu-restricted-extras unrar w32codecs
0 upgraded, 45 newly installed, 1 to remove and 4 not upgraded.
1 not fully installed or removed.
Need to get 46.9MB/47.0MB of archives.
After this operation, 78.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
0% [Working]
Get:1 http://archive.ubuntu.com karmic/universe freepats 20060219-1 [29.0MB]
Get:2 http://packages.medibuntu.org karmic/free apport-hooks-medibuntu 1medibuntu1 [2,592B]
Get:3 http://packages.medibuntu.org karmic/non-free libavutil-extra-49 4:0.5+svn20090706-2ubuntu3+medibuntu1 [97.3kB]
Get:4 http://packages.medibuntu.org karmic/non-free libpostproc-extra-51 4:0.5+svn20090706-2ubuntu3+medibuntu1 [69.7kB]
Get:5 http://packages.medibuntu.org karmic/non-free libswscale-extra-0 4:0.5+svn20090706-2ubuntu3+medibuntu1 [172kB]
Get:6 http://packages.medibuntu.org karmic/non-free libamrnb3 7.0.0.2-0.1medibuntu1 [138kB]
Get:7 http://packages.medibuntu.org karmic/non-free libamrwb3 7.0.0.3-0.0medibuntu1 [115kB]
Get:8 http://packages.medibuntu.org karmic/non-free w32codecs 20071007-0medibuntu5 [14.1MB]
Get:9 http://archive.ubuntu.com karmic/universe gstreamer0.10-pitfdll 0.9.1.1+cvs20080215-1ubuntu1 [78.4kB]
Get:10 http://archive.ubuntu.com karmic/multiverse libmp3lame0 3.98.2+debian-0ubuntu2 [251kB]
Get:11 http://archive.ubuntu.com karmic/universe libx264-67 1:0.svn20090621+git364d7d-0ubuntu2 [264kB]
Get:12 http://archive.ubuntu.com karmic/multiverse gstreamer0.10-plugins-ugly-multiverse 0.10.12-0ubuntu1 [60.8kB]
Get:13 http://archive.ubuntu.com karmic/universe liba52-0.7.4 0.7.4-11ubuntu1 [27.2kB]
Get:14 http://archive.ubuntu.com karmic/universe libcdaudio1 0.99.12p2-7 [45.8kB]
Get:15 http://archive.ubuntu.com karmic/universe libcelt0 0.6.1-1 [41.8kB]     
Get:16 http://archive.ubuntu.com karmic/universe libdirac0c2a 1.0.2-0ubuntu1 [410kB]
Get:17 http://archive.ubuntu.com karmic/universe libdvdread4 4.1.3-5ubuntu2 [64.2kB]
Get:18 http://archive.ubuntu.com karmic/universe libdvdnav4 4.1.3-3 [74.9kB]   
Get:19 http://archive.ubuntu.com dapper/universe libenca0 1.9-1 [71.1kB]       
Get:20 http://archive.ubuntu.com karmic/multiverse libfaac0 1.26-0.1ubuntu2 [61.4kB]
Get:21 http://archive.ubuntu.com karmic/universe libfaad0 2.6.1-3.1 [167kB]    
Get:22 http://archive.ubuntu.com karmic/universe libfreebob0 1.0.11-1build1 [155kB]
Get:23 http://archive.ubuntu.com dapper/main libid3tag0 0.15.1b-8 [34.9kB]     
Get:24 http://archive.ubuntu.com karmic/universe libkate1 0.3.3-1 [39.2kB]     
Get:25 http://archive.ubuntu.com karmic/universe libmimic0 1.0.4-2 [20.2kB]    
Get:26 http://archive.ubuntu.com karmic/universe libmms0 0.4-2 [28.7kB]        
Get:27 http://archive.ubuntu.com dapper-updates/main libmodplug0c2 1:0.7-5ubuntu0.6.06.2 [116kB]
Get:28 http://archive.ubuntu.com karmic/multiverse libmp4v2-0 1:1.6dfsg-0.2ubuntu5 [301kB]
Get:29 http://archive.ubuntu.com dapper/main libmpcdec3 1.2.2-1 [25.3kB]       
Get:30 http://archive.ubuntu.com karmic/universe libmpeg2-4 0.4.1-3 [55.9kB]   
Get:31 http://archive.ubuntu.com dapper/universe libopenspc0 0.3.99a-2 [27.0kB]
Get:32 http://archive.ubuntu.com karmic/universe libsidplay1 1.36.59-5 [73.5kB]
Get:33 http://archive.ubuntu.com karmic/universe libsoundtouch1c2 1.3.1-2 [27.1kB]
Get:34 http://archive.ubuntu.com karmic/universe libtwolame0 0.3.12-1 [53.6kB] 
Get:35 http://archive.ubuntu.com karmic/universe libwildmidi0 0.2.2-2 [41.9kB] 
Get:36 http://archive.ubuntu.com karmic/multiverse libxvidcore4 2:1.1.2-0.1ubuntu4 [217kB]
Get:37 http://archive.ubuntu.com karmic/multiverse ubuntu-restricted-extras 36 [5,500B]
Get:38 http://archive.ubuntu.com karmic/multiverse unrar 1:3.9.3-1 [103kB]     
Get:39 http://archive.ubuntu.com karmic/universe libass3 0.9.6-1 [45.7kB]      
Get:40 http://archive.ubuntu.com karmic/universe libdca0 0.0.5-3 [106kB]       
Get:41 http://archive.ubuntu.com dapper/universe libiptcdata0 0.2.1-0ubuntu2 [20.6kB]
Get:42 http://archive.ubuntu.com karmic/universe libopenjpeg2 1.3+dfsg-4 [79.3kB]
Fetched 46.9MB in 1min 52s (417kB/s)                                           
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 139209 files and directories currently installed.)
Removing flashplugin-nonfree ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing flashplugin-nonfree (--remove):
 subprocess installed pre-removal script returned error exit status 2
postinst called with argument `abort-remove'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by NoaHall on 2010-04-03
> **Masterion said:**
> @carlee: It's a long code, but, here it is:

```
ttf-unfonts-core.list
ttf-unfonts-core.md5sums
ttf-unfonts-core.postinst
ttf-unfonts-core.prerm
ttf-vlgothic.conffiles
ttf-vlgothic.list
ttf-vlgothic.md5sums
ttf-vlgothic.postinst
ttf-vlgothic.prerm
ttf-wqy-zenhei.conffiles
ttf-wqy-zenhei.list
ttf-wqy-zenhei.md5sums
ttf-wqy-zenhei.postinst
ttf-wqy-zenhei.prerm
tzdata.config
tzdata.list
tzdata.md5sums
tzdata.postinst
tzdata.postrm
tzdata.templates
ubufox.conffiles
ubufox.list
ubufox.md5sums
ubufox.preinst
ubuntu-artwork.list
ubuntu-artwork.md5sums
ubuntu-artwork.postinst
ubuntu-artwork.postrm
ubuntu-desktop.list
ubuntu-desktop.md5sums
ubuntu-docs.list
ubuntu-docs.md5sums
ubuntu-docs.postinst
ubuntu-docs.prerm
ubuntu-keyring.list
ubuntu-keyring.postinst
ubuntu-minimal.list
ubuntu-minimal.md5sums
ubuntuone-client-gnome.list
ubuntuone-client-gnome.md5sums
ubuntuone-client.list
ubuntuone-client.md5sums
ubuntu-sounds.list
ubuntu-sounds.md5sums
ubuntu-standard.list
ubuntu-standard.md5sums
ubuntu-system-service.conffiles
ubuntu-system-service.list
ubuntu-system-service.md5sums
ubuntu-system-service.postinst
ubuntu-system-service.preinst
ubuntu-system-service.prerm
ubuntu-wallpapers.list
ubuntu-wallpapers.md5sums
ubuntu-wallpapers.postinst
ubuntu-wallpapers.postrm
ubuntu-xsplash-artwork.list
ubuntu-xsplash-artwork.md5sums
ucf.conffiles
ucf.list
ucf.md5sums
ucf.postinst
ucf.postrm
ucf.preinst
ucf.templates
udev.conffiles
udev.list
udev.md5sums
udev.postinst
udev.postrm
udev.preinst
ufw.conffiles
ufw.config
ufw.list
ufw.md5sums
ufw.postinst
ufw.postrm
ufw.preinst
ufw.prerm
ufw.templates
ufw.triggers
unattended-upgrades.conffiles
unattended-upgrades.config
unattended-upgrades.list
unattended-upgrades.md5sums
unattended-upgrades.postinst
unattended-upgrades.postrm
unattended-upgrades.templates
uno-libs3.list
uno-libs3.md5sums
uno-libs3.postinst
uno-libs3.postrm
uno-libs3.shlibs
unzip.list
unzip.md5sums
update-inetd.list
update-inetd.postinst
update-inetd.postrm
update-inetd.templates
update-manager-core.conffiles
update-manager-core.list
update-manager-core.md5sums
update-manager-core.postinst
update-manager-core.preinst
update-manager-core.prerm
update-manager.list
update-manager.md5sums
update-manager.postinst
update-manager.preinst
update-manager.prerm
update-notifier-common.conffiles
update-notifier-common.list
update-notifier-common.md5sums
update-notifier-common.postinst
update-notifier.conffiles
update-notifier.list
update-notifier.md5sums
update-notifier.postinst
update-notifier.postrm
update-notifier.preinst
update-notifier.prerm
upstart.conffiles
upstart.list
upstart.md5sums
upstart.postinst
upstart.postrm
upstart.preinst
ureadahead.conffiles
ureadahead.list
ureadahead.md5sums
ureadahead.postinst
ureadahead.postrm
ureadahead.triggers
ure.list
ure.md5sums
ure.shlibs
usb-creator-common.conffiles
usb-creator-common.list
usb-creator-common.md5sums
usb-creator-common.postinst
usb-creator-common.preinst
usb-creator-common.prerm
usb-creator-gtk.list
usb-creator-gtk.md5sums
usb-creator-gtk.postinst
usb-creator-gtk.preinst
usb-creator-gtk.prerm
usbutils.list
usbutils.md5sums
usplash.conffiles
usplash.list
usplash.md5sums
usplash.postinst
usplash.postrm
usplash.preinst
usplash-theme-ubuntu.list
usplash-theme-ubuntu.md5sums
usplash-theme-ubuntu.postinst
usplash-theme-ubuntu.postrm
util-linux.conffiles
util-linux.list
util-linux.md5sums
util-linux.postinst
util-linux.postrm
util-linux.preinst
util-linux.prerm
uuid-runtime.list
uuid-runtime.md5sums
uuid-runtime.postinst
uuid-runtime.postrm
uuid-runtime.prerm
vbetool.list
vbetool.md5sums
vim-common.conffiles
vim-common.list
vim-common.md5sums
vim-common.postinst
vim-common.postrm
vim-common.preinst
vim-tiny.conffiles
vim-tiny.list
vim-tiny.md5sums
vim-tiny.postinst
vim-tiny.prerm
vinagre.list
vinagre.md5sums
vinagre.postinst
vinagre.postrm
vinagre.prerm
vino.conffiles
vino.list
vino.md5sums
vino.postinst
vino.prerm
w3m.conffiles
w3m.list
w3m.md5sums
w3m.postinst
w3m.postrm
w3m.prerm
wamerican.config
wamerican.list
wamerican.md5sums
wamerican.postinst
wamerican.postrm
wamerican.templates
wbritish.config
wbritish.list
wbritish.md5sums
wbritish.postinst
wbritish.postrm
wbritish.templates
wget.conffiles
wget.list
wget.md5sums
whiptail.list
whiptail.md5sums
whois.list
whois.md5sums
wireless-crda.list
wireless-crda.md5sums
wireless-tools.conffiles
wireless-tools.list
wireless-tools.md5sums
wodim.conffiles
wodim.list
wodim.md5sums
wodim.postinst
wodim.postrm
wodim.preinst
wpasupplicant.conffiles
wpasupplicant.list
wpasupplicant.md5sums
wpasupplicant.postinst
wpasupplicant.postrm
x11-apps.conffiles
x11-apps.list
x11-apps.md5sums
x11-apps.postinst
x11-apps.postrm
x11-apps.preinst
x11-common.conffiles
x11-common.config
x11-common.list
x11-common.md5sums
x11-common.postinst
x11-common.postrm
x11-common.preinst
x11-common.prerm
x11-common.templates
x11-session-utils.conffiles
x11-session-utils.list
x11-session-utils.md5sums
x11-utils.conffiles
x11-utils.list
x11-utils.md5sums
x11-utils.postinst
x11-utils.postrm
x11-xfs-utils.list
x11-xfs-utils.md5sums
x11-xkb-utils.list
x11-xkb-utils.md5sums
x11-xserver-utils.conffiles
x11-xserver-utils.list
x11-xserver-utils.md5sums
x11-xserver-utils.postinst
x11-xserver-utils.postrm
xauth.list
xauth.md5sums
xbitmaps.list
xbitmaps.md5sums
xchat-common.list
xchat-common.md5sums
xchat-common.postinst
xchat-common.prerm
xchat.list
xchat.md5sums
xchat.postinst
xchat.postrm
xcursor-themes.conffiles
xcursor-themes.list
xcursor-themes.md5sums
xcursor-themes.postinst
xcursor-themes.prerm
xdg-user-dirs.conffiles
xdg-user-dirs-gtk.conffiles
xdg-user-dirs-gtk.list
xdg-user-dirs-gtk.md5sums
xdg-user-dirs.list
xdg-user-dirs.md5sums
xdg-utils.list
xdg-utils.md5sums
xdg-utils.postinst
xdg-utils.prerm
xfonts-100dpi.conffiles
xfonts-100dpi.list
xfonts-100dpi.md5sums
xfonts-100dpi.postinst
xfonts-100dpi.postrm
xfonts-100dpi.preinst
xfonts-75dpi.conffiles
xfonts-75dpi.list
xfonts-75dpi.md5sums
xfonts-75dpi.postinst
xfonts-75dpi.postrm
xfonts-75dpi.preinst
xfonts-base.conffiles
xfonts-base.list
xfonts-base.md5sums
xfonts-base.postinst
xfonts-base.postrm
xfonts-base.preinst
xfonts-encodings.list
xfonts-encodings.md5sums
xfonts-mathml.conffiles
xfonts-mathml.list
xfonts-mathml.md5sums
xfonts-mathml.postinst
xfonts-mathml.prerm
xfonts-scalable.conffiles
xfonts-scalable.list
xfonts-scalable.md5sums
xfonts-scalable.postinst
xfonts-scalable.postrm
xfonts-utils.list
xfonts-utils.md5sums
xfonts-utils.postinst
xinit.conffiles
xinit.list
xinit.md5sums
xinput.list
xinput.md5sums
xkb-data.conffiles
xkb-data.list
xkb-data.md5sums
xml-core.list
xml-core.md5sums
xml-core.postinst
xml-core.postrm
xml-core.preinst
xml-core.prerm
xorg-docs-core.list
xorg-docs-core.md5sums
xorg-driver-fglrx.conffiles
xorg-driver-fglrx.list
xorg-driver-fglrx.md5sums
xorg-driver-fglrx.postinst
xorg-driver-fglrx.postrm
xorg-driver-fglrx.preinst
xorg-driver-fglrx.shlibs
xorg.list
xorg.preinst
xsane-common.list
xsane-common.md5sums
xsane.list
xsane.md5sums
xsane.postinst
xsane.postrm
xscreensaver-data.conffiles
xscreensaver-data.list
xscreensaver-data.md5sums
xscreensaver-data.postinst
xscreensaver-data.postrm
xscreensaver-gl.conffiles
xscreensaver-gl.list
xscreensaver-gl.md5sums
xscreensaver-gl.postinst
xscreensaver-gl.postrm
xserver-common.list
xserver-common.md5sums
xserver-xorg-core.conffiles
xserver-xorg-core.list
xserver-xorg-core.md5sums
xserver-xorg-core.postinst
xserver-xorg-core.postrm
xserver-xorg-core.preinst
xserver-xorg-input-all.list
xserver-xorg-input-all.preinst
xserver-xorg-input-evdev.list
xserver-xorg-input-evdev.md5sums
xserver-xorg-input-mouse.list
xserver-xorg-input-mouse.md5sums
xserver-xorg-input-synaptics.list
xserver-xorg-input-synaptics.md5sums
xserver-xorg-input-vmmouse.list
xserver-xorg-input-vmmouse.md5sums
xserver-xorg-input-wacom.list
xserver-xorg-input-wacom.md5sums
xserver-xorg-input-wacom.postinst
xserver-xorg-input-wacom.preinst
xserver-xorg.list
xserver-xorg.md5sums
xserver-xorg.postinst
xserver-xorg.postrm
xserver-xorg.preinst
xserver-xorg.prerm
xserver-xorg-video-all.list
xserver-xorg-video-all.preinst
xserver-xorg-video-apm.list
xserver-xorg-video-apm.md5sums
xserver-xorg-video-ark.list
xserver-xorg-video-ark.md5sums
xserver-xorg-video-ati.list
xserver-xorg-video-ati.md5sums
xserver-xorg-video-chips.list
xserver-xorg-video-chips.md5sums
xserver-xorg-video-cirrus.list
xserver-xorg-video-cirrus.md5sums
xserver-xorg-video-fbdev.list
xserver-xorg-video-fbdev.md5sums
xserver-xorg-video-geode.list
xserver-xorg-video-geode.md5sums
xserver-xorg-video-i128.list
xserver-xorg-video-i128.md5sums
xserver-xorg-video-i740.list
xserver-xorg-video-i740.md5sums
xserver-xorg-video-intel.list
xserver-xorg-video-intel.md5sums
xserver-xorg-video-intel.postinst
xserver-xorg-video-intel.postrm
xserver-xorg-video-intel.shlibs
xserver-xorg-video-mach64.list
xserver-xorg-video-mach64.md5sums
xserver-xorg-video-mga.list
xserver-xorg-video-mga.md5sums
xserver-xorg-video-neomagic.list
xserver-xorg-video-neomagic.md5sums
xserver-xorg-video-nv.list
xserver-xorg-video-nv.md5sums
xserver-xorg-video-openchrome.list
xserver-xorg-video-openchrome.md5sums
xserver-xorg-video-openchrome.postinst
xserver-xorg-video-openchrome.postrm
xserver-xorg-video-openchrome.shlibs
xserver-xorg-video-r128.list
xserver-xorg-video-r128.md5sums
xserver-xorg-video-radeon.list
xserver-xorg-video-radeon.md5sums
xserver-xorg-video-rendition.list
xserver-xorg-video-rendition.md5sums
xserver-xorg-video-s3.list
xserver-xorg-video-s3.md5sums
xserver-xorg-video-s3virge.list
xserver-xorg-video-s3virge.md5sums
xserver-xorg-video-savage.list
xserver-xorg-video-savage.md5sums
xserver-xorg-video-siliconmotion.list
xserver-xorg-video-siliconmotion.md5sums
xserver-xorg-video-sis.list
xserver-xorg-video-sis.md5sums
xserver-xorg-video-sisusb.list
xserver-xorg-video-sisusb.md5sums
xserver-xorg-video-tdfx.list
xserver-xorg-video-tdfx.md5sums
xserver-xorg-video-trident.list
xserver-xorg-video-trident.md5sums
xserver-xorg-video-tseng.list
xserver-xorg-video-tseng.md5sums
xserver-xorg-video-v4l.list
xserver-xorg-video-v4l.md5sums
xserver-xorg-video-vesa.list
xserver-xorg-video-vesa.md5sums
xserver-xorg-video-vmware.list
xserver-xorg-video-vmware.md5sums
xserver-xorg-video-voodoo.list
xserver-xorg-video-voodoo.md5sums
xsltproc.list
xsltproc.md5sums
xsplash.conffiles
xsplash.list
xsplash.md5sums
xterm.conffiles
xterm.list
xterm.md5sums
xterm.postinst
xterm.postrm
xterm.preinst
xterm.prerm
x-ttcidfont-conf.conffiles
x-ttcidfont-conf.config
x-ttcidfont-conf.list
x-ttcidfont-conf.md5sums
x-ttcidfont-conf.postinst
x-ttcidfont-conf.postrm
x-ttcidfont-conf.prerm
x-ttcidfont-conf.templates
xulrunner-1.9.1.conffiles
xulrunner-1.9.1-gnome-support.list
xulrunner-1.9.1-gnome-support.md5sums
xulrunner-1.9.1-gnome-support.postinst
xulrunner-1.9.1.list
xulrunner-1.9.1.md5sums
xulrunner-1.9.1.postinst
xulrunner-1.9.1.postrm
xulrunner-1.9.1.preinst
xulrunner-1.9.1.prerm
yelp.list
yelp.md5sums
yelp.postinst
yelp.postrm
yelp.prerm
zenity.list
zenity.md5sums
zip.list
zip.md5sums
zlib1g.list
zlib1g.md5sums
zlib1g.postinst
zlib1g.postrm
zlib1g.shlibs
zlib1g.symbols

```

That's just the end bit of the output.

```
ls /var/lib/dpkg/info/*flash*
``` Would be better.

---

### Post by Masterion on 2010-04-03
NoaHall, that returns as this:

```
/var/lib/dpkg/info/flashplugin-nonfree.config
/var/lib/dpkg/info/flashplugin-nonfree.list
/var/lib/dpkg/info/flashplugin-nonfree.md5sums
/var/lib/dpkg/info/flashplugin-nonfree.postinst
/var/lib/dpkg/info/flashplugin-nonfree.postrm
/var/lib/dpkg/info/flashplugin-nonfree.prerm
/var/lib/dpkg/info/flashplugin-nonfree.templates
```

---

### Post by NoaHall on 2010-04-03
```
 wget http://launchpadlibrarian.net/29383483/flash.patch -O- | sudo patch /var/lib/dpkg/info/flashplugin-nonfree.prerm && sudo dpkg --purge --force all flashplugin-nonfree
```
Try that.

---

### Post by Masterion on 2010-04-03
wget [http://launchpadlibrarian.net/29383483/flash.patch](http://launchpadlibrarian.net/29383483/flash.patch) -0- returns this:

```
--2010-04-03 20:37:02--  http://launchpadlibrarian.net/29383483/flash.patch
Resolving launchpadlibrarian.net... 91.189.89.228, 91.189.89.229
Connecting to launchpadlibrarian.net|91.189.89.228|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 789 [text/plain]
Saving to: `STDOUT'

 0% [                                       ] 0           --.-K/s              --- flashplugin-installer.prerm    2009-04-08 20:55:56.000000000 +0300
+++ flashplugin-installer.prerm    2009-07-22 11:17:03.625993396 +0300
@@ -27,16 +27,6 @@
         rm -rf /var/cache/flashplugin-installer-unpackdir
         rm -rf /var/cache/flashplugin-installer
         
-        for p in $VARIANTS; do 
-            update-alternatives --remove "$p-flashplugin" /usr/lib/flashplugin-installer/libflashplayer.so;
-        done
-        for p in $VARIANTS; do 
-            update-alternatives --remove "$p-flashplugin" /var/lib/flashplugin-installer/npwrapper.libflashplayer.so;
-        done
-        for p in $VARIANTS; do
-             [ `update-alternatives --list "$p-flashplugin" | wc -l` = 0 ]  && \
-                update-alternatives --remove-all "$p-flashplugin"
-        done
         ;;
     upgrade|deconfigure)
         update-rc.d -f flashplugin-installer remove >/dev/null 2>&1
100%[======================================>] 789         --.-K/s   in 0s      

2010-04-03 20:37:02 (75.2 MB/s) - `-' saved [789/789]

```While the first of the other two only produces a blank line. The last one was already stated.

---

### Post by NoaHall on 2010-04-03
No, it's all one command.```
wget http://launchpadlibrarian.net/29383483/flash.patch -O- | sudo patch /var/lib/dpkg/info/flashplugin-nonfree.prerm && sudo dpkg --purge --force all flashplugin-nonfree
``` All of it, in the terminal :)

---

### Post by Masterion on 2010-04-03
In that case, this comes up:

```
Resolving launchpadlibrarian.net... 91.189.89.228, 91.189.89.229
Connecting to launchpadlibrarian.net|91.189.89.228|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 789 [text/plain]
Saving to: `STDOUT'

100%[======================================>] 789         --.-K/s   in 0s      

2010-04-03 20:42:59 (14.5 MB/s) - `-' saved [789/789]

patching file /var/lib/dpkg/info/flashplugin-nonfree.prerm
Hunk #1 FAILED at 27.
1 out of 1 hunk FAILED -- saving rejects to file /var/lib/dpkg/info/flashplugin-nonfree.prerm.rej

```

---

### Post by NoaHall on 2010-04-03
> **Masterion said:**
> In that case, this comes up:

```
Resolving launchpadlibrarian.net... 91.189.89.228, 91.189.89.229
Connecting to launchpadlibrarian.net|91.189.89.228|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 789 [text/plain]
Saving to: `STDOUT'

100%[======================================>] 789         --.-K/s   in 0s      

2010-04-03 20:42:59 (14.5 MB/s) - `-' saved [789/789]

patching file /var/lib/dpkg/info/flashplugin-nonfree.prerm
Hunk #1 FAILED at 27.
1 out of 1 hunk FAILED -- saving rejects to file /var/lib/dpkg/info/flashplugin-nonfree.prerm.rej

```
Very well, try this - 

```
find /var/lib/dpkg/alternatives/*flash* -type f -size 0 | xargs sudo rm
```

---

### Post by Masterion on 2010-04-03
What comes up is this:

```
find: `/var/lib/dpkg/alternatives/*flash*': No such file or directory
rm: missing operand

```

---

### Post by sandyd on 2010-04-03
```

sudo rm /var/lib/dpkg/info/flashplugin-nonfree.postinst
sudo rm /var/lib/dpkg/info/flashplugin-nonfree.postrm
sudo rm /var/lib/dpkg/info/flashplugin-nonfree.prerm
sudo dpkg --force all --purge flashplugin-nonfree
```

---

### Post by Masterion on 2010-04-03
That did the trick, thanks!

---

### Post by theozzlives on 2010-04-03
Sorry, didn't know you were running Kubuntu, try:
```
sudo apt-get install kubuntu-restricted-extras
```

---

### Post by Kellemora on 2010-04-09
This is for CARLEE!

Just wanted to say thank you very much for your help!

I just upgraded to 10.4 Lucid and had a similar problem with Flash and NOTHING would get rid of it or fix it.

The message I was getting was:
"Package is in a very inconsistent state- you should reinstall it before attempting a removal."

Synaptic didn't work!
All the other suggestions I found didn't work!

Then I stumbled across your post and said what the heck, I'll try it!
I just finished burning a CD to install from the .iso as a last ditch try.
But before doing that, I used your suggestion (Post #28) and it fixed everything.  Reinstalled Flash from Synaptic and all is working great.
On an OLD 1.6 mHz computer yet!

So, once again, A HUMONGOUS Thank You!

TTUL
Gary

---

### Post by devall6 on 2012-12-15
I had this exact same problem when I did an upgrade from 11.04 to 12.04, this solved my problem, so thanks for the work on this one.  It really helped me out.

---

### Post by overdrank on 2012-12-15
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

