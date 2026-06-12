---
title: "Need to mount an NTFS...."
date: 2010-03-19
forum: New to Ubuntu
---

### Post by TurnOfTide on 2010-03-19
I dual boot. So I want to share media between the Ubuntu and Windows7. 
 
 
I use Ubuntu for programming. I use windows for gaming/media/running ps3 media server.
 
I still listen to music and download torrents when I am programming on Ubuntu.
 
 
 
My goal is to create an NTFS partition for media files, so of course both OS's can see them. Then I think it would be ideal to mount ~/Music to [new partition]/Music   (and repeat this for Downloads/Videos/Documents).
 
 
How should I best accomplish this task? I am mostly unsure of if this will mount properly. I am also open to other suggestions.

---

### Post by wjm on 2010-03-19
If you have an NTFS volume already you can mount it this way:

"sudo mount /dev/hda5 /path/where/you/mount/it -t ntfs"

replace "hda5" with whatever your drive is.

---

### Post by sisco311 on 2010-03-19
Mount the partition under /media/<mountpoint>:

[http://psychocats.net/ubuntu/mountwindows#ntfsconfig](http://psychocats.net/ubuntu/mountwindows#ntfsconfig)

and create symbolic links in your home directory:
```
ls -s -T /media/<mountpoint>/Music ~/Music
...
```

---

