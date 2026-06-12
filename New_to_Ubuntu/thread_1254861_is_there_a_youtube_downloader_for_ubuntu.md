---
title: "is there a youtube downloader for ubuntu?"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by 289531.EXE on 2009-08-31
i'd like to know. can anyone help?

---

### Post by MrWES on 2009-08-31
> **289531.EXE said:**
> i'd like to know. can anyone help?

There's a add on for Firefox called DownloadHelper.

[https://addons.mozilla.org/en-US/firefox/addon/3006]("https://addons.mozilla.org/en-US/firefox/addon/3006")

---

### Post by hockeytux on 2009-08-31
Yes, as a Firefox add-on:

[http://www.downloadhelper.net/](http://www.downloadhelper.net/)


Also theres a Linux version of Mozilla Miro.

---

### Post by suitedaces on 2009-08-31
if you're comfortable with the command line, try youtube-dl (sudo apt-get install youtube-dl ) to use it after installation, simply type "youtube dl www.youtube.com/whateverthevideocodeis"

---

### Post by MrWES on 2009-08-31
Nice!

---

### Post by CleverTrick on 2009-08-31
Make sure you have the latest version of the Firefox Download Helper if you use it. My older version couldn't grab the videos. The new one works nicely, though.

---

### Post by suitedaces on 2009-08-31
Though I personally prefer going into the temp file (/tmp) after the video is fully loaded, and simply dragging the file across into my videos folder

---

### Post by advocate 21 on 2009-08-31
Theres also a bookmark for that. [http://googlesystem.blogspot.com/2008/04/download-youtube-videos-as-mp4-files.html](http://googlesystem.blogspot.com/2008/04/download-youtube-videos-as-mp4-files.html)
scroll down from the site and rightclick "get youtube video" and say bookmark page. when you like a youtube vid, you can click the bookmark and itll download the vid for you on the spot, no interrogation.

---

### Post by earthpigg on 2009-08-31
> **suitedaces said:**
> Though I personally prefer going into the temp file (/tmp) after the video is fully loaded, and simply dragging the file across into my videos folder

i dig around in the ~/.mozilla folder, myself :D

---

### Post by sandyd on 2009-08-31
flashgot ;)

---

### Post by Tutigan on 2009-08-31
Have you tried downloadyoutubevideo.org? (I believe that's what it is)

---

### Post by dvlong on 2009-08-31
I'm using the Firefox add-on "flashgot" - really like it.

---

### Post by Cope57 on 2009-09-01
Just use bash...

```
#!bin/bash
bu="http://youtube.com/get_video.php?";mkdir -p ~/YouTube;cd ~/YouTube;read -p "YouTube url? " ur;read -p "Name? " nv
wget ${ur} -O /tmp/y1;uf=${bu}`grep player2.swf /tmp/y1 | cut -d? -f2 | cut -d\" -f1`;wget "${uf}" -O /tmp/y.flv
ffmpeg -i /tmp/y.flv -ab 56 -ar 22050 -b 500 -s 320x240 ${nv}.mpg;rm /tmp/y.flv; rm /tmp/y1;rm gmon.out; exit 
```

```

#!bin/bash
bu="http://youtube.com/get_video.php?"
mkdir -p ~/YouTube
cd ~/YouTube
read -p "YouTube url? " ur
read -p "Name? " nv
wget ${ur} -O /tmp/y1
uf=${bu}`grep player2.swf /tmp/y1 | cut -d? -f2 | cut -d\" -f1`
wget "${uf}" -O /tmp/y.flv
ffmpeg -i /tmp/y.flv -ab 56 -ar 22050 -b 500 -s 320x240 ${nv}.mpg
rm /tmp/y.flv
rm /tmp/y1
rm gmon.out
exit 
```

Either one works.

---

### Post by Ms_Angel_D on 2009-09-01
Have you tried PWN youtube, No downloading of softwares or add on's required and easy as pie :D

[http://deturl.com/](http://deturl.com/)

---

### Post by andrew.46 on 2009-09-01
Hi MrWes,

> **MrWES said:**
> Nice!

The repository version is a little dated, if you were keen you could try:
```

sudo apt-get remove youtube-dl
sudo wget http://bitbucket.org/rg3/youtube-dl/raw/2009.08.08/youtube-dl -O /usr/local/bin/youtube-dl
sudo chmod +x /usr/local/bin/youtube-dl
```

and then try a few youtube videos using the *-b* option...

All the best,

Andrew

---

### Post by anujpathania on 2009-09-01
FlashGot in Firefox Addons

or

MIRO 


Both works just fine.

---

### Post by hyperdude111 on 2009-09-01
Firefox addons have LOADs chose your favourite.

But an easy way of keeping a video on youtube is after the whole video is loaded go to your /tmp/ directory and the file will be there named as FLASHxxxx.flv you can also use that.

---

### Post by MrWES on 2009-09-01
> **andrew.46 said:**
> Hi MrWes,



The repository version is a little dated, if you were keen you could try:
```

sudo apt-get remove youtube-dl
sudo wget http://bitbucket.org/rg3/youtube-dl/raw/2009.08.08/youtube-dl -O /usr/local/bin/youtube-dl
sudo chmod +x /usr/local/bin/youtube-dl
```

and then try a few youtube videos using the *-b* option...

All the best,

Andrew

Will do -- I love being keen :)

As always,
Thanks

---

