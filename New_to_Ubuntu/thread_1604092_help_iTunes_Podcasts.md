---
title: "help iTunes Podcasts"
date: 2010-10-23
forum: New to Ubuntu
---

### Post by ianb72 on 2010-10-23
I swapping my main pc over to Ubuntu but I want to import my Tight Lines Podcast's that I've downloaded on my laptop on to my main pc with Ubuntu, can this be done?

I have transferred the files over to the  Home/Music Folder and tried importing all of the files in to Rhythmbox but they don't appear!

Hope I've explained it ok??
Ian

---

### Post by ivarn on 2010-10-23
In Rythmebox, go to Podcast, and add the RSS link for the podcast you want to hear.
If you don't have the rss link you'll find it on their website. When a new episode of the show is out, open up rythmebox and go to the podcasts section and click update.
If you listen to more then one podcast, you should go check out podcastalley.com.
Not as good as iTunes's podcast list but works fine.

---

### Post by ianb72 on 2010-10-23
The podcasts are already saved on my main pc (Ubunutu PC), I just copied them over from my laptop (windows laptop).

I have set up the link to download the new podcasts, but I wanna watch the ones I have already downloaded in Windows iTunes on my Ubuntu PC

---

### Post by ianb72 on 2010-10-24
So does anyone know how I can play and display all the Tight lines fishing podcasts which I have already downloaded on my windows laptop, on my main Ubuntu PC?

---

### Post by ubuntu27 on 2010-10-24
1) Launch iTunes

2) Click on the Podcast icon in the Source area on the left side of iTunes

3) Goto …

File > Export Song List

In the dialog box that appears select OPML from the formats drop down menu near the bottom of the window. Don’t forget to name your opml file and make sure there is a .opml extension on it.

5) Click save & your done!


NOW you can import OPML to your favorite podcast client


[http://www.ekoob.com/how-to-import-itunes-podcasts-to-rhythmbox-music-player-10564/](http://www.ekoob.com/how-to-import-itunes-podcasts-to-rhythmbox-music-player-10564/)

[http://goinglinux.com/articles/Subscribe.html](http://goinglinux.com/articles/Subscribe.html)

[http://www.linux.com/archive/feature/138031](http://www.linux.com/archive/feature/138031)

---

### Post by ianb72 on 2010-10-24
> **ubuntu27 said:**
> 1) Launch iTunes

2) Click on the Podcast icon in the Source area on the left side of iTunes

3) Goto …

File > Export Song List

In the dialog box that appears select OPML from the formats drop down menu near the bottom of the window. Don’t forget to name your opml file and make sure there is a .opml extension on it.

5) Click save & your done!


NOW you can import OPML to your favorite podcast client


[http://www.ekoob.com/how-to-import-itunes-podcasts-to-rhythmbox-music-player-10564/](http://www.ekoob.com/how-to-import-itunes-podcasts-to-rhythmbox-music-player-10564/)

[http://goinglinux.com/articles/Subscribe.html](http://goinglinux.com/articles/Subscribe.html)

[http://www.linux.com/archive/feature/138031](http://www.linux.com/archive/feature/138031)


[B]That only does the Podcast feeds, I know how to do that.

What I have done is copied all the saved iTunes podcast's from my Windows laptop on the the Music folder of my Ubuntu PC, but how do I get them to be displayed in Rhythmbox  so I can just pick out what I want to watch, withOUT downloading them all again??[/B]

---

### Post by ArgusVision on 2010-10-24
Where are they currently located? and what file type are they?

You say you want to "pick out what you want to **watch**" they aren't videos are they?
I hope that doesn't sound like too dumb a question, but I don't want to assume anything.

---

### Post by ianb72 on 2010-10-24
> **ArgusVision said:**
> Where are they currently located? and what file type are they?

You say you want to "pick out what you want to **watch**" they aren't videos are they?
I hope that doesn't sound like too dumb a question, but I don't want to assume anything.

They are located on the Ubuntu PC at **/home/ian/music** and they are **mp4** and **m4v** file formats

Yeah they are video's of the Tight Lines fishing programs from Sky Sports

---

### Post by ArgusVision on 2010-10-24
I think your root problem is that rythmbox doesn't handle video. It's an audio only player. You'll want to use mplayer, vlc or another video player to watch those.
If you use mplayer, you'll want to make sure you have the proper codecs.
You may need to enable the medibuntu repository to fetch them.

You can find the medibuntu repo, and instructions here.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

