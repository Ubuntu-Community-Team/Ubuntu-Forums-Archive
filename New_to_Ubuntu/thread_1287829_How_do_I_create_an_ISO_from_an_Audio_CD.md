---
title: "How do I create an ISO from an Audio CD?"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by kendoori on 2009-10-10
I have some instructional material on audio CDs that I would like to image to .iso so that I can mount and unmount as necessary. Brasero doesn't appear to be able to image to .iso. Can anyone advise on this?

---

### Post by MrWES on 2009-10-10
> **kendoori said:**
> I have some instructional material on audio CDs that I would like to image to .iso so that I can mount and unmount as necessary. Brasero doesn't appear to be able to image to .iso. Can anyone advise on this?

this might work, from the terminal:

```
genisoimage -r -J -o cd_image.iso /dev/xxx
```

or 

```
dd if=/dev/cdrom of=cd.iso
```

Substitute xxx for your cd device; should be /dev/scd0 or /dev/sr0, something along those lines.

Bill

P.S. I just noticed you're in Wilton :) -- I live in Middletown; what are the odds of that?

---

### Post by penguintutor on 2009-10-10
Assuming that you are referring to an audio CD rather than a CD with audio files on it then I don't believe it is possible.

The reason for this is that audio CDs have multiple tracks, but an ISO file is only a single track image, so even if you find a way to create the ISO it will most likely contain only the first track, or you will have to merge the tracks into a single track.

You can rip the audio off from the CD and then use the songs directly. You could even put that into an ISO CD image, but it will be as a data CD ISO containing WAV files (or whatever audio format you choose), not as an audio CD. It's probably better to just rip the files into a suitable format and then run using your normal audio player.

**If you want to create a Data CD image then:**

You can use Sound Juicer to rip the audio (it's "Audio CD Extractor" on the Ubuntu menu). You can use genisoimage to create an ISO with all the ripped files, but if you want a GUI application I like K3b. 

Using K3b, to create an image click on burn and then on the options panel choose "Only Create Image". If you chose data CD for the project then it will create an ISO - if however you choose Audio CD for the project then it will create WAV files (one for each track) rather than an ISO.

I hope this helps

---

### Post by Cresho on 2009-10-10
brasero does do iso. look carefully.  its very very easy.

oops...sorry, i was using isomaster.  it's in add/remove

---

### Post by Cuddles McKitten on 2009-10-10
To create an iso from a CD using Brasero (not using any console commands), right click on the CD on your desktop, click "Copy Disk", write to an image file, and -- in the properties -- choose ISO as the output format.

---

### Post by sandyd on 2009-10-10
Use acetoneiso.

---

### Post by bulletxt on 2009-10-10
As carlee said, use AcetoneISO: [http://www.acetoneteam.org](http://www.acetoneteam.org)

---

### Post by penguintutor on 2009-10-11
I haven't used AcetoneISO, but the FAQ on their website states:

When converting to ISO an image, will it do a 1:1 copy?
  No, you will loose all tracks of the image. Only first track will be converted to ISO. This is due to ISO specifications.


Again the problem is that CDs are multi-track, ISO is single track.

---

### Post by MelDJ on 2009-10-11
why not just copy disc. right click- then press copy disc?

---

### Post by MrWES on 2009-10-11
> **Cuddles McKitten said:**
> To create an iso from a CD using Brasero (not using any console commands), right click on the CD on your desktop, click "Copy Disk", write to an image file, and -- in the properties -- choose ISO as the output format.

I do not have the choice for ISO in properties, just toc cue raw, etc. no iso.

Bill

---

### Post by leomelo on 2009-10-11
I make all my .iso with Brasero. Open Brasero,go to 'Data project',then '+ Add' and select what you want to be burned as .iso.Select each item one by one.Then click '+ Add'.Where is said 'Data disc(x Oct 09)',you replace this with name you want for your cd or dvd.Then click 'Burn'.On the page that appears,after clicking 'Burn',replace also the word 'brasero'(from 'brasero.iso')with the name that you previously have chosen for your cd or dvd.
Remember,that Brasero is a Gnome application.K3b(3b=burn baby burn) and AcetoneISO are KDE applications.If you use,in Gnome,a KDE application or program you will have to install in Ubuntu all the KDE libreries required by  the KDE application.In Ubuntu,a Gnome application load faster than a KDE application.K3b is for KDE.Brasero is for Gnome.

---

### Post by bulletxt on 2009-10-12
AcetoneISO is not a kde application. It is a Qt4 application and does not depend on kde.

AcetoneISO can convert a cd audio to bin. Go under the Convert menu and you will find the "Convert Cd-Audio to image" utility. 2 clicks and you're done.

---

### Post by kendoori on 2009-10-12
Question, once this is a .bin, is this mountable? is not, how can I play them back without reburning them? I'm pretty sure that Brasero can do the same, but I couldn't figure out hot to play back from the bin file. 

Basically my desire is to store the instructional audio CDs intact and mount them when I want to play them back. I currently do this with DVDs

---

### Post by lukjad on 2009-10-12
> **kendoori said:**
> Question, once this is a .bin, is this mountable? is not, how can I play them back without reburning them? I'm pretty sure that Brasero can do the same, but I couldn't figure out hot to play back from the bin file. 

Basically my desire is to store the instructional audio CDs intact and mount them when I want to play them back. I currently do this with DVDs

From the first [answer]("http://ubuntuforums.org/showpost.php?p=8084188&postcount=2"): 
```
dd if=/dev/cdrom of=cd.iso
```

This will make a mountable ISO file.

---

### Post by bulletxt on 2009-10-12
> **lukjad007 said:**
> From the first [answer]("http://ubuntuforums.org/showpost.php?p=8084188&postcount=2"): 
```
dd if=/dev/cdrom of=cd.iso
```

This will make a mountable ISO file.

No, that won't create an image of a cdaudio. 

For kendoori:
no, you can't mount the image. there is nothing you can do about it. the only purpose of that utility is to backup your cdaudio on a file. To restore it as a cdaudio you must burn it back to a cd.

In other words, you can't make an image of a cdaudio and then mount it and listen to it as if it were a cdaudio. Maybe you can tell vlc or mplayer to read the *.toc file you get when converting it with AcetoneISO, but i'm not sure that will work. Try and let us know.

The best and only solution is this:
convert your cdaudio to wav of flac lossless format. Then convert the folder (that has the files) to ISO with AcetoneISO. There you go, you have an iso with original cdaudio format all in one iso file.

---

### Post by lukjad on 2009-10-12
Hm, you're right. I'm surprised at that, but it just goes to show you never know until you try.

---

### Post by bulletxt on 2009-10-12
> **lukjad007 said:**
> Hm, you're right. I'm surprised at that, but it just goes to show you never know until you try.

ISO images do not support multi-track, thus they cannot be used for audio CDs, VCD, and hybrid audio CDs, which are usually ripped as audio files. However, for disks that contain a single track of data followed by tracks of audio, such as video game disks, the first track can be ripped as an ISO, and the rest as audio files.

[http://en.wikipedia.org/wiki/Iso_image](http://en.wikipedia.org/wiki/Iso_image)

---

