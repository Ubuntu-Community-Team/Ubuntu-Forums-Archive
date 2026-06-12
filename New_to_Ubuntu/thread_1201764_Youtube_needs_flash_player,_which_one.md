---
title: "Youtube needs flash player, which one?"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by sunwatt on 2009-07-01
Choices are YUM for Linux, tar.gz, rpm and at the bottom .deb Ubuntu 8.04+

Thanks

Jim

---

### Post by buzzmandt on 2009-07-01
follow this guide and you can't go wrong:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by sunwatt on 2009-07-01
Thanks - I followed the instructions and the auto method worked. Now I can play mp3's!!!

Update manager started up, and is dl'ing a ton of stuff. 148 packages.

Its like you are telling a blind person what to do, I'm dos plain stupid, but I got the terminal thing done, and the music works now just from doing the 1st step. ([Medibuntu]("http://www.medibuntu.org/") repository.)

next Ill check you tube and see what happens.

No doubt I need to keep reading the link you sent me.... oh the pain.

BTW, this laptop has been an XP PC since 2004, its a Dell Inspiton 9100. 

It was totally infected by WiniBlue, locked up.

I just this morning installed 9.04 right on top of all that mess.

I can browse with Firefox, I imported my bookmarks, I can send email, I can play music.

Next is youtube.

I love Linux, never going back to Windoze.

Thanks everyone.

Oh the joy!

Jim

---

### Post by sunwatt on 2009-07-01
OK, I did the

 sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update

Music plays now, my mp3's. But when I use the test link  

