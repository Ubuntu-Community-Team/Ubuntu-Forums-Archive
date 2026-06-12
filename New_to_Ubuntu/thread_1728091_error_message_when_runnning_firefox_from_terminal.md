---
title: "error message when runnning firefox from terminal"
date: 2011-04-13
forum: New to Ubuntu
---

### Post by RememberWhenItRained on 2011-04-13
When i start firefox from the terminal, i soon get this message:
```
collin@collin:~$ *** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
``` firefox seems to function fine, but what is unhandled variable 18?

---

### Post by ajgreeny on 2011-04-13
As far as I can make out, nsplugin is not needed in a gnome system, but is more for kde and konqueror browser, where it enables netscape plugins to work.  I don't use kde so can not go any further than that, but if you are using only gnome, try removing nsplugin and see if the symptoms still exist.

PS:  this plugin seems to be needed for flash to work in some other browsers than firefox;  what flash version have you got and does it work well, or are you having problems with it?  Also, what other browsers do you use?

---

### Post by RememberWhenItRained on 2011-04-13
> **ajgreeny said:**
> As far as I can make out, nsplugin is not needed in a gnome system, but is more for kde and konqueror browser, where it enables netscape plugins to work.  I don't use kde so can not go any further than that, but if you are using only gnome, try removing nsplugin and see if the symptoms still exist.

PS:  this plugin seems to be needed for flash to work in some other browsers than firefox;  what flash version have you got and does it work well, or are you having problems with it?  Also, what other browsers do you use?
just firefox. other than firefox freezing occasionally when using flash, no. i have the latest version.

---

### Post by ajgreeny on 2011-04-13
Even though firefox appears to be running OK, try uninstalling any nsplugin apps you may have with ```
sudo apt-get remove konqueror-nsplugins nspluginwrapper
```and see if the error messages disappear.

Just out of interest, have you installed any kde applications, or in the past tried the KDE desktop, as either of those may have installed one or other of those two packages?

---

### Post by RememberWhenItRained on 2011-04-13
> **ajgreeny said:**
> Even though firefox appears to be running OK, try uninstalling any nsplugin apps you may have with ```
sudo apt-get remove konqueror-nsplugins nspluginwrapper
```and see if the error messages disappear.

Just out of interest, have you installed any kde applications, or in the past tried the KDE desktop, as either of those may have installed one or other of those two packages?
i was about to say no, but does Amarok use KDE?

---

### Post by sandyd on 2011-04-13
> **RememberWhenItRained said:**
> i was about to say no, but does Amarok use KDE?
yes.

---

### Post by RememberWhenItRained on 2011-04-13
> **sandyd said:**
> yes.
that and i installed an SWF plugin

---

### Post by lovinglinux on 2011-04-14
> **ajgreeny said:**
> As far as I can make out, nsplugin is not needed in a gnome system, but is more for kde and konqueror browser, where it enables netscape plugins to work.  I don't use kde so can not go any further than that, but if you are using only gnome, try removing nsplugin and see if the symptoms still exist.

PS:  this plugin seems to be needed for flash to work in some other browsers than firefox;  what flash version have you got and does it work well, or are you having problems with it?  Also, what other browsers do you use?

I use KDE and this is the first I read about such plugin. I don't use Konquerer tho, so I never needed such a thing.

> **ajgreeny said:**
> Even though firefox appears to be running OK, try uninstalling any nsplugin apps you may have with ```
sudo apt-get remove konqueror-nsplugins nspluginwrapper
```and see if the error messages disappear

The *nspluginwrapper* is used when running a 64bit system with flash from the repositories, which is 32bit.

> **RememberWhenItRained said:**
> that and i installed an SWF plugin

Please run the following commands in a Terminal and then copy the contents of the *firefox-report.txt* file that will be generated in your Desktop and paste here.


