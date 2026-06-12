---
title: "Finding bookmarks on dead HD"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by fieroguy19 on 2010-05-25
So my HD would not boot ubuntu so I used the install disk to gain access to the hard drive and copied the entire HD over to an external drive. I then did a fresh install on a new HD but cannot seem to find the bookmarks when I look through the files that were backed up on the external drive.

Thanks

---

### Post by tgalati4 on 2010-05-25
tgalati4@tpad-Gloria7 ~/.mozilla/firefox/4n0pfp5v.default $ ls -la book*
-rw-r--r-- 1 tgalati4 tgalati4 14475 2009-07-31 06:20 bookmarks.html

bookmarkbackups:
total 444
drwx------  2 tgalati4 tgalati4   140 2010-05-03 09:05 .
drwxr-xr-x 10 tgalati4 tgalati4   960 2010-05-24 21:34 ..
-rw-------  1 tgalati4 tgalati4 77909 2010-04-18 15:39 bookmarks-2010-04-18.json
-rw-------  1 tgalati4 tgalati4 78567 2010-04-22 17:48 bookmarks-2010-04-22.json
-rw-------  1 tgalati4 tgalati4 80275 2010-04-29 21:58 bookmarks-2010-04-29.json
-rw-------  1 tgalati4 tgalati4 81946 2010-05-01 16:11 bookmarks-2010-05-01.json
-rw-------  1 tgalati4 tgalati4 81858 2010-05-03 09:05 bookmarks-2010-05-03.json

For firefox, bookmarks are normally hidden in:

.mozilla/firefox/XXXXX.default/bookmarks.html

---

