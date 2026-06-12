---
title: "Music will not play"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by quinnten83 on 2009-01-31
I have this weird problem with music playback.
I just installed Intrepid.
I have sound, and I have codecs installed, but I can't play MP3.
every music player, just sits there when I start an mp3. The slider bar indicating progress does not start. When I tried it on the live cd there was no problem, and on a different computer, I don't have this problem.
The only thing I can think of is that I installed songbird from getdeb.net.
I can't remove that either as it does not appear in add/remove.

EDIT: forgot to ask if anybody has any ideas what it could be

---

### Post by diablo75 on 2009-01-31
How did you install the codecs?

---

### Post by cwsnyder on 2009-01-31
Do you have lame or twolame from the repository loaded?  One of these will be needed (usually lame) to play MP3s.  You can also load lame by enabling the ubuntu-restricted-extras, which would also load other needed codecs to play multimedia.

---

### Post by quinnten83 on 2009-01-31
I installed from command line.
First I tried scripting everything, but that only made me add repos that didn't exist, so I removed them manually.
Then I followed the instructions to add the medibuntu repos.
I then used the rest of my script to install all software at once, including the restricted extras. Java seems to be working fine.
I have sound out of everything else, and it isn't a sound problem. The music players just aren't reading the mp3, even though, they do load them.
One thing i noticed is that i need to enter a password everytime i try reaching my windows partitions (I dualboot). This was not the case with 8.04. 
I will probably reinstall tomorrow morning. 
A darn shame too, because this is the first time I don't have the random freeze-lockup issue on this computer with Ubuntu.

---

### Post by quinnten83 on 2009-01-31
I installed all the lames that I could find, that did not help.

---

### Post by quinnten83 on 2009-02-01
I'm having a serious WTF moment.
After sleeping one night, I woke up with the intention of reinstalling, and now it works.I have no idea what happened. It didn't work right after I installed lame(s) and de-installed songbird.
Ah well, lets just mark this as solved!!

---

