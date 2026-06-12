---
title: "VERY beginner. Want to play DVDs. Was told codec was missing....?"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by allflowersdie13 on 2009-09-26
Hi there,

Im so sorry for what Im sure is a very stupid question. I tried visiting the beginners guide ([http://ubuntuforums.org/showthread.php?t=766683&highlight=codec+vlc](http://ubuntuforums.org/showthread.php?t=766683&highlight=codec+vlc)) to this media but after running the quick and easy version and haven failed I find myself at an absolute loss.

My friend installed ubunu on my machine (Dell Inspiron 1501) not too long ago. Havent needed to watch dvds in a while so didnt realize there was problem.... 

But I was told to use VLC player so wala... we have a starting point. I texted him and he mentioned the codec or something was missing. SO when I try to play a dvd I get the small menu box and I get the main menu screen--yet once I cloick anything on the main menu the window disappears...

Once again I know this is a wicked stupid question. I just dont understand the forums yet. I feel like Ive been thrown into a foreign country ad I cant speak the language so need it broken down to its most simple components.

Thanks!

---

### Post by sukigenseki on 2009-09-26
open up a terminal and type this

sudo /usr/share/doc/libdvdread4/install-css.sh

(For legal reasons I imagine) playback of protected dvds is not enabled by default in the installation. Would do you more justice to look up why, but my best guess is the fact that it is a free distrobution that we use, and the software needed to play proprietary formats are usually not free. Don't quote me on it because I am not real well read on the subject, but either way this will let you play them. Good luck!

---

### Post by Mka on 2009-09-26
First include the medibuntu repositories by typing this on Terminal:
```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update
```

The, install these necessary stuff to play your DVDs:
```
sudo apt-get install libdvdcss2 libdvdread4 libdvdnav4
```

You should be able to play DVDs with Totem after this. Install VLC if you like it.

---

### Post by kansasnoob on 2009-09-26
First go to terminal and run:

```
sudo apt-get install ubuntu-restricted-extras
```

Then add Medibuntu:

```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update

```

Then:

```
sudo apt-get install libdvdcss2
```

If you installed i386 (32bit) then:

```
sudo apt-get install w32codecs
```

If it's 64bit:

```
sudo apt-get install w64codecs
```

---

### Post by kansasnoob on 2009-09-26
Oh, and be sure to restart Firefox afterwards!

---

