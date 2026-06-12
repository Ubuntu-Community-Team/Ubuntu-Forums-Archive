---
title: "clean install, now can't download VLC or soundKonverter.."
date: 2011-03-19
forum: New to Ubuntu
---

### Post by Baldrick_NZ on 2011-03-19
When I try. USC tells me to check my Internet connection, which is working fine. 

Using Sudo, I get this:

```
baldrick@baldrick-desktop:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libopenal1 wavpack mppenc vorbis-tools libxvidcore4
  cairo-dock-plug-ins-integration libsvga1 kdelibs-data mplayer
  kdemultimedia-kio-plugins xdotool cairo-dock-plug-ins mp3gain vorbisgain
  speex libmp3lame0 faad libavahi-qt3-1 icedax ffmpeg liblzo2-2 libavfilter0
  flac libdb4.7 apport-hooks-medibuntu timidity libqt3-mt
  cairo-dock-plug-ins-data timidity-daemon libetpan13 libfaac0 libavdevice52
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libcddb2 libdvbpsi5 libebml0 libiso9660-7 liblua5.1-0 libmatroska0
  libsdl-image1.2 libtar libupnp3 libvcdinfo0 libvlc2 libvlccore2
  libxcb-keysyms1 vlc-data vlc-nox vlc-plugin-pulse
Suggested packages:
  mozilla-plugin-vlc videolan-doc
The following NEW packages will be installed:
  libcddb2 libdvbpsi5 libebml0 libiso9660-7 liblua5.1-0 libmatroska0
  libsdl-image1.2 libtar libupnp3 libvcdinfo0 libvlc2 libvlccore2
  libxcb-keysyms1 vlc vlc-data vlc-nox vlc-plugin-pulse
0 upgraded, 17 newly installed, 0 to remove and 5 not upgraded.
Need to get 158kB/13.0MB of archives.
After this operation, 37.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err http://nz.archive.ubuntu.com/ubuntu/ lucid/universe libiso9660-7 0.81-4
  403  Forbidden
Err http://nz.archive.ubuntu.com/ubuntu/ lucid/universe libsdl-image1.2 1.2.10-1
  404  Not Found
Failed to fetch http://nz.archive.ubuntu.com/ubuntu/pool/universe/libc/libcdio/libiso9660-7_0.81-4_i386.deb  403  Forbidden
Failed to fetch http://nz.archive.ubuntu.com/ubuntu/pool/universe/s/sdl-image1.2/libsdl-image1.2_1.2.10-1_i386.deb  404  Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
baldrick@baldrick-desktop:~$ 

```

I run 'sudo apt-get update' as suggested, but it makes no difference. I'm not sure how to implement '--fix-missing'.

Any help would be much appreciated. Thanks.

---

### Post by Baldrick_NZ on 2011-03-19
Sorted.

Seems to have been an issue with the NZ mirror repos. Changed to Main Repo under software sources. Reloaded, and tried again. Both Packages installed fine.

---

