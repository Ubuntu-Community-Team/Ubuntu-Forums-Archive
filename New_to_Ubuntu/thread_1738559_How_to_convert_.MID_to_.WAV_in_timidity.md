---
title: "How to convert .MID to .WAV in timidity?"
date: 2011-04-24
forum: New to Ubuntu
---

### Post by boulezfan317 on 2011-04-24
Hello again! This is my second post and my first post was met with generous and detailed help, so thanks guys, you're awesome! 

I am trying to create high-quality audio files that are very precisely tuned according to a seventeenth century tuning system, for which to use as a practice and rehearsal tool for my early-baroque ensemble. I have struggled through installing Scala, a powerful program for re-tuning midi files (along with many, many,  other cool features) and I have installed and can play the re-tuned midi files with Timidity, apparently the only program which can render midi files using the midi tuning standard. Part of the description of the program is that it can convert midi files to quality wav files, but I cannot figure out how to do this! I have looked through this site [http://linux.die.net/man/1/timidity](http://linux.die.net/man/1/timidity) but I still have no idea. Could any of you musically inclined folks out there help me out? I also am having trouble getting my soundcard to work with some of the other audio packages out there (rosegarden, ardour, etc.) but I think I can find a lot about that elsewhere in the forums. 

Thanks for your help!!

---

### Post by 3rdalbum on 2011-04-24
```
timidity <inputfile> -Ow
```

(that's a capital o, and a lowercase w).

If you're not good at navigating the filesystem in the terminal, then just drag the MIDI file to the terminal window after typing the first space.

---

### Post by boulezfan317 on 2011-04-24
Oh so you need the carrots? That's what I was missing I guess.

---

### Post by boulezfan317 on 2011-04-24
I got it!  Thanks a MILLION.

---

### Post by boulezfan317 on 2011-04-24
Ok here's one more question along these same lines: Is there a way I can modify the timbre of the midi file and then export it to wav with the new timbre?

---

### Post by rosencrantz on 2011-04-24
OK, got the question wrong the first time ;-)
To get timbres/patches beyond the standard piano to play with timidity, you'll need to install freepats.
sudo apt-get install freepats

I was able to change patches by importing the midi file into Rosegarden and re-exporting again.
Wav export from timidity should conserve the patches.

---

### Post by 3rdalbum on 2011-04-25
> **rosencrantz said:**
> OK, got the question wrong the first time ;-)
To get timbres/patches beyond the standard piano to play with timidity, you'll need to install freepats.
sudo apt-get install freepats

I was able to change patches by importing the midi file into Rosegarden and re-exporting again.
Wav export from timidity should conserve the patches.

That's a good idea, I'd like to change the instruments in a MIDI file and I quite forgot that I could put it into a MIDI editor. I was trying to find a way of getting Timidity to do it too.

---

### Post by boulezfan317 on 2011-04-25
thanks you guys. Shall I assume all issues related to ardour, rosegarden, jack, asla, etc. belong in their own thread or have been covered in detail somewhere else? Having gone through some troubleshooting instructions I found on a couple of sites I discovered that my soundcard is not supported by linux (wtf?) so how come I can hear all sorts of sounds, (not to mention midi played through the ubuntu built in sound player and timidity) but I can't play a midi file in rosegarden? Am I daft?!?!

---

### Post by rosencrantz on 2011-04-25
If your sound card produces sound, I'd venture to say it's supported. Maybe the page you found was dated, there has been tremendous progress with hardware support in the last few years. Rosegarden doesn't play sound for me either, so it's probably a configuration problem.
On the whole, I'd suggest a new thread for your other questions, as they stray quite a bit from this thread's title. 
Apart from google, you can also try the forum search, if you haven't already. 
The general rule is new thread for new questions if they aren't direct follow-ups and bump (just post 'bump') if your unanswered post has been idle for more than a day and you want to get it to the top of the queue again.

---

### Post by stmiller on 2011-04-26
You'll need to pipe Rosegarden or other midi apps through a soft synth like fluidsynth (qsynth is the gui).

In fluidsynth you would load a soundfont.

Most Linux synth apps work with widely known and used files called soundfonts.

You can find literally thousands of free soundfonts on the web.

*.sf2

Some are hundreds of MB in size, some very small. 

[http://www.google.com/search?h&q=soundfonts](http://www.google.com/search?h&q=soundfonts)


You can even specify a soundfont in timidity's config files, etc.

---

