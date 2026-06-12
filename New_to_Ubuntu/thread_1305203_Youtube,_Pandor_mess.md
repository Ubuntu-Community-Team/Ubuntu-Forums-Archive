---
title: "Youtube, Pandor mess"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by rancor99 on 2009-10-29
Hey guys I am new to ubuntu version 9.04 or the most recent one, and I am running KDE GNOME Version 2.26.1,  My problem is with youtube videos,  I know I have read a lot about it and already installed flash-pluginnonfree or the like, and I have re-installed it looked for non installed packages, and I simply cannot get the video up and running, it starts and loads, but when it goes to play it freezes, no sound comes out.
I also have no problem with audio as I have Amarok playing music.   I just have difficulty streaming, hopefully one of you can help me with these issues.  I also can't get pandora playing.

---

### Post by Shpongle on 2009-10-29
have you installed kubuntu-restricted-extras

sudo apt-get install kubuntu-restricted-extras or you can use synaptic package manager system-> administration->synaptic and select the package

also see here [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by rancor99 on 2009-10-29
I have installed the Kubuntu restricted and all that and it still will not work

---

### Post by Shpongle on 2009-10-29
have you tried to watch vids on any other sites??

---

### Post by Shpongle on 2009-10-29
did you try these [https://help.ubuntu.com/community/RestrictedFormats/StreamingVideo](https://help.ubuntu.com/community/RestrictedFormats/StreamingVideo) 

what browser are you using ?

---

### Post by rancor99 on 2009-10-29
Yes I have hulu, surfthechannel.net, and anything with a flash player will not play for me its quite frustrating

---

### Post by rancor99 on 2009-10-29
I'm using firefox, and I'm not sure what version it is that I'm running of firefox

---

### Post by Shpongle on 2009-10-29
did you install the adobe flash plugin ? , did you install xine-plugin

see [https://help.ubuntu.com/community/RestrictedFormats/NonNativeCodecs?action=show&redirect=RestrictedFormats%2FWindowsCodecs](https://help.ubuntu.com/community/RestrictedFormats/NonNativeCodecs?action=show&redirect=RestrictedFormats%2FWindowsCodecs)
youll have to enable medibuntu [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by rancor99 on 2009-10-29
I installed the adobe flash plugin

---

### Post by Shpongle on 2009-10-29
what about the xine-plugin ??

---

### Post by Shpongle on 2009-10-29
see here too [http://ubuntuforums.org/showthread.php?t=966459](http://ubuntuforums.org/showthread.php?t=966459) if that doesnt work

---

### Post by rancor99 on 2009-10-29
just installed the xine plugin and it didn't help playing videos, I get a picture but it won't play, and there is no sound

---

### Post by tk03759 on 2009-10-29
Are you on a 64-bit system? Flash has some big incompatability issues on 64-bit systems.

Do you know if you got flash 10? Try removing Flash from Firefox via the Add-On Manager, and installing from Adobe's site: [http://get.adobe.com/flashplayer/]("http://get.adobe.com/flashplayer/")

---

### Post by rancor99 on 2009-10-29
I tried the sudo apt-get -f install and got this out
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  install-package gdebi-kde
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

---

### Post by rancor99 on 2009-10-29
I tried installing the .deb from the flash website and it came back with this error
Error: A later version is already installed
so I guess that mean I already have it?

---

### Post by rancor99 on 2009-10-29
Also I am running 32 bit not 64

---

### Post by rancor99 on 2009-10-29
I typed aboutLplugins into the firefox web browser, and this was the output
**Default Plugin**

 File name:  libnullplugin.so The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.   MIME Type Description Suffixes Enabled    * All types .* No  **Demo Print Plugin for unix/linux**

 File name:  libunixprintplugin.so The demo print plugin for unix.   MIME Type Description Suffixes Enabled    application/x-print-unix-nsplugin Demo Print Plugin for Unix/Linux .pnt Yes  **VLC Multimedia Plug-in**

 File name:  libvlcplugin.so Version 0.9.9a Grishenko, copyright 1996-2007 The VideoLAN Team
[http://www.videolan.org/](http://www.videolan.org/)   MIME Type Description Suffixes Enabled    audio/mpeg MPEG audio mp2,mp3,mpga,mpega Yes   audio/x-mpeg MPEG audio mp2,mp3,mpga,mpega Yes   video/mpeg MPEG video mpg,mpeg,mpe Yes   video/x-mpeg MPEG video mpg,mpeg,mpe Yes   video/mpeg-system MPEG video mpg,mpeg,mpe,vob Yes   video/x-mpeg-system MPEG video mpg,mpeg,mpe,vob Yes   audio/x-mpegurl MPEG audio m3u Yes   video/mp4 MPEG-4 video mp4,mpg4 Yes   audio/mp4 MPEG-4 audio mp4,mpg4 Yes   audio/x-m4a MPEG-4 audio m4a Yes   application/mpeg4-iod MPEG-4 video mp4,mpg4 Yes   application/mpeg4-muxcodetable MPEG-4 video mp4,mpg4 Yes   video/x-msvideo AVI video avi Yes   video/quicktime QuickTime video mov,qt Yes   application/x-ogg Ogg stream ogg Yes   application/ogg Ogg stream ogg Yes   application/x-vlc-plugin VLC plug-in vlc Yes   video/x-ms-asf-plugin Windows Media Video asf,asx Yes   video/x-ms-asf Windows Media Video asf,asx Yes   application/x-mplayer2 Windows Media 
Yes   video/x-ms-wmv Windows Media wmv Yes   video/x-ms-wvx Windows Media Video wvx Yes   audio/x-ms-wma Windows Media Audio wma Yes   application/x-google-vlc-plugin Google VLC plug-in 
Yes   audio/wav WAV audio wav Yes   audio/x-wav WAV audio wav Yes   audio/3gpp 3GPP audio 3gp,3gpp Yes   video/3gpp 3GPP video 3gp,3gpp Yes   audio/3gpp2 3GPP2 audio 3g2,3gpp2 Yes   video/3gpp2 3GPP2 video 3g2,3gpp2 Yes   video/divx DivX video divx Yes   video/flv FLV video flv Yes   video/x-flv FLV video flv Yes   video/x-matroska Matroska video mkv Yes   audio/x-matroska Matroska audio mka Yes   application/xspf+xml Playlist xspf xspf Yes  **DivX® Web Player**

 File name:  libtotem-mully-plugin.so DivX Web Player version 1.4.0.233   MIME Type Description Suffixes Enabled    video/divx AVI video divx Yes  **QuickTime Plug-in 7.2.0**

 File name:  libtotem-narrowspace-plugin.so The [Totem]("http://www.gnome.org/projects/totem/") 2.26.1 plugin handles video and audio streams.   MIME Type Description Suffixes Enabled    video/quicktime QuickTime video mov Yes   video/mp4 MPEG-4 video mp4 Yes   image/x-macpaint MacPaint Bitmap image pntg Yes   image/x-quicktime Macintosh Quickdraw/PICT drawing pict, pict1, pict2 Yes   video/x-m4v MPEG-4 video m4v Yes  **VLC Multimedia Plugin (compatible Totem 2.26.1)**

 File name:  libtotem-cone-plugin.so The [Totem]("http://www.gnome.org/projects/totem/") 2.26.1 plugin handles video and audio streams.   MIME Type Description Suffixes Enabled    application/x-vlc-plugin VLC Multimedia Plugin 
Yes   application/vlc VLC Multimedia Plugin 
Yes   video/x-google-vlc-plugin VLC Multimedia Plugin 
Yes   application/x-ogg Ogg multimedia file ogg Yes   application/ogg Ogg multimedia file ogg Yes   audio/ogg Ogg Audio oga Yes   audio/x-ogg Ogg Audio ogg Yes   video/ogg Ogg Video ogv Yes   video/x-ogg Ogg Video ogg Yes   application/annodex Annodex exchange format anx Yes   audio/annodex Annodex Audio axa Yes   video/annodex Annodex Video axv Yes   video/mpeg MPEG video mpg, mpeg, mpe Yes   audio/wav WAV audio wav Yes   audio/x-wav WAV audio wav Yes   audio/mpeg MP3 audio mp3 Yes   application/x-nsv-vp3-mp3 NullSoft video nsv Yes   video/flv Flash video flv Yes   application/x-totem-plugin Totem Multimedia plugin 
Yes  **Windows Media Player Plug-in 10 (compatible; Totem)**

 File name:  libtotem-gmp-plugin.so The [Totem]("http://www.gnome.org/projects/totem/") 2.26.1 plugin handles video and audio streams.   MIME Type Description Suffixes Enabled    application/x-mplayer2 AVI video avi, wma, wmv Yes   video/x-ms-asf-plugin ASF video asf, wmv Yes   video/x-msvideo AVI video asf, wmv Yes   video/x-ms-asf ASF video asf Yes   video/x-ms-wmv Windows Media video wmv Yes   video/x-wmv Windows Media video wmv Yes   video/x-ms-wvx Windows Media video wmv Yes   video/x-ms-wm Windows Media video wmv Yes   video/x-ms-wmp Windows Media video wmv Yes   application/x-ms-wms Windows Media video wms Yes   application/x-ms-wmp Windows Media video wmp Yes   application/asx Microsoft ASX playlist asx Yes   audio/x-ms-wma Windows Media audio wma Yes  **Shockwave Flash**

 File name:  libgnashplugin.so Shockwave Flash 9.0 r999. Gnash 0.8.5, the GNU SWF Player.   Copyright © 2006, 2007, 2008 [Free Software   Foundation]("http://www.fsf.org/"), Inc. 
Gnash comes with NO WARRANTY, to the extent permitted by law. You may redistribute copies of Gnash under the terms of the [GNU General Public   License]("http://www.gnu.org/licenses/gpl.html"). For more information about Gnash, see [   http://www.gnu.org/software/gnash]("http://www.gnu.org/software/gnash/").   Compatible Shockwave Flash 9.0 r999.   MIME Type Description Suffixes Enabled    application/x-shockwave-flash Shockwave Flash swf Yes  **DivX Browser Plug-In**

 File name:  mplayerplug-in-dvx.so [mplayerplug-in]("http://mplayerplug-in.sourceforge.net/") 3.55

Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using [MPlayer]("http://mplayerhq.hu/") 
JavaScript Enabled and Using GTK2 Widgets
  MIME Type Description Suffixes Enabled    video/divx DivX Media Format divx Yes   video/vnd.divx DivX Media Format divx Yes  **QuickTime Plug-in 7.4.5**

 File name:  mplayerplug-in-qt.so [mplayerplug-in]("http://mplayerplug-in.sourceforge.net/") 3.55

Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using [MPlayer]("http://mplayerhq.hu/") 
JavaScript Enabled and Using GTK2 Widgets
  MIME Type Description Suffixes Enabled    video/quicktime Quicktime mov Yes   video/x-quicktime Quicktime mov Yes   image/x-quicktime Quicktime mov Yes   video/quicktime Quicktime mp4 Yes   video/quicktime Quicktime - Session Description Protocol sdp Yes   application/x-quicktimeplayer Quicktime mov Yes   application/smil SMIL smil Yes  **RealPlayer 9**

 File name:  mplayerplug-in-rm.so [mplayerplug-in]("http://mplayerplug-in.sourceforge.net/") 3.55

Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using [MPlayer]("http://mplayerhq.hu/") 
JavaScript Enabled and Using GTK2 Widgets
  MIME Type Description Suffixes Enabled    audio/x-pn-realaudio RealAudio ram,rm Yes   application/vnd.rn-realmedia RealMedia rm Yes   application/vnd.rn-realaudio RealAudio ra,ram Yes   video/vnd.rn-realvideo RealVideo rv Yes   audio/x-realaudio RealAudio ra Yes   audio/x-pn-realaudio-plugin RealAudio rpm Yes   application/smil SMIL smil Yes  **Windows Media Player Plug-in**

 File name:  mplayerplug-in-wmp.so [mplayerplug-in]("http://mplayerplug-in.sourceforge.net/") 3.55

Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using [MPlayer]("http://mplayerhq.hu/") 
JavaScript Enabled and Using GTK2 Widgets
  MIME Type Description Suffixes Enabled    application/asx Media Files * Yes   video/x-ms-asf-plugin Media Files * Yes   video/x-msvideo AVI avi,* Yes   video/msvideo AVI avi,* Yes   application/x-mplayer2 Media Files * Yes   application/x-ms-wmv Microsoft WMV video wmv,* Yes   video/x-ms-asf Media Files asf,asx,* Yes   video/x-ms-wm Media Files wm,* Yes   video/x-ms-wmv Microsoft WMV video wmv,* Yes   audio/x-ms-wmv Windows Media wmv,* Yes   video/x-ms-wmp Windows Media wmp,* Yes   application/x-ms-wmp Windows Media wmp,* Yes   video/x-ms-wvx Windows Media wvx,* Yes   audio/x-ms-wax Windows Media wax,* Yes   audio/x-ms-wma Windows Media wma,* Yes   application/x-drm-v2 Windows Media asx,* Yes   audio/wav Microsoft wave file wav,* Yes   audio/x-wav Microsoft wave file wav,* Yes  **mplayerplug-in 3.55**

 File name:  mplayerplug-in.so [mplayerplug-in]("http://mplayerplug-in.sourceforge.net/") 3.55

Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using [MPlayer]("http://mplayerhq.hu/") 
JavaScript Enabled and Using GTK2 Widgets
  MIME Type Description Suffixes Enabled    video/mpeg MPEG mpg,mpeg Yes   audio/mpeg MPEG mpg,mpeg Yes   video/x-mpeg MPEG mpg,mpeg Yes   video/x-mpeg2 MPEG2 mpv2,mp2ve Yes   audio/mpeg MPEG mpg,mpeg Yes   audio/x-mpeg MPEG mpg,mpeg Yes   audio/mpeg2 MPEG audio mp2 Yes   audio/x-mpeg2 MPEG audio mp2 Yes   audio/mp4 MPEG 4 audio mp4 Yes   audio/x-mp4 MPEG 4 audio mp4 Yes   video/mp4 MPEG 4 Video mp4 Yes   video/3gpp MPEG 4 Video mp4,3gp Yes   audio/mpeg3 MPEG audio mp3 Yes   audio/x-mpeg3 MPEG audio mp3 Yes   audio/x-mpegurl MPEG url m3u Yes   audio/mp3 MPEG audio mp3 Yes   application/x-ogg Ogg Vorbis Media ogg Yes   audio/ogg Ogg Vorbis Audio ogg Yes   audio/x-ogg Ogg Vorbis Audio ogg Yes   application/ogg Ogg Vorbis / Ogg Theora ogg Yes   audio/flac FLAC Audio flac Yes   audio/x-flac FLAC Audio flac Yes   video/fli FLI animation fli,flc Yes   video/x-fli FLI animation fli,flc Yes   video/x-flv Flash Video flv Yes   video/vnd.vivo VivoActive viv,vivo Yes   application/x-nsv-vp3-mp3 Nullsoft Streaming Video nsv Yes   audio/x-mod Soundtracker mod Yes   audio/basic Basic Audio File au,snd Yes   audio/x-basic Basic Audio File au,snd Yes  **Xine Plugin**

 File name:  xineplugin.so Xine Plugin version 1.0.2, (c) [The Xine Project]("http://www.xinehq.de/").
Windows Media Player / RealPlayer / QuickTime compatible.   MIME Type Description Suffixes Enabled    application/annodex  Annodex media  anx Yes   application/x-annodex  Annodex media  anx Yes   audio/annodex  Annodex audio  axa Yes   audio/x-annodex  Annodex audio  axa Yes   video/annodex  Annodex video  axv Yes   video/x-annodex  Annodex video  axv Yes   video/msvideo  AVI video  avi Yes   video/x-msvideo  AVI video  avi Yes   video/x-flv  Flash video  flv Yes   video/flv  Flash video  flv Yes   application/x-flash-video  Flash video  flv Yes   video/x-ms-asf  ASF stream  asf Yes   video/x-ms-wmv  Windows Media Video  wmv Yes   audio/x-ms-wma  Windows Media Audio  wma Yes   application/vnd.ms-asf  ASF stream  asf Yes   application/x-mplayer2  mplayer2  asf,asx,asp Yes   video/x-ms-asf-plugin  mms animation  asf,asx,asp Yes   video/x-ms-wvx  wmv metafile  wvx Yes   video/x-ms-wax  wma metafile  wva Yes   video/x-flic  Autodesk FLIC files  fli,flc Yes   video/mkv  matroska  mkv Yes   video/x-matroska  matroska  mkv Yes   audio/x-aiff  AIFF audio  aif, aiff Yes   audio/aiff  AIFF audio  aif, aiff Yes   audio/x-pn-aiff  AIFF audio  aif, aiff Yes   audio/x-flac  FLAC Audio  flac Yes   audio/flac  FLAC Audio  flac Yes   audio/x-realaudio  RealAudio File  ra Yes   audio/basic  ULAW  snd,au Yes   audio/x-basic  ULAW  snd,au Yes   audio/x-pn-au  ULAW  snd,au Yes   audio/x-mod  SoundTracker/NoiseTracker/ProTracker Module  mod Yes   audio/mod  SoundTracker/NoiseTracker/ProTracker Module  mod Yes   audio/it  ImpulseTracker Module  it Yes   audio/x-it  ImpulseTracker Module  it Yes   audio/x-stm  ScreamTracker 2 Module  stm Yes   audio/x-s3m  ScreamTracker 3 Module  s3m Yes   audio/s3m  ScreamTracker 3 Module  s3m Yes   application/playerpro  669 Tracker Module  669 Yes   application/adrift  ADRIFT Module File  amf Yes   audio/med  Amiga MED/OctaMED Tracker Module Sound File  med Yes   audio/x-amf  ADRIFT Module File  amf Yes   audio/x-xm  FastTracker II Audio  xm Yes   audio/xm  FastTracker II Audio  xm Yes   video/quicktime  Quicktime animation  mov,qt Yes   video/x-quicktime  Quicktime animation  mov,qt Yes   audio/x-m4a  MPEG-4 audio  m4a,m4b Yes   application/x-quicktimeplayer  Quicktime list  qtl Yes   video/mp4  MPEG-4 video  mp4,mpg4 Yes   audio/mp4  MPEG-4 audio  mp4,mpg4 Yes   audio/x-8svx  IFF-8SVX Audio  8svx Yes   audio/8svx  IFF-8SVX Audio  8svx Yes   audio/x-16sv  IFF-16SV Audio  16sv Yes   audio/168sv  IFF-16SV Audio  16sv Yes   image/x-ilbm  IFF-ILBM Picture  ilbm Yes   image/ilbm  IFF-ILBM Picture  ilbm Yes   video/x-anim  IFF-ANIM Video  anim Yes   video/anim  IFF-ANIM Video  anim Yes   application/ogg  Ogg Stream  ogx Yes   application/x-ogg  Ogg Stream  ogx Yes   application/x-ogm  Ogg Stream  ogx Yes   application/x-ogm-audio  Ogg Audio  oga Yes   application/x-ogm-video  Ogg Video  ogv Yes   audio/ogg  Ogg Audio  oga Yes   audio/x-ogg  Ogg Audio  oga Yes   video/ogg  Ogg Video  ogv Yes   video/x-ogg  Ogg Video  ogv Yes   image/png  PNG image  png Yes   image/x-png  PNG image  png Yes   video/mng  MNG animation  mng Yes   video/x-mng  MNG animation  mng Yes   audio/x-pn-realaudio  Real Media file  ra, rm, ram Yes   audio/x-pn-realaudio-plugin  Real Media plugin file  rpm Yes   audio/x-real-audio  Real Media file  ra, rm, ram Yes   application/vnd.rn-realmedia  Real Media file  ra, rm, ram Yes   video/mpeg  MPEG animation  mpeg, mpg, mpe Yes   video/x-mpeg  MPEG animation  mpeg, mpg, mpe Yes   audio/x-wav  WAV audio  wav Yes   audio/wav  WAV audio  wav Yes   audio/x-pn-wav  WAV audio  wav Yes   audio/x-pn-windows-acm  WAV audio  wav Yes   audio/musepack  Musepack audio  mpc, mp+, mpp Yes   audio/x-musepack  Musepack audio  mpc, mp+, mpp Yes   audio/x-flac  FLAC Audio  flac Yes   audio/flac  FLAC Audio  flac Yes   audio/mpeg2  MPEG audio  mp2 Yes   audio/x-mpeg2  MPEG audio  mp2 Yes   audio/mpeg3  MPEG audio  mp3 Yes   audio/x-mpeg3  MPEG audio  mp3 Yes   audio/mpeg  MPEG audio  mpa,abs,mpega Yes   audio/x-mpeg  MPEG audio  mpa,abs,mpega Yes   audio/x-mpegurl  MPEG audio  mp3 Yes   audio/mpegurl  MPEG audio  mp3 Yes   audio/mp3  MPEG audio  mp3 Yes   audio/x-mp3  MPEG audio  mp3 Yes   audio/x-wavpack  WavPack audioaudio/x-scpls  pls: Winamp playlist: wv,wvp Yes   application/smil  SMIL playlist  smi, smil Yes   application/xspf+xml  XSPF playlist  xspf Yes   application/x-xine-plugin  Xine plugin  
Yes  **Shockwave Flash**

 File name:  libswfdecmozilla.so Shockwave Flash 9.0 r999   MIME Type Description Suffixes Enabled    application/x-shockwave-flash Adobe Flash movie swf Yes   application/futuresplash FutureSplash movie spl Yes

---

### Post by lovinglinux on 2009-10-29
See **Solution** [*[COLOR="Red"]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004).

---

### Post by thogor on 2009-11-01
Hi, after upgraded to 9.10 I found two problems, one bug to do with ecc modules, and my flash went a little nuts. It was not working with  surfthechannel.com, the final links to go to the actual player sites like youtube (click to go to host sites), clicked and nothing happened.
So stupidly tried to install newer version (32-bit), forcing the architecture, from the adobe site. Broke the plug-in functionality. Had to get the 64-bit version from adobe labs. Manually changed the libflashplayer.so and so far every thing seems to be working (no npwrapper ).

---

