---
title: "Finding files on my drives"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by OllieGab on 2009-02-01
I'm using Beagle in Ubuntu 8.10 to try to find files on my harddrive. For instance, trying to locate the bookmarks file for Firefox; whatever I put in the search text field (bookmarks/bookmark/bookm) I just get a message "no files found".
Does Beagle only serch my home folder? Surely there must be a way of finding ALL files on my computer, only if it's just "to look at"?

Cheers Ollie

---

### Post by RealPSL on 2009-02-01
I do not use beagle but based on experience with others there is a good possibility that by default it is only searching your home directory since that is where most of the files you have access to with sudo/gksudo would reside. You should however be able to change this configuration using **System > Preferences > Searching and Indexing**.

---

### Post by yeats on 2009-02-01
Could it be omitting hidden files (dot files)?  The firefox directory actually lives in your home directory in the hidden directory .mozilla (that's "dot" mozilla).

---

### Post by OllieGab on 2009-02-01
I added a couple of ticks in Application>System....
and it seems to have done the trick!
Thanks

PS I just realised that the bookmark file I was after can easily be exported from within Firefox, to wherever I want!

---

