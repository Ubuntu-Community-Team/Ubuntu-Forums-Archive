---
title: "Downloading youtube vids"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by John Hale on 2009-03-13
I used to be able to do this in windows but have yet to figure a way in linux I wish I understood this os I feel a right plank keep posting here

---

### Post by RedSingularity on 2009-03-13
download the plugin for firefox.

---

### Post by houbysoft.xf.cz on 2009-03-13
1) Copy video URL address
2) go to [http://houbysoft.com/youtube](http://houbysoft.com/youtube)
3) Paste the address into the box and download the video
4) Play it (it's a FLV file, you can play it for example in mplayer, VLC...)

---

### Post by roberto.eiberle on 2009-03-13
get downloadhelper for firefox and read easy instructios

---

### Post by John Hale on 2009-03-13
houbysoft can't make it work click download now it just sends me around in a circle, Shadow121 which plug in it was real player in windows and when I down load that i get a *.bin file I don't have a clue what to do with its like when I want to install something and I get a *.bz2 or other file and just don't know what or how to do thing I must be thick or too used to windows easy life anyway!

---

### Post by crjackson on 2009-03-13
> **roberto.eiberle said:**
> get downloadhelper for firefox and read easy instructios

+1

---

### Post by kaivalagi on 2009-03-13
Install "clive" from the repos, it is a command line tool for downloading from youtube

Visit the page where the video is, copy the url and do something like this in a terminal:

```
cd /path/where/you/want/the/video/stored
clive http://www.youtube.com/watch?v=wMroYWXfuJo
```

---

### Post by houbysoft.xf.cz on 2009-03-13
For using "my" method, you probably have to right click the download now button and then click "save target as".

+1 to clive however, I didn't know about it :)

---

### Post by lovinglinux on 2009-03-13
You can also install [Greasemonkey]("https://addons.mozilla.org/en-US/firefox/addon/748") extension for Firefox. There is a GM script that adds a link in the video page, so you can download it. The best part is that you can download the video as mp4, with better definition.

I guess the name of the script is "Download YouTube Videos as mp4"

---

### Post by andrew.46 on 2009-03-13
Hi,

This may be as good a time as any to pimp my guide for downloading the new high definition youtube videos:

Mini guide: Download high quality youtube vids suitable for your phone ...
[http://ubuntuforums.org/showthread.php?t=1037760](http://ubuntuforums.org/showthread.php?t=1037760)

[B][COLOR="Red"]================================================
Warning: Use of the commandline is required!!!!
================================================[/COLOR][/B]

Andrew

---

### Post by John Hale on 2009-03-13
Now all i need to do is convert flv to mpeg and I'm home and dry as I've downloaded the vids

---

### Post by Gillen on 2009-03-13
Hi,

This might be of interest, youtube flv videos are temporarily saved in your file system tmp folder. When the video finishes it stays in this tmp folder untill you close Firefox or start watching another video, so when you have finished watching a video just copy it out of the tmp folder onto your desktop, no need for plugins.
Winff might help convert the flv file, though I am not sure it will work with youtube flv's.

---

### Post by andrew.46 on 2009-03-13
Hi John,

> **John Hale said:**
> Now all i need to do is convert flv to mpeg and I'm home and dry as I've downloaded the vids

Can I ask what you are converting for? A specific player, software application etc?

Andrew

---

### Post by John Hale on 2009-03-13
Andrew, basically it's so that I can play them in a dvd player as either a video cd/dvd, found a site that downloaded youtube to *.mp4 only to find K3b needs mpeg 2 argh!!!!!!!!

---

### Post by lovinglinux on 2009-03-13
Avidemux can convert the files

---

