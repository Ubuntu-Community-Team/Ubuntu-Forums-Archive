---
title: "Videos refusing to play"
date: 2010-01-31
forum: New to Ubuntu
---

### Post by MrSnuggles on 2010-01-31
So right now I'm running Ubuntu 9.10, and whenever I try to watch a video online (Youtube, etc) I generally just get the sound and the video either wont play at all or I'll get a massive delay from it. My friend said it might be the codecs but I have NO clue what I'd be doing with them. I have a Radeon x1300 video card, and currently using Google Chrome. Any ideas?

---

### Post by J V on 2010-01-31
install ubuntu-restricted-extras and download flash from adobe, extract the flash plugin to the chrome plugins directory and it should work...

---

### Post by MrSnuggles on 2010-01-31
That's the thing, I already have flash installed. The videos are acting like they're very slowly loading, despite them being fully loaded.

---

### Post by Old_Grey_Wolf on 2010-01-31
Is online flash the only problem or do you have problems playing DVDs?

---

### Post by MrSnuggles on 2010-01-31
I'm not too sure about having trouble with DVD's, like today I've been trying to play District 9 and it refuses to run.

---

### Post by Old_Grey_Wolf on 2010-01-31
> **MrSnuggles said:**
> I'm not too sure about having trouble with DVD's, like today I've been trying to play District 9 and it refuses to run.

If you are having problems playing DVDs then you may have to install the ATI video drivers. You may also need to install codecs. 

For Ubuntu 9.10 codecs:

Enter this to get to the repository...
```
sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \--output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update
```
then enter this to get **all** of the multimedia codecs...
```
sudo apt-get install gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-fluendo-mp3 gstreamer0.10-gnonlin gstreamer0.10-sdl gstreamer-dbus-media-service gstreamer-tools freepats gstreamer0.10-gnomevfs liba52-0.7.4 libass3 libavcodec52 libavformat52 libavutil49 libcdaudio1 libcelt0 libdc1394-22 libdca0 libdirac0c2a libdvdnav4 libdvdread4 libenca0 libfaac0 libfaad0 libffado1 libfftw3-3 libfreebob0 libgsm1 libid3tag0 libiptcdata0 libjack0 libkate1 libmad0 libmimic0 libmjpegtools-1.9 libmms0 libmodplug0c2 libmp3lame0 libmpcdec3 libmpeg2-4 libofa0 libopenspc0 libpostproc51 libquicktime1 libschroedinger-1.0-0 libsidplay1 libsoundtouch1c2 libswscale0 libtwolame0 libwildmidi0 libx264-67 libxml++2.6-2 libxvidcore4 w32codecs libdvdcss2 libxine1-ffmpeg debhelper fakeroot libfftw3-dev jackd sidplay-base liblrdf0-dev xsidplay mplayer avifile-divx-plugin avifile-xvid-plugin dh-make g++-multilib g++-4.3-multilib gcc-4.3-doc libstdc++6-4.3-dbg cvs gettext-doc jack-tools libjackasyn0 avifile-mad-plugin avifile-mjpeg-plugin avifile-player avifile-utils avifile-vorbis-plugin avifile-win32-plugin libcurl3-dbg libgcrypt11-doc libggi-target-emu libggi-target-monotext libggimisc2 gnutls-doc gnutls-bin guile-gnutls krb5-doc libraptor1-doc libstdc++6-4.3-doc mplayer-doc diff-doc easytag-aac faac faad ffmpeg ffmpeg2theora flac gxine icedax id3tool id3v2 lame liba52-0.7.4-dev libavfilter0 libflac++6 libid3-3.8.3c2a libjpeg-progs libmozjs0d libmp4v2-0 libmpg123-0 libsox-fmt-alsa libsox-fmt-base libsox1a mpeg2dec mpeg3-utils mpegdemux mpg123 mpg321 libamrnb3 libamrwb3 sox tagtool twolame vorbis-tools gecko-mediaplayer build-essential comerr-dev cpp-4.3 dpkg-dev g++ g++-4.3 g++-4.4 g++-4.4-multilib gcc-4.3 gcc-4.3-base gcc-4.3-multilib gcc-4.4-multilib gcc-multilib gettext gnome-mplayer guile-1.8 html2text intltool-debian ladspa-sdk lib64gcc1 lib64gomp1 lib64stdc++6 libao2 libaudio2 libavdevice52 libavifile-0.7c2 libc6-amd64 libc6-dev-amd64 libcurl4-gnutls-dev libdiscid0 libgcc1-dbg libgcrypt11-dev libggi-target-terminfo libggi-target-x libggi2 libgii1 libgii1-target-x libgnutls-dev libgpg-error-dev libgssrpc4 libidn11-dev libkadm5srv6 libkdb5-4 libkrb5-dev libldap2-dev liblrdf0 liblzo2-2 libmail-sendmail-perl libmpeg3-1 libmusicbrainz3-6 libopenal1 libqt3-mt libqt4-xml libqtcore4 libqtgui4 libraptor1-dev libreadline5 libstdc++6-4.3-dev libstdc++6-4.4-dev libsvga1 libsys-hostname-long-perl libtasn1-3-dev libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x libxml2-dev libxslt1-dev mplayer-nogui mplayer-skins patch po-debconf qjackctl zlib1g-dev libdvbpsi5 libebml0 libiso9660-5 liblua5.1-0 libmatroska0 libsdl-image1.2 vlc libtar libvcdinfo0 libvlc2 libvlccore2 vlc-data vlc-nox vlc-plugin-pulse
```

---

### Post by lavinog on 2010-01-31
District 9 should work. I just watched it last night.

do you have desktop effects enabled? 
Are you using ubuntu 9.10?

---

