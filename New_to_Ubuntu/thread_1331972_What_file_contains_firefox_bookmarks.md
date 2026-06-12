---
title: "What file contains firefox bookmarks?"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by Miljet on 2009-11-19
I am running 9.04 and want to move my bookmarks to another computer that I just set up. But I can't figure which file to copy. I thought that it was bookmarks.html located in the ~/.mozilla directory, but I copied it over and it didn't change anything.

I know that I can export the bookmarks from one machine and import them at the other machine, but that just adds the bookmarks to the default one on the new machine. It takes about as long to sort that out as to manually enter them one at a time.

---

### Post by winotree on 2009-11-19
That html file is turned off by default but you can change *browser.bookmarks.autoExportHTML*  to *true* in *about:config*.  The other one, the one you're looking for is *bookmarkbackups* in ~/.mozilla -- I usually just use the last one, having saved an html copy at Google Docs.  Good luck on the move.  :)

---

### Post by Miljet on 2009-11-19
Thanks for the speedy response, neighbor. I'm off to try that. Will report back.

---

### Post by sgosnell on 2009-11-19
With Firefox 3, the bookmarks are no longer stored in bookmarks.html, but in places.sqlite, an sql database.  In order to transfer your bookmarks, start at Bookmarks, Organize Bookmarks, and either select Backup or Export.  You can get a .json file of a backup of your bookmarks, or export as html.  Put that file on your new machine, and import it via the file menu.

---

### Post by Miljet on 2009-11-19
Thanks sgosnell. That is exactly what I was trying to avoid, but it looks like that is the only choice. I had hoped that I could replace the entire file instead of merging two bookmarks files and having to sort through the resulting mess.

---

### Post by kaibob on 2009-11-19
I just copy over the places.sqlite file. I did that when I did a fresh install of 9.10 (from 9.04), and it worked fine. It overwrites the existing bookmarks on the target machine, but that appears to be what you want.

---

### Post by winotree on 2009-11-19
Oh, man, I never had to do that.  A copy of a file or a folder was always good enough -- guess I'll have to read about this merging process.

---

### Post by sgosnell on 2009-11-19
Just delete the bookmarks on the computer you're importing into, and you won't have to do any merging.

I use Xmarks to sync my bookmarks, and thus have identical bookmarks on all my computers.  It's a Firefox extension, and it works well for me.

---

### Post by egalvan on 2009-11-19
I always copied the entire *profile* directory.

---

### Post by sgosnell on 2009-11-19
That's probably the most complete method, because you probably want more than just bookmarks.  Having the plugins, extensions, etc without having to reinstall everything is nice.

---

### Post by oldfred on 2009-11-20
+1 for egalvan's copy entire profile.

I actual share profiles for both firefox and thunderbird in a shared partition for windows and Ubuntu. Then when I travel I copy the entire profiles to my portable and when home copy them back.
I had to edit profile.ini with the new default profile, but now they have a profile manager.

[http://kb.mozillazine.org/Profile_Manager](http://kb.mozillazine.org/Profile_Manager)

---

### Post by Miljet on 2009-11-20
Just as a follow up, I figured out how to do exactly what I wanted which was to replace the default bookmarks with one from another computer. I used the backup option to create a .json file in the desktop. I then copied that file into the ~/.mozilla/firefox/ptqq2wj9.default/bookmarkbackups subdirectory of the computer you are installing to. Then run restore on that computer, select the date of the file you just copied, and you are done.

---

### Post by sgosnell on 2009-11-20
Texas City didn't explode again this week, did it?  I didn't hear anything, but you never know.  ;-)

---

### Post by Miljet on 2009-11-21
Nope, we are all still here, happily running Ubuntu on all three computers!

---

