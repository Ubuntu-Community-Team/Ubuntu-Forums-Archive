---
title: "Ubuntu freezing"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by onlyf on 2008-12-21
Hi all
I am new to forums & this kind of thing. Please be patient with me.Had a really hard time trying to log on to this forum...my teenage son got it right. Have loaded Ubuntu 8.10 and loving it, except it has twice frozen on me, once in GUI & another in command prompt line. Have also not been able to change directories at command line. Could anyone please advise. I am a computer operator in a large company in which we do data & imaging using Unix servers, so I am sort of familiar with Unix commands & scripts but would certainly appreciate input from the forum. One other thing... does ver 8.10 include VLC in it's packages? Can't seem to find it.

---

### Post by ibizatunes on 2008-12-21
welcome , if you want to play restricted format do

```
sudo apt-get install ubuntu-restricted
```

and if you want to ```
sudo apt-get install vlc
```

[http://www.dailygyan.com/2008/11/10-things-you-should-do-immediately.html](http://www.dailygyan.com/2008/11/10-things-you-should-do-immediately.html)

Before you install did you check the cd image didnt have any faulty, and check memtest
Maybe ubuntu 8.04 will work better if you get lock ups, it been out for a 8months and has long term support, and had more bug fixed in it compared to ubuntu 8.10
But its up to you

---

### Post by Tomatz on 2008-12-21
If ubuntu freezes randomly its usually due to compiz (3d window manager). Run the folowing command to turn off compiz untill the next boot/logout.

```
metacity --replace
```


Leave the pc running for a few hours and give it some stress, if it doesn't freeze we will know the problem is compiz related. Then we can try to fix the issue.

;)

---

### Post by namdung on 2008-12-21
Hardy Heron 8.04.1 is a much stable version than 8.10. I got back to Hardy after some issues with Intrepid. 

Restricted software and codecs are not installed by default. So if you want to listen and watch proprietary audio/video formats then install GStreamer codecs from Add/Remove Software. Installing software from Synaptic Package Manager is easier.

---

### Post by onlyf on 2008-12-22
Thanks very much to you all. Will try out what you suggested.Did check the integrity of disk but did not do mem test.

---

