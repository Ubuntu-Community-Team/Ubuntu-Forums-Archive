---
title: "mp3 &gt; 5.1 channel audio"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by 4chan on 2010-06-13
greetings.. 
i'm using ubuntu lucid. currently i use PulseAudio.
i wonder if can get 5.1 audio from mp3 file on my quadrophonic speakers. thanks

---

### Post by cogier on 2010-06-13
If you have the hardware go to **System>Preferences>Sound** and select the **Output** tab. You can change the settings there.

---

### Post by 4chan on 2010-06-13
hi cogier. thanks for your quick response.
yes i already check sound preferences and choosing hardware profile to  : analog surround 5.1 output + analog stereo input. and on the output tab i have connector : analog output/amplifier.
but still when i play mp3 file. the sounds just the same in every channel. on a dvd movie i can play 5.1 audio output because the audio source is 5.1 but my question is how can i upmix mp3 file to 5.1 channel audio output? is there any specific DSP plugin or maybe specific audio player that can do the works?

regards

allison

---

### Post by durand on 2010-06-13
I think your sound card needs to support it, rather than ubuntu. In pulseaudio volume control, does the mp3 show 5 channels or just 2?

EDIT: In theory, it might be possible with the ecasound program. See this thread: [http://ubuntuforums.org/showthread.php?t=328347](http://ubuntuforums.org/showthread.php?t=328347)
It converts mono to stereo so higher conversion might be possible.

EDIT 2: Did you try changing the Audio Ouput to 5.1 channels in the default media player? You'll find it in the preferences. You should start there and see if it sounds better.

---

### Post by 4chan on 2010-06-13
hi durand 

i think my on board soundcard support 5.1 channel output because i can hear 5.1 channel audio from dvd playback. here's the screenshots from pavumeter when i play an mp3 file with rhythmbox

---

### Post by durand on 2010-06-13
Yeah, I got that however some good sound cards can also create virtual surround sound from a stereo source. They're quite expensive though. Anyway, you should try getting surround sound working from totem first. It's called "Movie Player". There's an option in the 3rd tab to output surround sound so I dunno, it might be able to synthesize surround sound. You should try it. I'm not sure about rhythmbox. It might have similar options but I've never used it.

---

### Post by 4chan on 2010-06-13
ok so i configure audio preferences on totem to provide me 5.1 output but nothing's changed sorry :(

---

### Post by durand on 2010-06-13
I'm not sure then :/ Sorry.

---

### Post by 4chan on 2010-06-15
thanks for tryin'

anyone?

---

### Post by Chesamo on 2010-06-15
As [MP3 Surround](http://en.wikipedia.org/wiki/MP3_Surround) is a proprietary technology (and relatively little-known compared to stereo MP3), you should probably double-check your MP3 files and make sure they're even 5.1.

---

### Post by 4chan on 2010-06-16
ok so there is no way i can upmix stereo mp3 to surround. thank you for all of your replies.


i will mark this thread as solved.

---

### Post by riger99 on 2010-11-21
This is not solved.

Please don't mark something as solved when it's not. ;)

---

