---
title: "play dvd in ubuntu 9.10"
date: 2009-12-25
forum: New to Ubuntu
---

### Post by lance bermudez on 2009-12-25
how do i play a dvd i got from walmart on my ubuntu? it is a dvd not a blue ray. I have tried vlc, moveplayer, and mplayer. they just error out. however they can see the dvd to mount and browser it but not play it. yes i have a dvd drive in my acer aspire 4720z

---

### Post by Timoteo32 on 2009-12-25
I'm not sure mate. I posted the same problem last night and have seen a few other threads. A few people gave me things to try but none of them worked. I ended up playing mine with Dell DVDPro that came on my laptop.

---

### Post by lance bermudez on 2009-12-25
i have libdvdcss2 installed i also have Ubuntu Restrictes Extras and xUbuntu Restrictes Extras all installed.

---

### Post by sgtGarcia on 2009-12-25
Do you have libdvdread4 installed??

---

### Post by lance bermudez on 2009-12-25
i have no idea why but it seems to work if i open vlc or mplayer and chose the play dvd feetcher. movie player just right click and open movie player. thanks for the help

---

### Post by Old_Grey_Wolf on 2009-12-25
Anyone with this problem, have you tried entering these commands?

```
sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \--output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update
```

and 
```
sudo apt-get install gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-fluendo-mp3 gstreamer0.10-gnonlin gstreamer0.10-sdl gstreamer-dbus-media-service gstreamer-tools freepats gstreamer0.10-gnomevfs liba52-0.7.4 libass3 libavcodec52 libavformat52 libavutil49 libcdaudio1 libcelt0 libdc1394-22 libdca0 libdirac0c2a libdvdnav4 libdvdread4 libenca0 libfaac0 libfaad0 libffado1 libfftw3-3 libfreebob0 libgsm1 libid3tag0 libiptcdata0 libjack0 libkate1 libmad0 libmimic0 libmjpegtools-1.9 libmms0 libmodplug0c2 libmp3lame0 libmpcdec3 libmpeg2-4 libofa0 libopenspc0 libpostproc51 libquicktime1 libschroedinger-1.0-0 libsidplay1 libsoundtouch1c2 libswscale0 libtwolame0 libwildmidi0 libx264-67 libxml++2.6-2 libxvidcore4 w32codecs libdvdcss2 libxine1-ffmpeg debhelper fakeroot libfftw3-dev jackd sidplay-base liblrdf0-dev xsidplay mplayer avifile-divx-plugin avifile-xvid-plugin dh-make g++-multilib g++-4.3-multilib gcc-4.3-doc libstdc++6-4.3-dbg cvs gettext-doc jack-tools libjackasyn0 avifile-mad-plugin avifile-mjpeg-plugin avifile-player avifile-utils avifile-vorbis-plugin avifile-win32-plugin libcurl3-dbg libgcrypt11-doc libggi-target-emu libggi-target-monotext libggimisc2 gnutls-doc gnutls-bin guile-gnutls krb5-doc libraptor1-doc libstdc++6-4.3-doc mplayer-doc diff-doc easytag-aac faac faad ffmpeg ffmpeg2theora flac gxine icedax id3tool id3v2 lame liba52-0.7.4-dev libavfilter0 libflac++6 libid3-3.8.3c2a libjpeg-progs libmozjs0d libmp4v2-0 libmpg123-0 libsox-fmt-alsa libsox-fmt-base libsox1a mpeg2dec mpeg3-utils mpegdemux mpg123 mpg321 libamrnb3 libamrwb3 sox tagtool twolame vorbis-tools gecko-mediaplayer build-essential comerr-dev cpp-4.3 dpkg-dev g++ g++-4.3 g++-4.4 g++-4.4-multilib gcc-4.3 gcc-4.3-base gcc-4.3-multilib gcc-4.4-multilib gcc-multilib gettext gnome-mplayer guile-1.8 html2text intltool-debian ladspa-sdk lib64gcc1 lib64gomp1 lib64stdc++6 libao2 libaudio2 libavdevice52 libavifile-0.7c2 libc6-amd64 libc6-dev-amd64 libcurl4-gnutls-dev libdiscid0 libgcc1-dbg libgcrypt11-dev libggi-target-terminfo libggi-target-x libggi2 libgii1 libgii1-target-x libgnutls-dev libgpg-error-dev libgssrpc4 libidn11-dev libkadm5srv6 libkdb5-4 libkrb5-dev libldap2-dev liblrdf0 liblzo2-2 libmail-sendmail-perl libmpeg3-1 libmusicbrainz3-6 libopenal1 libqt3-mt libqt4-xml libqtcore4 libqtgui4 libraptor1-dev libreadline5 libstdc++6-4.3-dev libstdc++6-4.4-dev libsvga1 libsys-hostname-long-perl libtasn1-3-dev libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x libxml2-dev libxslt1-dev mplayer-nogui mplayer-skins patch po-debconf qjackctl zlib1g-dev libdvbpsi5 libebml0 libiso9660-5 liblua5.1-0 libmatroska0 libsdl-image1.2 vlc libtar libvcdinfo0 libvlc2 libvlccore2 vlc-data vlc-nox vlc-plugin-pulse
```

