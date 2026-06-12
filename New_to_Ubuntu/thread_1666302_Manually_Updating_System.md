---
title: "Manually Updating System"
date: 2011-01-13
forum: New to Ubuntu
---

### Post by Rex Bouwense on 2011-01-13
When completing a search for updates manually, what is the difference between failed, ignore, hit, and done?  I have used the command line and the Update Manager and it never bothered me before but because I do not know and I am the type of person who has to know, I have to ask.

---

### Post by wannabegeek on 2011-01-13
I offer a guess...

hit --->found an update
ignore -->an update for a package related to one on your sources.list but not required
failed ---->problem with source or other....upate failed
done ----->update successful


I'll be curious to see if I am right when some one who actually knows responds...
wbg

---

### Post by Rex Bouwense on 2011-01-13
Thanks WBG.  It sounds good.  I was just curious.  If anyone really knows perhaps we will get an answer.

---

### Post by Smart Viking on 2011-01-13
I'm not sure that what i know is right.

When you update with apt-get, you look through the sources and see if there are new DiffIndex-es  to download for the sources, if there are changes, it will make a hit and download, if there are no changes, it will ignore it, if it failed, it might couldn't contact the server, it it's done it have download the DiffIndex
The DiffIndex is basically just a file which contains only the differences between what your system currently contains for which updates have an update etc. Warning: Don't take the above to be correct.

---

