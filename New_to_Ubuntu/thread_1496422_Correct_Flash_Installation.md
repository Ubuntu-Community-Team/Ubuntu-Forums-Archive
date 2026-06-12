---
title: "Correct Flash Installation"
date: 2010-05-29
forum: New to Ubuntu
---

### Post by cozski on 2010-05-29
I have upgraded from 9.04 to Lucid and my Flash Player does not function correctly when using Firefox. I'm using a 32bit OS on a 32bit system. Which version should I install at this page? [http://get.adobe.com/flashplayer/?promoid=BUIGP](http://get.adobe.com/flashplayer/?promoid=BUIGP)

[IMG]http://ubuntuforums.org/%3Ca%20href=http://www.imagebam.com/image/39a0b582436198%20target=_blank%3E[IMG]http://thumbnails26.imagebam.com/8244/39a0b582436198.gif[/IMG][/IMG]

Thanks.

---

### Post by nhasian on 2010-05-29
actually this is the latest version here:

[http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_rc6_linux_052510.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_rc6_linux_052510.tar.gz)

---

### Post by cozski on 2010-05-29
> **nhasian said:**
> actually this is the latest version here:

[http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_rc6_linux_052510.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_rc6_linux_052510.tar.gz)


Thanks... when I try to unpack the tar I get this back:
> 
cozski@cozski-laptop:~$ tar xfvz flashplayer10_1_rc6_linux_052510.tar.gz
tar: flashplayer10_1_rc6_linux_052510.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors

Any ideas?

---

### Post by sandyd on 2010-05-29
```

sudo apt-get remove flashplugin-nonfree flashplugin-installer
wget -c http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_rc6_linux_052510.tar.gz
tar xvfz flashplayer10_1_rc6_linux_052510.tar.gz
sudo mv libflashplayer.so /usr/lib/mozilla/plugins

```

---

### Post by cozski on 2010-05-30
Thanks Carlee... but unfortunately still no Flash working :(

---

### Post by edanto on 2010-05-30
For me, Carlee's instructions worked.  I've had stuttering flash play for months, until now.

THANKS!!

---

### Post by PinchedNerve on 2010-05-30
> **cozski said:**
> I have upgraded from 9.04 to Lucid and my Flash Player does not function correctly when using Firefox. I'm using a 32bit OS on a 32bit system. Which version should I install at this page? [http://get.adobe.com/flashplayer/?promoid=BUIGP](http://get.adobe.com/flashplayer/?promoid=BUIGP)

[IMG]http://ubuntuforums.org/%3Ca%20href=http://www.imagebam.com/image/39a0b582436198%20target=_blank%3E[IMG]http://thumbnails26.imagebam.com/8244/39a0b582436198.gif[/IMG][/IMG]

Thanks.

Could you please describe the issue in detail?

---

### Post by nhasian on 2010-05-30
are you in the same directory as the file you downloaded when you try to untar it?  you should be able to see it in the file list if you type:

```
ls
```

to see what directory your currently in type:

```
pwd
```

you could also just right click on it in nautilus an extract it there.

> **cozski said:**
> Thanks... when I try to unpack the tar I get this back:


Any ideas?

---

### Post by sandyd on 2010-05-30
oh wait. i 4got something... can you go into "about: plugins" in firefox (no space in between) and c&p lnto here?

---

### Post by sandyd on 2010-05-30
oh wait. i 4got something... can you go into "about: plugins" in firefox (no space in between) and c&p lnto here?

---

### Post by cozski on 2010-05-31
> **PinchedNerve said:**
> Could you please describe the issue in detail?

In detail... well I cant play any content when using my firefox browser... that's about it. I just keep getting a prompt saying I need to update to the latest version of Flash Player.

---

### Post by cozski on 2010-05-31
I'm not sure what you mean when you ask am I in the directory. The tar is in a folder named Downloads... when I type ls in terminal I get a list of files & folders but I don't see that specific one. RE: nautilus - I have no idea what that is. Sorry... kind of new to this :/

---

### Post by cozski on 2010-05-31
> **carlee said:**
> oh wait. i 4got something... can you go into "about: plugins" in firefox (no space in between) and c&p lnto here?

 **Installed plugins**

 Find more information about browser plugins at  [mozilla.org]("https://pfs.mozilla.org/plugins/"). 
 Help for installing plugins is available from  [plugindoc.mozdev.org]("http://plugindoc.mozdev.org/"). 
 **Default Plugin**

 File:  libnullplugin.soVersion:  1.0.0.15 The default plugin handles plugin data for mimetypes and extensions that  are not specified and facilitates downloading of new plugins.   MIME Type Description Suffixes Enabled    * All types .* No  **IcedTea NPR Web Browser Plugin  (using IcedTea6 1.8 (6b18-1.8-0ubuntu1))**

 File:  IcedTeaPlugin.soVersion:   The IcedTea NPR Web Browser Plugin (using IcedTea6 1.8  (6b18-1.8-0ubuntu1)) executes Java applets.   MIME Type Description Suffixes Enabled    application/x-java-vm IcedTea class,jar Yes   application/x-java-applet IcedTea class,jar Yes   application/x-java-applet;version=1.1 IcedTea class,jar Yes   application/x-java-applet;version=1.1.1 IcedTea class,jar Yes   application/x-java-applet;version=1.1.2 IcedTea class,jar Yes   application/x-java-applet;version=1.1.3 IcedTea class,jar Yes   application/x-java-applet;version=1.2 IcedTea class,jar Yes   application/x-java-applet;version=1.2.1 IcedTea class,jar Yes   application/x-java-applet;version=1.2.2 IcedTea class,jar Yes   application/x-java-applet;version=1.3 IcedTea class,jar Yes   application/x-java-applet;version=1.3.1 IcedTea class,jar Yes   application/x-java-applet;version=1.4 IcedTea class,jar Yes   application/x-java-applet;version=1.4.1 IcedTea class,jar Yes   application/x-java-applet;version=1.4.2 IcedTea class,jar Yes   application/x-java-applet;version=1.5 IcedTea class,jar Yes   application/x-java-applet;version=1.6 IcedTea class,jar Yes   application/x-java-applet;jpi-version=1.6.0_18 IcedTea class,jar Yes   application/x-java-bean IcedTea class,jar Yes   application/x-java-bean;version=1.1 IcedTea class,jar Yes   application/x-java-bean;version=1.1.1 IcedTea class,jar Yes   application/x-java-bean;version=1.1.2 IcedTea class,jar Yes   application/x-java-bean;version=1.1.3 IcedTea class,jar Yes   application/x-java-bean;version=1.2 IcedTea class,jar Yes   application/x-java-bean;version=1.2.1 IcedTea class,jar Yes   application/x-java-bean;version=1.2.2 IcedTea class,jar Yes   application/x-java-bean;version=1.3 IcedTea class,jar Yes   application/x-java-bean;version=1.3.1 IcedTea class,jar Yes   application/x-java-bean;version=1.4 IcedTea class,jar Yes   application/x-java-bean;version=1.4.1 IcedTea class,jar Yes   application/x-java-bean;version=1.4.2 IcedTea class,jar Yes   application/x-java-bean;version=1.5 IcedTea class,jar Yes   application/x-java-bean;version=1.6 IcedTea class,jar Yes   application/x-java-bean;jpi-version=1.6.0_18 IcedTea class,jar Yes  **iTunes Application Detector**

 File:  librhythmbox-itms-detection-plugin.soVersion:    This plug-in detects the presence of iTunes when opening iTunes Store  URLs in a web page with Firefox.   MIME Type Description Suffixes Enabled    application/itunes-plugin 

Yes  **VLC Multimedia Plugin (compatible  Totem 2.30.2)**

 File:  libtotem-cone-plugin.soVersion:   The [Totem]("http://www.gnome.org/projects/totem/") 2.30.2  plugin handles video and audio streams.   MIME Type Description Suffixes Enabled    application/x-vlc-plugin VLC Multimedia Plugin 
Yes   application/vlc VLC Multimedia Plugin 
Yes   video/x-google-vlc-plugin VLC Multimedia Plugin 
Yes   application/x-ogg Ogg multimedia file ogg Yes   application/ogg Ogg multimedia file ogg Yes   audio/ogg Ogg Audio oga Yes   audio/x-ogg Ogg Audio ogg Yes   video/ogg Ogg Video ogv Yes   video/x-ogg Ogg Video ogg Yes   application/annodex Annodex exchange format anx Yes   audio/annodex Annodex Audio axa Yes   video/annodex Annodex Video axv Yes   video/mpeg MPEG video mpg, mpeg, mpe Yes   audio/wav WAV audio wav Yes   audio/x-wav WAV audio wav Yes   audio/mpeg MP3 audio mp3 Yes   application/x-nsv-vp3-mp3 NullSoft video nsv Yes   video/flv Flash video flv Yes   application/x-totem-plugin Totem Multimedia plugin 
Yes  **Windows Media Player Plug-in 10  (compatible; Totem)**

 File:  libtotem-gmp-plugin.soVersion:   The [Totem]("http://www.gnome.org/projects/totem/") 2.30.2  plugin handles video and audio streams.   MIME Type Description Suffixes Enabled    application/x-mplayer2 AVI video avi, wma, wmv Yes   video/x-ms-asf-plugin ASF video asf, wmv Yes   video/x-msvideo AVI video asf, wmv Yes   video/x-ms-asf ASF video asf Yes   video/x-ms-wmv Windows Media video wmv Yes   video/x-wmv Windows Media video wmv Yes   video/x-ms-wvx Windows Media video wmv Yes   video/x-ms-wm Windows Media video wmv Yes   video/x-ms-wmp Windows Media video wmv Yes   application/x-ms-wms Windows Media video wms Yes   application/x-ms-wmp Windows Media video wmp Yes   application/asx Microsoft ASX playlist asx Yes   audio/x-ms-wma Windows Media audio wma Yes  **DivX® Web Player**

 File:  libtotem-mully-plugin.soVersion:   DivX Web Player version 1.4.0.233   MIME Type Description Suffixes Enabled    video/divx AVI video divx Yes  **QuickTime Plug-in 7.6.6**

 File:  libtotem-narrowspace-plugin.soVersion:    The [Totem]("http://www.gnome.org/projects/totem/") 2.30.2  plugin handles video and audio streams.   MIME Type Description Suffixes Enabled    video/quicktime QuickTime video mov Yes   video/mp4 MPEG-4 video mp4 Yes   image/x-macpaint MacPaint Bitmap image pntg Yes   image/x-quicktime Macintosh Quickdraw/PICT drawing pict, pict1, pict2 Yes   video/x-m4v MPEG-4 video m4v Yes

---

### Post by cozski on 2010-06-02
Still no flash... any help appreciated :)

