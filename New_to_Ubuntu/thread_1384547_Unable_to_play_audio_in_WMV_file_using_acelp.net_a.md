---
title: "Unable to play audio in WMV file using acelp.net audio codec"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by sokam on 2010-01-18
I have a bunch of video files (wmv) and somehow it won't play the audio in Ubuntu (9.10) using Totem (video only), MPlayer (video only also) or VLC (video only).  The video is fine.

I tested the same wmv files in Window and found that I am missing acelp.net audio codec.  So I installed acelp.net audio codec in window and they work fine with video AND audio.  (The location I download the window's audio codec does not have linux version)

My Question is:
How to install acelp.net audio codec in Ubuntu to make these file play with audio?

I believe I already installed all the codec I could find on Ubuntu.  But let me know how to verify as well.  

I also found that in the documentation, Mplayer should be able to play these files.  So Why can I?

[https://help.ubuntu.com/community/MPlayer](https://help.ubuntu.com/community/MPlayer)

---

### Post by cowboy7305 on 2010-01-18
Have you loaded all the gstreamer plug ins from the Ubuntu soft ware center

---

### Post by sokam on 2010-01-18
I got the following loaded:

GStreamer extra plugins
GStreamer ffmpeg video plugins
GStreamer plugins for mms, wavpack, quicktime, musepack
GStreamer plugins for aac, xvid, mpeg2, faad


Is that what you are looking for?

---

### Post by mc4man on 2010-01-18
If you're on a 32 bit install then you can get decoding of acelp in mplayer thru w32codecs which are available from medibuntu

If you're on a 64 bit install then you can't 
(the only solution there is to either build and install a 32 bit mplayer or run a windows 32 mplayer build thru wine

medibuntu repo install inst.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
after which
 
```
sudo apt-get install w32codecs
```

or just directly dl/ install from here with Gdebi

[http://packages.medibuntu.org/karmic/w32codecs.html](http://packages.medibuntu.org/karmic/w32codecs.html)

---

### Post by sokam on 2010-01-18
I am on 64bit.  Sadly.

I try to run mplayer thru wine but still don't have sound.  (I played with other file type and they are fine in wine).

So how do I force install the 32 bit mplayer on my 64 bit system.  I am reading this:
[http://www.unixtutorial.org/2008/03/install-32-bit-deb-packages-on-64-bit/](http://www.unixtutorial.org/2008/03/install-32-bit-deb-packages-on-64-bit/)

But I am having trouble finding the 32 bit mplayer to install. If possible, how can I force 32 bit mplayer to install in synaptic? Or else, where to download this.

---

### Post by mc4man on 2010-01-19
While for full functionality a 32 bit build and install is best, for a gui only mplayer to play troublesome files do this.

(depending on what ubuntu release/ wine ver. you may need to configure audio in winecfg to use oss instead of alsa - under audio tab uncheck alsa and ck. oss

In a terminal
```
mkdir winmplayer && cd winmplayer
```
```
wget -c ftp://ftp4.mplayerhq.hu/MPlayer/releases/win32/MPlayer-1.0rc2-gui.zip

```

```
unzip MPlayer-1.0rc2-gui.zip
```

```
wget -c http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007.orig.tar.gz
```

```
tar zxvf w32codecs_20071007.orig.tar.gz
```

```
mv ./all-20071007/* ./MPlayer-1.0rc2-gui/codecs

```

```
rmdir all-20071007
```

Inside of ~/winmplayer/Mplayer-1.0rc2-gui you'll find gmplayer.exe - open in wine, ect. (you can delete the zip and tar.gz still in winmplayer if you wish

You can create a launcher for it fairly easily

as far as a 32 bit build there are some threads - here are some things I found when trying last year on a live cd - post 28
[http://ubuntuforums.org/showthread.php?t=1232173&highlight=32+bit+mplayer&page=3](http://ubuntuforums.org/showthread.php?t=1232173&highlight=32+bit+mplayer&page=3)

Edit:
After fooling around with a bit - that mplayer worked much better in hardy, has some issues here in karmic though does work.
The video window will size to video being played, you can't make bigger without possible issue. So for a 720p file played full screen, for an .avi in a smaller window, ect. ect. 

Don't know if worth it...

---

### Post by sokam on 2010-01-20
Thanks, it works.  I can now play those wmv files with acelp.net audio codec.  And I see what you mean about the resizing issue.  After Toggle between full screen once, I can't move the video display anymore.  Kinda annoying but beat rebooting to Window from my computer.

I haven't try the method from the other link.

---

### Post by sokam on 2010-01-20
Hmmm... just tested a rm audio only file with Sipro/ACELP.NET codec and it won't open on mplayer 32 bit in wine.  But the other wmv files are fine with audio now.  Why?

Here is the rm file I was trying to listen:
[http://mfile.akamai.com/7870/rm/mitstorage.download.akamai.com/7870/6/6.774/ocw-6.774-16sep2004.rm](http://mfile.akamai.com/7870/rm/mitstorage.download.akamai.com/7870/6/6.774/ocw-6.774-16sep2004.rm)

[http://mfile.akamai.com/7870/rm/mitstorage.download.akamai.com/7870/6/6.774/ocw-6.774-21sep2004.rm](http://mfile.akamai.com/7870/rm/mitstorage.download.akamai.com/7870/6/6.774/ocw-6.774-21sep2004.rm)

---

### Post by mc4man on 2010-01-20
Those are slightly different format of Sipro ( RealAudio Sipro ), I don't think that win. mplayer can deal with ( a .so - see in red), (possibly there is a windows .dll that can be used...? - windows media runtime files

You could search for another win mplayer - what you're looking for is pre-built that will successfully install (doubtful) or like this one just is run.

May be better off with the 32 bit build which gives you a fully functioning mplayer

Your .rm's ( in mplayer, notice -playlist
Also they play back here in karmic with a working totem-xine I made

> mplayer -playlist [http://mfile.akamai.com/7870/rm/mitstorage.download.akamai.com/7870/6/6.774/ocw-6.774-21sep2004.rm](http://mfile.akamai.com/7870/rm/mitstorage.download.akamai.com/7870/6/6.774/ocw-6.774-21sep2004.rm)
Cache size set to 320 KBytes
Cache fill: 17.50% (57344 bytes)   
REAL file format detected.
Stream description: Audio Stream
Stream mimetype: audio/x-pn-realaudio
[real] Audio stream found, -aid 0
Clip info:
 title: OCW 6.774
 author: Academic Media Production Services
 copyright: (C) 2004 Massachusettes Institute of Technology
Opening audio decoder: [realaud] RealAudio decoder
opening shared obj '/usr/lib/codecs/[COLOR="Red"]sipr.so.6.0[/COLOR]'
Got sipr flavor 3 from bitrate 2000
AUDIO: 16000 Hz, 1 ch, s16le, 16.0 kbit/6.25% (ratio: 2000->32000)
[COLOR="Blue"]Selected audio codec: [rasipr] afm: realaud (RealAudio Sipro)[/COLOR]
Starting playback...


Vs. a acelp wmv that will play in the win player
> 
doug@doug-desktop:~$ mplayer '/home/doug/Videos/GipsyGuitar.wmv'
Selected video codec: [wmsdmod] vfm: dmo (Windows Media Screen Codec 2)

Opening audio decoder: [dshow] Win32/DirectShow decoders
AUDIO: 16000 Hz, 1 ch, s16le, 16.0 kbit/6.25% (ratio: 2000->32000)
Selected audio codec: [acelp] afm: dshow (ACELP.net Sipro Lab Audio)

Edit:
I guess there is a possibility that the linux realplayer could play those, - wouldn't know - won't install realplayer here to test

---

