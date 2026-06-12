---
title: "youtube  0 wont play"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by kimikrishna on 2009-03-10
i tried youtube...
i asked me install adobe player

i downloaded deb file and installde it too

restarted browser too

but still youtube is not playing vids

i again downloaded and installed

but no use...

any idea ?

---

### Post by gandaran on 2009-03-10
provide more info, ubuntu version 8.04 or 8.10, 32-bits or 64-bits? 
system fully updated or not?

---

### Post by hansdown on 2009-03-10
Hi kimikrishna.

Install flashplugin-nonfree from synaptic.

---

### Post by kimikrishna on 2009-03-10
i use ibex...
dont know how to find whether its 64 or 32 bit....

is it not free that plugon ??

---

### Post by gandaran on 2009-03-10
> **kimikrishna said:**
> i use ibex...
dont know how to find whether its 64 or 32 bit....

is it not free that plugon ??
yes it's free and it installs exactly the same adobe flash as the one you download from adobe.com, only the package has a deferent name, remove the one installed and try the flashplugin-nonfree, but before you install anything from apt-get/synaptic run the update either by command line (sudo apt-get update) or open synaptic package manager and click the reload button to get the new package list, if you don't do this first you mite install an old broken package.
now scroll down to flashplugin-nonfree, mark for install and click the apply button. 
if it still won't work I will give you instructions later on how to install flash manually.  
one question, do you have the flashblock add-on installed?

---

### Post by bwang on 2009-03-10
Try rebooting. Once, I couldn't get Flash to work, but a reboot fixed everything.

---

### Post by kimikrishna on 2009-03-11
i dont have flash block addon

rebooting is of no use....

i installed that plugin from synpentic too...../

but still youtube wont plaly videos

---

### Post by kimikrishna on 2009-03-11
but i have only noscript addon installed

but i allowed 
youtube site

---

### Post by gandaran on 2009-03-11
can you post the full output by typing this code in firefox url bar
```
about:plugins
```
and also this, open terminal and type **locate libflash**

---

### Post by kimikrishna on 2009-03-11
```
Installed plugins
Find more information about browser plugins at mozilla.org.
Help for installing plugins is available from plugindoc.mozdev.org.
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 r15

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
Totem Web Browser Plugin 2.24.2

    File name: libtotem-basic-plugin.so
    The Totem 2.24.2 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-ogg 	Ogg multimedia file 	ogg 	Yes
application/ogg 	Ogg multimedia file 	ogg 	Yes
audio/ogg 	Ogg Audio 	oga 	Yes
audio/x-ogg 	Ogg Audio 	ogg 	Yes
video/ogg 	Ogg Video 	ogv 	Yes
video/x-ogg 	Ogg Video 	ogg 	Yes
application/annodex 	application/annodex type 	anx 	Yes
audio/annodex 	audio/annodex type 	axa 	Yes
video/annodex 	video/annodex type 	axv 	Yes
video/mpeg 	MPEG video 	mpg, mpeg, mpe 	Yes
audio/wav 	WAV audio 	wav 	Yes
audio/x-wav 	WAV audio 	wav 	Yes
audio/mpeg 	MP3 audio 	mp3 	Yes
application/x-nsv-vp3-mp3 	NullSoft video 	nsv 	Yes
video/flv 	Flash video 	flv 	Yes
application/x-totem-plugin 	Totem Multimedia plugin 		Yes
Windows Media Player Plug-in 10 (compatible; Totem)

    File name: libtotem-gmp-plugin.so
    The Totem 2.24.2 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-mplayer2 	AVI video 	avi, wma, wmv 	Yes
video/x-ms-asf-plugin 	ASF video 	asf, wmv 	Yes
video/x-msvideo 	AVI video 	asf, wmv 	Yes
video/x-ms-asf 	ASF video 	asf 	Yes
video/x-ms-wmv 	Windows Media video 	wmv 	Yes
video/x-wmv 	Windows Media video 	wmv 	Yes
video/x-ms-wvx 	Windows Media video 	wmv 	Yes
video/x-ms-wm 	Windows Media video 	wmv 	Yes
video/x-ms-wmp 	Windows Media video 	wmv 	Yes
application/x-ms-wms 	Windows Media video 	wms 	Yes
application/x-ms-wmp 	Windows Media video 	wmp 	Yes
application/asx 	Microsoft ASX playlist 	asx 	Yes
audio/x-ms-wma 	Windows Media audio 	wma 	Yes
DivX® Web Player

    File name: libtotem-mully-plugin.so
    DivX Web Player version 1.4.0.233

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	AVI video 	divx 	Yes
QuickTime Plug-in 7.2.0

    File name: libtotem-narrowspace-plugin.so
    The Totem 2.24.2 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	QuickTime video 	mov 	Yes
video/mp4 	MPEG-4 video 	mp4 	Yes
image/x-macpaint 	MacPaint Bitmap image 	pntg 	Yes
image/x-quicktime 	Macintosh Quickdraw/PICT drawing 	pict, pict1, pict2 	Yes
video/x-m4v 	MPEG-4 video 	m4v 	Yes
Default Plugin

    File name: libnullplugin.so
    The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.

MIME Type 	Description 	Suffixes 	Enabled
* 	All types 	.* 	No
Demo Print Plugin for unix/linux

    File name: libunixprintplugin.so
    The demo print plugin for unix.

MIME Type 	Description 	Suffixes 	Enabled
application/x-print-unix-nsplugin 	Demo Print Plugin for Unix/Linux 	.pnt 	Yes

```