---

### Post by lovinglinux on 2010-06-02
> **cozski said:**
> Still no flash... any help appreciated :)

Please post the output of these commands:

```
locate libflashplayer.so
```

```
locate firefox
```

Are you using the default Firefox version or another version installed manually?

---

### Post by nhasian on 2010-06-02
you still haven't put the file libflashplayer.so in the correct directory /usr/lib/mozilla/plugins like carlee suggested back in post #4

> **carlee said:**
> ```

sudo apt-get remove flashplugin-nonfree flashplugin-installer
wget -c http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_rc6_linux_052510.tar.gz
tar xvfz flashplayer10_1_rc6_linux_052510.tar.gz
sudo mv libflashplayer.so /usr/lib/mozilla/plugins

```

---

### Post by cozski on 2010-06-04
> **lovinglinux said:**
> Please post the output of these commands:

```
locate libflashplayer.so
``````
locate firefox
```Are you using the default Firefox version or another version installed manually?

cozski@cozski-laptop:~$ sudo mv libflashplayer.so /usr/lib/mozilla/plugins
mv: cannot stat `libflashplayer.so': No such file or directory

Is what I get. Is this command trying to move the file to that particular location?

---

### Post by cozski on 2010-06-04
> **nhasian said:**
> you still haven't put the file libflashplayer.so in the correct directory /usr/lib/mozilla/plugins like carlee suggested back in post #4


Is what I get when I run the final command


> cozski@cozski-laptop:~$ sudo mv libflashplayer.so /usr/lib/mozilla/plugins
mv: cannot stat `libflashplayer.so': No such file or directory

---

### Post by cozski on 2010-06-04
> **lovinglinux said:**
> Please post the output of these commands:

```
locate libflashplayer.so
``````
locate firefox
```Are you using the default Firefox version or another version installed manually?

locate firefox gives this...