```


echo 'Ubuntu Architecture' > ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
uname -a >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Ubuntu Version' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat /etc/lsb-release >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox Packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'firefox*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox binaries' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
which firefox >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox >> ~/Desktop/firefox-report.txt
file /usr/local/bin/firefox >> ~/Desktop/firefox-report.txt
file /opt/firefox/firefox >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox divertion' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox.ubuntu >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Sources' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
ls /etc/apt/sources.list.d >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'flash*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Plugin locations' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate libflashplayer.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash symlinks' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/lib/firefox-addons/plugins/libflashplayer.so  >> ~/Desktop/firefox-report.txt
file /usr/lib/mozilla/plugins/flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
file /etc/alternatives/mozilla-flashplugin  >> ~/Desktop/firefox-report.txt
file /var/lib/flashplugin-installer/npwrapper.libflashplayer.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'pluginreg.dat' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat ~/.mozilla/firefox/**/pluginreg.dat >> ~/Desktop/firefox-report.txt
firefox ~/Desktop/firefox-report.txt
```

---

### Post by RememberWhenItRained on 2011-04-14
here:
```

Ubuntu Architecture

Linux collin 2.6.32-30-generic #59-Ubuntu SMP Tue Mar 1 21:30:46 UTC 2011 x86_64 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.2 LTS"

Firefox Packages

firefox						install
firefox-branding				install
firefox-gnome-support				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.16/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

google-earth.list

Flash packages

flashplugin-installer				install

Plugin locations

/usr/lib/flashplugin-installer/libflashplayer.so
/usr/share/ubufox/plugins/npwrapper.libflashplayer.so
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so

/usr/lib/firefox/plugins/flashplugin-alternative.so
/usr/lib/iceape/plugins/flashplugin-alternative.so
/usr/lib/iceweasel/plugins/flashplugin-alternative.so
/usr/lib/midbrowser/plugins/flashplugin-alternative.so
/usr/lib/mozilla/plugins/flashplugin-alternative.so
/usr/lib/xulrunner/plugins/flashplugin-alternative.so
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so

Flash symlinks

/usr/lib/firefox-addons/plugins/libflashplayer.so: ERROR: cannot open `/usr/lib/firefox-addons/plugins/libflashplayer.so' (No such file or directory)
/usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin'
/etc/alternatives/mozilla-flashplugin: symbolic link to `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so'
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped

pluginreg.dat

Generated File. Do not edit.

[HEADER]
Version:0.11:$

[PLUGINS]
npwrapper.libflashplayer.so:$
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so:$
:$
1302739594000:1:5:$
Shockwave Flash 10.2 r153:$
Shockwave Flash:$
2
0:application/x-shockwave-flash:Shockwave Flash:swf:$
1:application/futuresplash:FutureSplash Player:spl:$
librhythmbox-itms-detection-plugin.so:$
/usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so:$
:$
1277465636000:1:5:$
This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.:$
iTunes Application Detector:$
1
0:application/itunes-plugin:::$
libtotem-narrowspace-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so:$
:$
1274282974000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.30.2 plugin handles video and audio streams.:$
QuickTime Plug-in 7.6.6:$
5
0:video/quicktime:QuickTime video:mov:$
1:video/mp4:MPEG-4 video:mp4:$
2:image/x-macpaint:MacPaint Bitmap image:pntg:$
3:image/x-quicktime:Macintosh Quickdraw/PICT drawing:pict, pict1, pict2:$
4:video/x-m4v:MPEG-4 video:m4v:$
libtotem-mully-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-mully-plugin.so:$
:$
1274282974000:1:5:$
DivX Web Player version 1.4.0.233:$
DivXÂ® Web Player:$
1
0:video/divx:AVI video:divx:$
libtotem-gmp-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-gmp-plugin.so:$
:$
1274282974000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.30.2 plugin handles video and audio streams.:$
Windows Media Player Plug-in 10 (compatible; Totem):$
13
0:application/x-mplayer2:AVI video:avi, wma, wmv:$
1:video/x-ms-asf-plugin:ASF video:asf, wmv:$
2:video/x-msvideo:AVI video:asf, wmv:$
3:video/x-ms-asf:ASF video:asf:$
4:video/x-ms-wmv:Windows Media video:wmv:$
5:video/x-wmv:Windows Media video:wmv:$
6:video/x-ms-wvx:Windows Media video:wmv:$
7:video/x-ms-wm:Windows Media video:wmv:$
8:video/x-ms-wmp:Windows Media video:wmv:$
9:application/x-ms-wms:Windows Media video:wms:$
10:application/x-ms-wmp:Windows Media video:wmp:$
11:application/asx:Microsoft ASX playlist:asx:$
12:audio/x-ms-wma:Windows Media audio:wma:$
libtotem-cone-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-cone-plugin.so:$
:$
1274282974000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.30.2 plugin handles video and audio streams.:$
VLC Multimedia Plugin (compatible Totem 2.30.2):$
19
0:application/x-vlc-plugin:VLC Multimedia Plugin::$
1:application/vlc:VLC Multimedia Plugin::$
2:video/x-google-vlc-plugin:VLC Multimedia Plugin::$
3:application/x-ogg:Ogg multimedia file:ogg:$
4:application/ogg:Ogg multimedia file:ogg:$
5:audio/ogg:Ogg Audio:oga:$
6:audio/x-ogg:Ogg Audio:ogg:$
7:video/ogg:Ogg Video:ogv:$
8:video/x-ogg:Ogg Video:ogg:$
9:application/annodex:Annodex exchange format:anx:$
10:audio/annodex:Annodex Audio:axa:$
11:video/annodex:Annodex Video:axv:$
12:video/mpeg:MPEG video:mpg, mpeg, mpe:$
13:audio/wav:WAV audio:wav:$
14:audio/x-wav:WAV audio:wav:$
15:audio/mpeg:MP3 audio:mp3:$
16:application/x-nsv-vp3-mp3:NullSoft video:nsv:$
17:video/flv:Flash video:flv:$
```
18:application/x-totem-plugin:Totem Multimedia plugin::$

