---
title: "shn to mp3 conversion"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by hmich176 on 2008-12-20
I have many shn files.  They're taking up too much space at this point and I'd like to convert them to mp3s.  

What would be the best program to use and how should I go about installing it.

---

### Post by Elfy on 2008-12-20
[http://adventuresinswitching.blogspot.com/2008/04/convert-shn-shorten-to-mp3-or-flac-in.html](http://adventuresinswitching.blogspot.com/2008/04/convert-shn-shorten-to-mp3-or-flac-in.html)

Try that although personally I would convert to a different format than mp3

---

### Post by hmich176 on 2008-12-20
I'd go with flac myself, but space is an issue at the moment.  I'll go with flac once I get a much larger hard drive (external or not).

---

### Post by Elfy on 2008-12-21
I would keep a copy of the shn then - you wouldn't want to compress them to mp3 and then chnage the mp3 to flac

---

### Post by hmich176 on 2008-12-21
That would defeat the purpose. As much as I don't want to encode in a lossy format, I have no choice due to space issues.  

I can always download the shns again later.

---

### Post by cozmicharlie on 2008-12-22
forestpixie provided a good link for you.  One of my tutorials ([http://ubuntuforums.org/showthread.php?t=739658&highlight=shn](http://ubuntuforums.org/showthread.php?t=739658&highlight=shn)) was referenced in the blog but I have learned more since I wrote it (I need to update it) so I thought I would provide more info for you.

As per handling shn, the first thing to do is install the shorten codec.  It is really very simple.
[LIST=1]
[*]In a terminal type or cut and paste the following:
```
wget http://www.etree.org/shnutils/shorten/dist/src/shorten-3.6.1.tar.gz
```
[*]untar the folder
```
tar xvf shorten-3.6.1.tar.gz
```
[*]change directories to the shorten-3.6.1 folder
```
cd shorten-3.6.1
```
[*]Install the package
[/LIST]
```
./configure
```
```
make
```
```
sudo make install

```
Thats all you need to install the codec.

Now to convert to mp3 you can so do it as described in the blog or I like to use either PACPL or SoundKonverter (yes it is kde but it works fine on gnome and it converts a wide variety of music files including shn).  Once you have all the codecs installed (install the gstreamer or lame for mp3 also) you can just install SoundKonverter from Synatpic and you are done.

PACPL is a great little script that converts a large number of formats and can integrate in Amarok.
To install PACPL, follow this tutorial ([http://ubuntuforums.org/showthread.php?t=712064&highlight=pacpl](http://ubuntuforums.org/showthread.php?t=712064&highlight=pacpl)).  It does have a lot of dependencies but if you follow the tutorial the script will install all of them for you.

If you want to play shn, then the best player is xmms.  You can follow this tutorial ([http://ubuntuforums.org/showthread.php?t=833164&highlight=shn](http://ubuntuforums.org/showthread.php?t=833164&highlight=shn)) to install from source or their are now a number of deb packages ([http://ubuntuforums.org/showthread.php?t=795242](http://ubuntuforums.org/showthread.php?t=795242)) available that make it real easy to install.

Good luck and enjoy.

---