---

### Post by droadtrip on 2009-12-26
[FONT=Georgia][SIZE=3][COLOR=Navy]This is strange. i have always been able to play DVD's using VLC and Mplayer and some others. I usually spend a bit of extra time asking myself which is the best. But I will subscribe to this thread in case this problem ever happens and I'll be prepared. Thanks. [/COLOR][/SIZE][/FONT]

---

### Post by ludzi_1 on 2010-01-02
Thanks for posting, this been a great/quick help ;)

Ludek


> **Old_Gray_Wolf said:**
> Anyone with this problem, have you tried entering these commands?

```
sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \--output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update
```and 
```
sudo apt-get install gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-fluendo-mp3 gstreamer0.10-gnonlin gstreamer0.10-sdl gstreamer-dbus-media-service gstreamer-tools freepats gstreamer0.10-gnomevfs liba52-0.7.4 libass3 libavcodec52 libavformat52 libavutil49 libcdaudio1 libcelt0 libdc1394-22 libdca0 libdirac0c2a libdvdnav4 libdvdread4 libenca0 libfaac0 libfaad0 libffado1 libfftw3-3 libfreebob0 libgsm1 libid3tag0 libiptcdata0 libjack0 libkate1 libmad0 libmimic0 libmjpegtools-1.9 libmms0 libmodplug0c2 libmp3lame0 libmpcdec3 libmpeg2-4 libofa0 libopenspc0 libpostproc51 libquicktime1 libschroedinger-1.0-0 libsidplay1 libsoundtouch1c2 libswscale0 libtwolame0 libwildmidi0 libx264-67 libxml++2.6-2 libxvidcore4 w32codecs libdvdcss2 libxine1-ffmpeg debhelper fakeroot libfftw3-dev jackd sidplay-base liblrdf0-dev xsidplay mplayer avifile-divx-plugin avifile-xvid-plugin dh-make g++-multilib g++-4.3-multilib gcc-4.3-doc libstdc++6-4.3-dbg cvs gettext-doc jack-tools libjackasyn0 avifile-mad-plugin avifile-mjpeg-plugin avifile-player avifile-utils avifile-vorbis-plugin avifile-win32-plugin libcurl3-dbg libgcrypt11-doc libggi-target-emu libggi-target-monotext libggimisc2 gnutls-doc gnutls-bin guile-gnutls krb5-doc libraptor1-doc libstdc++6-4.3-doc mplayer-doc diff-doc easytag-aac faac faad ffmpeg ffmpeg2theora flac gxine icedax id3tool id3v2 lame liba52-0.7.4-dev libavfilter0 libflac++6 libid3-3.8.3c2a libjpeg-progs libmozjs0d libmp4v2-0 libmpg123-0 libsox-fmt-alsa libsox-fmt-base libsox1a mpeg2dec mpeg3-utils mpegdemux mpg123 mpg321 libamrnb3 libamrwb3 sox tagtool twolame vorbis-tools gecko-mediaplayer build-essential comerr-dev cpp-4.3 dpkg-dev g++ g++-4.3 g++-4.4 g++-4.4-multilib gcc-4.3 gcc-4.3-base gcc-4.3-multilib gcc-4.4-multilib gcc-multilib gettext gnome-mplayer guile-1.8 html2text intltool-debian ladspa-sdk lib64gcc1 lib64gomp1 lib64stdc++6 libao2 libaudio2 libavdevice52 libavifile-0.7c2 libc6-amd64 libc6-dev-amd64 libcurl4-gnutls-dev libdiscid0 libgcc1-dbg libgcrypt11-dev libggi-target-terminfo libggi-target-x libggi2 libgii1 libgii1-target-x libgnutls-dev libgpg-error-dev libgssrpc4 libidn11-dev libkadm5srv6 libkdb5-4 libkrb5-dev libldap2-dev liblrdf0 liblzo2-2 libmail-sendmail-perl libmpeg3-1 libmusicbrainz3-6 libopenal1 libqt3-mt libqt4-xml libqtcore4 libqtgui4 libraptor1-dev libreadline5 libstdc++6-4.3-dev libstdc++6-4.4-dev libsvga1 libsys-hostname-long-perl libtasn1-3-dev libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x libxml2-dev libxslt1-dev mplayer-nogui mplayer-skins patch po-debconf qjackctl zlib1g-dev libdvbpsi5 libebml0 libiso9660-5 liblua5.1-0 libmatroska0 libsdl-image1.2 vlc libtar libvcdinfo0 libvlc2 libvlccore2 vlc-data vlc-nox vlc-plugin-pulse
```

---

### Post by doublewitt on 2010-01-08
I was about to post the SAME problem...! but I followed Old_Gray_Wolf's advice above and all works fine now. I'm so happy...! thanks...:D

---