---

### Post by lovinglinux on 2011-04-14
> **RememberWhenItRained said:**
> here:
```

Ubuntu Architecture

Linux collin 2.6.32-30-generic #59-Ubuntu SMP Tue Mar 1 21:30:46 UTC 2011 x86_64 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.2 LTS"

Firefox Packages

firefox						install
firefox-branding				install
firefox-gnome-support				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.16/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

google-earth.list

Flash packages

flashplugin-installer				install

Plugin locations

/usr/lib/flashplugin-installer/libflashplayer.so
/usr/share/ubufox/plugins/npwrapper.libflashplayer.so
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so

/usr/lib/firefox/plugins/flashplugin-alternative.so
/usr/lib/iceape/plugins/flashplugin-alternative.so
/usr/lib/iceweasel/plugins/flashplugin-alternative.so
/usr/lib/midbrowser/plugins/flashplugin-alternative.so
/usr/lib/mozilla/plugins/flashplugin-alternative.so
/usr/lib/xulrunner/plugins/flashplugin-alternative.so
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so

Flash symlinks

/usr/lib/firefox-addons/plugins/libflashplayer.so: ERROR: cannot open `/usr/lib/firefox-addons/plugins/libflashplayer.so' (No such file or directory)
/usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin'
/etc/alternatives/mozilla-flashplugin: symbolic link to `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so'
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped

pluginreg.dat

Generated File. Do not edit.

[HEADER]
Version:0.11:$

[PLUGINS]
npwrapper.libflashplayer.so:$
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so:$
:$
1302739594000:1:5:$
Shockwave Flash 10.2 r153:$
Shockwave Flash:$
2
0:application/x-shockwave-flash:Shockwave Flash:swf:$
1:application/futuresplash:FutureSplash Player:spl:$
librhythmbox-itms-detection-plugin.so:$
/usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so:$
:$
1277465636000:1:5:$
This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.:$
iTunes Application Detector:$
1
0:application/itunes-plugin:::$
libtotem-narrowspace-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so:$
:$
1274282974000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.30.2 plugin handles video and audio streams.:$
QuickTime Plug-in 7.6.6:$
5
0:video/quicktime:QuickTime video:mov:$
1:video/mp4:MPEG-4 video:mp4:$
2:image/x-macpaint:MacPaint Bitmap image:pntg:$
3:image/x-quicktime:Macintosh Quickdraw/PICT drawing:pict, pict1, pict2:$
4:video/x-m4v:MPEG-4 video:m4v:$
libtotem-mully-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-mully-plugin.so:$
:$
1274282974000:1:5:$
DivX Web Player version 1.4.0.233:$
DivXÂ® Web Player:$
1
0:video/divx:AVI video:divx:$
libtotem-gmp-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-gmp-plugin.so:$
:$
1274282974000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.30.2 plugin handles video and audio streams.:$
Windows Media Player Plug-in 10 (compatible; Totem):$
13
0:application/x-mplayer2:AVI video:avi, wma, wmv:$
1:video/x-ms-asf-plugin:ASF video:asf, wmv:$
2:video/x-msvideo:AVI video:asf, wmv:$
3:video/x-ms-asf:ASF video:asf:$
4:video/x-ms-wmv:Windows Media video:wmv:$
5:video/x-wmv:Windows Media video:wmv:$
6:video/x-ms-wvx:Windows Media video:wmv:$
7:video/x-ms-wm:Windows Media video:wmv:$
8:video/x-ms-wmp:Windows Media video:wmv:$
9:application/x-ms-wms:Windows Media video:wms:$
10:application/x-ms-wmp:Windows Media video:wmp:$
11:application/asx:Microsoft ASX playlist:asx:$
12:audio/x-ms-wma:Windows Media audio:wma:$
libtotem-cone-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-cone-plugin.so:$
:$
1274282974000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.30.2 plugin handles video and audio streams.:$
VLC Multimedia Plugin (compatible Totem 2.30.2):$
19
0:application/x-vlc-plugin:VLC Multimedia Plugin::$
1:application/vlc:VLC Multimedia Plugin::$
2:video/x-google-vlc-plugin:VLC Multimedia Plugin::$
3:application/x-ogg:Ogg multimedia file:ogg:$
4:application/ogg:Ogg multimedia file:ogg:$
5:audio/ogg:Ogg Audio:oga:$
6:audio/x-ogg:Ogg Audio:ogg:$
7:video/ogg:Ogg Video:ogv:$
8:video/x-ogg:Ogg Video:ogg:$
9:application/annodex:Annodex exchange format:anx:$
10:audio/annodex:Annodex Audio:axa:$
11:video/annodex:Annodex Video:axv:$
12:video/mpeg:MPEG video:mpg, mpeg, mpe:$
13:audio/wav:WAV audio:wav:$
14:audio/x-wav:WAV audio:wav:$
15:audio/mpeg:MP3 audio:mp3:$
16:application/x-nsv-vp3-mp3:NullSoft video:nsv:$
17:video/flv:Flash video:flv:$
```
18:application/x-totem-plugin:Totem Multimedia plugin::$

Everything looks fine. I don't know what is unhandled variable 18, but looks to me is due to the fact that you are using a 32bit flash plugin on a 64bit machine. If you want to get rid of the message, try my [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/161939/") extension. It will detect installed flash plugins, remove them and install the beta 64bit from Adobe.

---

### Post by RememberWhenItRained on 2011-04-14
> **lovinglinux said:**
> Everything looks fine. I don't know what is unhandled variable 18, but looks to me is due to the fact that you are using a 32bit flash plugin on a 64bit machine. If you want to get rid of the message, try my [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/161939/") extension. It will detect installed flash plugins, remove them and install the beta 64bit from Adobe.

thanks!

---

