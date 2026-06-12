---
title: "Trying to rip CD's to MP3 via Rythmbox 0.12.5"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by edpatterson on 2010-01-09
I am not able to rip CD's to MP3 format. MP3 does not show up in the selectable choices in Preferences, but if I click on Edit it is there. 

Is there an easier graphical way to rip CD's to MP3 on Ubuntu. I am running the 9.10 release which I am quickly becoming disillusioned with.

Ed

---

### Post by starcannon on 2010-01-09
> **edpatterson said:**
> I am not able to rip CD's to MP3 format. MP3 does not show up in the selectable choices in Preferences, but if I click on Edit it is there. 

Is there an easier graphical way to rip CD's to MP3 on Ubuntu. I am running the 9.10 release which I am quickly becoming disillusioned with.

Ed

You'll needs some restricted stuff installed first.
So that said, you may like to add the medibuntu repositories from [here]("https://help.ubuntu.com/community/Medibuntu"), or just use the code below in a terminal Applications>Accessories>Terminal

CTRL+C copy the code below
Shift+CTRL+V to paste it into a terminal
```

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```When that finishes, run this command:
```

sudo apt-get install ubuntu-restricted-extras

```That should get the mp3 option lit up for you.

If it still won't light up, come back and repost to this thread, we can try the "lame" codec next.

GL and HF

P.S. No reason to be disillusioned, not every codec, or piece of software can be put on a single install CD, some of it has to be downloaded. Relax and enjoy, Ubuntu is really a lot of fun if you can let it be.

---

### Post by howefield on 2010-01-09
> **edpatterson said:**
> Is there an easier graphical way to rip CD's to MP3 on Ubuntu.

A decent program for that is ripperx. It is in the repository so can be easily installed with Synaptic.

---

### Post by starcannon on 2010-01-09
> **howefield said:**
> A decent program for that is ripperx. It is in the repository so can be easily installed with Synaptic.
+1 
RipperX is my favorite mp3 ripper.

```

sudo apt-get install ripperx

```

---

### Post by odysseusjak on 2010-01-10
I prefer Banshee.  You can set the bit rate when you import the CD into your library.

---

### Post by edpatterson on 2010-01-10
> **starcannon said:**
> +1 
RipperX is my favorite mp3 ripper.

```

sudo apt-get install ripperx

```

Installed RipperX, configured it for MP3 128 bit, ripped a CD then double clicked one of the files. Movie player opened with the error: An error occurred, Internal data flow error. Then I tried VLC media player:"VLC can't recognize the input's format:
The format of '/home/ed/Music/Attack Attack! - Someday Came Suddenly/Attack Attack! - Bro, Ashleys Here.mp3' cannot be detected. Have a look at the log for details." (my son's 'angry music', not mine). Music Player simply would not open the file. Sigh, this was so easy with 9.04.

[more info]
After a failed attempt to find the docs for RipperX I went into the config and had it save the wav files and re-ripped the CD. The wav files played, the mp3 files failed. I looked at the actual files and the mp3 files are only 135 to 155 bytes in length.

Ed

---

### Post by turvyc on 2010-01-10
My preferred ripping app is Sound-Juicer. It's super-lightweight and simple, and just gets 'er done.

```
sudo apt-get install sound-juicer
```

---

### Post by ptviperz on 2010-01-10
Rubyripper is very good also

---

### Post by edpatterson on 2010-01-10
Tried Sound Juicer. Selected the MP3 format, ripped the CD, files are ogg.

Here is the GStreamer Pipeline info:
```

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=6 ! id3v2mux

```
extension is mp3

---

### Post by D1Knight on 2010-01-10
Hi! Just my 2 cents.;) I have used Asunder (available in Synaptic) many times with excellent results. :DI find it to be very, very easy. IMHO, I haven't found one better, yet. :)Asunder is worth a try. Enjoy and have fun.

---

### Post by lidex on 2010-01-10
edpatterson:
ripperx is the best I've seen. Something is not right. Make sure you have the multiverse repository enabled. In Jaunty that's "System>Administration>Software Sources". Run these commands:
```
sudo apt-get update
```
```
sudo aptitude install ubuntu-restricted-extras lame libmp3lame0 libtwolame0 toolame
```

In rx make sure you select "Encode" radio button. In config/Mp3 tab choose "lame" as encoder plugin.

---

### Post by inspiredminds on 2010-08-03
Hey all,

I agree with some of the ppl here and suggest RipperX. It can be found in the repository and can be  installed using Synaptic(dependencies will be taken care of). I am using  it for a week now and it is nice. 
You can choose from various bit rates including 128k, 256k and 320k(max).
can choose different VBR quality 
Can rip to mp3, ogg, flac
Has CDDB which can find track info online and attach tag n ids to the tracks
Has GUI and in few clicks you are good to go !!! 
I am using it on 10.04 and so far so good :grin:

---

### Post by John Peschken on 2010-08-03
Hey Thanks, Man! That worked for me after trying Xripper, Asunder, and everything else I could find.  Nothing worked.  I struggled with it for days.  I bought Nero for Linux hoping to get this one last thing working for me, but that crashes every time I try to access the online CD database.  No response from Nero support after 3 days.  Buyer's remorse there!

---

### Post by ianp5a on 2010-09-01
I've just installed ripperX (v 2.7.2)from the Ubuntu software center and i'm getting the same problems as edpatterson. The MP3s are just 20k in size

More: Encode is on. Ripping to WAV works OK.No changes to the defaul config settings was made.

---

### Post by ianp5a on 2010-09-24
So I gave up with RipperX not working and found that Sound Juicer works fine.

---

### Post by linjofitnes on 2010-10-02
Instlled ripperx and have had same problems and issues as ianp5a. I've followed the information Lidex posted and it works a treat.

---

