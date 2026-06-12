---
title: "Play Videos in Ubuntu?"
date: 2010-09-21
forum: New to Ubuntu
---

### Post by Suzanne42 on 2010-09-21
How do I play youtube or any other videos on an Ubuntu platform? Is there anything I can install via the terminal?I added the Adobe plugin but that doesn't seem to help.

---

### Post by mikewhatever on 2010-09-21
The only thing required is 'flashplugin-installer'. There are other plugins to handle flash (gnash, swfdec), don't install them if you want to use the adobe plugin.

---

### Post by Ripfox on 2010-09-21
Go to Synaptic and search for ubuntu-restricted-extras. Make sure you restart your browser before it will play flash vids.

---

### Post by alphacrucis2 on 2010-09-21
If you are running Ubuntu 64 bit then look here:

[http://www.omgubuntu.co.uk/2010/09/install-64bit-flash-from-a-ppa-or-deb/]("http://www.omgubuntu.co.uk/2010/09/install-64bit-flash-from-a-ppa-or-deb/")

---

### Post by mastablasta on 2010-09-21
> **Ripfox said:**
> Go to Synaptic ....
 
or Ubuntu software center

---

### Post by powerpleb on 2010-09-21
> **Suzanne42 said:**
> How do I play youtube or any other videos on an Ubuntu platform? Is there anything I can install via the terminal?I added the Adobe plugin but that doesn't seem to help.

Also, go to Applications/Sound & Video/Movie Player
That'll play most video files, even YouTube I think. 
Again, as others have mentioned you'll need ubuntu-restricted-extras installed to watch a lot of them.

---

### Post by Rasa1111 on 2010-09-21
> **Ripfox said:**
> Go to Synaptic and search for ubuntu-restricted-extras. Make sure you restart your browser before it will play flash vids.

^this. +1

or you can use the simplest way...

in terminal
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Suzanne42 on 2010-09-21
I get an error when I try installing via the terminal:

ERROR:
E: Internal Error, Could not perform immediate configuration (2) on mountall

---

### Post by mikewhatever on 2010-09-21
Do you mind posting all of the output and the preceding command and not just the last line.

---

### Post by Suzanne42 on 2010-09-21
Output:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  upower linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
  libupower-glib1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  ca-certificates-java cabextract consolekit fontconfig-config freepats gdm
  gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad
  gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-base
  gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly
  gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pulseaudio
  icedtea-6-jre-cacao icedtea6-plugin ifupdown indicator-applet
  indicator-applet-session initramfs-tools initramfs-tools-bin java-common
  lib32asound2 liba52-0.7.4 libaccess-bridge-java libaccess-bridge-java-jni
  libasound2 libass4 libatk1.0-0 libavcodec-extra-52 libavformat52
  libavutil-extra-49 libc-bin libc-dev-bin libc6 libc6-dev libc6-i386
  libcdaudio1 libcdio10 libcelt0-0 libdbus-glib-1-2 libdc1394-22 libdca0
  libdevkit-power-gobject1 libdirac-encoder0 libdrm-nouveau1 libdrm-radeon1
  libdvdnav4 libdvdread4 libenca0 libfaac0 libfaad2 libfftw3-3 libflite1
  libfontconfig1 libglib2.0-0 libgme0 libgsm1 libgstreamer-plugins-base0.10-0
  libgstreamer0.10-0 libid3tag0 libindicator0 libiptcdata0 libjack0 libkate1
  libmad0 libmimic0 libmjpegtools-1.9 libmms0 libmodplug0c2 libmp3lame0
  libmp4v2-0 libmpcdec3 libmpeg2-4 libnih-dbus1 libnih1 libofa0
  libopencore-amrnb0 libopencore-amrwb0 libopenjpeg2 liborc-0.4-0 libplymouth2
  libpopt0 libpostproc51 libquicktime1 libschroedinger-1.0-0 libsidplay1
  libsoundtouch1c2 libsqlite3-0 libssl0.9.8 libswscale0 libtwolame0 libudev0
  libupower-glib1 libusb-1.0-0 libwildmidi0 libx264-85 libxklavier16
  libxvidcore4 mountall openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib
  plymouth ttf-dejavu-extra ttf-liberation ttf-mscorefonts-installer tzdata
  tzdata-java udev unrar upower upstart ureadahead xulrunner-1.9.2
Suggested packages:
  uswsusp gok default-jre equivs lib32asound2-plugins libfaad0 glibc-doc
  libdvdcss2 debhelper fakeroot build-essential libfftw3-dev
  gstreamer0.10-plugins jackd sidplay-base xsidplay sun-java6-fonts
  ttf-sazanami-gothic ttf-kochi-gothic ttf-sazanami-mincho ttf-kochi-mincho
  ttf-telugu-fonts ttf-oriya-fonts ttf-kannada-fonts ttf-bengali-fonts
  watershed
Recommended packages:
  indicator-sound indicator-application indicator-me manpages-dev head
  plymouth-theme-ubuntu-text plymouth-theme
The following packages will be REMOVED:
  devicekit-power gnome-power-manager indicator-session ubuntu-desktop usplash
  usplash-theme-ubuntu
The following NEW packages will be installed:
  ca-certificates-java cabextract freepats gstreamer0.10-ffmpeg
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse
  gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
  icedtea-6-jre-cacao icedtea6-plugin initramfs-tools-bin java-common
  liba52-0.7.4 libaccess-bridge-java libaccess-bridge-java-jni libass4
  libavcodec-extra-52 libavformat52 libavutil-extra-49 libcdaudio1 libcdio10
  libcelt0-0 libdc1394-22 libdca0 libdirac-encoder0 libdrm-nouveau1 libdvdnav4
  libdvdread4 libenca0 libfaac0 libfaad2 libfftw3-3 libflite1 libgme0 libgsm1
  libid3tag0 libindicator0 libiptcdata0 libjack0 libkate1 libmad0 libmimic0
  libmjpegtools-1.9 libmms0 libmodplug0c2 libmp3lame0 libmp4v2-0 libmpcdec3
  libmpeg2-4 libnih-dbus1 libnih1 libofa0 libopencore-amrnb0
  libopencore-amrwb0 libopenjpeg2 liborc-0.4-0 libplymouth2 libpostproc51
  libquicktime1 libschroedinger-1.0-0 libsidplay1 libsoundtouch1c2 libswscale0
  libtwolame0 libupower-glib1 libusb-1.0-0 libwildmidi0 libx264-85
  libxklavier16 libxvidcore4 openjdk-6-jre openjdk-6-jre-headless
  openjdk-6-jre-lib plymouth ttf-dejavu-extra ttf-liberation
  ttf-mscorefonts-installer tzdata-java ubuntu-restricted-extras unrar upower
  xulrunner-1.9.2
The following packages will be upgraded:
  consolekit fontconfig-config gdm gstreamer0.10-plugins-base
  gstreamer0.10-plugins-good gstreamer0.10-pulseaudio ifupdown
  indicator-applet indicator-applet-session initramfs-tools lib32asound2
  libasound2 libatk1.0-0 libc-bin libc-dev-bin libc6 libc6-dev libc6-i386
  libdbus-glib-1-2 libdevkit-power-gobject1 libdrm-radeon1 libfontconfig1
  libglib2.0-0 libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 libpopt0
  libsqlite3-0 libssl0.9.8 libudev0 mountall tzdata udev upstart ureadahead
34 upgraded, 82 newly installed, 6 to remove and 1144 not upgraded.
Need to get 0B/118MB of archives.
After this operation, 200MB of additional disk space will be used.
Do you want to continue [Y/n]? y
E: Internal Error, Could not perform immediate configuration (2) on mountall

---

### Post by powerpleb on 2010-09-21
You can try these two commands to force package manager to fix any problems:
```
sudo dpkg --configure -a
```
```
sudo apt-get install -f
```

If things go well you should be able to run:
```
sudo aptitude update
```
```
sudo aptitude safe-upgrade
```
These commands will update all the packages on your machine.

Then you can run:
```
sudo aptitude install ubuntu-restricted-extras
```

Otherwise, I don't know.

---

