---
title: "Ubuntu 10.04 Overheating Problem"
date: 2010-05-31
forum: New to Ubuntu
---

### Post by alfa_80 on 2010-05-31
Hi all,

I'm on ubuntu 10.04 via HP laptop. Its processor is Core 2 Duo T8100 @2.10GHz with 3GiB of Ram..With 9.10 previously, i didn't have this sort of problem but now, it's really bad. Even when i watch "youtube", the temperature will tremendously increase up to 100++ deg celcius.

Is there any remedy?? And I do not want to downgrade to 9.10 though.

Thanks in advance..

-alfa-

---

### Post by nhasian on 2010-05-31
my HP laptop has an Intel Core2Duo CPU T7700 @ 2.40GHz and I am not experiencing that problem.  my CPU is idling at 50C right now even with an nvidia8600 GPU. 

100C is not good you will probably start to smell plastic at that temperature.  Can you verify that your fans are not clogged up with dust and spinning properly?  also if your cpu spikes you can see what process is taking up all your resources with the terminal command:

```
top
```

unfortunately flash does eat up a lot of CPU cycles in linux as it is not optimized as well as in windows (thats totally adobe's fault btw)
you can get newer flash plugins for firefox for either ubuntu 32bit or 64bit.

first make sure to remove any flash plugins you have installed. then install one of the following:

[Adobe Flash 10.1 Release Candidate 6 32-bit]("http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_rc6_linux_052510.tar.gz") (released May 25th)
[URL="http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz"]
Adobe Flash 10.0 64bit[/URL] (released Feb 11th)

after you extract the file it should be copied to:

/usr/lib/mozilla/plugins/libflashplayer.so

that should help your flash performance

---

### Post by philinux on 2010-05-31
Also see the General Help sticky, last post I think.

---

### Post by alfa_80 on 2010-05-31
> **nhasian said:**
> my HP laptop has an Intel Core2Duo CPU T7700 @ 2.40GHz and I am not experiencing that problem.  my CPU is idling at 50C right now even with an nvidia8600 GPU. 

100C is not good you will probably start to smell plastic at that temperature.  Can you verify that your fans are not clogged up with dust and spinning properly?  also if your cpu spikes you can see what process is taking up all your resources with the terminal command:

```
top
```unfortunately flash does eat up a lot of CPU cycles in linux as it is not optimized as well as in windows (thats totally adobe's fault btw)
you can get newer flash plugins for firefox for either ubuntu 32bit or 64bit.

first make sure to remove any flash plugins you have installed. then install one of the following:

[Adobe Flash 10.1 Release Candidate 6 32-bit]("http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_rc6_linux_052510.tar.gz") (released May 25th)
[URL="http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz"]
Adobe Flash 10.0 64bit[/URL] (released Feb 11th)

after you extract the file it should be copied to:

/usr/lib/mozilla/plugins/libflashplayer.so

that should help your flash performance

I've tried to substitute with the new version of adobe flash as you suggested, but unfortunately, it's not yet successful. 

I guess it might be the newer version of NVIDIA (nvidia-current) is the culprit. Does it make sense?? Are you using nvidia-current as well?

---

### Post by nhasian on 2010-05-31
yes i've tried both the native nvidia driver in linux, but i had to switch to the nvidia-current for my Boxee software.  they both worked fine for me.  There's even newer nvidia drivers in the PPA but i haven't tried that one yet.

can you verify that you have installed the adobe flash correctly in your browser by typing:

```
about:plugins
```

---

### Post by alfa_80 on 2010-05-31
> **nhasian said:**
> yes i've tried both the native nvidia driver in linux, but i had to switch to the nvidia-current for my Boxee software.  they both worked fine for me.  There's even newer nvidia drivers in the PPA but i haven't tried that one yet.

can you verify that you have installed the adobe flash correctly in your browser by typing:

```
about:plugins
```

Below, i just copied and pasted the output after query:
> 
Installed plugins
Find more information about browser plugins at mozilla.org.
Help for installing plugins is available from plugindoc.mozdev.org.
Xine Plugin

    File: xineplugin.so
    Version: 
    Xine Plugin version 1.0.2, (c) The Xine Project.
    Windows Media Player / RealPlayer / QuickTime compatible.

MIME Type     Description     Suffixes     Enabled
application/annodex     Annodex media     anx     Yes
application/x-annodex     Annodex media     anx     Yes
audio/annodex     Annodex audio     axa     Yes
audio/x-annodex     Annodex audio     axa     Yes
video/annodex     Annodex video     axv     Yes
video/x-annodex     Annodex video     axv     Yes
audio/x-pn-realaudio     Real Media file     ra, rm, ram     Yes
audio/x-pn-realaudio-plugin     Real Media plugin file     rpm     Yes
audio/x-real-audio     Real Media file     ra, rm, ram     Yes
application/vnd.rn-realmedia     Real Media file     ra, rm, ram     Yes
video/x-flic     Autodesk FLIC files     fli,flc     Yes
audio/x-8svx     IFF-8SVX Audio     8svx     Yes
audio/8svx     IFF-8SVX Audio     8svx     Yes
audio/x-16sv     IFF-16SV Audio     16sv     Yes
audio/168sv     IFF-16SV Audio     16sv     Yes
image/x-ilbm     IFF-ILBM Picture     ilbm     Yes
image/ilbm     IFF-ILBM Picture     ilbm     Yes
video/x-anim     IFF-ANIM Video     anim     Yes
video/anim     IFF-ANIM Video     anim     Yes
application/ogg     Ogg Stream     ogx     Yes
application/x-ogg     Ogg Stream     ogx     Yes
application/x-ogm     Ogg Stream     ogx     Yes
application/x-ogm-audio     Ogg Audio     oga     Yes
application/x-ogm-video     Ogg Video     ogv     Yes
audio/ogg     Ogg Audio     oga     Yes
audio/x-ogg     Ogg Audio     oga     Yes
video/ogg     Ogg Video     ogv     Yes
video/x-ogg     Ogg Video     ogv     Yes
video/quicktime     Quicktime animation     mov,qt     Yes
video/x-quicktime     Quicktime animation     mov,qt     Yes
audio/x-m4a     MPEG-4 audio     m4a,m4b     Yes
application/x-quicktimeplayer     Quicktime list     qtl     Yes
video/mp4     MPEG-4 video     mp4,mpg4     Yes
audio/mp4     MPEG-4 audio     mp4,mpg4     Yes
video/msvideo     AVI video     avi     Yes
video/x-msvideo     AVI video     avi     Yes
audio/x-aiff     AIFF audio     aif, aiff     Yes
audio/aiff     AIFF audio     aif, aiff     Yes
audio/x-pn-aiff     AIFF audio     aif, aiff     Yes
audio/x-flac     FLAC Audio     flac     Yes
audio/flac     FLAC Audio     flac     Yes
audio/x-realaudio     RealAudio File     ra     Yes
audio/basic     ULAW     snd,au     Yes
audio/x-basic     ULAW     snd,au     Yes
audio/x-pn-au     ULAW     snd,au     Yes
audio/x-mod     SoundTracker/NoiseTracker/ProTracker Module     mod     Yes
audio/mod     SoundTracker/NoiseTracker/ProTracker Module     mod     Yes
audio/it     ImpulseTracker Module     it     Yes
audio/x-it     ImpulseTracker Module     it     Yes
audio/x-stm     ScreamTracker 2 Module     stm     Yes
audio/x-s3m     ScreamTracker 3 Module     s3m     Yes
audio/s3m     ScreamTracker 3 Module     s3m     Yes
application/playerpro     669 Tracker Module     669     Yes
application/adrift     ADRIFT Module File     amf     Yes
audio/med     Amiga MED/OctaMED Tracker Module Sound File     med     Yes
audio/x-amf     ADRIFT Module File     amf     Yes
audio/x-xm     FastTracker II Audio     xm     Yes
audio/xm     FastTracker II Audio     xm     Yes
video/mkv     matroska     mkv     Yes
video/x-matroska     matroska     mkv     Yes
video/x-flv     Flash video     flv     Yes
video/flv     Flash video     flv     Yes
application/x-flash-video     Flash video     flv     Yes
image/png     PNG image     png     Yes
image/x-png     PNG image     png     Yes
video/mng     MNG animation     mng     Yes
video/x-mng     MNG animation     mng     Yes
video/x-ms-asf     ASF stream     asf     Yes
video/x-ms-wmv     Windows Media Video     wmv     Yes
audio/x-ms-wma     Windows Media Audio     wma     Yes
application/vnd.ms-asf     ASF stream     asf     Yes
application/x-mplayer2     mplayer2     asf,asx,asp     Yes
video/x-ms-asf-plugin     mms animation     asf,asx,asp     Yes
video/x-ms-wvx     wmv metafile     wvx     Yes
video/x-ms-wax     wma metafile     wva     Yes
audio/x-wav     WAV audio     wav     Yes
audio/wav     WAV audio     wav     Yes
audio/x-pn-wav     WAV audio     wav     Yes
audio/x-pn-windows-acm     WAV audio     wav     Yes
audio/musepack     Musepack audio     mpc, mp+, mpp     Yes
audio/x-musepack     Musepack audio     mpc, mp+, mpp     Yes
audio/x-wavpack     WavPack audio     wv,wvp     Yes
audio/x-flac     FLAC Audio     flac     Yes
audio/flac     FLAC Audioaudio/x-scpls     pls: Winamp playlist: flac     Yes
application/smil     SMIL playlist     smi, smil     Yes
application/xspf+xml     XSPF playlist     xspf     Yes
application/x-xine-plugin     Xine plugin         Yes
DivX Browser Plug-In

    File: gecko-mediaplayer-dvx.so
    Version: 
    Gecko Media Player 0.9.9.2

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer

MIME Type     Description     Suffixes     Enabled
video/divx     DivX Media Format     divx     Yes
video/vnd.divx     DivX Media Format     divx     Yes
QuickTime Plug-in 7.6.4

    File: gecko-mediaplayer-qt.so
    Version: 
    Gecko Media Player 0.9.9.2

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer

MIME Type     Description     Suffixes     Enabled
video/quicktime     Quicktime     mov     Yes
video/x-quicktime     Quicktime     mov     Yes
image/x-quicktime     Quicktime     mov     Yes
video/quicktime     Quicktime     mp4     Yes
video/quicktime     Quicktime - Session Description Protocol     sdp     Yes
application/x-quicktimeplayer     Quicktime     mov     Yes
RealPlayer 9

    File: gecko-mediaplayer-rm.so
    Version: 
    Gecko Media Player 0.9.9.2

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer

MIME Type     Description     Suffixes     Enabled
audio/x-pn-realaudio     RealAudio     ram,rm     Yes
application/vnd.rn-realmedia     RealMedia     rm     Yes
application/vnd.rn-realaudio     RealAudio     ra,ram     Yes
video/vnd.rn-realvideo     RealVideo     rv     Yes
audio/x-realaudio     RealAudio     ra     Yes
audio/x-pn-realaudio-plugin     RealAudio     rpm     Yes
application/smil     SMIL     smil     Yes
Windows Media Player Plug-in

    File: gecko-mediaplayer-wmp.so
    Version: 
    Gecko Media Player 0.9.9.2

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer

MIME Type     Description     Suffixes     Enabled
application/asx     Media Files     *     Yes
video/x-ms-asf-plugin     Media Files     *     Yes
video/x-msvideo     AVI     avi,*     Yes
video/msvideo     AVI     avi,*     Yes
application/x-mplayer2     Media Files     *     Yes
application/x-ms-wmv     Microsoft WMV video     wmv,*     Yes
video/x-ms-asf     Media Files     asf,asx,*     Yes
video/x-ms-asx     Media Files     asx,*     Yes
video/x-ms-wm     Media Files     wm,*     Yes
video/x-ms-wmv     Microsoft WMV video     wmv,*     Yes
audio/x-ms-wmv     Windows Media     wmv,*     Yes
video/x-ms-wmp     Windows Media     wmp,*     Yes
application/x-ms-wmp     Windows Media     wmp,*     Yes
video/x-ms-wvx     Windows Media     wvx,*     Yes
audio/x-ms-wax     Windows Media     wax,*     Yes
audio/x-ms-wma     Windows Media     wma,*     Yes
application/x-drm-v2     Windows Media     asx,*     Yes
audio/wav     Microsoft wave file     wav,*     Yes
audio/x-wav     Microsoft wave file     wav,*     Yes
mplayerplug-in is now gecko-mediaplayer 0.9.9.2

    File: gecko-mediaplayer.so
    Version: 
    Gecko Media Player 0.9.9.2

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer

MIME Type     Description     Suffixes     Enabled
audio/x-mpegurl     MPEG Playlist     m3u     Yes
video/mpeg     MPEG     mpg,mpeg     Yes
audio/mpeg     MPEG     mpg,mpeg     Yes
video/x-mpeg     MPEG     mpg,mpeg     Yes
video/x-mpeg2     MPEG2     mpv2,mp2ve     Yes
audio/mpeg     MPEG     mpg,mpeg     Yes
audio/x-mpeg     MPEG     mpg,mpeg     Yes
audio/mpeg2     MPEG audio     mp2     Yes
audio/x-mpeg2     MPEG audio     mp2     Yes
audio/mp4     MPEG 4 audio     mp4     Yes
audio/x-mp4     MPEG 4 audio     mp4     Yes
video/mp4     MPEG 4 Video     mp4     Yes
video/x-m4v     MPEG 4 Video     m4v     Yes
video/3gpp     MPEG 4 Video     mp4,3gp     Yes
audio/mpeg3     MPEG audio     mp3     Yes
audio/x-mpeg3     MPEG audio     mp3     Yes
audio/x-mpegurl     MPEG url     m3u     Yes
audio/mp3     MPEG audio     mp3     Yes
application/x-ogg     Ogg Vorbis Media     ogg,oga,ogm     Yes
application/ogg     Ogg Vorbis Media     ogg,oga,ogm     Yes
audio/x-ogg     Ogg Vorbis Audio     ogg,oga     Yes
audio/ogg     Ogg Vorbis Audio     ogg,oga     Yes
video/x-ogg     Ogg Vorbis Video     ogg,ogm     Yes
video/ogg     Ogg Vorbis Video     ogg,ogm     Yes
application/x-vlc-plugin     VLC plug-in     vlc     Yes
application/x-google-vlc-plugin     Google VLC plug-in         Yes
audio/flac     FLAC Audio     flac     Yes
audio/x-flac     FLAC Audio     flac     Yes
video/fli     FLI animation     fli,flc     Yes
video/x-fli     FLI animation     fli,flc     Yes
video/x-flv     Flash Video     flv     Yes
video/flv     Flash Video     flv     Yes
video/vnd.vivo     VivoActive     viv,vivo     Yes
audio/x-matroska     Matroska Audio     mka     Yes
video/x-matroska     Matroska Video     mkv     Yes
application/x-nsv-vp3-mp3     Nullsoft Streaming Video     nsv     Yes
audio/x-mod     Soundtracker     mod     Yes
audio/x-aiff     AIFF Audio     aif     Yes
audio/basic     Basic Audio File     au,snd     Yes
audio/x-basic     Basic Audio File     au,snd     Yes
audio/midi     MIDI Audio     mid,midi,kar     Yes
audio/x-scpls     Shoutcast Playlist     pls     Yes
video/x-mng     Multiple-Image Network Graphics     mng     Yes
iTunes Application Detector

    File: librhythmbox-itms-detection-plugin.so
    Version: 
    This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.

MIME Type     Description     Suffixes     Enabled
application/itunes-plugin             Yes
VLC Multimedia Plugin (compatible Totem 2.30.2)

    File: libtotem-cone-plugin.so
    Version: 
    The Totem 2.30.2 plugin handles video and audio streams.

MIME Type     Description     Suffixes     Enabled
application/x-vlc-plugin     VLC Multimedia Plugin         Yes
application/vlc     VLC Multimedia Plugin         Yes
video/x-google-vlc-plugin     VLC Multimedia Plugin         Yes
application/x-ogg     Ogg multimedia file     ogg     Yes
application/ogg     Ogg multimedia file     ogg     Yes
audio/ogg     Ogg Audio     oga     Yes
audio/x-ogg     Ogg Audio     ogg     Yes
video/ogg     Ogg Video     ogv     Yes
video/x-ogg     Ogg Video     ogg     Yes
application/annodex     Annodex exchange format     anx     Yes
audio/annodex     Annodex Audio     axa     Yes
video/annodex     Annodex Video     axv     Yes
video/mpeg     MPEG video     mpg, mpeg, mpe     Yes
audio/wav     WAV audio     wav     Yes
audio/x-wav     WAV audio     wav     Yes
audio/mpeg     MP3 audio     mp3     Yes
application/x-nsv-vp3-mp3     NullSoft video     nsv     Yes
video/flv     Flash video     flv     Yes
application/x-totem-plugin     Totem Multimedia plugin         Yes
Windows Media Player Plug-in 10 (compatible; Totem)

    File: libtotem-gmp-plugin.so
    Version: 
    The Totem 2.30.2 plugin handles video and audio streams.

MIME Type     Description     Suffixes     Enabled
application/x-mplayer2     AVI video     avi, wma, wmv     Yes
video/x-ms-asf-plugin     ASF video     asf, wmv     Yes
video/x-msvideo     AVI video     asf, wmv     Yes
video/x-ms-asf     ASF video     asf     Yes
video/x-ms-wmv     Windows Media video     wmv     Yes
video/x-wmv     Windows Media video     wmv     Yes
video/x-ms-wvx     Windows Media video     wmv     Yes
video/x-ms-wm     Windows Media video     wmv     Yes
video/x-ms-wmp     Windows Media video     wmv     Yes
application/x-ms-wms     Windows Media video     wms     Yes
application/x-ms-wmp     Windows Media video     wmp     Yes
application/asx     Microsoft ASX playlist     asx     Yes
audio/x-ms-wma     Windows Media audio     wma     Yes
DivX® Web Player

    File: libtotem-mully-plugin.so
    Version: 
    DivX Web Player version 1.4.0.233

MIME Type     Description     Suffixes     Enabled
video/divx     AVI video     divx     Yes
QuickTime Plug-in 7.6.6

    File: libtotem-narrowspace-plugin.so
    Version: 
    The Totem 2.30.2 plugin handles video and audio streams.

MIME Type     Description     Suffixes     Enabled
video/quicktime     QuickTime video     mov     Yes
video/mp4     MPEG-4 video     mp4     Yes
image/x-macpaint     MacPaint Bitmap image     pntg     Yes
image/x-quicktime     Macintosh Quickdraw/PICT drawing     pict, pict1, pict2     Yes
video/x-m4v     MPEG-4 video     m4v     Yes
Shockwave Flash

    File: libflashplayer.so
    Version: 
    Shockwave Flash 10.1 r53

MIME Type     Description     Suffixes     Enabled
application/x-shockwave-flash     Shockwave Flash     swf     Yes
application/futuresplash     FutureSplash Player     spl     Yes




---

### Post by alfa_80 on 2010-05-31
Another problem I have is about my external cooler/fan is not working any longer..I'm quite sure it's not because of the USB port because when I tried to use my USB stick, it worked fine..

Any ideas?

Thanks in advance..

---

### Post by csdiwhitt on 2010-08-25
Ubuntu 10.04 overheating is software related. I am running an AMD 3 processor using Ubuntu 10.04,2.30.2, (Ubuntu 2010-06-25), 2.6.32-24-generic (#41-Ubuntu SMP Thu Aug 19 01:38:40 UTC 2010),4.4.3 (x86_64-linux-gnu).

Two pieces of software are causing high (to 100% all three processors) processor utilization:

Adobe Flash Player 10.1 and tracker metadata database, index and search tool.

I have observed both take the processor X3 to 100% on the monitor and drop to 10 to 20% X3 as soon as I stop them.

Before you spend a lot of worry over your hardware check the system monitor.

Adobe Flash Player 10.1 problem occurs as soon as I get on a web site that uses that level of the player.  I can play everything up through 7 without a problem,

Tracker is different, as long as it is indexing it runs fine, but as soon as it finishes, instead of going dormant, it starts hogging processor time.  I have uninstalled it because I have to Kill it every time I restart.

---

### Post by myromance123 on 2010-10-14
I use a HP Pavilion DV3500 with an Nvidia card. My overheating went to a point of making my laptop not able to stand for more than a couple of minutes after loading into any OS. At first (since I use Ubuntu more frequently than Windoze), I though Ubuntu was unable to switch the fan on as no air was coming out anymore (or very little).

 I sent it in for a check at the HP outlet, they replaced my Nvidia card's fan. It had failed (or either got extremely clogged with dust due to HP's faulty design).

This is a typical problem with HP systems.

This is just my experience, wanted to share it with you.

---

