---
title: "Help! No media player works..."
date: 2009-06-07
forum: New to Ubuntu
---

### Post by melrokz on 2009-06-07
My friend is running Ubuntu 9.04 with a ATI mobility radeon hd 2600 card + 2 gb RAM. VLC player does not work properly when installed through the repos. It displays the video in a new window called 'xvideo' The video output setting is 'opengl'

Also, upon installing mplayer, the video plays only in a small window and does not work fullscreen! Only a black screen comes sometimes...

I have installed the 'fglrx' binary ATI drivers for him. Could this be due to this driver that uses OpenGL?

Or, will there be any other media player out there that works? He prefers a player with video window inbuilt (like vlc)

---

### Post by melrokz on 2009-06-07
Plz help me! Anything...

---

### Post by jbruced on 2009-06-07
Does vlc work except only in a separate screen?

If so, you can change its settings to keep the controls with the screen.

---

### Post by kansasnoob on 2009-06-07
To get to my multi-media happy place in Ubuntu I always begin by installing the Medibuntu repo:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

as shown go to Terminal and run the following commands:

```
sudo wget http://www.medibuntu.org/sources.list.d/jaunty.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

then:

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

and:

```
sudo apt-get install libdvdcss2
```

and (assuming this is 32 bit, if not refer to the Medibuntu link above):

```
sudo apt-get install w32codecs
```

and (Medibuntu repo not needed for this but you want it anyway):

> sudo apt-get install ubuntu-restricted-extras

NOTE: substitute kubuntu or xubuntu with ubuntu if that's what you're running.

Now lets close the terminal and move to Synaptic Package Manager. Click on "Search" (not Quick Search or Rebuilding Search) and type **flash**. Then scroll through and be certain that "gnash", "swfdec-gnome", or "swfdec-mozilla" are NOT installed. If any of them are mark them for "complete removal".

Next type **vlc** in the Search bar. Be certain that mozilla-plugin-vlc, vlc, vlc-nox, and vlc-plugin-pulse ARE installed. If not mark them for installation.

Now type **totem** into the Search bar. Be certain that totem, totem-common, totem-gstreamer, totem-mozilla, totem-plugins, totem-plugins-extra, and totem-xine ARE installed. Again, if any are not then mark them for installation.

Of course then you'll want to click on Apply and follow the screen prompts to complete the installation.

I don't care much for mplayer but there are many different front-ends for it. Of them all I prefer smplayer.

I much prefer totem-xine (which will show up separately now in Sound & Video) for DVD playback.

As far as flash in Firefox I also always install the latest Flashblock to improve overall performance by going to Tools > Add-ons > Get Add-ons.

Of course there are many, many options. The sticky **Comprehensive Multimedia & Video Howto** here is a good place to start:

[http://ubuntuforums.org/forumdisplay.php?f=334](http://ubuntuforums.org/forumdisplay.php?f=334)

Everyone finds there own favorite combination.

---

### Post by kansasnoob on 2009-06-07
Oops! "sudo apt-get install ubuntu-restricted-extras" should have been in code tags like this:

```
sudo apt-get install ubuntu-restricted-extras
```

rather than guote tags. Sorry.

---

### Post by pous on 2009-06-14
> **kansasnoob said:**
> To get to my multi-media happy place in Ubuntu ...

thanks, i was having lots of trouble with certain video files online... and finally solved it.

---

