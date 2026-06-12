---
title: "apt-get/synaptic wont fetch"
date: 2009-08-15
forum: New to Ubuntu
---

### Post by muted1987 on 2009-08-15
both using apt-get and synaptic when trying to install something i get no progress this is what i get using apt-get:-

```
muted@muted-desktop:~$ sudo apt-get install gnome-alsamixer alsa-oss ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  freepats gstreamer0.10-pitfdll gstreamer0.10-plugins-bad
  gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse
  libass1 libavcodec-unstripped-52 libavutil-unstripped-49 libcdaudio1
  libcelt0 libdc1394-22 libdca0 libenca0 libfaac0 libfaad0 libffado0
  libfftw3-3 libfreebob0 libgmyth0 libiptcdata0 libjack0 liblrdf0
  libmjpegtools-1.9 libmms0 libmodplug0c2 libmp3lame0 libmpcdec3
  libneon27-gnutls libofa0 libopenspc0 libquicktime1 libraptor1
  libsoundtouch1c2 libwildmidi0 libx264-65 libxml++2.6-2 libxvidcore4
  raptor-utils
Suggested packages:
  libfftw3-dev jackd liblrdf0-dev
Recommended packages:
  w32codecs
The following packages will be REMOVED
  libavcodec52 libavutil49
The following NEW packages will be installed
  alsa-oss freepats gnome-alsamixer gstreamer0.10-pitfdll
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse
  gstreamer0.10-plugins-ugly-multiverse libass1 libavcodec-unstripped-52
  libavutil-unstripped-49 libcdaudio1 libcelt0 libdc1394-22 libdca0 libenca0
  libfaac0 libfaad0 libffado0 libfftw3-3 libfreebob0 libgmyth0 libiptcdata0
  libjack0 liblrdf0 libmjpegtools-1.9 libmms0 libmodplug0c2 libmp3lame0
  libmpcdec3 libneon27-gnutls libofa0 libopenspc0 libquicktime1 libraptor1
  libsoundtouch1c2 libwildmidi0 libx264-65 libxml++2.6-2 libxvidcore4
  raptor-utils ubuntu-restricted-extras
0 upgraded, 41 newly installed, 2 to remove and 0 not upgraded.
Need to get 39.4MB of archives.
After this operation, 53.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  alsa-oss freepats gnome-alsamixer gstreamer0.10-pitfdll libenca0 libass1
  libcdaudio1 libcelt0 libdc1394-22 libdca0 libfaad0 libgmyth0 libiptcdata0
  libxml++2.6-2 libffado0 libfreebob0 libjack0 libraptor1 liblrdf0 libmms0
  libmodplug0c2 libmpcdec3 libneon27-gnutls libfftw3-3 libofa0 libopenspc0
  libsoundtouch1c2 libwildmidi0 gstreamer0.10-plugins-bad libfaac0
  libavutil-unstripped-49 libmp3lame0 libx264-65 libxvidcore4
  libavcodec-unstripped-52 libquicktime1 libmjpegtools-1.9
  gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse
  raptor-utils ubuntu-restricted-extras
Install these packages without verification [y/N]? y
0% [Waiting for headers]

```


as you can see it jsut stalls at fetching headers and this only happened when i removed pulseaudio which has stopped screen freezing issues. I now have no sound and no way to download anything to get required packages from the repos any ideas to what has broken?

---

### Post by ptn107 on 2009-08-15
Try changing servers.  System -> Administration -> Software Sources.  On the first tab change the "Download from:" server to other and select another.  Close out and try again.

---

### Post by muted1987 on 2009-08-15
> **ptn107 said:**
> Try changing servers.  System -> Administration -> Software Sources.  On the first tab change the "Download from:" server to other and select another.  Close out and try again.


worked a treat dont know why i didnt think of that thanks.

---

