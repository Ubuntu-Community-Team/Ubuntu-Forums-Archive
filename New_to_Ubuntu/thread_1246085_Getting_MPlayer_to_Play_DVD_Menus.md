---
title: "Getting MPlayer to Play DVD Menus"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by todd1049 on 2009-08-21
I am trying to get DVDs to play on my system with Ubuntu 8.04.  I have tried all the things recommended in the "Comprehensive Multimedia & Video Howto" sticky, and have at least succeeded to the point where MPlayer will play a DVD.  However, it ignores the DVD menu, e.g. so you can choose episodes or subtitles, and my efforts to go the menu in MPlayer do not work.  MPlayer just plays the move straight away as soon as it is inserted.  How can I fix that?  Thanks for your help.

---

### Post by coldReactive on 2009-08-21
This often will happen on Linux actually. Try right-clicking the DVD Video output and going to root menu or title menu.

---

### Post by diablo75 on 2009-08-21
If you haven't done it already, you need to install the libdvdcss2 decoder package, contained in the Medibuntu repositories.  You can read more about the legal aspect of doing this here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

To install, click on Applications>Accessories>Terminal.  Then paste in the following text:

```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update
```

...and press enter.  Once it's finished, paste in this text:

```
sudo apt-get install libdvdcss2
```

Once that's done, check for updates once more and install them.  You should be able to play DVDs in their entirety using just about any media software you wish.

---

### Post by Nepherte on 2009-08-21
> **todd1049 said:**
> I am trying to get DVDs to play on my system with Ubuntu 8.04.  I have tried all the things recommended in the "Comprehensive Multimedia & Video Howto" sticky, and have at least succeeded to the point where MPlayer will play a DVD.  However, it ignores the DVD menu, e.g. so you can choose episodes or subtitles, and my efforts to go the menu in MPlayer do not work.  MPlayer just plays the move straight away as soon as it is inserted.  How can I fix that?  Thanks for your help.
Try this:
```
mplayer dvdnav://
```
This will tell mplayer to play the dvd navigation menu. You will need mplayer libdvdnav support though.

---

### Post by andrew.46 on 2009-08-21
Hi todd,

> **todd1049 said:**
> I am trying to get DVDs to play on my system with Ubuntu 8.04.  I have tried all the things recommended in the "Comprehensive Multimedia & Video Howto" sticky, and have at least succeeded to the point where MPlayer will play a DVD.  However, it ignores the DVD menu

As Nepherte mentions your copy of MPlayer needs to have support for DVD navigation compiled in and this is not the case with the repository MPlayer. Newer copies of MPlayer have vastly improved access to dvd menus and you can pick up such a copy by compiling it yourself or, probably a little easier, grabbing it from RVMs PPA along with a copy of his SMPlayer.

All the best,

Andrew

---

### Post by wwwookie on 2010-09-15
Hi Todd,

I hope you get a notification email and see this!

I have been using a newer version of mplayer compiled with dvdnav support from a subversion snapshot on their website, but still get problems with dvd menus  and subtitles. You might notice the dvd menu buttons with mplayer  come out as pale squares instead of text. this seems to be because the button's *background* is being shown rather than the button itself. This is not ideal, but the problem gets worse with subtitles, which are not shown at all when accessed from the menu.

While bugs like this seem to get  fixed quite quickly, I would recommend using the **Xine** media player instead. Xine is posibly not as robust as mplayer, but it can handle menus fine. It comes with two frontends: gxine and xine-ui. It is worth noting gxine seems to crash my window manager - so I would I would suggest using xine-ui.

```
sudo apt-get install xine-ui
```

should do the trick

Note:- The package name and the command are different: it uses the command **xine**, not **xine-ui**

Peace

---

### Post by philinux on 2010-09-15
Thread is a over a year old.
Closed. RIP

---

