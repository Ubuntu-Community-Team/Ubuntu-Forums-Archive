---
title: "how do we convert wav files to something i can use"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by busemans on 2009-01-20
i want to load to an mp3 player but the files are wav and the mp3 doesn't recognize them.  is there some kind of converter i can use.

---

### Post by Dougie187 on 2009-01-20
mencoder might do it.
or ffmpeg

---

### Post by roquefilipe on 2009-01-20
there is the SoundConverter ([http://soundconverter.berlios.de/](http://soundconverter.berlios.de/)), but if you may want to do more than just conversion, try Audacity, it is an audio editor.

---

### Post by wolfen69 on 2009-01-20
btw, soundconverter is available in synaptic package manager.

---

### Post by donkyhotay on 2009-01-20
I use audacity with lame to do conversions like that, It's probably overkill though since it's designed to actually edit audio files rather then convert them.

---

### Post by busemans on 2009-01-20
i tried that soundconverter and konverter.  i downloaded lame but can't get it to load up.  i think you have to be smarter then the computer but i don't think i am winning right now.

---

### Post by SunnyRabbiera on 2009-01-20
> **busemans said:**
> i tried that soundconverter and konverter.  i downloaded lame but can't get it to load up.  i think you have to be smarter then the computer but i don't think i am winning right now.

You dont need to install anything on some site somewhwere if you know what to do.
Instead of randomly downloading stuff from the net we use repositories to do the job, if you need Mp3 encoding and such its easy to get via the repositories.

---

### Post by busemans on 2009-01-20
ok,  sorry.  not wav,  wma files.  how do we convert those.

---

### Post by donkyhotay on 2009-01-20
Lame isn't something you can use directly from a GUI, it's a CLI program. As I said before, I use audacity *with* lame to export to mp3 format. Audacity will work just fine without lame you just can't export to mp3. Lame will also work without audacity it just requires you to be comfortable with bash.

---

### Post by busemans on 2009-01-20
i got it to work.  i used sound converter and it had a little link on the bottom that asked how to install.  from there it had an mp3 converter that downloaded.  now everything is great.

thanks guys.:KS

---

### Post by blueridgedog on 2009-01-20
If you have a file that is say mysong.wma, you could:
```

mplayer -vo null -vc dummy -af resample=44100 -ao pcm:waveheader mysong.wma && lame -m s audiodump.wav -o mysong.mp3
```

mplayer will make a vile called audiodump.wav, then lame will convert it.

---

### Post by djbarroso on 2009-01-22
@blueridgedog: I was also trying to convert WMA to MP3, and I used your code above... Just wanted to point out that the '-ao pcm -waveheader' section has to be changed to '-ao pcm:waveheader', as per the error message I got ('-waveheader has been removed. Use -ao pcm:waveheader instead'). After that was done, it worked great for me! Thanks!

---

### Post by JMJ_coder on 2009-01-22
oggenc -- will convert from wav to ogg

---

### Post by blueridgedog on 2009-01-22
> **djbarroso said:**
> @blueridgedog: I was also trying to convert WMA to MP3, and I used your code above... Just wanted to point out that the '-ao pcm -waveheader' section has to be changed to '-ao pcm:waveheader', as per the error message I got ('-waveheader has been removed. Use -ao pcm:waveheader instead'). After that was done, it worked great for me! Thanks!

Thanks...I corrected my post.

---