> cozski@cozski-laptop:~$ locate firefox
/etc/firefox
/etc/firefox-3.0
/etc/firefox-3.5
/etc/alternatives/firefox-homepage
/etc/alternatives/firefox-homepage-locales
/etc/apparmor.d/usr.bin.firefox
/etc/apparmor.d/usr.bin.firefox-3.5
/etc/apparmor.d/disable/usr.bin.firefox
/etc/apparmor.d/disable/usr.bin.firefox-3.5
/etc/firefox/pref
/etc/firefox/profile
/etc/firefox/pref/firefox.js
/etc/firefox/profile/bookmarks.html
/etc/firefox/profile/chrome
/etc/firefox/profile/localstore.rdf
/etc/firefox/profile/mimeTypes.rdf
/etc/firefox/profile/prefs.js
/etc/firefox/profile/chrome/userChrome-example.css
/etc/firefox/profile/chrome/userContent-example.css
/etc/firefox-3.0/pref
/etc/firefox-3.0/pref/apturl.js
/etc/firefox-3.5/pref
/etc/firefox-3.5/profile
/etc/firefox-3.5/pref/firefox.js
/etc/firefox-3.5/profile/bookmarks.html
/etc/firefox-3.5/profile/chrome
/etc/firefox-3.5/profile/localstore.rdf
/etc/firefox-3.5/profile/mimeTypes.rdf
/etc/firefox-3.5/profile/prefs.js
/etc/firefox-3.5/profile/chrome/userChrome-example.css
/etc/firefox-3.5/profile/chrome/userContent-example.css
/home/cozski/.config/ubuntu-tweak/appcenter/appcenter/logo/firefox-icon.png
/home/cozski/.config/ubuntu-tweak/appcenter/appcenter/logo/firefox-logo.png
/home/cozski/.icons/firefox-document.png
/home/cozski/.local/share/Trash/info/firefox.desktop.trashinfo
/home/cozski/.local/share/applications/firefox.desktop
/home/cozski/.mozilla/firefox
/home/cozski/.mozilla/firefox/Crash Reports
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski
/home/cozski/.mozilla/firefox/profiles.ini
/home/cozski/.mozilla/firefox/Crash Reports/InstallTime20100401074458
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/.parentlock
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/Cache
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/OfflineCache
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/XPC.mfasl
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/XUL.mfasl
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/adblockplus
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/blocklist.xml
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/bookmarkbackups
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/bookmarks.html
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/cert8.db
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/cert_override.txt
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/chrome
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/compatibility.ini
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/compreg.dat
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/content-prefs.sqlite
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/cookies.sqlite
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/cookies.sqlite-journal
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/dh-conv-rules.rdf
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/dh-media-lists.rdf
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/dh-smart-names.rdf
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/downloads.sqlite
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions.cache
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions.ini
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions.rdf
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/formhistory.sqlite
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/key3.db
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/lightweighttheme-footer
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/lightweighttheme-header
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/localstore.rdf
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/mimeTypes.rdf
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/minidumps
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/permissions.sqlite
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/places.sqlite
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/places.sqlite-journal
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/pluginreg.dat
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/prefs.js
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/search.json
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/search.sqlite
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/secmod.db
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/signons.sqlite
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/urlclassifier3.sqlite
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/urlclassifierkey3.txt
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/webappsstore.sqlite
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/xpti.dat
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/Cache/_CACHE_001_
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/Cache/_CACHE_002_
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/Cache/_CACHE_003_
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/Cache/_CACHE_MAP_
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/OfflineCache/index.sqlite
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/adblockplus/patterns-backup1.ini
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/adblockplus/patterns-backup2.ini
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/adblockplus/patterns-backup3.ini
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/adblockplus/patterns-backup4.ini
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/adblockplus/patterns-backup5.ini
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/adblockplus/patterns.ini
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/bookmarkbackups/bookmarks-2010-05-27.json
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/bookmarkbackups/bookmarks-2010-05-28.json
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/bookmarkbackups/bookmarks-2010-05-29.json
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/bookmarkbackups/bookmarks-2010-05-31.json
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/bookmarkbackups/bookmarks-2010-06-02.json
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/chrome/userChrome-example.css
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/chrome/userContent-example.css
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/chrome
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/chrome.manifest
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/components
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/defaults
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/install.rdf
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/local
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/chrome/dwhelper.jar
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/components/dhAddToBlackListProcessor.js
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/components/dhConvConfHandler.js
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/components/dhConvertMgr.js
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/components/dhCopyUrlProcessor.js
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/components/dhCore.js
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/components/dhDOMHook.js
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/components/dhDownloadConvertProcessor.js
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/components/dhDownloadMgr.js
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/components/dhDownloadProcessor.js
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/components/dhDumpProcessor.js
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/components/dhFlashgotDownloadProcessor.js
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/components/dhIContextItem.xpt
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/components/dhIConversionListener.xpt
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/components/dhIConvertMgr.xpt
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/components/dhICore.xpt
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/components/dhIDOMHook.xpt
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/components/dhIDownloadListener.xpt
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/components/dhIDownloadMgr.xpt
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/components/dhIMP3Tunes.xpt
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/components/dhIMediaListMgr.xpt
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/components/dhIProbe.xpt
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/components/dhIProbeMouseListener.xpt
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/components/dhIProcessor.xpt
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/components/dhISmartNamer.xpt
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/components/dhITwitter.xpt
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/components/dhIUtilService.xpt
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/components/dhIYTHQChecker.xpt
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/components/dhIYTHQCheckerListener.xpt
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/components/dhIYoutubeTool.xpt
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/components/dhLicenseHandler.js
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/components/dhMP3Tunes.js
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/components/dhMP3TunesLockerProcessor.js
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/components/dhMP3TunesMobileProcessor.js
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/components/dhMediaListMgr.js
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/components/dhMedialinkProbe.js
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/components/dhNetworkProbe.js
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/components/dhQuickDownloadProcessor.js
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/components/dhSafeModeHandler.js
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/components/dhSecretHelperProcessor.js
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/components/dhSmartNamer.js
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/components/dhTestProbe.js
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/components/dhTwitterProcessor.js
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/components/dhUtilService.js
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/components/dhYTHQChecker.js
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/components/dhYoutubeLinksContextItem.js
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/components/dhYoutubeProbe.js
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/defaults/preferences
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/defaults/preferences/prefs-dwhelper.js
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/extensions/{b9db16a4-6edc-47ec-a1f4-b86292ed211d}/local/wm.png
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/minidumps/1696bc2a-407a-e0af-5a791151-1e6d78be.dmp
/home/cozski/.mozilla/firefox/ba2yy8gq.Cozski/minidumps/500b3b5a-a817-9560-0e7b3f94-0c062f71.dmp
/opt/firefox
/opt/firefox/.autoreg
/opt/firefox/LICENSE
/opt/firefox/README.txt
/opt/firefox/Throbber-small.gif
/opt/firefox/application.ini
/opt/firefox/blocklist.xml
/opt/firefox/browserconfig.properties
/opt/firefox/chrome
/opt/firefox/components
/opt/firefox/crashreporter
/opt/firefox/crashreporter-override.ini
/opt/firefox/crashreporter.ini
/opt/firefox/defaults
/opt/firefox/dictionaries
/opt/firefox/extensions
/opt/firefox/firefox
/opt/firefox/firefox-bin
/opt/firefox/greprefs
/opt/firefox/icons
/opt/firefox/libfreebl3.chk
/opt/firefox/libfreebl3.so
/opt/firefox/libmozjs.so
/opt/firefox/libnspr4.so
/opt/firefox/libnss3.so
/opt/firefox/libnssckbi.so
/opt/firefox/libnssdbm3.chk
/opt/firefox/libnssdbm3.so
/opt/firefox/libnssutil3.so
/opt/firefox/libplc4.so
/opt/firefox/libplds4.so
/opt/firefox/libsmime3.so
/opt/firefox/libsoftokn3.chk
/opt/firefox/libsoftokn3.so
/opt/firefox/libsqlite3.so
/opt/firefox/libssl3.so
/opt/firefox/libxpcom.so
/opt/firefox/libxul.so
/opt/firefox/modules
/opt/firefox/mozilla-xremote-client
/opt/firefox/platform.ini
/opt/firefox/plugins
/opt/firefox/removed-files
/opt/firefox/res
/opt/firefox/run-mozilla.sh
/opt/firefox/searchplugins
/opt/firefox/update.locale
/opt/firefox/updater
/opt/firefox/updater.ini
/opt/firefox/chrome/browser.jar
/opt/firefox/chrome/browser.manifest
/opt/firefox/chrome/classic.jar
/opt/firefox/chrome/classic.manifest
/opt/firefox/chrome/comm.jar
/opt/firefox/chrome/comm.manifest
/opt/firefox/chrome/en-US.jar
/opt/firefox/chrome/en-US.manifest
/opt/firefox/chrome/icons
/opt/firefox/chrome/pippki.jar
/opt/firefox/chrome/pippki.manifest
/opt/firefox/chrome/reporter.jar
/opt/firefox/chrome/reporter.manifest
/opt/firefox/chrome/toolkit.jar
/opt/firefox/chrome/toolkit.manifest
/opt/firefox/chrome/icons/default
/opt/firefox/chrome/icons/default/default16.png
/opt/firefox/chrome/icons/default/default32.png
/opt/firefox/chrome/icons/default/default48.png
/opt/firefox/components/FeedConverter.js
/opt/firefox/components/FeedProcessor.js
/opt/firefox/components/FeedWriter.js
/opt/firefox/components/GPSDGeolocationProvider.js
/opt/firefox/components/NetworkGeolocationProvider.js
/opt/firefox/components/WebContentConverter.js
/opt/firefox/components/browser.xpt
/opt/firefox/components/components.list
/opt/firefox/components/fuelApplication.js
/opt/firefox/components/jsconsole-clhandler.js
/opt/firefox/components/libbrowsercomps.so
/opt/firefox/components/libbrowserdirprovider.so
/opt/firefox/components/libdbusservice.so
/opt/firefox/components/libimgicon.so
/opt/firefox/components/libmozgnome.so
/opt/firefox/components/libnkgnomevfs.so
/opt/firefox/components/nsAddonRepository.js
/opt/firefox/components/nsBadCertHandler.js
/opt/firefox/components/nsBlocklistService.js
/opt/firefox/components/nsBrowserContentHandler.js
/opt/firefox/components/nsBrowserGlue.js
/opt/firefox/components/nsContentDispatchChooser.js
/opt/firefox/components/nsContentPrefService.js
/opt/firefox/components/nsDefaultCLH.js
/opt/firefox/components/nsDownloadManagerUI.js
/opt/firefox/components/nsExtensionManager.js
/opt/firefox/components/nsFilePicker.js
/opt/firefox/components/nsFormAutoComplete.js
/opt/firefox/components/nsHandlerService.js
/opt/firefox/components/nsHelperAppDlg.js
/opt/firefox/components/nsLivemarkService.js
/opt/firefox/components/nsLoginInfo.js
/opt/firefox/components/nsLoginManager.js
/opt/firefox/components/nsLoginManagerPrompter.js
/opt/firefox/components/nsMicrosummaryService.js
/opt/firefox/components/nsPlacesAutoComplete.js
/opt/firefox/components/nsPlacesDBFlush.js
/opt/firefox/components/nsPlacesTransactionsService.js
/opt/firefox/components/nsPrivateBrowsingService.js
/opt/firefox/components/nsProxyAutoConfig.js
/opt/firefox/components/nsSafebrowsingApplication.js
/opt/firefox/components/nsSearchService.js
/opt/firefox/components/nsSearchSuggestions.js
/opt/firefox/components/nsSessionStartup.js
/opt/firefox/components/nsSessionStore.js
/opt/firefox/components/nsSetDefaultBrowser.js
/opt/firefox/components/nsSidebar.js
/opt/firefox/components/nsTaggingService.js
/opt/firefox/components/nsTryToClose.js
/opt/firefox/components/nsURLFormatter.js
/opt/firefox/components/nsUpdateService.js
/opt/firefox/components/nsUpdateServiceStub.js
/opt/firefox/components/nsUpdateTimerManager.js
/opt/firefox/components/nsUrlClassifierLib.js
/opt/firefox/components/nsUrlClassifierListManager.js
/opt/firefox/components/nsWebHandlerApp.js
/opt/firefox/components/pluginGlue.js
/opt/firefox/components/storage-Legacy.js
/opt/firefox/components/storage-mozStorage.js
/opt/firefox/components/txEXSLTRegExFunctions.js
/opt/firefox/defaults/autoconfig
/opt/firefox/defaults/pref
/opt/firefox/defaults/profile
/opt/firefox/defaults/autoconfig/platform.js
/opt/firefox/defaults/autoconfig/prefcalls.js
/opt/firefox/defaults/pref/channel-prefs.js
/opt/firefox/defaults/pref/firefox-branding.js
/opt/firefox/defaults/pref/firefox-l10n.js
/opt/firefox/defaults/pref/firefox.js
/opt/firefox/defaults/pref/reporter.js
/opt/firefox/defaults/profile/bookmarks.html
/opt/firefox/defaults/profile/chrome
/opt/firefox/defaults/profile/localstore.rdf
/opt/firefox/defaults/profile/mimeTypes.rdf
/opt/firefox/defaults/profile/prefs.js
/opt/firefox/defaults/profile/chrome/userChrome-example.css
/opt/firefox/defaults/profile/chrome/userContent-example.css
/opt/firefox/dictionaries/en-US.aff
/opt/firefox/dictionaries/en-US.dic
/opt/firefox/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}
/opt/firefox/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}/icon.png
/opt/firefox/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}/install.rdf
/opt/firefox/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}/preview.png
/opt/firefox/greprefs/all.js
/opt/firefox/greprefs/security-prefs.js
/opt/firefox/greprefs/xpinstall.js
/opt/firefox/icons/document.png
/opt/firefox/icons/mozicon128.png
/opt/firefox/icons/updater.png
/opt/firefox/modules/CertUtils.jsm
/opt/firefox/modules/DownloadLastDir.jsm
/opt/firefox/modules/DownloadUtils.jsm
/opt/firefox/modules/FileUtils.jsm
/opt/firefox/modules/ISO8601DateUtils.jsm
/opt/firefox/modules/LightweightThemeConsumer.jsm
/opt/firefox/modules/LightweightThemeManager.jsm
/opt/firefox/modules/Microformats.js
/opt/firefox/modules/NetUtil.jsm
/opt/firefox/modules/NetworkPrioritizer.jsm
/opt/firefox/modules/PlacesDBUtils.jsm
/opt/firefox/modules/PluralForm.jsm
/opt/firefox/modules/SpatialNavigation.js
/opt/firefox/modules/WindowDraggingUtils.jsm
/opt/firefox/modules/XPCOMUtils.jsm
/opt/firefox/modules/ctypes.jsm
/opt/firefox/modules/debug.js
/opt/firefox/modules/distribution.js
/opt/firefox/modules/openLocationLastURL.jsm
/opt/firefox/modules/utils.js
/opt/firefox/plugins/libnullplugin.so
/opt/firefox/res/EditorOverride.css
/opt/firefox/res/arrow.gif
/opt/firefox/res/arrowd.gif
/opt/firefox/res/broken-image.png
/opt/firefox/res/charsetData.properties
/opt/firefox/res/charsetalias.properties
/opt/firefox/res/contenteditable.css
/opt/firefox/res/designmode.css
/opt/firefox/res/dtd
/opt/firefox/res/entityTables
/opt/firefox/res/fonts
/opt/firefox/res/forms.css
/opt/firefox/res/grabber.gif
/opt/firefox/res/hiddenWindow.html
/opt/firefox/res/html
/opt/firefox/res/html.css
/opt/firefox/res/langGroups.properties
/opt/firefox/res/language.properties
/opt/firefox/res/loading-image.png
/opt/firefox/res/mathml.css
/opt/firefox/res/quirk.css
/opt/firefox/res/svg.css
/opt/firefox/res/table-add-column-after-active.gif
/opt/firefox/res/table-add-column-after-hover.gif
/opt/firefox/res/table-add-column-after.gif
/opt/firefox/res/table-add-column-before-active.gif
/opt/firefox/res/table-add-column-before-hover.gif
/opt/firefox/res/table-add-column-before.gif
/opt/firefox/res/table-add-row-after-active.gif
/opt/firefox/res/table-add-row-after-hover.gif
/opt/firefox/res/table-add-row-after.gif
/opt/firefox/res/table-add-row-before-active.gif
/opt/firefox/res/table-add-row-before-hover.gif
/opt/firefox/res/table-add-row-before.gif
/opt/firefox/res/table-remove-column-active.gif
/opt/firefox/res/table-remove-column-hover.gif
/opt/firefox/res/table-remove-column.gif
/opt/firefox/res/table-remove-row-active.gif
/opt/firefox/res/table-remove-row-hover.gif
/opt/firefox/res/table-remove-row.gif
/opt/firefox/res/ua.css
/opt/firefox/res/unixcharset.properties
/opt/firefox/res/viewsource.css
/opt/firefox/res/dtd/mathml.dtd
/opt/firefox/res/dtd/xhtml11.dtd
/opt/firefox/res/entityTables/html40Latin1.properties
/opt/firefox/res/entityTables/html40Special.properties
/opt/firefox/res/entityTables/html40Symbols.properties
/opt/firefox/res/entityTables/htmlEntityVersions.properties
/opt/firefox/res/entityTables/mathml20.properties
/opt/firefox/res/entityTables/transliterate.properties
/opt/firefox/res/fonts/mathfont.properties
/opt/firefox/res/fonts/mathfontSTIXNonUnicode.properties
/opt/firefox/res/fonts/mathfontSTIXSize1.properties
/opt/firefox/res/fonts/mathfontStandardSymbolsL.properties
/opt/firefox/res/fonts/mathfontUnicode.properties
/opt/firefox/res/html/folder.png
/opt/firefox/searchplugins/amazondotcom.xml
/opt/firefox/searchplugins/answers.xml
/opt/firefox/searchplugins/creativecommons.xml
/opt/firefox/searchplugins/eBay.xml
/opt/firefox/searchplugins/google.xml
/opt/firefox/searchplugins/wikipedia.xml
/opt/firefox/searchplugins/yahoo.xml
/usr/bin/firefox
/usr/bin/firefox.ubuntu
/usr/lib/firefox-3.6.3
/usr/lib/firefox-addons
/usr/lib/firefox-3.6.3/.autoreg
/usr/lib/firefox-3.6.3/abrowser
/usr/lib/firefox-3.6.3/application.ini
/usr/lib/firefox-3.6.3/blocklist.xml
/usr/lib/firefox-3.6.3/browserconfig.properties
/usr/lib/firefox-3.6.3/chrome
/usr/lib/firefox-3.6.3/components
/usr/lib/firefox-3.6.3/defaults
/usr/lib/firefox-3.6.3/dictionaries
/usr/lib/firefox-3.6.3/distribution
/usr/lib/firefox-3.6.3/extensions
/usr/lib/firefox-3.6.3/ffox-beta-profile-migration-dialog
/usr/lib/firefox-3.6.3/firefox
/usr/lib/firefox-3.6.3/firefox-
/usr/lib/firefox-3.6.3/firefox-bin
/usr/lib/firefox-3.6.3/firefox-restart-required.update-notifier
/usr/lib/firefox-3.6.3/firefox.sh
/usr/lib/firefox-3.6.3/greprefs
/usr/lib/firefox-3.6.3/icons
/usr/lib/firefox-3.6.3/libfreebl3.chk
/usr/lib/firefox-3.6.3/libfreebl3.so
/usr/lib/firefox-3.6.3/libmozjs.so
/usr/lib/firefox-3.6.3/libnspr4.so
/usr/lib/firefox-3.6.3/libnss3.so
/usr/lib/firefox-3.6.3/libnssckbi.so
/usr/lib/firefox-3.6.3/libnssdbm3.chk
/usr/lib/firefox-3.6.3/libnssdbm3.so
/usr/lib/firefox-3.6.3/libnssutil3.so
/usr/lib/firefox-3.6.3/libplc4.so
/usr/lib/firefox-3.6.3/libplds4.so
/usr/lib/firefox-3.6.3/libsmime3.so
/usr/lib/firefox-3.6.3/libsoftokn3.chk
/usr/lib/firefox-3.6.3/libsoftokn3.so
/usr/lib/firefox-3.6.3/libsqlite3.so
/usr/lib/firefox-3.6.3/libssl3.so
/usr/lib/firefox-3.6.3/libxpcom.so
/usr/lib/firefox-3.6.3/libxul.so
/usr/lib/firefox-3.6.3/modules
/usr/lib/firefox-3.6.3/platform.ini
/usr/lib/firefox-3.6.3/plugins
/usr/lib/firefox-3.6.3/res
/usr/lib/firefox-3.6.3/run-mozilla.sh
/usr/lib/firefox-3.6.3/searchplugins
/usr/lib/firefox-3.6.3/chrome/browser-branding-en-US.jar
/usr/lib/firefox-3.6.3/chrome/browser-branding-en-US.manifest
/usr/lib/firefox-3.6.3/chrome/browser-branding.jar
/usr/lib/firefox-3.6.3/chrome/browser-branding.manifest
/usr/lib/firefox-3.6.3/chrome/browser.jar
/usr/lib/firefox-3.6.3/chrome/browser.manifest
/usr/lib/firefox-3.6.3/chrome/classic.jar
/usr/lib/firefox-3.6.3/chrome/classic.manifest
/usr/lib/firefox-3.6.3/chrome/comm.jar
/usr/lib/firefox-3.6.3/chrome/comm.manifest
/usr/lib/firefox-3.6.3/chrome/en-US.jar
/usr/lib/firefox-3.6.3/chrome/en-US.manifest
/usr/lib/firefox-3.6.3/chrome/icons
/usr/lib/firefox-3.6.3/chrome/pippki.jar
/usr/lib/firefox-3.6.3/chrome/pippki.manifest
/usr/lib/firefox-3.6.3/chrome/toolkit.jar
/usr/lib/firefox-3.6.3/chrome/toolkit.manifest
/usr/lib/firefox-3.6.3/chrome/icons/default
/usr/lib/firefox-3.6.3/chrome/icons/default/default16.png
/usr/lib/firefox-3.6.3/chrome/icons/default/default32.png
/usr/lib/firefox-3.6.3/chrome/icons/default/default48.png
/usr/lib/firefox-3.6.3/components/FeedConverter.js
/usr/lib/firefox-3.6.3/components/FeedProcessor.js
/usr/lib/firefox-3.6.3/components/FeedWriter.js
/usr/lib/firefox-3.6.3/components/GPSDGeolocationProvider.js
/usr/lib/firefox-3.6.3/components/NetworkGeolocationProvider.js
/usr/lib/firefox-3.6.3/components/WebContentConverter.js
/usr/lib/firefox-3.6.3/components/browser.xpt
/usr/lib/firefox-3.6.3/components/fuelApplication.js
/usr/lib/firefox-3.6.3/components/jsconsole-clhandler.js
/usr/lib/firefox-3.6.3/components/libbrowsercomps.so
/usr/lib/firefox-3.6.3/components/libbrowserdirprovider.so
/usr/lib/firefox-3.6.3/components/libdbusservice.so
/usr/lib/firefox-3.6.3/components/libimgicon.so
/usr/lib/firefox-3.6.3/components/libmozgnome.so
/usr/lib/firefox-3.6.3/components/libnkgnomevfs.so
/usr/lib/firefox-3.6.3/components/nsAddonRepository.js
/usr/lib/firefox-3.6.3/components/nsBadCertHandler.js
/usr/lib/firefox-3.6.3/components/nsBlocklistService.js
/usr/lib/firefox-3.6.3/components/nsBrowserContentHandler.js
/usr/lib/firefox-3.6.3/components/nsBrowserGlue.js
/usr/lib/firefox-3.6.3/components/nsContentDispatchChooser.js
/usr/lib/firefox-3.6.3/components/nsContentPrefService.js
/usr/lib/firefox-3.6.3/components/nsDefaultCLH.js
/usr/lib/firefox-3.6.3/components/nsDownloadManagerUI.js
/usr/lib/firefox-3.6.3/components/nsExtensionManager.js
/usr/lib/firefox-3.6.3/components/nsFilePicker.js
/usr/lib/firefox-3.6.3/components/nsFormAutoComplete.js
/usr/lib/firefox-3.6.3/components/nsHandlerService.js
/usr/lib/firefox-3.6.3/components/nsHelperAppDlg.js
/usr/lib/firefox-3.6.3/components/nsLivemarkService.js
/usr/lib/firefox-3.6.3/components/nsLoginInfo.js
/usr/lib/firefox-3.6.3/components/nsLoginManager.js
/usr/lib/firefox-3.6.3/components/nsLoginManagerPrompter.js
/usr/lib/firefox-3.6.3/components/nsMicrosummaryService.js
/usr/lib/firefox-3.6.3/components/nsPlacesAutoComplete.js
/usr/lib/firefox-3.6.3/components/nsPlacesDBFlush.js
/usr/lib/firefox-3.6.3/components/nsPlacesTransactionsService.js
/usr/lib/firefox-3.6.3/components/nsPrivateBrowsingService.js
/usr/lib/firefox-3.6.3/components/nsProxyAutoConfig.js
/usr/lib/firefox-3.6.3/components/nsSafebrowsingApplication.js
/usr/lib/firefox-3.6.3/components/nsSearchService.js
/usr/lib/firefox-3.6.3/components/nsSearchSuggestions.js
/usr/lib/firefox-3.6.3/components/nsSessionStartup.js
/usr/lib/firefox-3.6.3/components/nsSessionStore.js
/usr/lib/firefox-3.6.3/components/nsSetDefaultBrowser.js
/usr/lib/firefox-3.6.3/components/nsSidebar.js
/usr/lib/firefox-3.6.3/components/nsTaggingService.js
/usr/lib/firefox-3.6.3/components/nsTryToClose.js
/usr/lib/firefox-3.6.3/components/nsURLFormatter.js
/usr/lib/firefox-3.6.3/components/nsUpdateTimerManager.js
/usr/lib/firefox-3.6.3/components/nsUrlClassifierLib.js
/usr/lib/firefox-3.6.3/components/nsUrlClassifierListManager.js
/usr/lib/firefox-3.6.3/components/nsWebHandlerApp.js
/usr/lib/firefox-3.6.3/components/pluginGlue.js
/usr/lib/firefox-3.6.3/components/storage-Legacy.js
/usr/lib/firefox-3.6.3/components/storage-mozStorage.js
/usr/lib/firefox-3.6.3/components/txEXSLTRegExFunctions.js
/usr/lib/firefox-3.6.3/defaults/autoconfig
/usr/lib/firefox-3.6.3/defaults/pref
/usr/lib/firefox-3.6.3/defaults/profile
/usr/lib/firefox-3.6.3/defaults/syspref
/usr/lib/firefox-3.6.3/defaults/autoconfig/platform.js
/usr/lib/firefox-3.6.3/defaults/autoconfig/prefcalls.js
/usr/lib/firefox-3.6.3/defaults/pref/channel-prefs.js
/usr/lib/firefox-3.6.3/defaults/pref/firefox-branding.js
/usr/lib/firefox-3.6.3/defaults/pref/firefox-l10n.js
/usr/lib/firefox-3.6.3/defaults/pref/firefox.js
/usr/lib/firefox-3.6.3/defaults/pref/kde.js
/usr/lib/firefox-3.6.3/defaults/pref/ubuntu-useragent.js
/usr/lib/firefox-3.6.3/distribution/distribution.ini
/usr/lib/firefox-3.6.3/distribution/searchplugins
/usr/lib/firefox-3.6.3/greprefs/all.js
/usr/lib/firefox-3.6.3/greprefs/security-prefs.js
/usr/lib/firefox-3.6.3/greprefs/xpinstall.js
/usr/lib/firefox-3.6.3/icons/document.png
/usr/lib/firefox-3.6.3/icons/mozicon128.png
/usr/lib/firefox-3.6.3/modules/CertUtils.jsm
/usr/lib/firefox-3.6.3/modules/DownloadLastDir.jsm
/usr/lib/firefox-3.6.3/modules/DownloadUtils.jsm
/usr/lib/firefox-3.6.3/modules/FileUtils.jsm
/usr/lib/firefox-3.6.3/modules/ISO8601DateUtils.jsm
/usr/lib/firefox-3.6.3/modules/LightweightThemeConsumer.jsm
/usr/lib/firefox-3.6.3/modules/LightweightThemeManager.jsm
/usr/lib/firefox-3.6.3/modules/Microformats.js
/usr/lib/firefox-3.6.3/modules/NetUtil.jsm
/usr/lib/firefox-3.6.3/modules/NetworkPrioritizer.jsm
/usr/lib/firefox-3.6.3/modules/PlacesDBUtils.jsm
/usr/lib/firefox-3.6.3/modules/PluralForm.jsm
/usr/lib/firefox-3.6.3/modules/SpatialNavigation.js
/usr/lib/firefox-3.6.3/modules/WindowDraggingUtils.jsm
/usr/lib/firefox-3.6.3/modules/XPCOMUtils.jsm
/usr/lib/firefox-3.6.3/modules/ctypes.jsm
/usr/lib/firefox-3.6.3/modules/debug.js
/usr/lib/firefox-3.6.3/modules/distribution.js
/usr/lib/firefox-3.6.3/modules/openLocationLastURL.jsm
/usr/lib/firefox-3.6.3/modules/utils.js
/usr/lib/firefox-3.6.3/res/EditorOverride.css
/usr/lib/firefox-3.6.3/res/arrow.gif
/usr/lib/firefox-3.6.3/res/arrowd.gif
/usr/lib/firefox-3.6.3/res/broken-image.png
/usr/lib/firefox-3.6.3/res/charsetData.properties
/usr/lib/firefox-3.6.3/res/charsetalias.properties
/usr/lib/firefox-3.6.3/res/contenteditable.css
/usr/lib/firefox-3.6.3/res/designmode.css
/usr/lib/firefox-3.6.3/res/dtd
/usr/lib/firefox-3.6.3/res/entityTables
/usr/lib/firefox-3.6.3/res/fonts
/usr/lib/firefox-3.6.3/res/forms.css
/usr/lib/firefox-3.6.3/res/grabber.gif
/usr/lib/firefox-3.6.3/res/hiddenWindow.html
/usr/lib/firefox-3.6.3/res/html
/usr/lib/firefox-3.6.3/res/html.css
/usr/lib/firefox-3.6.3/res/langGroups.properties
/usr/lib/firefox-3.6.3/res/language.properties
/usr/lib/firefox-3.6.3/res/loading-image.png
/usr/lib/firefox-3.6.3/res/mathml.css
/usr/lib/firefox-3.6.3/res/quirk.css
/usr/lib/firefox-3.6.3/res/svg.css
/usr/lib/firefox-3.6.3/res/table-add-column-after-active.gif
/usr/lib/firefox-3.6.3/res/table-add-column-after-hover.gif
/usr/lib/firefox-3.6.3/res/table-add-column-after.gif
/usr/lib/firefox-3.6.3/res/table-add-column-before-active.gif
/usr/lib/firefox-3.6.3/res/table-add-column-before-hover.gif
/usr/lib/firefox-3.6.3/res/table-add-column-before.gif
/usr/lib/firefox-3.6.3/res/table-add-row-after-active.gif
/usr/lib/firefox-3.6.3/res/table-add-row-after-hover.gif
/usr/lib/firefox-3.6.3/res/table-add-row-after.gif
/usr/lib/firefox-3.6.3/res/table-add-row-before-active.gif
/usr/lib/firefox-3.6.3/res/table-add-row-before-hover.gif
/usr/lib/firefox-3.6.3/res/table-add-row-before.gif
/usr/lib/firefox-3.6.3/res/table-remove-column-active.gif
/usr/lib/firefox-3.6.3/res/table-remove-column-hover.gif
/usr/lib/firefox-3.6.3/res/table-remove-column.gif
/usr/lib/firefox-3.6.3/res/table-remove-row-active.gif
/usr/lib/firefox-3.6.3/res/table-remove-row-hover.gif
/usr/lib/firefox-3.6.3/res/table-remove-row.gif
/usr/lib/firefox-3.6.3/res/ua.css
/usr/lib/firefox-3.6.3/res/unixcharset.properties
/usr/lib/firefox-3.6.3/res/viewsource.css
/usr/lib/firefox-3.6.3/res/dtd/mathml.dtd
/usr/lib/firefox-3.6.3/res/dtd/xhtml11.dtd
/usr/lib/firefox-3.6.3/res/entityTables/html40Latin1.properties
/usr/lib/firefox-3.6.3/res/entityTables/html40Special.properties
/usr/lib/firefox-3.6.3/res/entityTables/html40Symbols.properties
/usr/lib/firefox-3.6.3/res/entityTables/htmlEntityVersions.properties
/usr/lib/firefox-3.6.3/res/entityTables/mathml20.properties
/usr/lib/firefox-3.6.3/res/entityTables/transliterate.properties
/usr/lib/firefox-3.6.3/res/fonts/mathfont.properties
/usr/lib/firefox-3.6.3/res/fonts/mathfontSTIXNonUnicode.properties
/usr/lib/firefox-3.6.3/res/fonts/mathfontSTIXSize1.properties
/usr/lib/firefox-3.6.3/res/fonts/mathfontStandardSymbolsL.properties
/usr/lib/firefox-3.6.3/res/fonts/mathfontUnicode.properties
/usr/lib/firefox-3.6.3/res/html/folder.png
/usr/lib/firefox-addons/extensions
/usr/lib/firefox-addons/plugins
/usr/lib/firefox-addons/searchplugins
/usr/lib/firefox-addons/extensions/langpack-en-AU@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-en-CA@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-en-GB@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-en@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}
/usr/lib/firefox-addons/extensions/langpack-en-GB@firefox-3.6.ubuntu.com/chrome
/usr/lib/firefox-addons/extensions/langpack-en-GB@firefox-3.6.ubuntu.com/chrome.manifest
/usr/lib/firefox-addons/extensions/langpack-en-GB@firefox-3.6.ubuntu.com/install.rdf
/usr/lib/firefox-addons/extensions/langpack-en-GB@firefox-3.6.ubuntu.com/chrome/en-GB.jar
/usr/lib/firefox-addons/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}/icon.png
/usr/lib/firefox-addons/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}/install.rdf
/usr/lib/firefox-addons/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}/preview.png
/usr/lib/firefox-addons/searchplugins/common
/usr/lib/firefox-addons/searchplugins/en-GB
/usr/lib/firefox-addons/searchplugins/en-US
/usr/lib/firefox-addons/searchplugins/en-GB/amazondotcom.xml
/usr/lib/firefox-addons/searchplugins/en-GB/answers.xml
/usr/lib/firefox-addons/searchplugins/en-GB/creativecommons.xml
/usr/lib/firefox-addons/searchplugins/en-GB/eBay.xml
/usr/lib/firefox-addons/searchplugins/en-GB/google.xml
/usr/lib/firefox-addons/searchplugins/en-GB/wikipedia.xml
/usr/lib/firefox-addons/searchplugins/en-GB/yahoo.xml
/usr/lib/firefox-addons/searchplugins/en-US/amazondotcom.xml
/usr/lib/firefox-addons/searchplugins/en-US/answers.xml
/usr/lib/firefox-addons/searchplugins/en-US/creativecommons.xml
/usr/lib/firefox-addons/searchplugins/en-US/eBay.xml
/usr/lib/firefox-addons/searchplugins/en-US/google.xml
/usr/lib/firefox-addons/searchplugins/en-US/wikipedia.xml
/usr/lib/firefox-addons/searchplugins/en-US/yahoo.xml
/usr/lib/python2.6/dist-packages/mechanize/_firefox3cookiejar.py
/usr/lib/python2.6/dist-packages/mechanize/_firefox3cookiejar.pyc
/usr/share/firefox
/usr/share/app-install/desktop/firefox-greasemonkey.desktop
/usr/share/app-install/desktop/firefox-launchpad-plugin.desktop
/usr/share/app-install/desktop/firefox-ubuntu-it-menu.desktop
/usr/share/app-install/desktop/firefox-webdeveloper.desktop
/usr/share/app-install/desktop/firefox.desktop
/usr/share/app-install/icons/firefox-greasemonkey.xpm
/usr/share/app-install/icons/firefox-installer.png
/usr/share/app-install/icons/firefox-launchpad-plugin.xpm
/usr/share/app-install/icons/firefox-themes-ubuntu.xpm
/usr/share/app-install/icons/firefox-ubuntu-it-menu.png
/usr/share/app-install/icons/firefox-webdeveloper.xpm
/usr/share/applications/firefox-mozilla-build.desktop
/usr/share/applications/firefox.desktop
/usr/share/apport/package-hooks/firefox.py
/usr/share/bug/firefox
/usr/share/bug/firefox/presubj
/usr/share/doc/firefox
/usr/share/doc/firefox-branding
/usr/share/doc/firefox-gnome-support
/usr/share/doc/firefox/MPL.gz
/usr/share/doc/firefox/README.Debian
/usr/share/doc/firefox/changelog.Debian.gz
/usr/share/doc/firefox/copyright
/usr/share/doc/firefox/firefox.cfg
/usr/share/doc/firefox-branding/changelog.Debian.gz
/usr/share/doc/firefox-branding/copyright
/usr/share/doc/firefox-gnome-support/changelog.Debian.gz
/usr/share/doc/firefox-gnome-support/copyright
/usr/share/firefox/defaults
/usr/share/firefox/defaults/pref
/usr/share/firefox/defaults/pref/apturl.js
/usr/share/menu/firefox
/usr/share/pixmaps/firefox-mozilla-build.png
/usr/share/pixmaps/firefox.png
/usr/share/pyshared/mechanize/_firefox3cookiejar.py
/usr/share/ubuntu-artwork/home/firefox-index.html
/usr/share/ubuntu-docs/common/prepare-firefox-startpage-translations
/usr/share/ubuntu-docs/libs/img/firefox-3.5.png
/var/lib/dpkg/alternatives/firefox-homepage
/var/lib/dpkg/info/firefox-3.5.list
/var/lib/dpkg/info/firefox-3.5.postrm
/var/lib/dpkg/info/firefox-branding.list
/var/lib/dpkg/info/firefox-branding.md5sums
/var/lib/dpkg/info/firefox-gnome-support.list
/var/lib/dpkg/info/firefox-gnome-support.md5sums
/var/lib/dpkg/info/firefox-gnome-support.postinst
/var/lib/dpkg/info/firefox-gnome-support.prerm
/var/lib/dpkg/info/firefox-mozilla-build.list
/var/lib/dpkg/info/firefox-mozilla-build.postrm
/var/lib/dpkg/info/firefox-mozilla-build.preinst
/var/lib/dpkg/info/firefox.conffiles
/var/lib/dpkg/info/firefox.list
/var/lib/dpkg/info/firefox.md5sums
/var/lib/dpkg/info/firefox.postinst
/var/lib/dpkg/info/firefox.postrm
/var/lib/dpkg/info/firefox.preinst
/var/lib/dpkg/info/firefox.prerm

