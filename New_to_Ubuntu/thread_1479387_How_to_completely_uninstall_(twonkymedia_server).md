---
title: "How to completely uninstall (twonkymedia server)"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by Steven_S on 2010-05-10
I'm posting this here, as I imagine the answer may also be useful for other pieces of software...

I have installed Twonkymedia server through a shell script. I tried it out - nice, by the way - but now want to completely remove it from my system. How do I do that?

The installation has made a folder under /var and one under /usr/local, but how do I know what other files it has written? 

And when I find them, can I just remove these files and folders, and that's it? In my "other OS", that would get me into deep waters. But what about in Ubuntu?

PS I should add that I already stopped the application running (using kill); I imagine that might be useful before trying to remove it :-).

---

### Post by Steven_S on 2010-05-11
Nobody? 

In essence, the question is how to remove *any* software that has not been installed using synaptic or the software centre...

---

### Post by Absolut Newbee on 2010-05-11
try looking in Synaptic Package Manager, and there complete removel

---

### Post by Steven_S on 2010-05-11
Thanks - I tried that, but the package is not in Synaptic (or at least, I couldn't find it). 

I imagine people would have the same question for anything they install from .sh, or using a "tarball"...

---

### Post by Paqman on 2010-05-11
> **Steven_S said:**
> 
I imagine people would have the same question for anything they install from .sh, or using a "tarball"...

Have a look in the original download, there might be an uninstall script, and/or a readme that'll tell you what you need to delete.

---

### Post by Steven_S on 2010-05-11
Thanks for that tip!

Ok, I found the install log: 

> Installing TwonkyMedia server into directory /usr/local/twonkymedia
./
./twonkymedia
./plugins/
./plugins/mediafusion-integration.plugin
./plugins/mediafusion-integration-plugin
./plugins/itunes-import
./plugins/itunes-import.plugin
./mediafusion_keystore.dat
./RevisionHistory
./twonkymedia.sh
./resources/
./resources/TwonkyMediaConfig.js
./resources/index.html
./resources/radio-sel.gif
./resources/website-bg.gif
./resources/photo-sel.gif
./resources/TMS_Logo_transparent.png
./resources/video-sel.gif
./resources/webbrowse-settings.gif
./resources/music.gif
./resources/strings-chs.txt
./resources/views/
./resources/views/folder.view.xml
./resources/views/simple.view.xml
./resources/views/advanced.view.xml
./resources/views/classified.view.xml
./resources/views/view-definitions.xml
./resources/views/ipodlike.view.xml
./resources/head-background.jpg
./resources/wmdrm-trouble.htm
./resources/webbrowse-e61-upload.gif
./resources/devicedescription-dlna-1-0.xml
./resources/webbrowse-play.gif
./resources/devicedescription-redsonic.xml
./resources/platform-specific-menu-grouping.js
./resources/strings-ru.txt
./resources/mb-video-sel.gif
./resources/strings-it.txt
./resources/devicedescription-dlna-1-5.xml
./resources/clients.db
./resources/twonkymedia.gif
./resources/empty.gif
./resources/webbrowse-logo.gif
./resources/nocover_audio.jpg
./resources/menu-background.jpg
./resources/right.gif
./resources/twonkyicon-120x120.png
./resources/webbrowse-psp-home.gif
./resources/photo.gif
./resources/config.html
./resources/mb-video.gif
./resources/webbrowse-psp-upload.gif
./resources/mediabrowser.gif
./resources/webbrowse-psp-play.gif
./resources/twonkyicon-48x48.png
./resources/strings-es.txt
./resources/mb-music.gif
./resources/webbrowse-upload.gif
./resources/webbrowse.css
./resources/twonkyicon-120x120.jpg
./resources/config-content.html
./resources/webbrowse-e61-play.gif
./resources/wait.htm
./resources/tri-blau.gif
./resources/favicon.ico
./resources/status-sel.gif
./resources/TwonkyMediaConfig.css
./resources/webbrowse-psp-settings.gif
./resources/strings-jp.txt
./resources/webbrowse-back.gif
./resources/status.gif
./resources/cart.gif
./resources/config-head.html
./resources/webbrowse-e61-prev.gif
./resources/mb-config.gif
./resources/webbrowse-n95-upload.gif
./resources/mediabrowser-sel.gif
./resources/webbrowse-psp-back.gif
./resources/webbrowse-pc.gif
./resources/comingsoon.gif
./resources/devicedescription-xbox.xml
./resources/cds.xml
./resources/mb-music-sel.gif
./resources/config.gif
./resources/webbrowse-e61.css
./resources/arrow_test_small.gif
./resources/webbrowse-psp-next.gif
./resources/mb-radio-sel.gif
./resources/webbrowse-prev.gif
./resources/cds-hdrl.xml
./resources/strings-de.txt
./resources/webbrowse-e61-settings.gif
./resources/folder.gif
./resources/cms.xml
./resources/arrow-left.gif
./resources/arrow-right.gif
./resources/home.gif
./resources/mb-photo.gif
./resources/webbrowse-n95-next.gif
./resources/TwonkyMediaServer_logo.jpg
./resources/webbrowse-n95-prev.gif
./resources/strings-fr.txt
./resources/wait.gif
./resources/transcoding.db
./resources/webbrowse-n95-settings.gif
./resources/mb-photo-sel.gif
./resources/strings-cht.txt
./resources/webbrowse-psp-logo.gif
./resources/webbrowse-home.gif
./resources/stop.gif
./resources/devicedescription-win7.xml
./resources/twonkyicon-80x80.jpg
./resources/webbrowse-n95.css
./resources/music-sel.gif
./resources/rss.gif
./resources/mb-header-logo.gif
./resources/webbrowse-e61-next.gif
./resources/webbrowse-mobile.gif
./resources/mb-radio.gif
./resources/radio.gif
./resources/left.gif
./resources/nocover_video.jpg
./resources/strings-nl.txt
./resources/webbrowse-psp-prev.gif
./resources/webbrowse-psp.css
./resources/webbrowse-e61-home.gif
./resources/msreg.xml
./resources/protocolinfo.xml
./resources/webbrowse-n95-play.gif
./resources/nocover_photo.jpg
./resources/TM_16x16.png
./resources/webbrowse-e61-back.gif
./resources/record.gif
./resources/webbrowse-n95-back.gif
./resources/devicedescription-tmm.xml
./resources/twonkyicon-48x48.jpg
./resources/cds-noupdate.xml
./resources/webbrowse-e61-logo.gif
./resources/attention-small.gif
./resources/TwonkyMediaConfig_grouping.js
./resources/norss.gif
./resources/strings-ko.txt
./resources/strings-en.txt
./resources/webbrowse-next.gif
./resources/strings-fi.txt
./resources/video.gif
./resources/mb-headerBG-kachel.gif
./resources/config-menu.html
./resources/webbrowse-n95-home.gif
./resources/devicedescription-yamaha.xml
./twonkymedia-server-default.ini
./twonkymediaserver
./bg_trans
./cgi-bin/
./cgi-bin/ffmpeg-avi-flv.desc
./cgi-bin/ffmpeg-mov-flv.desc
./cgi-bin/flac.location
./cgi-bin/convert
./cgi-bin/any-mp3.desc
./cgi-bin/ffmpeg-ts-mp4.desc
./cgi-bin/ffmpeg-mpg-wmv.desc
./cgi-bin/ffmpeg-wmv-flv.desc
./cgi-bin/convert-readme.txt
./cgi-bin/ffmpeg-flv-mpg.desc
./cgi-bin/cgi-jpegscale
./cgi-bin/ffmpeg-mpg-flv.desc
./cgi-bin/ffmpeg-msvideo-flv.desc
./cgi-bin/ffmpeg-asf-flv.desc
./cgi-bin/ffmpeg-msdvr-mpeg.desc
./cgi-bin/convert-jpeg.desc
./cgi-bin/thumbs-jpeg.desc
./cgi-bin/ffmpeg.location
./cgi-bin/flac-wav.desc
./cgi-bin/convert.location
./cgi-bin/ffmpeg-mp4-flv.desc
./cgi-bin/ffmpeg-divx-mpeg.desc
./cgi-bin/jpeg-scale.desc
./Linux-HowTo.txt
./initial_keystore.dat
./start_bgtrans.sh
./radio.m3u
`/usr/local/twonkymedia/twonkymedia.sh' -> `/etc/init.d/twonkyserver'
Starting server ...
Starting /usr/local/twonkymedia/twonkymedia ... Daemonizing...
Daemonizing...

Installation finished

If I delete /usr/local/twonkymedia, does that take care of everything?

I have also found a Twonkymedia folder under /var. I presume that got there by starting the server, so I'll get rid of that too then?

PS Sorry for the long paste. I haven't found how to make a scroll box for that...

---

### Post by Paqman on 2010-05-11
> **Steven_S said:**
> 
If I delete /usr/local/twonkymedia, does that take care of everything?

I have also found a Twonkymedia folder under /var. I presume that got there by starting the server, so I'll get rid of that too then?


That looks like it should take care of it. There might also be a .folder in your home folder with some settings in it.

---

### Post by Steven_S on 2010-05-11
Thanks! 

Sorry if these questions seem strange. I'm just used to XP leaving a trail of trash behind after uninstalling, and I want to understand how to leave my Ubuntu install clean and smooth. I understand there are no problems similar to the Windows registry, but I still figure that it is better not to leave bits and pieces lying around.

---

### Post by Kobalt on 2010-05-11
In the Twonky archive you should find an INSTALL file, which also contains instructions for removal. 
Usually, for programs installed with the command line, you should use a command to uninstall that will take care of everything : 
```
sudo ./uninstall *xxx*
```

---

### Post by Paqman on 2010-05-11
> **Steven_S said:**
> Thanks! 

Sorry if these questions seem strange. I'm just used to XP leaving a trail of trash behind after uninstalling, and I want to understand how to leave my Ubuntu install clean and smooth. I understand there are no problems similar to the Windows registry, but I still figure that it is better not to leave bits and pieces lying around.

By far the best thing to do is only ever install things from the repos, a PPA, or a .deb file. If you do that, they'll uninstall completely cleanly. Tarballs, .sh installers, etc should be avoided if at all possible. They tend to result in messy installs like this, and unstable systems. Stick to the package manager and all will be smooth sailing.

---

### Post by richaoj on 2011-01-23
did anyone find out how to do this?

---

### Post by mitanc on 2011-07-29
I basically just ran the command 

```
sudo chmod -x /etc/init.d/twonkyserver
```

This disables the service on startup and twonky is out of your way.  I wouldn't worry about the space taken up on the system as its negligible.  

What do you guys think?

---

### Post by djroketboy on 2011-10-30
> **mitanc said:**
> I basically just ran the command 

```
sudo chmod -x /etc/init.d/twonkyserver
```

This disables the service on startup and twonky is out of your way.  I wouldn't worry about the space taken up on the system as its negligible.  

What do you guys think?

I think they should have a proper way to remove the software from your system. 

I am so frustrated right now trying to get this removed.

---

### Post by Steve54 on 2011-10-31
> **Paqman said:**
> By far the best thing to do is only ever install things from the repos, a PPA, or a .deb file. If you do that, they'll uninstall completely cleanly. Tarballs, .sh installers, etc should be avoided if at all possible. They tend to result in messy installs like this, and unstable systems. Stick to the package manager and all will be smooth sailing.
 
I couldn't find this with Synaptic, is it because it's a full commercial program?

---

### Post by amdenis on 2012-09-07
obviously, the software installed other than via .deb packages won't be found in Synaptic.

the following worked for me:

```
sudo rm -r /var/twonky
sudo rm -r /usr/local/twonky
sudo rm /etc/init.d/twonkyserver
```

fortunately, this piece of software didnt put anything to rc*'s scripts, so these commands should be enough.

---