for firefox url bar

---

### Post by kimikrishna on 2009-03-11
for libflash in cli

```
/usr/lib/adobe-flashplugin/libflashplayer.so
/usr/lib/flashplugin-nonfree/libflashplayer.so
/usr/lib/flashplugin-nonfree-extrasound/libflashsupport.so
/usr/lib/iceweasel/libflashsupport.so
/usr/lib/openoffice/program/libflash680li.so
/usr/lib/xulrunner/libflashsupport.so

```

---

### Post by kimikrishna on 2009-03-11
I usually watch vids from youtube.....
now i cant :( i have all flash plgns installed too :(

---

### Post by abybaddi on 2009-03-11
Tell me how many types  of files you can play, the apps installed in Sound & Video Section and whether Gstreamer plugins are installed or not.

---

### Post by LowSky on 2009-03-11
```
sudo apt-get intall ubuntu-restricted-extras
``` then reboot, every website should work.

if not go to /home/username/.mozilla and delte the folder. restart Firefox and it will recreate that folder, back up bookmarks before proceeding

---

### Post by kimikrishna on 2009-03-11
> **abybaddi said:**
> Tell me how many types  of files you can play, the apps installed in Sound & Video Section and whether Gstreamer plugins are installed or not.
hwo do i know that "how many" that ubuntu plays ??

am i computer ? :( :(

plz be clear

---

### Post by abybaddi on 2009-03-11
Don't you try to open any movies, musics, etc.? How many of them plays?

---

### Post by kimikrishna on 2009-03-11
> **LowSky said:**
> ```
sudo apt-get intall ubuntu-restricted-extras
``` then reboot, every website should work.

if not go to /home/username/.mozilla and delte the folder. restart Firefox and it will recreate that folder, back up bookmarks before proceeding
ok..
i will do this

---

### Post by kimikrishna on 2009-03-11
i have vlc player....
that plays almost everything :P

---

### Post by abybaddi on 2009-03-11
Install gstreamer0.10-ffmpeg_0.10.5-1_i386, gstreamer0.10-fluendo-mp3_0.10.7.debian-1_i386, gstreamer0.10-fluendo-mpegdemux_0.10.15-1_i386, gstreamer0.10-fluendo-mpegmux_0.10.4-1_i386, gstreamer0.10-plugins-bad_0.10.8-1_i386, gstreamer0.10-plugins-ugly_0.10.7-3_i386 and then you would be able to play all the media files. Also Re-install the Adobe flash 10 from the website.

---

### Post by abybaddi on 2009-03-11
After that reboot and everything should work perfectly, And if not see that all the plug-ins are enabled in firefox.

---

### Post by gandaran on 2009-03-11
> **kimikrishna said:**
> for libflash in cli

```
/usr/lib/adobe-flashplugin/libflashplayer.so
/usr/lib/flashplugin-nonfree/libflashplayer.so
/usr/lib/flashplugin-nonfree-extrasound/libflashsupport.so
/usr/lib/iceweasel/libflashsupport.so
/usr/lib/openoffice/program/libflash680li.so
/usr/lib/xulrunner/libflashsupport.so

```
you have two flash packages installed, no need for that, both install exactly the same adobe flash, so remove either the adobe-flashplugin or flashplugin-nonfree, remove also flashplugin-nonfree-extrasound, to many packages can conflict, only one flash package is enough,
the adobe flash shows up in firefox plugins correctly, check if it's enabled (tools » addons » plugins » shockwave flash » enable/disable) and disable all your addons installed then try again.
check also if java script is enabled too.

---

### Post by aktiwers on 2009-03-11
You can use Movie Player to watch Youtube. Just enable the Youtube plugin.

If you want to install flash manually run this (on 32bit):
```

wget [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz)
tar xvzf install_flash_player_10_linux.tar.gz 
cp install_flash_player_10_linux/libflashplayer.so $HOME/.mozilla/plugins/

```And restart Firefox.

On 64Bit:
```

cd  $HOME/.mozilla/plugins/
wget [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz)
tar xvzf libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz

```And restart Firefox.

You can now delete the downloaded files in your Home Folder.

---

### Post by kimikrishna on 2009-03-12
> **aktiwers said:**
> You can use Movie Player to watch Youtube. Just enable the Youtube plugin.

If you want to install flash manually run this (on 32bit):
```

wget [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz)
tar xvzf install_flash_player_10_linux.tar.gz 
cp install_flash_player_10_linux/libflashplayer.so $HOME/.mozilla/plugins/

```And restart Firefox.

On 64Bit:
```

cd  $HOME/.mozilla/plugins/
wget [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz)
tar xvzf libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz

```And restart Firefox.

You can now delete the downloaded files in your Home Folder.
```
 wget http://fpdownload.macromedia.com/get...0_linux.tar.gz
--2009-03-12 00:01:06--  http://fpdownload.macromedia.com/get...0_linux.tar.gz
Resolving fpdownload.macromedia.com... 125.252.206.70
Connecting to fpdownload.macromedia.com|125.252.206.70|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2009-03-12 00:01:07 ERROR 404: Not Found.
```


now what ?

---

### Post by kimikrishna on 2009-03-12
no... sorry the lnk works...

but i exactly copy pasted so that the .... in between got in as such,,,,
```
http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz
```

but in that the "..." came as such when copied

---

### Post by kimikrishna on 2009-03-12
ok....
help me with this one...
idownloaded and did tar xvzf but this wont work

```
krishna@ubuntu:~$ cp install_flash_player_10_linux/libflashplayer.so $HOME/.mozilla/plugins/
cp: cannot create regular file `/home/krishna/.mozilla/plugins/': Is a di
```

---

### Post by kimikrishna on 2009-03-12
now. i learnt that i have 64 bits by creating another topic.....

now,. i am trying this 64 bit as you said

but it says : 
```
bash: cd: /home/krishna/.mozilla/plugins/: No such file or directory
```

---

### Post by zabien1970 on 2009-03-12
I may have a fix, someone please stop me if I'm wrong, from reading your posts it sounds like youtube was working then it stopped, I had this recently happen after doing some updates and was frustrated for awhile. adding 'media wrap' from firefox addons fixed it and all is fine now, I am running 32bit though but I don't know if that matters for firefox. 
 Here's the link

 [https://addons.mozilla.org/en-US/firefox/search?q=media%20wrap](https://addons.mozilla.org/en-US/firefox/search?q=media%20wrap)

---

### Post by gandaran on 2009-03-12
> **kimikrishna said:**
> now. i learnt that i have 64 bits by creating another topic.....

now,. i am trying this 64 bit as you said

but it says : 
```
bash: cd: /home/krishna/.mozilla/plugins/: No such file or directory
```
are you really sure it's 64-bits? then how did you install the adobe-flashplugin package from adobe.com? this package won't install on 64-bits systems!
to find out the version type on terminal/console **uname -m** post the result back here.
you don't need to run all those codes to install the tar.gz flash package.
do it the easy way, download the 32-bits or 64-bits .tar.gz flash package, right click the package, choose extract here from the menu, now just move the libflashplayer.so file to a browser plugins folder, try moving it to /home/krishna/.mozilla/plugins/ (you have to make the plugins folder) as it seems flash installed in the file system is not working for you so try this home user .mozilla/plugins folder, and remember you have to remove all the other flash packages installed in the file system or it won't work.

---

### Post by kimikrishna on 2009-03-12
> **gandaran said:**
> are you really sure it's 64-bits? then how did you install the adobe-flashplugin package from adobe.com? this package won't install on 64-bits systems!
to find out the version type on terminal/console **uname -m** post the result back here.
you don't need to run all those codes to install the tar.gz flash package.
do it the easy way, download the 32-bits or 64-bits .tar.gz flash package, right click the package, choose extract here from the menu, now just move the libflashplayer.so file to a browser plugins folder, try moving it to /home/krishna/.mozilla/plugins/ (you have to make the plugins folder) as it seems flash installed in the file system is not working for you so try this home user .mozilla/plugins folder, and remember you have to remove all the other flash packages installed in the file system or it won't work.
see this topic ......
```
http://ubuntuforums.org/showthread.php?t=1093833
```

---

### Post by gandaran on 2009-03-12
you system is 32-bits, now have you tried removing every flash installed in file system and just install the flash in home .mozilla/plugins?
get the tar.gz flash package here [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

---

