---
title: "Volume equalizing on songs"
date: 2011-03-20
forum: New to Ubuntu
---

### Post by jrspotts on 2011-03-20
I have multiple songs from different sources.  I am loading them all on a single flash drive to play in my vehicle.  The volume level is different on each song since they are from different sources.  Is there a way to have all the songs at the same volume level?  Thank you in advance

---

### Post by alzie on 2011-03-20
In Windows I used a program called mp3gain.  There is a similar program called easymp3gain-gtk in the repositories.  I have no experience with it but it looks like the version I used.

Basically it normalizes the volumes of the music files to balance "quieter" and "louder" songs so you don't get the jarring volume changes.  Reducing the louder songs reduces clipping as well.

Give it a shot if you'd like.

You should be able to adjust the volume for music in a target file so you can do a test to see if it works for you and not have to worry about messing up your library.

---

### Post by ankspo71 on 2011-03-20
Hi,
There are applications that can adjust sound volume level of your audio files... even recursively throughout many files and folders if you wish, by writing some "gain" metadata directly to the files. These applications help 'normalize' your tracks (in a sense) in such a way that they all appear to have the same volume output afterwards.

"EasyMP3gain-gtk"  is one of those applications. 
It is a front end to MP3Gain, VorbisGain and AACGain. 
A description can be found here: 
[http://sourceforge.net/projects/easymp3gain/](http://sourceforge.net/projects/easymp3gain/) "

Another application is called "Qtgain". 
It is a front end to MP3Gain, VorbisGain, AACGain and Metaflac
A description can be found here:
[http://qt-apps.org/content/show.php?action=content&content=56842](http://qt-apps.org/content/show.php?action=content&content=56842)

Note that both applications are found in Ubuntu's repositories (eg Software Center, Synaptic Package Manager), so there isn't a need to download them from their homepages.

PS: I only used these types of applications for MP3 files, so I'm not sure how many other audio file types they support. PS Again: Make a backup of your audio files first, just in case you find yourself being unable to revert the changes they make to the files.

Hope this helps.

---

