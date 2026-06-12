---
title: "Flash player is only working on some sites? Please help"
date: 2011-01-16
forum: New to Ubuntu
---

### Post by Ziadance on 2011-01-16
[SIZE=3]Hello
Flash player is only working on certain sites, youtube is fine but videos on facebook and the bbc news website do not play.  

When I follow the link to install the latest version of flash player I get the message that it is already installed.  

Any suggestions? 
I thank you in anticipation of your replies :D  
[/SIZE]

---

### Post by Perfect Storm on 2011-01-16
Can you please post the output of

```
about:plugins
```
(put this command in your adresse box of your browser).

---

### Post by taseedorf on 2011-01-16
I've had this same problem.  The reason being is that Flash is only a container and the underlying codec is usually the issue.  First off, completely remove flash via Synaptic.  Secondly, install the restricted extras and the gstreamer plugins via Synaptic.  Then, reinstall flash.  All should work fine.  Let us know. :)

---

### Post by zeroseven0183 on 2011-01-16
Is this on Mozilla Firefox or on Google Chrome (Chromium)?

---

### Post by Ziadance on 2011-01-16
.

---

### Post by Ziadance on 2011-01-16
> **zeroseven0183 said:**
> Is this on Mozilla Firefox or on Google Chrome (Chromium)?

Hi it's Firefox

---

### Post by Ziadance on 2011-01-16
> **Artificial Intelligence said:**
> Can you please post the output of

```
about:plugins
```(put this command in your adresse box of your browser).
  **Installed plug-ins**

 Find more information about browser plug-ins at  [mozilla.org]("https://pfs.mozilla.org/plugins/"). 
 Help for installing plug-ins is available from  [plugindoc.mozdev.org]("http://plugindoc.mozdev.org/"). 
 **Adobe Reader 9.4**

 File:  nppdf.soVersion:   The Adobe Reader plugin is used to enable viewing of PDF and FDF files from within the browser.    MIME Type Description Suffixes Enabled    application/pdf Portable Document Format pdf Yes   application/vnd.fdf Acrobat Forms Data Format fdf Yes   application/vnd.adobe.xfdf XML Version of Acrobat Forms Data Format xfdf Yes   application/vnd.adobe.xdp+xml Acrobat XML Data Package xdp Yes   application/vnd.adobe.xfd+xml Adobe FormFlow99 Data File xfd Yes  **VLC Multimedia Plugin (compatible Totem 2.32.0)**

 File:  libtotem-cone-plugin.soVersion:   The [Totem]("http://www.gnome.org/projects/totem/") 2.32.0 plugin handles video and audio streams.   MIME Type Description Suffixes Enabled    application/x-vlc-plugin VLC Multimedia Plugin 
