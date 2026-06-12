---
title: "rsync problem."
date: 2009-11-18
forum: New to Ubuntu
---

### Post by Irishboy on 2009-11-18
Hey Guys,

I am completely new to linux and ubuntu as such. I recently installed 'wubi' ubuntu 9.10 and was going through the rsync utility since i had to back u some files. it is throwing me an error which googled but came up with nothing. i would appreciate if you guys could help me. here is the command i used to run the utility

rsync -azvv /home/path/folder1 /media/folder1 

here is the error i get at the terminal:

[B]sending incremental file list
delta-transmission disabled for local transfer or --whole-file
Files/
Files/syntax.pl
total: matches=0  hash_hits=0  false_alarms=0 data=3623

sent 3750 bytes  received 35 bytes  7570.00 bytes/sec
total size is 3623  speedup is 0.96[/B] 

thanks
Irishboy

---

### Post by XCan on 2009-11-19
I take it you're trying to sync files from your Ubuntu wubi container to your Windows partition? Mayhaps rsync doesn't like that for some reason. Could you try to sync to a directory in your wubi container
```

rsync -avz /home/path/folder1 /home/path/folder1testsync

```

---

### Post by meson2439 on 2009-11-19
If there is no urgency to archive the folders, why don't you do just 

```
rsync -r /home/path/folder1 /media/folder1
```

Also please check if the hard disk you are transferring it into is mounted or not, and be sure that the path exist. If it also gives an error, try adding sudo before rsync.

---

### Post by Irishboy on 2009-11-19
Hi XCan,

Your idea worked. i was trying to rsync from my wubi container to the win partition. i changed it and rsync'ed to a local folder and it worked. Thanks for the help guys

---

