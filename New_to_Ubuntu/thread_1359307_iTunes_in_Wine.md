---
title: "iTunes in Wine"
date: 2009-12-19
forum: New to Ubuntu
---

### Post by Captainflowers91 on 2009-12-19
So I installed the latest version of Wine for Ubuntu 9.10. Anyway, is there anywhere to download a later version of iTunes for Ubuntu? I have an iPod classic and it won't run on the older versions. I already have GTKPod, I just want to be able to play my itunes videos in Ubuntu

---

### Post by Puck7 on 2009-12-19
Looking at the wine-hq.org [page of iTunes]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=18308"), it seems that the latest version just doesn't work.

Have you seen [the official doc]("https://help.ubuntu.com/9.10/musicvideophotos/C/music-portable.html") page from the ubuntu site? Did Banshee work?

---

### Post by Norm24 on 2009-12-19
Maybe try Sonbird with the ipod plugin?

---

### Post by Bigtime_Scrub on 2009-12-19
gtkpod, amarok, and Rhythmbox will all transfer video to the ipod classic as long as you convert the video into mp4 format. As far as I know, itunes doesn't work in linux at all. 



What generation ipod do you have? If it is 5th gen or older I believe you can convert the video with vlc. 6th gen I had to jump through a few hoops. 

Use Avidemux, then you need to set the audio as FACC.

Also see this old thread of mine. 

[http://ubuntuforums.org/showthread.php?t=814776](http://ubuntuforums.org/showthread.php?t=814776)

---

### Post by Extract_Here on 2009-12-19
I just installed songbird and its great. It practically looks like itunes. Itunes will never run in linux. Apple is so concerned about keeping their software closed source. the only reason it runs in windows is because MS paid them to get that.

---

### Post by Captainflowers91 on 2009-12-19
Well I tried installing Songbird, but it won't start, idk

---

### Post by Extract_Here on 2009-12-19
thats because its a tar.gz file and you have to make it run. do you need info?

---

### Post by akoskm on 2009-12-19
> **Captainflowers91 said:**
> Well I tried installing Songbird, but it won't start, idk

Do not play with additional things like compiling and running zillion things. It doesn't worth, and it's unnecessary... Try to find something in the repositories like banshee...

---

### Post by sandyd on 2009-12-19
run this....
```

gksudo gedit /etc/apt/sources.list
```
add this on a blank line at the bottom of the file
```

deb [http://ppa.launchpad.net/songbird-daily/ppa/ubuntu](http://ppa.launchpad.net/songbird-daily/ppa/ubuntu) karmic main 
deb-src [http://ppa.launchpad.net/songbird-daily/ppa/ubuntu](http://ppa.launchpad.net/songbird-daily/ppa/ubuntu) karmic main 
```
save, close and run
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 5719E347
sudo apt-get update
sudo apt-get install songbird
```

---

### Post by Captainflowers91 on 2009-12-23
Ok, thanks, that got songbird running. Wow, it looks really nice for a free open-source music player!

---

### Post by dertdamb on 2010-01-20
How can I get iPod support? The plugin is no longer available for download.

---

### Post by celticbhoy on 2010-01-30
> **dertdamb said:**
> How can I get iPod support? The plugin is no longer available for download.

Yeah, you will need to get a songbird version prior to 1.4. If you un-install the version you have, and then check out getdeb's legacy page I think they have a 1.2 version there.

---

### Post by freak42 on 2010-01-30
> **Extract_Here said:**
> ... the only reason it runs in windows is because MS paid them to get that.

complete nonsense!

---

