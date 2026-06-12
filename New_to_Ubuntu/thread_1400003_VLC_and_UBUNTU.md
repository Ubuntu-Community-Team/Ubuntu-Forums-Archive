---
title: "VLC and UBUNTU"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by squrl on 2010-02-06
Quick short question I hope.

Is it possible to play WAV files in vlc with Ubuntu 8.04 ???

If so what has to be added. Right now all it plays is MP3's

---

### Post by synapsys on 2010-02-06
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by chaanakya_chiraag on 2010-02-06
Hmmm...normally it's the other way around, and besides, VLC should be able to play wavs out of the box...  Have you tried opening a wav file with totem?

---

### Post by SPazzo on 2010-02-06
Have you played the WAV file with any other programs?  Is it possible that it got corrupted?

---

### Post by squrl on 2010-02-06
I just did the extras install bit. It says they are already installed in the latest version. 

I also can play the wav files in player I think it is. VLC plays the MP3 files fine. 

Any thing else I might try??

---

### Post by macabrem on 2010-02-06
How did you install VLC?  Through Synaptic?  I'm wondering if the version or installation you have is missing something.

---

### Post by squrl on 2010-02-06
So do I but I've tried to reinstall it a couple times. The file shows up and the indicator moves like its playing there just isn't any sound.

---

### Post by squrl on 2010-02-06
bump please

---

### Post by chewearn on 2010-02-06
Somebody ask how you install VLC and you didn't answer.

Also, here is another question, what is the version of VLC you have?

Depending on the wav file, you might need to get newer VLC version.  For instance, I have wav file of 8kHz  IMA-ADPCM.  This file played fine using SMPlayer 0.6.8 (mplayer back-end), but stutters when played by VLC 0.9.9a

---

### Post by squrl on 2010-02-06
I loaded the program through synaptic. The version says it is 08.6e

---

### Post by chewearn on 2010-02-06
Open: VLC > Menu > View > Messages
Then, open and play the problematic wav file.
Paste the output messages here (put [noparse]```
 
```[/noparse] tag between the output for easy reading.)

---

