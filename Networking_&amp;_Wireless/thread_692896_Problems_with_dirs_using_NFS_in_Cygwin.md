---
title: "Problems with dirs using NFS in Cygwin"
date: 2008-02-10
forum: Networking &amp; Wireless
---

### Post by x300 on 2008-02-10
I've set up a computer running Mythbuntu and I want to access all my music/videos... on my windows computer without scp:ing them over. 
Therefore I've succesfully set up an NFS server using Cygwin, but when I try to mount files and folders that are outside Cygwins own structure (i.e. trying to mount /cygdrive/d/) I get permission denied in Mythbuntu.
I can see the files when i type "sudo ls mnt", and I can copy them with "sudo cp mnt/movie.avi .", but I want MythTV to automaticly see these files and update the database. (This works if the files are in "C:\Cygwin\somwhere" and I mount them from there)

Does anyone have any idea for a fix?

---