and locate libflashplayer.so doesn't give anything. I used the default version installed with UNR, version 3.6.3

---

### Post by lovinglinux on 2010-06-04
Try these:

```
sudo ln -s /usr/lib/mozilla/plugins/flashplugin-alternative.so /usr/lib/firefox-addons/plugins/libflashplayer.so

sudo ln -s /usr/lib/mozilla/plugins/flashplugin-alternative.so /opt/firefox/plugins/libflashplayer.so
```

Restart Firefox.

---

### Post by cozski on 2010-06-04
> **lovinglinux said:**
> Try these:

```
sudo ln -s /usr/lib/mozilla/plugins/flashplugin-alternative.so /usr/lib/firefox-addons/plugins/libflashplayer.so

sudo ln -s /usr/lib/mozilla/plugins/flashplugin-alternative.so /opt/firefox/plugins/libflashplayer.so
```Restart Firefox.

Did that... no change. The 2nd command gets this

> cozski@cozski-laptop:~$ /mozilla/plugins/flashplugin-alternative.so /opt/firefox/plugins/libflashplayer.so
bash: /mozilla/plugins/flashplugin-alternative.so: No such file or directory

---

### Post by lovinglinux on 2010-06-04
> **cozski said:**
> Did that... no change. The 2nd command gets this

