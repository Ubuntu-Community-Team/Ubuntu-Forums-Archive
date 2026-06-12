---
title: "VLC player wont seem to play DVD's"
date: 2009-12-25
forum: New to Ubuntu
---

### Post by Rave Gloves on 2009-12-25
I had a thread about this a while ago and it got sorted, with a clean install i lost all my files etc so i followed the steps in the last thread to get me VLC player and the addons for DVD i followed the steps but VLC gives me a series of errors and shuts down quickly.

I cant get a good look at the errors beacuse it shuts down so fast but it is something like. VLC failed to read file. could not read file. 

Anyone know how to fix this?

---

### Post by alien8predator on 2009-12-25
I'm still quite new to ubuntu/linux myself but I'm sure there's a way to look into a log file somewhere to reread errors.

---

### Post by tom.swartz07 on 2009-12-25
> **Rave Gloves said:**
> I had a thread about this a while ago and it got sorted, with a clean install i lost all my files etc so i followed the steps in the last thread to get me VLC player and the addons for DVD i followed the steps but VLC gives me a series of errors and shuts down quickly.

I cant get a good look at the errors beacuse it shuts down so fast but it is something like. VLC failed to read file. could not read file. 

Anyone know how to fix this?

could you specify how you set it up?
perhaps you are simply missing an encoder/decoder?

I might suggest trying ubuntu-restricted-extras from the software center; it includes many files and programs that are used on a daily basis; flash, mp3 support, java, etc. That might clear up any support problem you have with the DVD decoding

---

### Post by Rave Gloves on 2009-12-25
> **tom.swartz07 said:**
> could you specify how you set it up?
perhaps you are simply missing an encoder/decoder?

I might suggest trying ubuntu-restricted-extras from the software center; it includes many files and programs that are used on a daily basis; flash, mp3 support, java, etc. That might clear up any support problem you have with the DVD decoding

Open up a terminal (Applications > Accessories > Terminal) and then type;



sudo aptitude install libdvdcss2 && sudo /usr/share/doc/libdvdread4/./install-css.sh

This is DVD support. Then when it's done type this;


sudo apt-get install vlc mplayer

This is what i followed. I have installed the ubuntu restricted areas from they synpatic. Anything else?

---

### Post by tom.swartz07 on 2009-12-25
> **Rave Gloves said:**
> Open up a terminal (Applications > Accessories > Terminal) and then type;



sudo aptitude install libdvdcss2 && sudo /usr/share/doc/libdvdread4/./install-css.sh

This is DVD support. Then when it's done type this;


sudo apt-get install vlc mplayer

This is what i followed. I have installed the ubuntu restricted areas from they synpatic. Anything else?

try launching it from the command line terminal
```
vlc
```
see if it throws any errors as it starts

---

### Post by Rave Gloves on 2009-12-25
```
andrew@andrew-laptop:~$ vlc
VLC media player 0.9.9a Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=2ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "en_GB"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.

```
It started fine.

---

### Post by tom.swartz07 on 2009-12-25
Try running these commands. I found it on a very similar thread here on the forums and they seem very sound. The first command will add the medibuntu repository to your system, to keep you up to date with the various media formats, etc. The second installs practically every plugin that you would need for playing a DVD. Note that although there is a large list there, and many of them may not be needed for your specific problem, they will clear up any missing add ons and applications needed to play practically any format dvd or media file in the future.

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

### Post by Rave Gloves on 2009-12-25
> **tom.swartz07 said:**
> Try running these commands. I found it on a very similar thread here on the forums and they seem very sound. The first command will add the medibuntu repository to your system, to keep you up to date with the various media formats, etc. The second installs practically every plugin that you would need for playing a DVD. Note that although there is a large list there, and many of them may not be needed for your specific problem, they will clear up any missing add ons and applications needed to play practically any format dvd or media file in the future.

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

Just tried this, and VLC is still not reading. I dont really know what else im ment to do ):

---

### Post by tom.swartz07 on 2009-12-28
> **Rave Gloves said:**
> Just tried this, and VLC is still not reading. I dont really know what else im ment to do ):

try sudo apt-get install gxine

---

### Post by Sir Jasper on 2009-12-29
Hi,

I got a DVD for Christmas and I could not play it using Totem so eventually I read VLC worked (but Totem did not) and installed that.

It still would not work until I googled and found this code:

sudo /usr/share/doc/libdvdread4/install-css.sh

(which is very similar, but not identical, to the code given above).

I did not uninstall Totem so 
after inserting my DVD, I waited for Totem to fail (as usual) then I closed it
then
typed vlc in my terminal
then chose Media > Open Disc
and it worked.

My regards

PS Chris Edgell (see very recent thread) may have got Totem to play a DVD.

---

### Post by nick_geetar on 2009-12-29
I'm having the same problem. I just installed ubuntu studio and VLC isn't doing anything It just flashes when I try to load a dvd and doesn't do anything after.

---

### Post by e-Gee on 2009-12-29
Try to install codecs from medibuntu repository and libavcodec-extra-52 also from medibuntu not the one in repo

---

### Post by nick_geetar on 2009-12-29
So I Tried all of the prior possible solutions still getting a error.
nick@ubuntu:~$ vlc
VLC media player 1.0.2 Goldeneye
[0xb349b8] main interface error: no interface module matched "globalhotkeys,none"
[0xb349b8] main interface error: no suitable interface module
[0xa1e888] main libvlc error: interface "globalhotkeys,none" initialization failed
[0xa1e888] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.

---

### Post by JonEK90 on 2009-12-31
I was also having problems, I went through the steps above and installed all the codecs etc and still no joy.

I found on the VideoLAN forum:
*"Reset your plugins cache (~/.cache/vlc)"*

so I deleted the contents of the cache and now it is all working - yea!

I hope this is useful,
 - jon.

---

### Post by Rave Gloves on 2010-01-02
oddly VLC is now playing Dvd's i have no idea why it is after not working all the other times, but thanks anyway guys!

---

