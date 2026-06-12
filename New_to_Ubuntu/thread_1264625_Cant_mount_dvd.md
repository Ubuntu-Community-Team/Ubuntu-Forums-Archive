---
title: "Cant mount dvd"
date: 2009-09-12
forum: New to Ubuntu
---

### Post by burnetbj on 2009-09-12
Hello people

I purchased a DVD on Ebay that is a burnt DVD (go figure) on how to rebuild a Shovelhead Motor. I cant get laptop to mount the disc, but it will play in my PS3. How could a person find the file type in Ubuntu, properties give me almost no information.

I have restricted extras installed dvdcss and read4 as well. Any ideas would be appreciated. Hauling a 32" tube tv a PS3 and cables out to the garage just wont cut it.I need to be able to watch the dvd and work on the bike at same time.

Thanks for your time

---

### Post by zman58 on 2009-09-12
> **burnetbj said:**
> Hello people

I purchased a DVD on Ebay that is a burnt DVD (go figure) on how to rebuild a Shovelhead Motor. I cant get laptop to mount the disc, but it will play in my PS3. How could a person find the file type in Ubuntu, properties give me almost no information.

I have restricted extras installed dvdcss and read4 as well. Any ideas would be appreciated. Hauling a 32" tube tv a PS3 and cables out to the garage just wont cut it.I need to be able to watch the dvd and work on the bike at same time.

Thanks for your time
Is this the very first time you are trying to view a DVD (movie) on your laptop with Ubuntu?

---

### Post by burnetbj on 2009-09-12
It might be actually I cant remember we have 3 laptops here amount many other devices.

I just tried the huge dvd playback tutorial in here......probably did more damage then good. i seen it wanted to remove stuff and add stuff in the same command alot inwhich i didnt know what it was ...heh

Anyhow I am assuming if the Ps3 can play it its a decoder issue of some kind. I seen a section in the tutorial to set region but was reading from other users that linux didnt seem to care from one region to the next. the DVD would be a US region.

Would be nice to get a $99.99 Ubuntu version out there that has all the purchased codecs and decoders you could shake a stick at. Sometimes this Free thing gets in the way of sanity. Just give me a Ubuntu version I can play media with and I can support the developers with cash. I get the free software but untill Linux has the ability to compete in the media department give us a purchase option and a chance to help finance the Free Developers.

I can play almost everything with the restricted installed but I see countless people having DVD issues

Thanks again for the help

---

### Post by ScoobyDan on 2009-09-12
> **burnetbj said:**
> ...Hauling a 32" tube tv a PS3 and cables out to the garage just wont cut it.I need to be able to watch the dvd and work on the bike at same time...

Why not work on the bike in your front room then? ;) :D

> **burnetbj said:**
> ...Would be nice to get a $99.99 Ubuntu version out there that has all the purchased codecs and decoders you could shake a stick at. Sometimes this Free thing gets in the way of sanity. Just give me a Ubuntu version I can play media with and I can support the developers with cash. I get the free software but untill Linux has the ability to compete in the media department give us a purchase option and a chance to help finance the Free Developers...

Have you tried [Linux Mint]("http://www.linuxmint.com/")?

---

### Post by zman58 on 2009-09-12
The reason I asked if it is the first time is that you want to make sure your hardware and the media you are trying to play can work together. I have had many DVD issues with burned media where the particular DVD drive could not reliably read the media which was burned in another DVD reader/writer. I have even had problems with my stand-alone DVD player in some cases trying to playback DVDs.

I have had success getting DVDs to playback in Ubuntu. I happen to be playing Office Volume 2 DVD currently in this system which is Ubuntu 8.04 LTS. I also was able to get Ubuntu 9.04 to successfully play DVDs.

You have to dig a little, but it does work.

 - Add gstreamer0.10-ffmpeg

 - Add gstreamer0.10-plugins-ugly

 - Add gstreamer0.10-plugins-bad

 - DVD playback. Add CSS (content scrambling system) using script:
   sudo /usr/share/doc/libdvdread4/install-css.sh
   
[https://help.ubuntu.com/9.04/musicvideophotos/C/video-dvd.html](https://help.ubuntu.com/9.04/musicvideophotos/C/video-dvd.html)

---

### Post by mapes12 on 2009-09-13
Try re installing ubuntu-restricted-extras via Synpatic and then cut and paste these Terminal commands to make sure you have everything possible to play DVD's: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

BTW what kind of bike is a Shovelhead? I have a 30 year old Yam XS 650 roadster - just restored it - mint!

---

