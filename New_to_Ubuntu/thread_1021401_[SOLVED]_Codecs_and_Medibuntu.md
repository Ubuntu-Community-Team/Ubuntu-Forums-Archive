---
title: "[SOLVED] Codecs and Medibuntu"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by lun on 2008-12-25
I am trying to install codecs, but not from gstreamer (which works), but from medibuntu.  I added medibuntu to the repositories and installed the music and video codecs according to [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) but every time i tried to run media with restricted codecs, i get this message:

> The required software to play this file is not installed. You need to install suitable codecs to play media files. Do you want to search for a codec that supports the selected file?


I found this in a post a few minutes ago:

kansasnoob
> I used to install the whole Medibuntu repo but now I just install the separate libdvdcss2 and w32codecs packages

so i removed medibuntu from the repositories and still receive the same message.  My understanding is that restricted media ought to play flawlessly when i enable these packages.  I am assuming there is something simple that i am missing, so any help will be appreciated.

---

### Post by Moop on 2008-12-25
I use the medibuntu repository. There's some good stuff in there like google earth etc. 

Have you installed the ubuntu restricted extras package?

---

### Post by Toshibawarrior on 2008-12-25
What I always do after adding the  Medibuntu repository (keep in mind that deleting the medibuntu repo is not going to uninstall anything you already installed using Synaptic or APT) is installing the restricted extras...

Go into Synaptic Package Manager and search for:

- ubuntu-restricted-extras
- libdvdcss2
- libdvdread3
- libdvdnav4

And that should be it...After installing these packages any media should be played in Ubuntu.

Report back if it doesn't work.

---

### Post by benny bronx on 2008-12-25
What media player are you using? It is my understanding that totem-gstreamer does not use the win32 codecs, and xine may require the installation of some additional plugins from the repos.  Mplayer, on the other hand should automatically use the win32 codecs.

---

### Post by bumanie on 2008-12-25
If you have installed codecs from medibuntu repository corretly, you should not be having issues - may be try another player to confirm whether the codecs are working or not. vlc player plays nearly all codecs, give it a try. > sudo apt-get install vlc

---

### Post by lun on 2008-12-25
> What media player are you using? It is my understanding that totem-gstreamer does not use the win32 codecs, and xine may require the installation of some additional plugins from the repos. Mplayer, on the other hand should automatically use the win32 codecs.

I am using the default rhythmbox and totem.  I would assume that ```
sudo apt-get install libdvdcss2 && sudo apt-get install w32codecs
``` would do the job (after adding medibuntu to the repositories).  I want to avoid VLC for right now.

I am installing ubuntu-restricted-extras right now (i am using a slow connection).  I thought ubuntu-restricted-extras was separate from medibuntu though..?

thanks
nick

---

### Post by albinootje on 2008-12-25
> **lun said:**
> I am using the default rhythmbox and totem.  I would assume that ```
sudo apt-get install libdvdcss2 && sudo apt-get install w32codecs
``` would do the job (after adding medibuntu to the repositories).  I want to avoid VLC for right now.

If you really want to stick to totem (instead of testing smplayer, xine, and vlc), then you can replace totem-gstreamer by totem-xine if you like.
For me that worked better.

This webpage could be useful to read more about those two different totem backends.
[http://www.funnestra.org/ubuntu/intrepid/#totem](http://www.funnestra.org/ubuntu/intrepid/#totem)

---

### Post by bumanie on 2008-12-25
It is a possibility that with a slow internet connection, that thing have not downloaded correctly. Try > sudo dpkg --configure -aThis will download any broken packages (if you have any). It could be the problem.

---

### Post by lun on 2008-12-25
> If you really want to stick to totem (instead of testing smplayer, xine, and vlc), then you can replace totem-gstreamer by totem-xine if you like.

Still, rhythmbox is not recognizing the codecs i have installed.

But before i figure out which of those run better, my terminal is stuck in the ubuntu-restricted-extras install with a package configuration for sun-java6-jre license page.  It has a list of terms and agreements and definitions and stuff and is gray and blue.  I cannot figure out how to exit it and get back to the main terminal.  I have tried hitting ESC, CTRL+C, and CTRL+Q, but cannot get out of this screen.:confused:

I attached an image of my terminal.

---

### Post by Toshibawarrior on 2008-12-25
> **lun said:**
> Still, rhythmbox is not recognizing the codecs i have installed.

But before i figure out which of those run better, my terminal is stuck in the ubuntu-restricted-extras install with a package configuration for sun-java6-jre license page.  It has a list of terms and agreements and definitions and stuff and is gray and blue.  I cannot figure out how to exit it and get back to the main terminal.  I have tried hitting ESC, CTRL+C, and CTRL+Q, but cannot get out of this screen.:confused:

I attached an image of my terminal.

Try to press the TAB key until <Ok> is highlighted...That's what I always do.

---

### Post by lun on 2008-12-25
> Try to press the TAB key until <Ok> is highlighted...That's what I always do.

:oops:

---

### Post by Toshibawarrior on 2008-12-25
> **lun said:**
> :oops:

Heh! No problem. Sometimes it's the easiest things that get us stuck. :-D

---

### Post by lun on 2008-12-25
Update:  OK, i installed ubuntu-restricted-extras and can now utilize restricted codecs :P.  I have one remaining question, is ubuntu-restricted-extras part of medibuntu, or or could i install it without adding medibuntu to the repository?  If not (which i think is the case), then what does medibuntu do?  it did not allow restricted codecs to function when when i added it and installed libdvdcss2 and w32codecs.

Thanks for all the help,
nick:popcorn:

---

### Post by Toshibawarrior on 2008-12-25
> **lun said:**
> Update:  OK, i installed ubuntu-restricted-extras and can now utilize restricted codecs :P.  I have one remaining question, is ubuntu-restricted-extras part of medibuntu, or or could i install it without adding medibuntu to the repository?  If not (which i think is the case), then what does medibuntu do?  it did not allow restricted codecs to function when when i added it and installed libdvdcss2 and w32codecs.

Thanks for all the help,
nick:popcorn:

It's weird because I never get any problems with it. In fact ubuntu-restricted-extras installs better when Medibuntu is added to the repositories. Anyway, Medibuntu is supposed to be a source for stronger codecs and media-based programs such as ffmpeg and libraries such as libdvdcss, and libdvdread.

I may be uninformed on this matter, to if anyone has a better explanation please come around and tell us ;)!

---