Please post the output of this:

```
ls /usr/lib/mozilla/plugins
ls /usr/lib/firefox-addons/plugins
```

---

### Post by cozski on 2010-06-04
> **lovinglinux said:**
> Please post the output of this:

```
ls /usr/lib/mozilla/plugins
ls /usr/lib/firefox-addons/plugins
```

> cozski@cozski-laptop:~$ ls /usr/lib/mozilla/plugins
libjavaplugin.so                       libtotem-cone-plugin.so  libtotem-mully-plugin.so
librhythmbox-itms-detection-plugin.so  libtotem-gmp-plugin.so   libtotem-narrowspace-plugin.so

and

> cozski@cozski-laptop:~$ ls /usr/lib/firefox-addons/plugins
libflashplayer.so


---

### Post by lovinglinux on 2010-06-04
Do this:

```
sudo apt-get purge swfdec-mozilla
sudo apt-get purge mozilla-plugin-gnash
sudo apt-get purge adobe-flashplugin
sudo apt-get purge flashplugin-nonfree
sudo apt-get purge flashplugin-installer
rm -f $HOME/.mozilla/plugins/*flash*so
rm -rf $HOME/.wine/dosdevices/c:/windows/system32/Macromed/Flash
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/libflashplayer.so
sudo apt-get install flashplugin-nonfree
sudo ln -s /usr/lib/mozilla/plugins/flashplugin-alternative.so /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo ln -s /usr/lib/mozilla/plugins /opt/firefox/
```

