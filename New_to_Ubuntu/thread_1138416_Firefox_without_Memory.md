---
title: "Firefox without Memory"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by Doc Catfish on 2009-04-26
My firefox has lost its memory.  It lost its bookmarks and all its history.  I can not use back function to return to previous page.  

I recently installed google earth.   I used forums learn to change name of libcrypto file.  

Any help would be greatly appreciated

---

### Post by llamabr on 2009-04-26
This happened to me once, and it turned out the disk was full.  Try doing an 

```
sudo apt-get clean
```

and cleaning out your home dir of trash.

---

### Post by lukjad on 2009-04-26
EDIT: llamabr is most likely the right one. Start with his. If that command doesn't fix it, try mine after.

Well, there are two possibilities. One, something is stopping Firefox from storing data, or two, there was a setting in Firefox that tells it to not save its history. 

Close all instances of Firefox and open your home directory (*Places->Home Folder*) and unhide the hidden folders (Ctrl+H). Then go to the **.mozilla** folder and rename it to **bk.mozilla**. Then reopen Firefox and see if that fixes the problem. If it does, then you know it was only a setting. If not, then we can try something else.

---

### Post by Doc Catfish on 2009-04-26
Thanks for your help

007 that got firefox working.  I still have lost all my bookmarks, but at least it works.

---

### Post by cariboo on 2009-04-26
Your bookmarks are probably still in the backup mozilla directory. Open nautlus and navigate to the mozilla directory you renamed then go to firefox/xxxxx.default, where xxxx is a string of random letters and numbers, this is where you bookmarks file is located, it is called bookmarks.html

---

### Post by Doc Catfish on 2009-04-26
Again thanks;

I am not familiar with nautilus.  But, I found a file called 'bookmarkbackups'  in there I found some items with dates followed by .json

Are those what I'm looking for and if so what do I next?

---

### Post by lukjad on 2009-04-26
Close Firefox and then take these files and copy them to your new firefox/[RANDOM].default/bookmarkbackups folder. Then open Firefox and see if the bookmarks are there.

---

### Post by Doc Catfish on 2009-04-26
I can find only one 'bookmarksbackup' folder.  It is in places>home>bk.mozilla>firefox>xxxxdefault> then bookmarkbackups

I do have a firefox folder found places>home>firefox  and there is a default folder there.  There isn't a bookmarksbackup folder in that default.  Also that default folder doesn't have the random symbols preceding it.

And again thanks.

If it makes any difference--Once I renamed the mozilla folder the I think it came back as the earlier 2. version of firefox rather than the 3. version

---

### Post by lukjad on 2009-04-26
Oh, it's probably because you need to unhide the .mozilla folder again (*Ctrl+H*). Look for a .mozilla folder and the bookmarksbackup folder within it. See if that works.

---

### Post by Doc Catfish on 2009-04-26
Bingo

You folks are great

---

### Post by lukjad on 2009-04-26
Our pleasure. :) 

The bookmarks are back now?

---

### Post by Doc Catfish on 2009-04-26
Yes they are with ubuntu forums added :D

---

### Post by lukjad on 2009-04-27
Great! Also, as a tip, go to *Bookmarks->Organize Bookmarks->Import and Backup->Export HTML*. This will make a single, easily copied HTML files that you can read of all your bookmarks.

---

### Post by Doc Catfish on 2009-04-28
Well it happened again.  I used the same fix, but is there something in googleearth that causes this problem?  Also should I post this elsewhere?

---

