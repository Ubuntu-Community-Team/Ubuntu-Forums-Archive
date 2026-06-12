---
title: "Getting Mp3s/Video Plugins/Codecs"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by rob86 on 2009-08-31
I'm using Ubuntu 9.04 32bit .When I try to open divx videos or mp3s, it won't work. That's okay, I expected I  needed a codec/plugin. Problem is, whenever Ubuntu tries to find a "plugin", it never does. Even for Mp3 decoding. How do I get mp3s and DivX (or XVid) videos working? Where do I find these plugins or codecs?

---

### Post by earthpigg on 2009-08-31
close firefox and your music player.

go to applications -> accessories -> terminal. enter this:

> sudo apt-get install ubuntu-restricted-extras

start firefox and/or your music player.

:D

---

### Post by MrWES on 2009-08-31
From a terminal, Applications | Accessories | Terminal:

```
sudo apt-get install ubuntu-restricted-extras
```

Marines make the best friends -- for life!

---

### Post by Old_Grey_Wolf on 2009-08-31
Someone posted a very useful HOWTO; however, I can't find the link. I take no credit for his work. Here is what he had to getting multimedia working. Cut and paste the Code in the terminal.

if you have Ubuntu 9.04 "Jaunty Jackalope" simply do the following from a terminal window:

```
sudo wget http://www.medibuntu.org/sources.list.d/jaunty.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

Several codecs and plug-ins are needed for playing a variety multimedia formats correctly...
```
sudo apt-get install gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-fluendo-mp3 gstreamer0.10-gnonlin gstreamer0.10-plugins-farsight gstreamer0.10-sdl gstreamer-dbus-media-service gstreamer-tools
```

Install these as well (some may already be installed at this point, no worries)
```
sudo apt-get install realplayer w32codecs libdvdcss2 libxine1-ffmpeg debhelper fakeroot libfftw3-dev jackd sidplay-base liblrdf0-dev xsidplay mplayer avifile-divx-plugin avifile-xvid-plugin dh-make g++-multilib g++-4.3-multilib gcc-4.3-doc libstdc++6-4.3-dbg cvs gettext-doc jack-tools libjackasyn0 avifile-mad-plugin avifile-mjpeg-plugin avifile-player avifile-utils avifile-vorbis-plugin avifile-win32-plugin libcurl3-dbg libgcrypt11-doc libggi-target-emu libggi-target-monotext libggimisc2 gnutls-doc gnutls-bin guile-gnutls krb5-doc libraptor1-doc libstdc++6-4.3-doc mplayer-doc diff-doc
```

Last but not least...
```
sudo apt-get install easytag faac faad ffmpeg ffmpeg2theora flac gxine icedax id3tool id3v2 lame liba52-0.7.4-dev libavfilter0 libflac++6 libid3-3.8.3c2a libjpeg-progs libmozjs0d libmp4v2-0 libmpg123-0 libsox-fmt-alsa libsox-fmt-base libsox1 mpeg2dec mpeg3-utils mpegdemux mpg123 mpg321 libamrnb3 libamrwb3 sox tagtool toolame vorbis-tools gecko-mediaplayer

```
Install some fonts.
```
sudo apt-get install msttcorefonts mplayer-fonts ttf-xfree86-nonfree xfs
```

Adobe Flash too&#8230;
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by akhe on 2009-11-02
all the things you installed by the command line is also in that package of restricted plugins ??? or there is some differece?

---

### Post by earthpigg on 2009-11-02
doing all of the above in any particular order will have you set up with damn near everything that is available.

plenty of how-to guides around for migrating fonts from any old Windows install to Ubuntu, too, if you want that. not sure if that is allowed by forum guidelines though for a variety of rediculous legal reasons.

font piracy? please...

sorry, that last bit was entirely off topic :D

---

### Post by akhe on 2009-11-07
I am asking you, please can you tell me what is the difference between making this:

sudo apt-get install ubuntu-restricted-extras
and all the things you post.

( what exactly is not included in this "restricted extras" )

but I feel that is enough what you write there, but I am interested in it. thanks.

---

### Post by earthpigg on 2009-11-07
the codecs to play commerical region-coded DVD's is not included in ubuntu-restricted-extras. off the top of my head, the rest is.

---

