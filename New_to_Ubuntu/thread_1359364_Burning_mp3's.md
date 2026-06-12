---
title: "Burning mp3's"
date: 2009-12-19
forum: New to Ubuntu
---

### Post by Dobbie03 on 2009-12-19
Ok this is the situation, I have a song that my Grandparents love, the recently both passed away and it is their memorial service today.  I need to burn their song which is an mp3 to play on a non-compatible cd player.  Is there a program on Ubuntu which can do this?  I know Windows Media Player automatically converts to a .wav file.  Please help.

---

### Post by Mrandersonjr on 2009-12-19
sudo apt-get install audacity (in terminal),then import the mp3 and export as a wav or any other file you want.

---

### Post by seeker5528 on 2009-12-19
K3B is my preference, but Brasero provides the option to create an audio CD as well. The audio CD format is it's own form of audio, not a .wav, so if media player converts to .wav it is just a temporary intermadiate step from compressed format to uncompress format to the format that audio CDs use.

Later, Seeker

---

### Post by Dobbie03 on 2009-12-19
Awesome thank you.

---

### Post by candtalan on 2009-12-19
> **MattDobson said:**
> Awesome thank you.

It is possible you will need to install some codecs, 
some notes here might be useful (see #19)
[http://ubuntuforums.org/showthread.php?t=1341165&page=2](http://ubuntuforums.org/showthread.php?t=1341165&page=2)

---

