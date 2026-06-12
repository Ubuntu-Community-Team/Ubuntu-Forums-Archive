---
title: "What Happened to WMA?"
date: 2010-02-26
forum: New to Ubuntu
---

### Post by Martin Marshalek on 2010-02-26
So I just got done reinstalling Ubuntu, updating, installing drivers, restoring backups, and installing updates from non-Ubuntu repositories (namely, flash64 and Firefox 3.6). When I went to reward myself with some music I just restored, I found that it wouldn't play in Totem or Rhythmbox. I have installed all the of gstreamer plugins that I normally use bad, ugly, their multiverse variants, and ffmpeg yet it complains that a "Windows Media Audio 9 Decoder is required." These files are 256kbps bit rate and there are about 3GB worth of them. Is there another codec I need to install or am I up the creek without a paddle here?

---

### Post by Locke_99GS on 2010-02-26
[http://www.medibuntu.org](http://www.medibuntu.org)

---

### Post by Martin Marshalek on 2010-02-26
Thanks, until now I only used Medibuntu for DVD stuff but this works too. Just curious though, does the w64codecs package only work with xine or will it integrate with gstreamer as well?

---

### Post by Martin Marshalek on 2010-02-26
I installed the w64codecs and nothing happened. Does that mean they don't include wma also?

---

### Post by Martin Marshalek on 2010-02-26
Okay, so I decided to list the packages I installed because this seems to be a non issue for nearly everyone.

Gstreamer: bad, bad-multiverse, ugly, ugly-multiverse, and ffmpeg (these as opposed to those installed by default and their dependencies)

I don't want to use the restricted extras packages because I have no need to for microsoft fonts or the 32 bit wrapped flash plugin, but I have installed every multimedia codec from it's dependency list. I also tried the w64codecs package from medibuntu to no avail. I don't know what else to do!

---

### Post by Martin Marshalek on 2010-02-26
Okay, I found [this thread]("http://ubuntuforums.org/showthread.php?t=1370891") which seems to give me some help. I found a set of wma's that do play, and they are listed as WMA 8 in the properties whereas the rest give an error for WMA 9 when I try to play them. According to the thread, the only way to use WMA is Mplayer, Xine, or something called gstreamer-0.10-pitfdll which apparently allows gstreamer to use the codecs from medibuntu. Either pitfdll is no longer in the repos or it is 32bit only, because I cannot find it in synaptic. Is all of this true or is there another way/a way to install pitfdll in 64 bit.

---

### Post by wilee-nilee on 2010-02-26
Not sure your argument for not just installing the restricted extras is valid except for those who want the leanest possible setup in their minds. Have you considered just using winff or handbrake in MS or Ubuntu to reformat the media to what works for you.

It may be that the restricted extras wouldn't fix the problem though. I have run into MS formated media at times that just wont work when it should so I reformat it.

---

### Post by Martin Marshalek on 2010-02-26
Yeah it seems that gstreamer won't play anything passed WMA version 8 so that's a dead end. Xine on the other hand should be able to so, I guess my last question on the matter is: Are there any xine-based media players (similar to Rhythmbox, not just a video type player like Totem) that are gtk? I realize I could use Amarok, but I might as well just switch over to KDE if I'm gonna be using some other qt stuff.

---

### Post by NightwishFan on 2010-02-26
You can use some QT programs, KDE tends to have GTK ones. Try VLC (not xine), xfmedia, or gxine.

---

### Post by Martin Marshalek on 2010-02-26
Thanks for the help but I decided to just take the music I had from my DSi, which I had converted to .m4a and copy that to my computer. My main concern was that there was a problem with my computer but I know see that this is not the case. I was confused because when I first started with Ubuntu (8.10) I was able to play .wma just fine but I guess that was because I had ripped them at lower quality so they were saved as WMA 8 and were able to play.

---

### Post by empty_spaces on 2010-02-26
I could be wrong, but I seem to remember from some older thread that you need the Fluendo codecs for WMA9 and higher.

See link below for the Fluendo Codec site.
[http://www.fluendo.com/shop/product/complete-set-of-playback-plugins/](http://www.fluendo.com/shop/product/complete-set-of-playback-plugins/)

---

### Post by Martin Marshalek on 2010-02-26
Thanks, I did read about the fluendo plugins but I would rather not pay 28 Euros (I don't know how much that is off the top of my head in USD but probably quite a difference in the wrong direction based off the way the economy is going here in the US) for some codecs. Sure, I could torrent them as has been said in other places on the net but again, I can play my music in another format legally, so that's good enough for me. It seems it can be done for free with gstreamer in 32 bit but switching is not an option as the whole reason for me reinstalling Ubuntu is its free offering of a 64bit OS. Maybe in future versions there will be a plugin to handle WMA 9 but for now, I'll stick to .m4a and .mp3.

Thanks for the help though, it is much appreciated, I'm just glad that there is nothing wrong with my system as fsck already failed on my first reboot and just hung (I think it was corrected with an update as, once I updated everything seemed fine).

---

