---
title: "how to play mp3 songs and videos like avi,mp4, without having an internet connection?"
date: 2011-08-14
forum: New to Ubuntu
---

### Post by rayinferno on 2011-08-14
Hey guys

Im joined the world of ubuntu a few days back. I dont have an internet connection. Now I cant download the necessary codecs required to play files like .mp3, .avi, .mp4, .flv, .mkv, .mpeg etc. i mean the basic files generally required to run the audio and video files. Ive done a dual booting installation alongwith windows 7. Now if i have to run those files what would i have to do????

Please guys any kind of help is required! I totally dont have any clue! :(


so please HELP!

---

### Post by justifier on 2011-08-14
you will need an internet connection of some kind to get the codecs on there. you obviously have access to one as you are on here, and downloaded ubuntu. All you need to do is go to [http://packages.medibuntu.org/natty/index.html](http://packages.medibuntu.org/natty/index.html) and download the .deb files for the ones you need. I would recommend at least:

mencoder
mplayer
non-free-codecs
w32codecs
w64codecs

and any others there you want, why not download the lot and install  what you need. Just pop them onto a memory stick then on your ubuntu system, either double click on them or run the following in a terminal 

sudo dpkg -i <path to codec> 

Hope that helps a little.

---

### Post by akand074 on 2011-08-14
Download the ubuntu-restricted-extras package when you have an internet connection. Then you'll be able to run them fine without an internet connection. Ubuntu has the option in the installer to install those during the installation of Ubuntu, did you not check it?

---

### Post by rayinferno on 2011-08-14
thnx a lot Justifier.. i really appreciate it. :) I will do it..

---

### Post by rayinferno on 2011-08-15
> **akand074 said:**
> Download the ubuntu-restricted-extras package when you have an internet connection. Then you'll be able to run them fine without an internet connection. Ubuntu has the option in the installer to install those during the installation of Ubuntu, did you not check it?
@ akand074


no i didnt know about the packages sadly.. I checked it out. But there are a lot of stuffs and to be very frank everything is looking kinda gibberish to me! I wish i knew which packages to install or how to know which are the right packages that im looking for??

---

### Post by akand074 on 2011-08-15
It's one package that installs everything you need.

---

### Post by robgraves on 2011-08-15
open a terminal and just type in:

 sudo apt-get install ubuntu-restricted-extras

enter your password and let it do it's thing, then you're done.

:guitar:

---

### Post by sandyd on 2011-08-15
You might also want to install Medibuntu (dvd playing & such).

You can install Medibuntu by going to Applications -> Accessories -> Terminal, and typing

```

#add Medibuntu
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

sudo apt-get install app-install-data-medibuntu apport-hooks-medibuntu

#restricted codecs, dvd drm decrypter, vlc media player, ffmpeg restricted, mplayer, w64/32codecs, gstreamer ugly
sudo apt-get install libavcodec-extra-52 libavdevice-extra-52 libavfilter-extra-1 libavformat-extra-52 libavutil-extra-50 libdvdcss2 vlc libpostproc-extra-51 mplayer non-free-codecs gstreamer0.10-plugins-ugly

```

Ive taken the liberty of adding almost every codec that I know about. They may be restricted in your country, so you might wanna check. But then again, they obviously aren't gonna come knocking on your door and arresting you for downloading the restricted codecs...

If your confused about the codecs & multimedia & Medibuntu on linux, check out NixiePixel -> [http://www.youtube.com/watch?v=NT7urt5UcQg](http://www.youtube.com/watch?v=NT7urt5UcQg)

She has some nice vids for those starting linux.

P.S. nothing shows up in the terminal when you type your password.

---

### Post by anieruddha on 2011-08-16
google, download & install. "vlc offline installer".

I found one link :
[http://rapidshare.com/files/222292699/VLC_offline_installer.tar.gz](http://rapidshare.com/files/222292699/VLC_offline_installer.tar.gz)

---

