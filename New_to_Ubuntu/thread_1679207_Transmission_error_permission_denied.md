---
title: "Transmission error permission denied"
date: 2011-01-31
forum: New to Ubuntu
---

### Post by Johnny420 on 2011-01-31
I am having  trouble w/ transmission downloads
Transmission connects starts to download and then returns permission denied error
I have it set to download into my standard Downloads folder so I don't see what the problem is

---

### Post by weedeater64 on 2011-01-31
What's the exact error?

Is it an error from the external net maybe?

---

### Post by mr.farenheit on 2011-01-31
i've been having a similar problem. transmission won't download at all from external torrents but it will download the ubuntu iso's. in your case right click the folder and check the permissions marked, then if so, change them if needed.

---

### Post by Johnny420 on 2011-01-31
the exact error is
Error: Permission denied (/media/movie.avi)

---

### Post by matt_symes on 2011-01-31
Hi

Who is the owner and what are the permission of /media/movie.avi ?

```
ls -l /media
```

That is a small L above. Where are the files set to download to in transmission ? 

Kind regards

---

### Post by arnab_das on 2011-01-31
simple solution, try another torrent client :)

deluge is a good one. there are a million of these torrent clients listed on ubuntu software center. search and download.

---

### Post by Johnny420 on 2011-02-01
downloaded deluge and it is working fine...Thanx for the tip

BUT...the question remains.

I am kinda C.D.O. (O.C.D. in the RIGHT ORDER!!) and I need to understand why My machine has stopped doing something that it was doing just fine.

ls -l /media returned this:

drwx------ 8 johnny johnny 4096 2011-01-31 15:25 Data

I still dont understand the permissions code at the front of this line

---

### Post by matt_symes on 2011-02-01
Hi

> 
ls -l /media returned this:

drwx------ 8 johnny johnny 4096 2011-01-31 15:25 Data

the folder /media does not have a file called movie.avi so i can only assume it's an issue with transmission. Did you move the file movie.avi ? Is it still referenced in transmission ? If it is, try removing it from transmission.

This is a tutorial on file permissions.

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Kind regards

---

