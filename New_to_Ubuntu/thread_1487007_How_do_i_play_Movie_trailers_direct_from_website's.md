---
title: "How do i play Movie trailers direct from website's...?"
date: 2010-05-18
forum: New to Ubuntu
---

### Post by liviococcia on 2010-05-18
Hello Members, hope you can help me.

I'm using Ubuntu 10.04 and a T-Mobile 'Mobile' broadband connection.

If i go to say 'Apple Mac's' website, and want to watch a movie trailer, how do i get Mozilla Firefox to play the trailer straight off the web-page trailer link.

What i have tried so far is, i did download and installed MPlayer, i thought this would work straight away, but apparently this needed a Mozilla-Mplayer plugin, i found a related website for this, but could not follow it's instructions at all, it seemed they way it was explained on the website seemed very complicated for any newbie of Ubuntu to understandable, to me anyway.

I then followed a Ubuntu help page on the main Ubuntu website, it was regarding the installation of the 'ubuntu-restricted-extras package', i followed all it's instructions, and as far as i could tell in the details of the 'Terminal' window, it had been installed successfully, this did not seem to enable anything in 'Firefox', and i just came out with the same problem.

So if anyone has a simple solution, a bit of easy to use software that installs and will enable this function, i would be very grateful for the info and help.

Kind regards
Livio

---

### Post by ajgreeny on 2010-05-18
There are several things I would do which should help out.

1.  Enable the medibuntu repositories by following this guide [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

2.  Install the many and various packages that are needed from those repos.  I always install the w32codecs (w64codecs if running 64 bit ubuntu) and libdvdcss2. That will get you all the codecs you could want and the DVD encryption decoder for needed for playback of commercial DVDs.

3.  Install ubuntu-restricted-extras (you already did that)

4.  Install either adobe-flashplugin or flashplugin-installer.  Both will get you to the same place, ie with adobe flash 10.0.r45 installed and ready to play in Firefox.

5.  Uninstall totem-mozilla and install gecko-mediaplayer for much better playback of internet multimedia.  This is a bit of a personal thing, but I've never managed to find anything great about totem-mozilla.  I used to use mozilla-mplayer as you have tried, but that has now stopped any further development and gecko-mediaplayer has taken over from it.

Give those things a try and come back if you have any other problems.

---

### Post by Linux_junkie on 2010-05-18
If your wanting to watch movie trailers from a Mac website I'm assuming the trailers will be in Quicktime format so you will need to download and install the codec for that format. Also check in Firefox under the Tools menu -->  Manage  Content plug in to see if the Quicktime plugin is installed.

---

### Post by liviococcia on 2010-05-19
Thanks ajgreeny and Linux_junkie, i forgot to mention, as you said, i did at the same time as installing the 'ubuntu-restricted-extras' also install 'medibuntu','libdvdcss2' and the w32codecs, i followed both helpfiles at the time.

I've now done as you suggested, installed the gecko-mediaplayer (GNOME player), removed the 'totem-mozilla' player and plugins.

I've checked in Mozilla Firefox under 'Tools'>'Add-ons' and noticed the Gecko-Mediaplayer plug-in is there, but also 'Quicktime' and 'Adobe flash' plug-ins are also there, there's also a DivX plug-in and a 'Windows Mediaplayer' one aswell.

What happens now is, when i go to the Apple Mac website and go to there film trailers section and click on the 'Watch trailer' button, a media player style panel opens (i think websites own media controls are still hiding behind though), it's starts to play as the progress bar is moving, but the viewing window is completely black, this is the same issue i had when i first tried the watch a trailer, and Mozilla Firefox presented me with a popup window to 'search for a suitable plugin', i can't remember what they were at that time but it was two files though.

The problem sort of reminds me of the days long ago, when Windows had various problems with overlay graphics acceleration.

Thanks for all the help, if there's anything else i missed or can try this info would be great.

regard

---

### Post by ajgreeny on 2010-05-20
Using synaptic search for flash, gnash and swfdec and check that you don't have any extraneous flash packages installed alongside adobe-flashplugin (or flashplugin-installer).

If you have sfwdec or gnash, for example uninstall them, as they seem to conflict with adobe flashplayer.

---

### Post by liviococcia on 2010-05-21
Thanks again ajgreeny, i'll give your instructions a go and report back, but if i don't have much success i think i'll hold on and see if something gets resolved in the future.

kind regards

---

### Post by liviococcia on 2010-05-23
Hello Members, and thanks for the help, just to report i had no sucess trying to play Quicktime movie trailers form the Apple movie trailer website, i think it's more the fault of Apple not validating that there's a quicktime player installed.

Anyway.., as i mentioned in my previous post, i'll leave this alone for now, maybe it will get sorted out over time, and future Ubuntu updates. I did come accross another movie trailer website that does work well though, [www.movieweb.com](www.movieweb.com) plays video well, and without any issues.

kind regards to you all
Livio

---