[http://www.apple.com/trailers/](http://www.apple.com/trailers/)

The audio plays but no video. Same thing on youtube, "needs latest flash player installed".

Ive rebbooted, and installed Wine, and Ktorrent, rebooted again, and still no youtube videos.

I was told to never download off webpages, only use Synaptic. So I didnt dl any of the linux choices offered by Adobe.

Any suggestions on getting web videos to play?

This morning my laptop was infected and frozen, this afternoon Im cruising with Ubuntu 9.04 so if it takes me afew days to get youtube, I wont complain.

thanks

Jim

---

### Post by SunnyRabbiera on 2009-07-01
For flash you cant go wrong with the .deb installer.
For Ubuntu .deb is sort of like .exe on windows.
The hardy build is good for all versions of ubuntu Hardy and up.
For the other kinds of videos you may find on the net you may need more repositories and packages.
A good start is to install the Ubuntu restricted extras package:
[http://packages.ubuntu.com/search?keywords=ubuntu+restricted+extras&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=ubuntu+restricted+extras&searchon=names&suite=all&section=all)

Also medibuntu helps:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Medibuntu is a repository containing codecs that have legal issues behind them that prevent them from being shipped by Ubuntu by default.
But if you need extra help installing packages, using repositories cant go wrong here:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by sunwatt on 2009-07-01
Thanks for the reply, your saying I shud install .deb Ubuntu 8.04+ ? From the Adobe site youtube takes me to?

Today I installed Wine and Ktorrent, from Synaptic. Ive never dl'd off a website and installed before

Just want to be real sure. Today is my 1st day doing this stuff

thanks

Jim

---

### Post by skierkyles on 2009-07-01
> **sunwatt said:**
> Thanks for the reply, your saying I shud install .deb Ubuntu 8.04+ ? From the Adobe site youtube takes me to?

Today I installed Wine and Ktorrent, from Synaptic. Ive never dl'd off a website and installed before

Just want to be real sure. Today is my 1st day doing this stuff

thanks

Jim

Downloading it from the Adobe site should work just fine, just download it and double click the .deb file on your desktop.

---

### Post by hyperdude111 on 2009-07-01
An easier way to get all the codecs without mediabuntu is this command.

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by SunnyRabbiera on 2009-07-01
> **sunwatt said:**
> Thanks for the reply, your saying I shud install .deb Ubuntu 8.04+ ? From the Adobe site youtube takes me to?

Today I installed Wine and Ktorrent, from Synaptic. Ive never dl'd off a website and installed before

Just want to be real sure. Today is my 1st day doing this stuff

thanks

Jim

You could install it from the adobe site but using the Ubuntu restricted package also works about the same way though the restricted extras package does give you more then just flash.

> **hyperdude111 said:**
> An easier way to get all the codecs without mediabuntu is this command.

```
sudo apt-get install ubuntu-restricted-extras
```


Yes though the medibuntu repositories come in handy as not all codecs are installed with the restricted extras package.

Anyhow there is a slight learning curve with using Ubuntu but lucky for you there is plenty of documentation and packages out there to help you get pretty much all you need for multimedia.

---

### Post by sunwatt on 2009-07-01
People, we got utube!

You'all are the best

THANK YOU

Jim

---

### Post by buzzmandt on 2009-07-01
> **sunwatt said:**
> OK, I did the

 sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update

Music plays now, my mp3's. But when I use the test link  

[http://www.apple.com/trailers/](http://www.apple.com/trailers/)

The audio plays but no video. Same thing on youtube, "needs latest flash player installed".

Ive rebbooted, and installed Wine, and Ktorrent, rebooted again, and still no youtube videos.

I was told to never download off webpages, only use Synaptic. So I didnt dl any of the linux choices offered by Adobe.

Any suggestions on getting web videos to play?

This morning my laptop was infected and frozen, this afternoon Im cruising with Ubuntu 9.04 so if it takes me afew days to get youtube, I wont complain.

thanks

Jim

I don't think you followed the rest of that installation guide or this post would not have been posted.  Find the version of *ubuntu you have and execute the code.  You'll have every codec you'll ever need.

The installation part of the guide is as follows:
> Note: Those of you installing Sun Java will be asked to accept an end-user license agreement (EULA) before the installation of the Sun Java packages begins. Press the tab key on your keyboard (above the caps lock key), followed by the enter key to accept the EULA and complete the installation.

32-Bit Ubuntu Users:

sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar

32-Bit Kubuntu Users:

sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree libk3b2-extracodecs libmp3lame0 libtunepimp5-mp3 libxine1-ffmpeg non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar

32-Bit Xubuntu Users:

sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar

64-Bit Ubuntu Users:

sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs ia32-sun-java6-bin icedtea6-plugin libmp3lame0 non-free-codecs openjdk-6-jre unrar

64-Bit Kubuntu Users:

sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree ia32-libs ia32-sun-java6-bin icedtea6-plugin libk3b2-extracodecs libmp3lame0 libtunepimp5-mp3 libxine1-ffmpeg non-free-codecs openjdk-6-jre unrar

64-Bit Xubuntu Users:

sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs ia32-sun-java6-bin icedtea6-plugin libmp3lame0 non-free-codecs openjdk-6-jre unrar



---

### Post by sunwatt on 2009-07-03
> **hyperdude111 said:**
> An easier way to get all the codecs without mediabuntu is this command.

```
sudo apt-get install ubuntu-restricted-extras
```
I entered that and now I lost vlc audio. And Totem will not play. Before totem played the audio, but not the video.

But vlc was working till I entered   
sudo apt-get install ubuntu-restricted-extras

---

### Post by sunwatt on 2009-07-03
> **buzzmandt said:**
> I don't think you followed the rest of that installation guide or this post would not have been posted.  Find the version of *ubuntu you have and execute the code.  You'll have every codec you'll ever need.

The installation part of the guide is as follows:
OK, I pasted this into terminal

32-Bit Ubuntu Users:

sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar


Now VLC plays audio and video again!  (glx output) Totem plays audio but no video.

Gnome plays avi's!!  Thats am improvement !!  No Totem, buy we got Gnome Media Player and VLC working great!

And yes, utube still plays!

I got it recovered a little, time to go to bed, before I do more harm

Thanks

Jim

---

