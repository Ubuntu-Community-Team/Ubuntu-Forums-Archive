---
title: "How to download streaming videos from internet"
date: 2010-11-04
forum: New to Ubuntu
---

### Post by karthick87 on 2010-11-04
How to download streaming videos from websites like youtube..?

---

### Post by Hippytaff on 2010-11-04
I used to do it with quicktime on windows, don't know if you can with linux though?

---

### Post by julio_cortez on 2010-11-04
Maybe you can try using firefox with an extension:
[https://addons.mozilla.org/firefox/search/?q=youtube&cat=1%2C5&lver=any&pid=1&sort=&pp=20&lup=&advanced=](https://addons.mozilla.org/firefox/search/?q=youtube&cat=1%2C5&lver=any&pid=1&sort=&pp=20&lup=&advanced=)

---

### Post by bioterror on 2010-11-04
> **getyourkarthick said:**
> How to download streaming videos from websites like youtube..?

**apt-cache show youtube-dl** gives me something like this:
> 
Package: youtube-dl
Priority: extra
Section: universe/web
Suggests: rtmpdump
Filename: pool/universe/y/youtube-dl/youtube-dl_2010.04.04-1_all.deb
Description: download videos from youtube
 youtube-dl is a small command-line program to download videos from
 YouTube.com and other sites that don't provide direct links to the
 videos served.
 .
 youtube-dl allows the user, among other things, to choose a specific
 video quality to download (if available) or let the program
 automatically determine the best quality video to grab. It supports
 downloading entire playlists and all videos from a given user.
 .
 Currently supported sites are video.google.com, youtube, photobucket,
 and metacafe.
Homepage: [http://bitbucket.org/rg3/youtube-dl/](http://bitbucket.org/rg3/youtube-dl/)


---

### Post by Verbeck on 2010-11-04
isn't downloading youtube videos against thier Terms of service? anyway, flash content usually gets downloaded to your temp directory

---

### Post by nitstorm on 2010-11-04
> **getyourkarthick said:**
> How to download streaming videos from websites like youtube..?


As said above by Verbeck all flash content gets stored in /tmp folder, you might also consider using wget to get your videos or any content for that matter. Check out the following link,
[http://lifehacker.com/161202/geek-to-live--mastering-wget](http://lifehacker.com/161202/geek-to-live--mastering-wget)

---

### Post by tajiknomi on 2010-11-04
[SIZE=2]Firefox can do it easy...Go to..

TOOLS>ADD-onn>Get Add on's>(type their "**Download helper**") and you will get a **list of it**....select your choice it will give you an **icon**(once u have open Youtube site).....
[/SIZE]

---

### Post by The Foz on 2010-11-04
As one of the other posts suggested, the flash video is stored in /tmp.

It will be called something like 'FlashXXz6kynv', where the part after 'Flash' is an automatically generated sequence number. The file normally remains there until you close the page. If not, pause the playback before the end. You must wait until the whole file is downloaded, indicated on YouTube by the red bar at the bottom of the video playback area.

Once it is complete, you can just copy it to somewhere else. You will probably want to rename it, and add a '.flv' file extension.

---

### Post by karthick87 on 2010-11-04
> **The Foz said:**
> As one of the other posts suggested, the flash video is stored in /tmp.

It will be called something like 'FlashXXz6kynv', where the part after 'Flash' is an automatically generated sequence number. The file normally remains there until you close the page. If not, pause the playback before the end. You must wait until the whole file is downloaded, indicated on YouTube by the red bar at the bottom of the video playback area.

Once it is complete, you can just copy it to somewhere else. You will probably want to rename it, and add a '.flv' file extension.

Will give a try :)

---

### Post by coffee412 on 2010-11-04
> **getyourkarthick said:**
> How to download streaming videos from websites like youtube..?

If its specifically Youtube then here is how its done:

Go to youtube and click on the video like your going to watch it. Then go to your /tmp folder after its done playing and you will see the video file sitting in there. Copy it to your home folder.

Doesnt work with google videos. What I do for sites that stream but do not really cache it to your temp folder is I use Xvidcap to capture the video as it plays and I run a cable from my headset plugin to my line in on sound card and capture sound that way. Then I load up in avidemux and sync the sound.

I understand a new plugin for firefox is in development called "Rainbox". Its gonna be a while though.

Anyways, my 2 above tricks work great for me.

---

### Post by dzon65 on 2011-03-10
There's lots of download addons for FF. However, those increase the load on your bandwidth.
Btw, flv's aren't stored in the tmp file these days but in mozilla's cache folder.

---

### Post by migel_wimtore on 2011-03-10
Id go the firefox addon route. That way ther is no fiddling about, you just click an icon in the statusbar once youv decided you want a vid.

I can personally recommend embedded objects:

[https://addons.mozilla.org/en-US/firefox/search/?q=embedded+objects&cat=all&x=0&y=0](https://addons.mozilla.org/en-US/firefox/search/?q=embedded+objects&cat=all&x=0&y=0)

Its brilliant, there is hardly a video it cant download and in sorts of formats too, even divx!

---

