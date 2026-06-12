---
title: "Flash applications/streaming"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by Tprimex3000 on 2009-08-27
It seems that I can't exactly stream video on youtube correctly, nor do many flash applications work properly. I've tried unistalling and reinstalling flash, but there was no success. The audio works(usually) and the video streams about 1 frame ever 10 seconds. Same with other applications, such as the photo uploader for photobucket.

---

### Post by Perfect Storm on 2009-08-27
A little bit more info is needed,

Ubuntu version?
32-bit/64-bit?
How did you install flash and version?

Also type this in firefox adresse box and post it;
```
about:plugins
```

---

### Post by Tprimex3000 on 2009-08-27
Right, sorry. 32-bit, 9.04, I installed it via
```
sudo apt-get install adobe-flashplugin
```(I believe)

**Default Plugin**

 File name:  libnullplugin.so The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.   MIME Type Description Suffixes Enabled    * All types .* No  **Demo Print Plugin for unix/linux**

 File name:  libunixprintplugin.so The demo print plugin for unix.   MIME Type Description Suffixes Enabled    application/x-print-unix-nsplugin Demo Print Plugin for Unix/Linux .pnt Yes  **DivX® Web Player**

 File name:  libtotem-mully-plugin.so DivX Web Player version 1.4.0.233   MIME Type Description Suffixes Enabled    video/divx AVI video divx Yes  **QuickTime Plug-in 7.2.0**

 File name:  libtotem-narrowspace-plugin.so The [Totem]("http://www.gnome.org/projects/totem/") 2.26.1 plugin handles video and audio streams.   MIME Type Description Suffixes Enabled    video/quicktime QuickTime video mov Yes   video/mp4 MPEG-4 video mp4 Yes   image/x-macpaint MacPaint Bitmap image pntg Yes   image/x-quicktime Macintosh Quickdraw/PICT drawing pict, pict1, pict2 Yes   video/x-m4v MPEG-4 video m4v Yes  **VLC Multimedia Plugin (compatible Totem 2.26.1)**

 File name:  libtotem-cone-plugin.so The [Totem]("http://www.gnome.org/projects/totem/") 2.26.1 plugin handles video and audio streams.   MIME Type Description Suffixes Enabled    application/x-vlc-plugin VLC Multimedia Plugin 
Yes   application/vlc VLC Multimedia Plugin 
Yes   video/x-google-vlc-plugin VLC Multimedia Plugin 
Yes   application/x-ogg Ogg multimedia file ogg Yes   application/ogg Ogg multimedia file ogg Yes   audio/ogg Ogg Audio oga Yes   audio/x-ogg Ogg Audio ogg Yes   video/ogg Ogg Video ogv Yes   video/x-ogg Ogg Video ogg Yes   application/annodex Annodex exchange format anx Yes   audio/annodex Annodex Audio axa Yes   video/annodex Annodex Video axv Yes   video/mpeg MPEG video mpg, mpeg, mpe Yes   audio/wav WAV audio wav Yes   audio/x-wav WAV audio wav Yes   audio/mpeg MP3 audio mp3 Yes   application/x-nsv-vp3-mp3 NullSoft video nsv Yes   video/flv Flash video flv Yes   application/x-totem-plugin Totem Multimedia plugin 
Yes  **Windows Media Player Plug-in 10 (compatible; Totem)**

 File name:  libtotem-gmp-plugin.so The [Totem]("http://www.gnome.org/projects/totem/") 2.26.1 plugin handles video and audio streams.   MIME Type Description Suffixes Enabled    application/x-mplayer2 AVI video avi, wma, wmv Yes   video/x-ms-asf-plugin ASF video asf, wmv Yes   video/x-msvideo AVI video asf, wmv Yes   video/x-ms-asf ASF video asf Yes   video/x-ms-wmv Windows Media video wmv Yes   video/x-wmv Windows Media video wmv Yes   video/x-ms-wvx Windows Media video wmv Yes   video/x-ms-wm Windows Media video wmv Yes   video/x-ms-wmp Windows Media video wmv Yes   application/x-ms-wms Windows Media video wms Yes   application/x-ms-wmp Windows Media video wmp Yes   application/asx Microsoft ASX playlist asx Yes   audio/x-ms-wma Windows Media audio wma Yes  **Java(TM) Plug-in 1.5.0_18-b02**

 File name:  libjavaplugin_oji.so Java(TM) Plug-in 1.5.0_18   MIME Type Description Suffixes Enabled    application/x-java-vm Java 
Yes   application/x-java-applet Java 
Yes   application/x-java-applet;version=1.1 Java 
Yes   application/x-java-applet;version=1.1.1 Java 
Yes   application/x-java-applet;version=1.1.2 Java 
Yes   application/x-java-applet;version=1.1.3 Java 
Yes   application/x-java-applet;version=1.2 Java 
Yes   application/x-java-applet;version=1.2.1 Java 
Yes   application/x-java-applet;version=1.2.2 Java 
Yes   application/x-java-applet;version=1.3 Java 
Yes   application/x-java-applet;version=1.3.1 Java 
Yes   application/x-java-applet;version=1.4 Java 
Yes   application/x-java-applet;version=1.4.1 Java 
Yes   application/x-java-applet;version=1.4.2 Java 
Yes   application/x-java-applet;version=1.5 Java 
Yes   application/x-java-applet;jpi-version=1.5.0_18 Java 
Yes   application/x-java-bean Java 
Yes   application/x-java-bean;version=1.1 Java 
Yes   application/x-java-bean;version=1.1.1 Java 
Yes   application/x-java-bean;version=1.1.2 Java 
Yes   application/x-java-bean;version=1.1.3 Java 
Yes   application/x-java-bean;version=1.2 Java 
Yes   application/x-java-bean;version=1.2.1 Java 
Yes   application/x-java-bean;version=1.2.2 Java 
Yes   application/x-java-bean;version=1.3 Java 
Yes   application/x-java-bean;version=1.3.1 Java 
Yes   application/x-java-bean;version=1.4 Java 
Yes   application/x-java-bean;version=1.4.1 Java 
Yes   application/x-java-bean;version=1.4.2 Java 
Yes   application/x-java-bean;version=1.5 Java 
Yes   application/x-java-bean;jpi-version=1.5.0_18 Java 
Yes  **Shockwave Flash**

 File name:  libswfdecmozilla.so Shockwave Flash 9.0 r999   MIME Type Description Suffixes Enabled    application/x-shockwave-flash Adobe Flash movie swf Yes   application/futuresplash FutureSplash movie spl Yes

Sorry that formatting came out a little messy.

---

### Post by Tprimex3000 on 2009-08-27
Bumping, because it seems these forums don't treat edited posts as new posts.

---

