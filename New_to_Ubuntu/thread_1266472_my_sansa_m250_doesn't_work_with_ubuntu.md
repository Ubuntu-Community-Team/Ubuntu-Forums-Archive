---
title: "my sansa m250 doesn't work with ubuntu"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by thomz92 on 2009-09-14
i noticed on my windows computer that when i plugged my mp3 player in it that it showed up as a sansa mp3 player and not like a removable device like flash drives or something. anyway, when it pops up on my ubuntu comp it shows a few folders (that don't show up on my windows comp) and the music i have on there doesn't show up. and if i put music on there, it doesn't play... is there anyway i can make it compatible? maybe completely format it or something?

---

### Post by Jaymac on 2009-09-14
Have you set it to MSC mode?

I think it's in Settings > USB > MSC or something.

---

### Post by thomz92 on 2009-09-14
"settings"? wheres that?

---

### Post by thomz92 on 2009-09-14
ok i set it to MSC mode. i didn't realize you were talking about the mp3 player. it now recognized it as an mp3 player, but when i try to view the files it still doesn't show any mp3 files. it has an "audible" and a "record" folder and some .sys and .sdk files, but no music. when i try to view the mp3 player with rhythmbox, it says it can't upload because the MIME file type can't be identified or something like that. what now??
out of curiosity, what is MSC mode anyway?

---

### Post by thomz92 on 2009-09-15
bump...

---

### Post by Geoff918 on 2009-09-15
I have no knowledge of this specific item, but I found something that may be of use to you:

[http://ubuntuforums.org/archive/index.php/t-734495.html](http://ubuntuforums.org/archive/index.php/t-734495.html)

It even says [SOLVED...] so that's a good sign.

---

### Post by Garrovick on 2009-09-15
Did you try the Sansa Forums?

The best you can do with Linux and Sansa is just dreg and drop files.

Forget Audible, and resume/bookmarking stuff.

---

### Post by thomz92 on 2009-09-16
thanks Geoff918! that helped a lot

for other m250 users heres what i did:

first i changed it to MSC mode. then i plugged it into my windows computer and deleted all the songs on it, so it was just like when i got it. then i unplugged it and plugged it into my ubuntu 9.04 comp. i opened gedit and pasted this into a new document:

audio_folders=MUSIC/,RECORD/

then i saved it as ".is_audio_player" in my sansa m250's root folder. I made a new folder in the main root folder named "MUSIC", which is where i put all my music. rhythmbox recognizes it perfectly and uploades them all without any error, and everything works great! thank u very much

---

