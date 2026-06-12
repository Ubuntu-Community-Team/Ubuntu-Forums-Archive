---
title: "Ubuntu 11.04 on iMac problems..."
date: 2011-06-02
forum: New to Ubuntu
---

### Post by ishueli on 2011-06-02
Hello there,
 
I am a new comer to Linux systems. I recently installed Ubuntu 11.04 on my imac machine (iMac 2.4Ghz, 4GB RAM, 21" with Snow Leopard OSX). Ubuntu 11.04 was installed from a bootable CD on a newly created partition (ext4) on iMac. I have rEFIt installed on my iMac which allows me to have triple boot options). I found Ubuntu similar to OSX and sometimes faster with some applications. I am not a an expert by any chance, however like to play with technology. With GOOGLE help I manged to sort out most of the problems that I encountered during installation. The most disappointing feature of Linux systems is difficulty in rolling back any changes. You have to reinstall the software in most cases as the rollback solution is not easy to find. Anyhow after nearly 7-8 reinstallations I am stuck with following issues - 
 
- vlc media player will not install (error during installation)
- ubuntu restricted extras will not install (error during installation)
- error while updating 'recommended upgrades' especially upgrading 'libre office core' and other libre office aplications (email merge etc).
 
During one of previous reinstallations everything did work alright except for the Bluetooth and I tried to upgrade the Kernel (as advised by one of the threads) and the system crashed. So I reinstalled Ubuntu 11.04 and tried to set it up again. However this time I am stuck with the issues mentioned above. I would appreciate if an expert can guide me to sort the issues out properly. Also if I can have the solution to the bluetooth problem so that I can use Magic mouse with Ubuntu 11.04.
 
The rest of the system work pretty good and quite user friendly.
 
With Regards

---

### Post by LowSky on 2011-06-02
open terminal

type or copy this command
```

sudo apt-get update && sudo apt-get update && sudo apt-get upgrade && sudo apt-get install ubuntu-restriced-extras vlc

```

hopefully that fixes your issues with installing and upgrades. And yes i did repeat a command, sometimes it needs to be done.

---

### Post by ishueli on 2011-06-02
Appreciate your willingness to help..

I started with one command at a time

Here is what I got for [COLOR=Red]Upgrade Command

[/COLOR]shailesh@shailesh-iMac:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Here is what I got for [COLOR=Red]Restricted extras[/COLOR]

shailesh@shailesh-iMac:~$ sudo apt-get install ubuntu-restricted extras
[sudo] password for shailesh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ubuntu-restricted
E: Unable to locate package extras

Here is what I got for [COLOR=Red]VLC

[/COLOR]shailesh@shailesh-iMac:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  liba52-0.7.4 libass4 libavcodec52 libavformat52 libavutil50 libcddb2
  libdc1394-22 libdca0 libdirac-encoder0 libdvbpsi6 libdvdnav4 libdvdread4
  libebml3 libenca0 libfaad2 libgsm1 libiso9660-7 libkate1 libmad0
  libmatroska3 libmodplug1 libmpcdec6 libmpeg2-4 libpostproc51
  libschroedinger-1.0-0 libsdl-image1.2 libswscale0 libtar libtwolame0
  libupnp3 libva-x11-1 libva1 libvcdinfo0 libvlc5 libvlccore4 libvpx0
  libx264-106 libxcb-keysyms1 libxcb-randr0 libxcb-xv0 vlc-data vlc-nox
  vlc-plugin-notify vlc-plugin-pulse
Suggested packages:
  libdvdcss2 debhelper mozilla-plugin-vlc videolan-doc
The following NEW packages will be installed:
  liba52-0.7.4 libass4 libavcodec52 libavformat52 libavutil50 libcddb2
  libdc1394-22 libdca0 libdirac-encoder0 libdvbpsi6 libdvdnav4 libdvdread4
  libebml3 libenca0 libfaad2 libgsm1 libiso9660-7 libkate1 libmad0
  libmatroska3 libmodplug1 libmpcdec6 libmpeg2-4 libpostproc51
  libschroedinger-1.0-0 libsdl-image1.2 libswscale0 libtar libtwolame0
  libupnp3 libva-x11-1 libva1 libvcdinfo0 libvlc5 libvlccore4 libvpx0
  libx264-106 libxcb-keysyms1 libxcb-randr0 libxcb-xv0 vlc vlc-data vlc-nox
  vlc-plugin-notify vlc-plugin-pulse
0 upgraded, 45 newly installed, 0 to remove and 0 not upgraded.
Need to get 310 kB/21.3 MB of archives.
After this operation, 61.3 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/main libdc1394-22 i386 2.1.2-3ubuntu3
  The HTTP server sent an invalid Content-Range header [IP: 91.189.92.162 80]
Err [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/universe libdca0 i386 0.0.5-3
  Bad header line [IP: 91.189.92.162 80]
Err [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/universe libupnp3 i386 1:1.6.6-5
  Bad header line [IP: 91.189.92.162 80]
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/pool/main/libd/libdc1394-22/libdc1394-22_2.1.2-3ubuntu3_i386.deb](http://id.archive.ubuntu.com/ubuntu/pool/main/libd/libdc1394-22/libdc1394-22_2.1.2-3ubuntu3_i386.deb)  The HTTP server sent an invalid Content-Range header [IP: 91.189.92.162 80]
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/pool/universe/libd/libdca/libdca0_0.0.5-3_i386.deb](http://id.archive.ubuntu.com/ubuntu/pool/universe/libd/libdca/libdca0_0.0.5-3_i386.deb)  Bad header line [IP: 91.189.92.162 80]
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/pool/universe/libu/libupnp/libupnp3_1.6.6-5_i386.deb](http://id.archive.ubuntu.com/ubuntu/pool/universe/libu/libupnp/libupnp3_1.6.6-5_i386.deb)  Bad header line [IP: 91.189.92.162 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

Thanks

---

### Post by ishueli on 2011-06-02
I guess I typed incorrect command for Restricted Extras

After putting in the correct command I see this

shailesh@shailesh-iMac:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for shailesh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  adobe-flash-properties-gtk adobe-flashplugin ca-certificates-java freepats
  gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3 gstreamer0.10-pitfdll
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse
  gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
  icedtea-6-jre-cacao icedtea-6-jre-jamvm icedtea-netx icedtea-plugin
  icedtea6-plugin liba52-0.7.4 libaccess-bridge-java libaccess-bridge-java-jni
  libass4 libavcodec-extra-52 libavformat52 libavutil-extra-50 libcdaudio1
  libcelt0-0 libdc1394-22 libdca0 libdirac-encoder0 libdirectfb-1.2-9
  libdvdnav4 libdvdread4 libenca0 libfaac0 libfaad2 libfftw3-3 libflite1
  libgif4 libgme0 libgsm1 libid3tag0 libkate1 libmad0 libmimic0
  libmjpegtools-1.9 libmms0 libmodplug1 libmp3lame0 libmp4v2-0 libmpcdec6
  libmpeg2-4 libmusicbrainz4c2a libnss3-1d libofa0 liboil0.3
  libopencore-amrnb0 libopencore-amrwb0 libopenjpeg2 libopenspc0 libpostproc51
  libquicktime1 librtmp0 libschroedinger-1.0-0 libsidplay1 libsoundtouch0
  libswscale0 libts-0.0-0 libtwolame0 libva1 libvpx0 libwildmidi1 libx264-106
  libxvidcore4 libzbar0 openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib
  tsconf tzdata-java ubuntu-restricted-addons
Suggested packages:
  konqueror-nsplugins ttf-xfree86-nonfree xfs libnspr4-0d libfaad0 libdvdcss2
  debhelper libfftw3-dev sidplay-base xsidplay sun-java6-fonts
  ttf-sazanami-gothic ttf-kochi-gothic ttf-sazanami-mincho ttf-kochi-mincho
  ttf-telugu-fonts ttf-oriya-fonts ttf-kannada-fonts ttf-bengali-fonts
Recommended packages:
  w32codecs
The following NEW packages will be installed:
  adobe-flash-properties-gtk adobe-flashplugin ca-certificates-java freepats
  gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3 gstreamer0.10-pitfdll
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse
  gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
  icedtea-6-jre-cacao icedtea-6-jre-jamvm icedtea-netx icedtea-plugin
  icedtea6-plugin liba52-0.7.4 libaccess-bridge-java libaccess-bridge-java-jni
  libass4 libavcodec-extra-52 libavformat52 libavutil-extra-50 libcdaudio1
  libcelt0-0 libdc1394-22 libdca0 libdirac-encoder0 libdirectfb-1.2-9
  libdvdnav4 libdvdread4 libenca0 libfaac0 libfaad2 libfftw3-3 libflite1
  libgif4 libgme0 libgsm1 libid3tag0 libkate1 libmad0 libmimic0
  libmjpegtools-1.9 libmms0 libmodplug1 libmp3lame0 libmp4v2-0 libmpcdec6
  libmpeg2-4 libmusicbrainz4c2a libnss3-1d libofa0 liboil0.3
  libopencore-amrnb0 libopencore-amrwb0 libopenjpeg2 libopenspc0 libpostproc51
  libquicktime1 librtmp0 libschroedinger-1.0-0 libsidplay1 libsoundtouch0
  libswscale0 libts-0.0-0 libtwolame0 libva1 libvpx0 libwildmidi1 libx264-106
  libxvidcore4 libzbar0 openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib
  tsconf tzdata-java ubuntu-restricted-addons ubuntu-restricted-extras
0 upgraded, 80 newly installed, 0 to remove and 0 not upgraded.
Need to get 84.7 MB/99.5 MB of archives.
After this operation, 204 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/main openjdk-6-jre-headless i386 6b22-1.10.1-0ubuntu1
  The HTTP server sent an invalid Content-Range header [IP: 91.189.92.171 80]
Err [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/main ca-certificates-java all 20100412
  Bad header line [IP: 91.189.92.171 80]
Get:1 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/universe freepats all 20060219-1 [29.0 MB]
0% [1 freepats 0 B/29.0 MB 0%]
Get:2 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/universe libavutil-extra-50 i386 4:0.6.2-1ubuntu2 [78.0 kB]
Get:3 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/universe libmp3lame0 i386 3.98.4-0ubuntu1 [253 kB]
Get:4 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/universe libopenjpeg2 i386 1.3+dfsg-4 [79.3 kB]
Get:5 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/universe libxvidcore4 i386 2:1.2.2+debian-1ubuntu2 [251 kB]
Get:6 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/multiverse libavcodec-extra-52 i386 4:0.6.2-1ubuntu2 [4,482 kB]
Get:7 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/universe gstreamer0.10-ffmpeg i386 0.10.11-4 [118 kB]
Get:8 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/universe liboil0.3 i386 0.3.17-2ubuntu1 [127 kB]
Get:9 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/universe gstreamer0.10-fluendo-mp3 i386 0.10.15.debian-1 [87.6 kB]
Get:10 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/universe gstreamer0.10-pitfdll i386 0.9.1.1+cvs20080215-1ubuntu2 [79.3 kB]
Get:11 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/universe libcdaudio1 i386 0.99.12p2-9 [46.0 kB]
Get:12 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/universe libcelt0-0 i386 0.7.1-1 [39.0 kB]
Err [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/main libdc1394-22 i386 2.1.2-3ubuntu3
  The HTTP server sent an invalid Content-Range header [IP: 91.189.88.40 80]
Err [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/universe libdca0 i386 0.0.5-3   
  Bad header line [IP: 91.189.88.40 80]
Err [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/main tsconf all 1.0-7build1     
  Bad header line [IP: 91.189.88.40 80]
40% [Waiting for headers]                                                      
40% [Waiting for headers]
Get:13 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/main libts-0.0-0 i386 1.0-7build1 [28.3 kB]
Get:14 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/main libdirectfb-1.2-9 i386 1.2.10.0-4ubuntu2 [1,132 kB]
Get:15 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/main libflite1 i386 1.4-release-2 [14.4 MB]
Get:16 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/universe libgme0 i386 0.5.5-2 [142 kB]
Get:17 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/universe libmimic0 i386 1.0.4-2ubuntu1 [19.5 kB]
Get:18 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/universe libmms0 i386 0.6.2-1 [31.5 kB]
Get:19 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/main libmusicbrainz4c2a i386 2.1.5-4ubuntu2 [81.5 kB]
Get:20 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/main libfftw3-3 i386 3.2.2-1 [1,456 kB]
Get:21 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/main libofa0 i386 0.9.3-3.1 [56.6 kB]
Get:22 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/universe libopenspc0 i386 0.3.99a-2 [27.0 kB]
Get:23 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/universe librtmp0 i386 2.3-2 [48.2 kB]
Get:24 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/universe libsoundtouch0 i386 1.5.0-4 [37.7 kB]
Get:25 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/universe libwildmidi1 i386 0.2.3.2-2 [61.2 kB]
Get:26 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/universe libzbar0 i386 0.10+doc-4ubuntu2 [93.2 kB]
Get:27 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/universe gstreamer0.10-plugins-bad i386 0.10.21-1ubuntu11 [1,604 kB]
Get:28 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/multiverse libfaac0 i386 1.26-0.1ubuntu2 [61.4 kB]
Get:29 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/universe libquicktime1 i386 2:1.1.5-1ubuntu3 [295 kB]
Get:30 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/multiverse libmjpegtools-1.9 i386 1:1.9.0-0.5ubuntu4 [240 kB]
Get:31 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/multiverse gstreamer0.10-plugins-bad-multiverse i386 0.10.21-1 [98.2 kB]
Get:32 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/main libid3tag0 i386 0.15.1b-10build2 [35.5 kB]
Get:33 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/universe libopencore-amrnb0 i386 0.1.2-1 [90.1 kB]
Get:34 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/universe libopencore-amrwb0 i386 0.1.2-1 [46.9 kB]
Get:35 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/universe libsidplay1 i386 1.36.59-5 [73.5 kB]
Get:36 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/universe gstreamer0.10-plugins-ugly i386 0.10.17-1ubuntu2 [315 kB]
Get:37 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/multiverse gstreamer0.10-plugins-ugly-multiverse i386 0.10.17-1 [53.7 kB]
Get:38 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/main libgif4 i386 4.1.6-9 [40.0 kB]
Get:39 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/main libaccess-bridge-java-jni i386 1.26.2-5 [3,694 B]
Get:40 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/main openjdk-6-jre i386 6b22-1.10.1-0ubuntu1 [209 kB]
Get:41 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/main libaccess-bridge-java all 1.26.2-5 [410 kB]
Get:42 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/multiverse libmp4v2-0 i386 1:1.6dfsg-0.2ubuntu9 [267 kB]
Get:43 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/multiverse ubuntu-restricted-addons i386 7 [2,530 B]
Get:44 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/multiverse ubuntu-restricted-extras i386 43 [3,084 B]
Get:45 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/main icedtea-6-jre-cacao i386 6b22-1.10.1-0ubuntu1 [414 kB]
Get:46 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/main icedtea-6-jre-jamvm i386 6b22-1.10.1-0ubuntu1 [525 kB]
Get:47 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/main icedtea-netx i386 1.1~20110420-0ubuntu1 [450 kB]
Get:48 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/main icedtea-plugin i386 1.1~20110420-0ubuntu1 [191 kB]
Get:49 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/universe icedtea6-plugin i386 6b21.1~20110420-0ubuntu1 [942 B]
Fetched 57.6 MB in 5min 9s (186 kB/s)                                            
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/pool/main/o/openjdk-6/openjdk-6-jre-headless_6b22-1.10.1-0ubuntu1_i386.deb](http://id.archive.ubuntu.com/ubuntu/pool/main/o/openjdk-6/openjdk-6-jre-headless_6b22-1.10.1-0ubuntu1_i386.deb)  The HTTP server sent an invalid Content-Range header [IP: 91.189.92.171 80]
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/pool/main/c/ca-certificates-java/ca-certificates-java_20100412_all.deb](http://id.archive.ubuntu.com/ubuntu/pool/main/c/ca-certificates-java/ca-certificates-java_20100412_all.deb)  Bad header line [IP: 91.189.92.171 80]
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/pool/main/libd/libdc1394-22/libdc1394-22_2.1.2-3ubuntu3_i386.deb](http://id.archive.ubuntu.com/ubuntu/pool/main/libd/libdc1394-22/libdc1394-22_2.1.2-3ubuntu3_i386.deb)  The HTTP server sent an invalid Content-Range header [IP: 91.189.88.40 80]
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/pool/universe/libd/libdca/libdca0_0.0.5-3_i386.deb](http://id.archive.ubuntu.com/ubuntu/pool/universe/libd/libdca/libdca0_0.0.5-3_i386.deb)  Bad header line [IP: 91.189.88.40 80]
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/pool/main/t/tslib/tsconf_1.0-7build1_all.deb](http://id.archive.ubuntu.com/ubuntu/pool/main/t/tslib/tsconf_1.0-7build1_all.deb)  Bad header line [IP: 91.189.88.40 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

Regards

---

### Post by ishueli on 2011-06-02
By the way I managed to get 'libre-office' error resolved by following one of the threads which I cant locate now but I followed following commands

# sudo su
# apt-get update

Then I purged libre office

# sudo apt-get purge libreoffice

Then I reinstalled Libre Office

#sudo apt-get update libreoffice

And finally I run the upgrade command

sudo apt-get upgrade

This command installed all the upgrades correctly for libreoffice

Hope this helps.

To resolve VLC & RESTRICTED ISSUES I tried to get to the root directory and tried to run the same procedure but it gives the same error.

Regards

---

### Post by ishueli on 2011-06-02
I tried the whole command as advised....still no luck

xxxxxxx@shailesh-iMac:~$ sudo apt-get update && sudo apt-get update && sudo apt-get upgrade && sudo apt-get install ubuntu-restricted-extras vlc
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                               
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty InRelease                               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                   
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty-updates InRelease                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                                 
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty Release.gpg                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                     
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty-updates Release.gpg                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages         
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner i386 Packages                   
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty Release                                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex        
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty-updates Release                         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty/main Sources                            
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty/restricted Sources                      
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty/universe Sources                        
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty/multiverse Sources                      
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty/main i386 Packages                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty/restricted i386 Packages                
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty/universe i386 Packages                  
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty/multiverse i386 Packages                
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty/main TranslationIndex                   
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty/multiverse TranslationIndex             
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty/restricted TranslationIndex             
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty/universe TranslationIndex               
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty-updates/restricted i386 Packages        
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty-updates/main i386 Packages              
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty-updates/multiverse i386 Packages        
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty-updates/universe i386 Packages          
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty-updates/main TranslationIndex           
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty-updates/multiverse TranslationIndex     
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty-updates/restricted TranslationIndex     
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty-updates/universe TranslationIndex       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US                      
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_US     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty/main Translation-en_US
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty/main Translation-en
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty/multiverse Translation-en_US
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty/multiverse Translation-en
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty/restricted Translation-en_US
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty/restricted Translation-en
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty/universe Translation-en_US
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty/universe Translation-en
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty-updates/main Translation-en_US
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty-updates/multiverse Translation-en_US
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty-updates/restricted Translation-en_US
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty-updates/universe Translation-en_US
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty-updates/universe Translation-en
Reading package lists... Done
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                   
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty InRelease                               
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty-updates InRelease                       
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                             
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty Release.gpg                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release                          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release                                 
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty-updates Release.gpg                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                                
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner i386 Packages                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages         
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty Release                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex        
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty-updates Release                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty/main Sources                            
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty/restricted Sources                      
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty/universe Sources                        
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty/multiverse Sources                      
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty/main i386 Packages                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty/restricted i386 Packages                
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty/universe i386 Packages                  
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty/multiverse i386 Packages                
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty/main TranslationIndex                   
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty/multiverse TranslationIndex             
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty/restricted TranslationIndex             
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty/universe TranslationIndex               
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty-updates/restricted i386 Packages        
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty-updates/main i386 Packages              
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty-updates/multiverse i386 Packages        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty-updates/universe i386 Packages          
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty-updates/main TranslationIndex           
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty-updates/multiverse TranslationIndex     
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty-updates/restricted TranslationIndex     
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty-updates/universe TranslationIndex       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US                      
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_US               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en          
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty/main Translation-en_US
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty/main Translation-en
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty/multiverse Translation-en_US
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty/multiverse Translation-en
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty/restricted Translation-en_US
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty/restricted Translation-en
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty/universe Translation-en_US
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty/universe Translation-en
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty-updates/main Translation-en_US
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty-updates/multiverse Translation-en_US
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty-updates/restricted Translation-en_US
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty-updates/universe Translation-en_US
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) natty-updates/universe Translation-en
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  adobe-flash-properties-gtk adobe-flashplugin ca-certificates-java freepats
  gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3 gstreamer0.10-pitfdll
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse
  gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
  icedtea-6-jre-cacao icedtea-6-jre-jamvm icedtea-netx icedtea-plugin
  icedtea6-plugin liba52-0.7.4 libaccess-bridge-java libaccess-bridge-java-jni
  libass4 libavcodec-extra-52 libavformat52 libavutil-extra-50 libcdaudio1
  libcddb2 libcelt0-0 libdc1394-22 libdca0 libdirac-encoder0 libdirectfb-1.2-9
  libdvbpsi6 libdvdnav4 libdvdread4 libebml3 libenca0 libfaac0 libfaad2
  libfftw3-3 libflite1 libgif4 libgme0 libgsm1 libid3tag0 libiso9660-7
  libkate1 libmad0 libmatroska3 libmimic0 libmjpegtools-1.9 libmms0
  libmodplug1 libmp3lame0 libmp4v2-0 libmpcdec6 libmpeg2-4 libmusicbrainz4c2a
  libnss3-1d libofa0 liboil0.3 libopencore-amrnb0 libopencore-amrwb0
  libopenjpeg2 libopenspc0 libpostproc51 libquicktime1 librtmp0
  libschroedinger-1.0-0 libsdl-image1.2 libsidplay1 libsoundtouch0 libswscale0
  libtar libts-0.0-0 libtwolame0 libupnp3 libva-x11-1 libva1 libvcdinfo0
  libvlc5 libvlccore4 libvpx0 libwildmidi1 libx264-106 libxcb-keysyms1
  libxcb-randr0 libxcb-xv0 libxvidcore4 libzbar0 openjdk-6-jre
  openjdk-6-jre-headless openjdk-6-jre-lib tsconf tzdata-java
  ubuntu-restricted-addons vlc-data vlc-nox vlc-plugin-notify vlc-plugin-pulse
Suggested packages:
  konqueror-nsplugins ttf-xfree86-nonfree xfs libnspr4-0d libfaad0 libdvdcss2
  debhelper libfftw3-dev sidplay-base xsidplay sun-java6-fonts
  ttf-sazanami-gothic ttf-kochi-gothic ttf-sazanami-mincho ttf-kochi-mincho
  ttf-telugu-fonts ttf-oriya-fonts ttf-kannada-fonts ttf-bengali-fonts
  mozilla-plugin-vlc videolan-doc
Recommended packages:
  w32codecs
The following NEW packages will be installed:
  adobe-flash-properties-gtk adobe-flashplugin ca-certificates-java freepats
  gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3 gstreamer0.10-pitfdll
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse
  gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
  icedtea-6-jre-cacao icedtea-6-jre-jamvm icedtea-netx icedtea-plugin
  icedtea6-plugin liba52-0.7.4 libaccess-bridge-java libaccess-bridge-java-jni
  libass4 libavcodec-extra-52 libavformat52 libavutil-extra-50 libcdaudio1
  libcddb2 libcelt0-0 libdc1394-22 libdca0 libdirac-encoder0 libdirectfb-1.2-9
  libdvbpsi6 libdvdnav4 libdvdread4 libebml3 libenca0 libfaac0 libfaad2
  libfftw3-3 libflite1 libgif4 libgme0 libgsm1 libid3tag0 libiso9660-7
  libkate1 libmad0 libmatroska3 libmimic0 libmjpegtools-1.9 libmms0
  libmodplug1 libmp3lame0 libmp4v2-0 libmpcdec6 libmpeg2-4 libmusicbrainz4c2a
  libnss3-1d libofa0 liboil0.3 libopencore-amrnb0 libopencore-amrwb0
  libopenjpeg2 libopenspc0 libpostproc51 libquicktime1 librtmp0
  libschroedinger-1.0-0 libsdl-image1.2 libsidplay1 libsoundtouch0 libswscale0
  libtar libts-0.0-0 libtwolame0 libupnp3 libva-x11-1 libva1 libvcdinfo0
  libvlc5 libvlccore4 libvpx0 libwildmidi1 libx264-106 libxcb-keysyms1
  libxcb-randr0 libxcb-xv0 libxvidcore4 libzbar0 openjdk-6-jre
  openjdk-6-jre-headless openjdk-6-jre-lib tsconf tzdata-java
  ubuntu-restricted-addons ubuntu-restricted-extras vlc vlc-data vlc-nox
  vlc-plugin-notify vlc-plugin-pulse
0 upgraded, 100 newly installed, 0 to remove and 0 not upgraded.
Need to get 27.2 MB/113 MB of archives.
After this operation, 245 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/main openjdk-6-jre-headless i386 6b22-1.10.1-0ubuntu1
  The HTTP server sent an invalid Content-Range header
Err [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/main ca-certificates-java all 20100412
  Bad header line
Err [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/main libdc1394-22 i386 2.1.2-3ubuntu3
  The HTTP server sent an invalid Content-Range header
Err [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/universe libdca0 i386 0.0.5-3
  Bad header line
Err [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/main tsconf all 1.0-7build1
  Bad header line
Err [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) natty/universe libupnp3 i386 1:1.6.6-5
  Connection failed
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/pool/main/o/openjdk-6/openjdk-6-jre-headless_6b22-1.10.1-0ubuntu1_i386.deb](http://id.archive.ubuntu.com/ubuntu/pool/main/o/openjdk-6/openjdk-6-jre-headless_6b22-1.10.1-0ubuntu1_i386.deb)  The HTTP server sent an invalid Content-Range header
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/pool/main/c/ca-certificates-java/ca-certificates-java_20100412_all.deb](http://id.archive.ubuntu.com/ubuntu/pool/main/c/ca-certificates-java/ca-certificates-java_20100412_all.deb)  Bad header line
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/pool/main/libd/libdc1394-22/libdc1394-22_2.1.2-3ubuntu3_i386.deb](http://id.archive.ubuntu.com/ubuntu/pool/main/libd/libdc1394-22/libdc1394-22_2.1.2-3ubuntu3_i386.deb)  The HTTP server sent an invalid Content-Range header
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/pool/universe/libd/libdca/libdca0_0.0.5-3_i386.deb](http://id.archive.ubuntu.com/ubuntu/pool/universe/libd/libdca/libdca0_0.0.5-3_i386.deb)  Bad header line
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/pool/main/t/tslib/tsconf_1.0-7build1_all.deb](http://id.archive.ubuntu.com/ubuntu/pool/main/t/tslib/tsconf_1.0-7build1_all.deb)  Bad header line
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/pool/universe/libu/libupnp/libupnp3_1.6.6-5_i386.deb](http://id.archive.ubuntu.com/ubuntu/pool/universe/libu/libupnp/libupnp3_1.6.6-5_i386.deb)  Connection failed
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by ishueli on 2011-06-03
Any help coming from any corner of the world on VLC & UBUNTU RESTRICTED EXTRAS installation problems that I am facing?

---