Restart Firefox. It should work.

---

### Post by cozski on 2010-06-04
> **lovinglinux said:**
> Do this:

```
sudo apt-get purge swfdec-mozilla
sudo apt-get purge mozilla-plugin-gnash
sudo apt-get purge adobe-flashplugin
sudo apt-get purge flashplugin-nonfree
sudo apt-get purge flashplugin-installer
rm -f $HOME/.mozilla/plugins/*flash*so
rm -rf $HOME/.wine/dosdevices/c:/windows/system32/Macromed/Flash
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/libflashplayer.so
sudo apt-get install flashplugin-nonfree
sudo ln -s /usr/lib/mozilla/plugins/flashplugin-alternative.so /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo ln -s /usr/lib/mozilla/plugins /opt/firefox/plugins
```Restart Firefox. It should work.


YAY!! We have life!

Thanks a million, I really appreciate you taking the time to help me resolve this problem. It does appear to have been a consistent issue when I first started using UNR and it was really beginning to frustrate me. Thanks again... you'll be rewarded in Heaven or some such similar place :P

---

### Post by lovinglinux on 2010-06-04
> **cozski said:**
> YAY!! We have life!

Thanks a million, I really appreciate you taking the time to help me resolve this problem. It does appear to have been a consistent issue when I first started using UNR and it was really beginning to frustrate me. Thanks again... you'll be rewarded in Heaven or some such similar place :P

You are welcome.

---

