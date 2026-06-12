---
title: "[SOLVED] Firefox: Bookmarks Disappear from Toolbar"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by ms2756 on 2009-01-05
Alright, I just can't figure this out:
I drag a tab onto the bookmark toolbar and then they disappear the next time I start Firefox. I am almost sure the history gets erased too. That's just a pain in the ***. And yeah, I installed my Ubuntu yesterday.

Thanks in advance.

---

### Post by blazemore on 2009-01-05
Press Alt+F2 and type in "firefox -profilemanager" without the quotes and press Enter.
Click the profile "Default" or similar, and press delete.
Now create a new profile with the default settings (It should be clear how to do this).

---

### Post by ms2756 on 2009-01-05
Sorry, kinda fell asleep.
Tried it, said "could not open location..." The terminal command doesn't work either.
Any more suggestions?

---

### Post by theacerguy on 2009-01-05
reinstall firefox i would say or if you deleted things like cookies that might do it not recomended option reinstall ubuntu (i had to loads with xp and opensuse only installed ubuntu yesterday)

---

### Post by ms2756 on 2009-01-05
Thanks, but I don't want to reinstall firefox - I don't see how that would change anything (it's the latest version). This post should make the thread fresh, so maybe someone will suggest something else...

---

### Post by cong06 on 2009-01-05
If you re-install it should help to purge your settings.

```
sudo apt-get purge firefox
sudo apt-get install firefox
```

Is your home directory full? Could you be clear on where it throws the error: "could not open location..." ?

---

### Post by ms2756 on 2009-01-05
I'm sorry for being unclear. There is no error, just when I close Firefox and then reopen it, all the favorites get erased from the bookmarks toolbar. I really don't know how to explain it any clearer...

Ok, say you go to a page [www.youtube.com](www.youtube.com) and click "star" in the right corner of the command line. That adds "YouTube" to favorites. However, after closing and then opening Firefox again, the bookmarks/favorites disappear, almost as if all cache has been erased (I'm actually pretty sure all browsing history gets erased).

If you don't know the answer to that question right away, never mind. I'll just take it up with Firefox.

---

### Post by ms2756 on 2009-01-05
I'm sorry for being unclear. There is no error, just when I close Firefox and then reopen it, all the favorites get erased from the bookmarks toolbar. I really don't know how to explain it any clearer...

Ok, say you go to a page [www.youtube.com](www.youtube.com) and click "star" in the right corner of the command line. That adds "YouTube" to favorites. However, after closing and then opening Firefox again, the bookmarks/favorites disappear, almost as if all cache has been erased (I'm actually pretty sure all browsing history gets erased).

If you don't know the answer to that question right away, never mind. I'll just take it up with Firefox.

---

### Post by cong06 on 2009-01-05
> **ms2756 said:**
> 
Tried it, said "could not open location..." The terminal command doesn't work either.

What were you doing when it said this? that's what I was asking.

[QUOTE=ms2756]Ok, say you go to a page [www.youtube.com](www.youtube.com) and click "star" in the right corner of the command line. That adds "YouTube" to favorites. However, after closing and then opening Firefox again, the bookmarks/favorites disappear, almost as if all cache has been erased (I'm actually pretty sure all browsing history gets erased).[/quote]
I assume you know that when you click the star, bookmarks get placed in an "unsorted" folder that you can only access if you go to:
Bookmarks > Organize Bookmarks
and scroll down to the folder:
"Unsorted Bookmarks"

---

### Post by alecz20 on 2009-07-09
You marked this as solved, how did you solve it?

I have the same problem and it happened only recently.

I have write permissions on all files in .../,mozilla/firefox

If I add a bookmark it doesn't get saved when I close firefox, so when I restart it I don't see it anymore.

So how was this solved?

---

