---
title: "Rename Audio Track"
date: 2010-10-20
forum: New to Ubuntu
---

### Post by tikitikimaji on 2010-10-20
So I have some music files that I cannot modify.  I would like to change the name of the artist for organization purposes but cannot seem to alter the file in any way, other than the name of the track.  The artist name remains "unkown."  In Rhythmbox I can change the name of the artist, but when I close it and re-open it, the name is back to Unknown.  I even tried converting the file to a different audio format.

Is there any way to reset the audio information?

Thanks

---

### Post by plucky on 2010-10-20
> **tikitikimaji said:**
> So I have some music files that I cannot modify.  I would like to change the name of the artist for organization purposes but cannot seem to alter the file in any way, other than the name of the track.  The artist name remains "unkown."  In Rhythmbox I can change the name of the artist, but when I close it and re-open it, the name is back to Unknown.  I even tried converting the file to a different audio format.

Is there any way to reset the audio information?

Thanks

Make sure you are the file owner ```
ls -l <name of file>
``` after you cd  to the correct directory.

Or 

Right click on the file and select "Properties" permissions tab and make sure your username is the current owner.

Then use rhythmbox to change the artist name.


Good Luck

---

### Post by tikitikimaji on 2010-10-20
Under properties, I am the owner but I still can't change the artist, album or any other info.

And when I type in the code it says no file or directory, was the <file name> the same as location from the properties box?

---

### Post by MartyBuntu on 2010-10-20
**EasyTAG** is in the repositories.

It's a fairly comprehensive MP3 re-tagger. It'll do what you're looking for.

---

### Post by tikitikimaji on 2010-10-20
ok EasyTag was shaky, but it worked!  Thanks!

---

