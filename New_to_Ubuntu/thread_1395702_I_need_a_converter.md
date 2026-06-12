---
title: "I need a converter"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by GaaraOfDSand on 2010-02-01
As the titles says, I need a converter..

I downloaded some amiga audio (.mod) and a 2 minute track is less than 1mb, since I have quite a few .mp3's I was wondering if there is a way to convert .mp3 to .mod for space reasons..

(I don't know if this helps or anything, I use fluxbox on Xubuntu.)

Thanks in advance for the help.

---

### Post by J V on 2010-02-01
sudo apt-get install handbrake-gtk

---

### Post by Rhubarb on 2010-02-01
A converter simply doesn't exist for such a thing.

A mod file is simply a file containing a few samples combined with something similar to midi.

Consider this:
You can read and play sheet music for the piano, but you can't convert some music you hear back into sheet music.
(music you hear is equivalent to your mp3s, and sheet music is equivalent to your mod files).

If you wish to shrink the size of your mp3s, you could re-encode them at a lower bitrate (in mp3 or ogg vorbis if you wish).
- But a problem with this is that you will lose quality in the process, unless of course you re-rip your music from CD to a better sound format such as ogg vorbis.

I hope I made some sense for you, you really can't convert mp3 --> mod.

Edit: J V's reply of using handbrake-gtk is incorrect, as handbrake is used for converting video formats to other formats / bitrates.  It's simply not (easily) possible to convert mp3 to mod

---

### Post by GaaraOfDSand on 2010-02-01
Thanks for the replies. At least now I know that it is not possible, and for the handbrake-gtk:

riddlebox@BrainSlug:~$ sudo apt-get install handbrake-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package handbrake-gtk

I even tried looking in synaptic.. Anyway if it's not possible then there's nothing else to do. Thanks again. =)

---

### Post by JohnAStebbins on 2010-02-01
Handbrake isn't in the standard repository.  But it's available in a PPA.

[https://edge.launchpad.net/~handbrake-ubuntu/+archive/ppa?field.series_filter=](https://edge.launchpad.net/~handbrake-ubuntu/+archive/ppa?field.series_filter=)

---

### Post by seeker5528 on 2010-02-01
I think Sox handles .mod audio files and sox is recommended by Soundconvert giving some expectation that soundconvert can use Sox when it's installed.

Soundconverter uses gstreamer, but I think the gstreamer-bad plugins support .mod audio files.

SoundKonverter may work also, if you use the phonon-xine backend.

Later, Seeker

---

### Post by NightwishFan on 2010-02-01
Please note that Mp3 is a lossy file. Converting to Mp3s will always result in loss of quality. (This is true for any lossy formats though some more than others).

Something like FLAC is a lossless file, it will retain full file integrity, but be a much larger file format. (I use this).

If you convert an mp3 to flac it will work as a flac file but still sound like an exact copy of an mp3. (Generally rip uncompressed cd audio to flac to compress and retain full quality)

To save space you can convert a lossy file like mp3 to a smaller mp3 or the open source ogg format, but there will be a loss of quality.

Any format that is smaller than oggvorbis/mp3 is likely midi data or similar, which requires a synth to play.


My advice would be (if you have the hard drive space) to use FLAC for any CDs you rip, and convert them to mp3/ogg to transport them. That will optimize quality and space saving when needed. If you have low hardrive space, then mp3/ogg are basically as good as you can get for space saving on general purpose audio.

Please feel free to ask any questions or correct if I said anything wrong above.

---

### Post by nhasian on 2010-02-01
> **GaaraOfDSand said:**
> I was wondering if there is a way to convert .mp3 to .mod for space reasons..

Good 'ol amiga 500.  thats how i started my adventures with computers.  mp3 files are already compressed audio, so converting them to something else will not save space.  you can however lower the quality of the mp3 to reduce the file size if that is your goal.  for example lowering the mp3 audio file from 256kbps to 96kbps would decrease the file size to save hard disk space.  you can do that with lots of programs, i prefer [audacity]("http://audacity.sourceforge.net/").

for example on my brother's Samsung Impression (although its a brand new phone) stupid programmers decided to limit the filesize of mp3 ringtones to 300k.  so when we download ringtones above that filesize limit, we just downsample it to reduce the filesize then upload it to the phone.

alternatively, you could just buy a new hard disk.  1 terabyte is like $70 now right?

---

### Post by GaaraOfDSand on 2010-02-02
Thanks for all the replies, so if mp3 is the way to go, then I guess I'll just mark the thread as solved, I'll leave it open till tomorrow maybe someone will give another option, lowering the quality is solving the space issue sure, but listening to poor audio is just not for me. 

One thing I was thinking about though, back in the days they made damn good quality audio in such a small space damn! You gotta give'em credit for that.

Thanks again.

---

