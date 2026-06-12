---
title: "[SOLVED] How do I get movies and view them?"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by greenleaves123 on 2008-12-26
I did a bit of research on this and discovered there is FrostWire which is like LimeWire.

I downloaded FrostWire. I tried downloading a movie but I couldn't get it to play.

I have the Totem Movie Player.

There are different files on FrostWire, mp4, mpg, mov and avi. Does it matter which ones I download?

Here is some info about my system:

Dell Inspiron Mini 9
Ubuntu 8.04 (Hardy)
Memory 883.2MB
Intel Atom 1.60GHz
Disk space 23.7GB

I know I don't have much harddrive. I bought this SDHD card that holds 16GB. I don't play on storing tons of movies, just maybe a couple, enough for a longish flight on a plane. 

I don't know what is wrong. I am willing to pay for movies if I need too, but I don't even know where to go to get them.

How do I get movies and play them?

---

### Post by dmillerw on 2008-12-26
Have you installed the video codecs?

---

### Post by greenleaves123 on 2008-12-26
I don't know. My netbook came with everything pre-installed. How do I find out and if I don't have them, how do I get them?

---

### Post by dmillerw on 2008-12-26
When you start Totem, it should prompt you to install them, you may also want to try installing VLC.

---

### Post by greenleaves123 on 2008-12-26
Totem doesn't prompt me to install anything when I start it. Is VLC another video player?

Do I need two? I don't want to download unnecessary applications.

---

### Post by dmillerw on 2008-12-26
If Totem doesn't prompt you for anything, you probably already have the codecs and its the video.

VLC is a media player that doesn't require codecs, it might be worth a try if you want.

---

### Post by nhasian on 2008-12-27
yes I prefer VLC.  easy to install from a terminal type:

```
sudo apt-get install vlc
```

if you wish to use totem you'll need to install the codecs by enabling medibuntu repo:

Ubuntu 8.10 "Intrepid Ibex":

```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

Ubuntu 8.04 "Hardy Heron":

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

Then, add the GPG Key:
```

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

now you can install the video codecs with:

```
sudo apt-get install w32codecs
```

---

### Post by bodhi.zazen on 2008-12-27
See here :

[Ubuntu Linux play encrypted DVDs]("http://www.cyberciti.biz/faq/howto-ubuntu-linux-playback-dvd/") 

If you have problems with sound, in preferences, use the OSS driver.

---

### Post by nhasian on 2008-12-27
bodhi.zazen, actually I left out the instructions for dvd playback on purpose because I thought netbooks didnt come with cd/dvd drives.  Then i remembered you could always attach an external one hah

---

### Post by LowSky on 2008-12-27
um since when is it cool to tell someone how to watch illeagally downloaded movies? NOT cool. I'm mean i'm not for the RIAA or anything but telling how to watch his illeagal movie that he got from some P2P is like giving a guy a bullet for a gun

btw

```
sudo apt-get install ubuntu-restricted-extras 
```

That should get nearly any movie you need to work

---

### Post by greenleaves123 on 2008-12-27
Thanks a lot everyone! I really don't mind paying for movies, but I don't know where to find good legal movies to buy. I read that itunes doesn't work with Ubuntu and some other sites I searched mostly have soft core porn. LOL They don't have the Hollywood hits. 

I would rather pay for movies actually, but I don't have an external optical drive. That plus I don't have any DVDs currently.

---

### Post by evilkastel on 2008-12-27
Oh... if you seek peace of mind you migh buy the dvd of the movie you downloaded, so you'll be in a gray area. I do not mind what are you using the codecs for, so, i believe most of was there to be said in the matter of playing movies on ubuntu has been said. good luck.

---

### Post by linux_tech on 2008-12-27
Some decent video players are:
totem
VLC
Banshee

You may also want to try
beep-media-player

There are alot of good recommendations here as well-
[http://www.ubuntugeek.com/ubuntu-media-players-overview.html](http://www.ubuntugeek.com/ubuntu-media-players-overview.html)

---

### Post by greenleaves123 on 2008-12-27
Thanks, buying the movies is a great idea. 

I tried downloading and installing the xine thing, but it didn't work, it said it couldn't be found or something.

Then I installed the Ubuntu restricted extras and it worked. I don't know if I can get movies to play yet as I've deleted the movie I did download. I'll need to download some movie again.

I'll get back to you about if it works or not. Thanks!

---

### Post by linux_tech on 2008-12-27
Here is a link for playing dvds in ubuntu 8.1-
[https://help.ubuntu.com/8.10/musicvideophotos/C/video.html#video-dvd](https://help.ubuntu.com/8.10/musicvideophotos/C/video.html#video-dvd)

---

### Post by bodhi.zazen on 2008-12-27
> **LowSky said:**
> um since when is it cool to tell someone how to watch illeagally downloaded movies? NOT cool.

I missed that, you are correct. I thought this thread was about playing DVD that one had purchased.

Now that you have brought that detail to my attention I will close this thread.

The OP question has been asked and answered and NO we do not support pirating software, music, or movies.

---

