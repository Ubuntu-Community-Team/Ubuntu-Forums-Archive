---
title: "syncing two folders where files sourcefiles without brackets[] and target files with"
date: 2008-04-08
forum: Networking &amp; Wireless
---

### Post by byenary on 2008-04-08
Hello,
Not realy ubuntu but general linux but since I only and always use ubuntu i'll post it here :)
I am familiar to sync two folders using rsync or cp -rvu.
The problem that i'm facing now is i have a remote ssh folder wich contains a bunch of files with this structure folders main folder source subfolders 10000,11000,12000 and so on each subfolder contains 10000 files.
The files on the remote location are in this form 10001.RTE,10002.RTE,10002.RTE ....
On the target system it needs to be the same folderstructure but the all files need to be in this shape [10001].RTE,[10002].RTE ...
So it seems that i cant't use rsync in this situation, can sombody give a direction on how is should or could handle this.
Take in count that source dir is more than 1 TB.

Thx a lot

---

