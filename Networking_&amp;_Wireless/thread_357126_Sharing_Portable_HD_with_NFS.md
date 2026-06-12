---
title: "Sharing Portable HD with NFS"
date: 2007-02-09
forum: Networking &amp; Wireless
---

### Post by alphane on 2007-02-09
Hi guys,

Managed to get NFS sharing going between my Dapper desktop and my Dapper laptop using another of the excellent comminity how-to's.

My question now is, how can I, if at all, share my External USB HD that's semi-permanantly hooked up to my desktop with my laptop?

On my desktops exports list I have something like the following (I'm at work currently, so can't access directly)

/home/andy (+ all the share connections + wr options)
/media/portableHD (+ all the share connections + wr options)

On my laptop I can mount my home folder and gain access to my files on my desktop PC, but when trying to mount the HD it says the file (device?) wasn't found.

Now, I don't know whether I'm allowed to share anything outside of my home folder.  But if I am, I'd think I'm going wrong by trying to share the /media/portableHD folder.

Should I be trying to share the /dev/(whatever the HD is called) instead?

Any help appreciated, I'm trying to set it up so I can watch downloaded material on my TV downstairs through my laptop, rather than having to watch it over my desktop upstairs.

Thanks in advance.

---

### Post by Jussi Kukkonen on 2007-02-09
Sounds like you are doing it right... Some things to check :
1. /etc/exports is senisitive to whitespace -- make sure the line is exactly like the working ones
2. have you remembered to run ***exportfs -ra*** after editing exports-file? (/proc/fs/nfs/exports will show active exports I believe)

---

### Post by alphane on 2007-02-09
Thanks for the response,

The whitespace thing I wasn't aware of, will check that when I get home.

I am running **exportfs -ra** after changes, and also something else, can't remamber what right now lol, probably stop/starting NFS server (said to do it in the tutorial).

Hopefully, my mistake will be as silly as leaving an extra line or space at the end of the file!  It's going to get really annoying if I have to copy files from my HD to my desktop's Home folder to watch things over my laptop...

---

### Post by Jussi Kukkonen on 2007-02-09
> It's going to get really annoying if I have to copy files from my HD to my desktop's Home folder to watch things over my laptop...
You won't -- I do pretty much the same thing you're trying to do, my exports file looks like this:
```
/media/data/music 192.168.0.106(rw,sync) 
/media/data/pics 192.168.0.106(rw,sync) 

```

---

### Post by eecharlie on 2007-03-31
found answer elsewhere, don't see where to delete messages!

---

