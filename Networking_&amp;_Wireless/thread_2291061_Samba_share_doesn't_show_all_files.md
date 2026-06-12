---
title: "Samba share doesn't show all files"
date: 2015-08-17
forum: Networking &amp; Wireless
---

### Post by Myoldmopar on 2015-08-17
I'm on 14.04.  I have a Netgear router that has a (readyshare) USB port where I keep a 2TiB drive as our home backup.  It works well, I am able to mount it in Ubuntu and access it on Windows boxes with _almost_ no issue.  On Ubuntu, it doesn't seem to list all the files in the folders.  It lists an odd number, like 141 in one folder and 148 in another.  And I can verify by accessing them on other machines or hooking it up directly to my machine, that it has much more than that.

Any thought on what samba issue could limit the number of files shown?

---

### Post by ablinkin on 2015-08-17
have you tried from a command line with a ls -al?

---