Yes   application/vlc VLC Multimedia Plugin 
Yes   video/x-google-vlc-plugin VLC Multimedia Plugin 
Yes   application/x-ogg Ogg multimedia file ogg Yes   application/ogg Ogg multimedia file ogg Yes   audio/ogg Ogg Audio oga Yes   audio/x-ogg Ogg Audio ogg Yes   video/ogg Ogg Video ogv Yes   video/x-ogg Ogg Video ogg Yes   application/annodex Annodex exchange format anx Yes   audio/annodex Annodex Audio axa Yes   video/annodex Annodex Video axv Yes   video/mpeg MPEG video mpg, mpeg, mpe Yes   audio/wav WAV audio wav Yes   audio/x-wav WAV audio wav Yes   audio/mpeg MP3 audio mp3 Yes   application/x-nsv-vp3-mp3 NullSoft video nsv Yes   video/flv Flash video flv Yes   video/webm WebM video webm Yes   application/x-totem-plugin Totem Multimedia plugin 
Yes  **Windows Media Player Plug-in 10 (compatible; Totem)**

 File:  libtotem-gmp-plugin.soVersion:   The [Totem]("http://www.gnome.org/projects/totem/") 2.32.0 plugin handles video and audio streams.   MIME Type Description Suffixes Enabled    application/x-mplayer2 AVI video avi, wma, wmv Yes   video/x-ms-asf-plugin ASF video asf, wmv Yes   video/x-msvideo AVI video asf, wmv Yes   video/x-ms-asf ASF video asf Yes   video/x-ms-wmv Windows Media video wmv Yes   video/x-wmv Windows Media video wmv Yes   video/x-ms-wvx Windows Media video wmv Yes   video/x-ms-wm Windows Media video wmv Yes   video/x-ms-wmp Windows Media video wmv Yes   application/x-ms-wms Windows Media video wms Yes   application/x-ms-wmp Windows Media video wmp Yes   application/asx Microsoft ASX playlist asx Yes   audio/x-ms-wma Windows Media audio wma Yes  **DivX® Web Player**

 File:  libtotem-mully-plugin.soVersion:   DivX Web Player version 1.4.0.233   MIME Type Description Suffixes Enabled    video/divx AVI video divx Yes  **QuickTime Plug-in 7.6.6**

 File:  libtotem-narrowspace-plugin.soVersion:   The [Totem]("http://www.gnome.org/projects/totem/") 2.32.0 plugin handles video and audio streams.   MIME Type Description Suffixes Enabled    video/quicktime QuickTime video mov Yes   video/mp4 MPEG-4 video mp4 Yes   image/x-macpaint MacPaint Bitmap image pntg Yes   image/x-quicktime Macintosh Quickdraw/PICT drawing pict, pict1, pict2 Yes   video/x-m4v MPEG-4 video m4v Yes  **Shockwave Flash**

 File:  libgnashplugin.soVersion:   Shockwave Flash 10.1 r999.
Gnash 0.8.8, the GNU SWF Player.   Copyright (C) 2006, 2007, 2008, 2009, 2010   [Free   Software Foundation]("http://www.fsf.org/"), Inc. 
   Gnash comes with NO WARRANTY, to the extent permitted by law.   You  may redistribute copies of Gnash under the terms of the   [GNU General Public   License]("http://www.gnu.org/licenses/gpl.html"). For more information about Gnash, see [   http://www.gnu.org/software/gnash]("http://www.gnu.org/software/gnash/").   
  Compatible Shockwave Flash 10.1 r999.   MIME Type Description Suffixes Enabled    application/x-shockwave-flash Shockwave Flash swf Yes  **iTunes Application Detector**

 File:  librhythmbox-itms-detection-plugin.soVersion:   This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.   MIME Type Description Suffixes Enabled    application/itunes-plugin 

Yes

---

### Post by Perfect Storm on 2011-01-16
> File: libtotem-narrowspace-plugin.soVersion: The Totem 2.32.0 plugin handles video and audio streams. MIME Type Description Suffixes Enabled video/quicktime QuickTime video mov Yes video/mp4 MPEG-4 video mp4 Yes image/x-macpaint MacPaint Bitmap image pntg Yes image/x-quicktime Macintosh Quickdraw/PICT drawing pict, pict1, pict2 Yes video/x-m4v MPEG-4 video m4v Yes Shockwave Flash

File: libgnashplugin.soVersion: Shockwave Flash 10.1 r999.
Gnash 0.8.8, the GNU SWF Player. Copyright (C) 2006, 2007, 2008, 2009, 2010 Free Software Foundation, Inc. 
Gnash comes with NO WARRANTY, to the extent permitted by law. You may redistribute copies of Gnash under the terms of the GNU General Public License. For more information about Gnash, see [http://www.gnu.org/software/gnash](http://www.gnu.org/software/gnash). 
Compatible Shockwave Flash 10.1 r999. MIME Type Description Suffixes Enabled application/x-shockwave-flash Shockwave Flash swf Yes iTunes Application Detector

Gnash is installed, not flash.

```
sudo apt-get remove gnash && sudo apt-get install flashplugin-installer
```

Or open Ubuntu Software Center to uninstall gnash and install flash.

---

### Post by Ziadance on 2011-01-16
Hi
Thanks for the speedy replies, I think it's worked but unfortunately my Internet has slowed right down.

I'll post as soon as I'm sure.

---

