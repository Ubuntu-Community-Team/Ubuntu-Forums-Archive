---
title: "Cant edit mp3 tags in rhythmbox"
date: 2010-03-27
forum: New to Ubuntu
---

### Post by Dobbie03 on 2010-03-27
I am trying to edit songs which are labelled incorrectly using Rhythmbox, but when I change the title or genre or correct spelling in reverts back to its original incorrect title.

Is there something I need installed to do this or am I expecting too much from Rhythmbox to be able to edit tags as well?

---

### Post by dearingj on 2010-03-27
Rhythmbox usually can edit tags. I'm guessing this is a permissions problem: you for some reason you don't have permission to write to those particular files. Try entering this command in a terminal:
```
chmod u+w /path/to/music/folder -R
```

That should give you write permissions to every file in your music folder.

---

### Post by Dobbie03 on 2010-03-27
I tried that but this is the response:


chmod: cannot access `/media/music': No such file or directory


All my music is on a external.

---

### Post by 2hot6ft2 on 2010-03-27
> **MattDobson said:**
> I tried that but this is the response:


chmod: cannot access `/media/music': No such file or directory


All my music is on a external.
You have to give it the correct path to your music folder that's what
 /**path**/**to**/**music**/**folder**
means, we don't know where your music is stored. Mine is on another partition in a folder by a name I gave it.

Is the external drive named music ?
Then it would be
/media/music

If the drive is named junk and the music folder is on it then it would be
/media/junk/music
get it
and if you have any spaces in the volume name of the drive you will have problems. Replace spaces with - or _

---

### Post by Dobbie03 on 2010-03-27
ah sorry, I put the path to my music  media/Music and it still came up with that result.

---

### Post by zeroseven0183 on 2010-03-27
There is bug report about having issues updating the song properties which could be the same as yours.
Check out [Bug #530372]("https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/530372") and [Bug #315708]("https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/315708")

---

### Post by Dobbie03 on 2010-03-27
I found the issue, I forgot the capital M for music.

Cheers to 2hot6ft2.

---

