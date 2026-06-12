---
title: "file transfer to NFS share crash"
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by daanemanz on 2008-05-11
After having too much trouble with setting up a Samba share in Hardy, I decided to give NFS a go. I followed some guide to set it up on my Hardy x86_64 server, which went -surprisingly- well.

Also, I can mount the NFS share on my laptop (also Hardy, x86_32) and I can transfer files from the server to my laptop. However, if I try to transfer files back to the server, this seems to stop after the first ~30 MB and then proceeds only VERY slowly.

What could be the problem here? I attached my /etc/fstab for reference. Any help would me much appreciated!

---

### Post by nixscripter on 2008-05-11
Two things strike me, but I don't know if they will solve the problem.

First, I notice that you are specifying the buffer sizes (rsize and wsize options). Supposedly it is supposed to make your NFS connection faster, but I think it might have an effect on the client-side caching that NFS does. Try removing it just to see what happens.

Second, jyou specified a timeout, but not **soft**. Is that implied? I would put it in explicitly just in case.

I would also simply add that NFS is designed for optimizing transfers of many small files (less than 50 MB). Having used it in several capacities, single file transfers are just not efficient. What is "very slowly" in terms of data rate?

---

### Post by daanemanz on 2008-05-12
> **nixscripter said:**
> Two things strike me, but I don't know if they will solve the problem.

First, I notice that you are specifying the buffer sizes (rsize and wsize options). 

Well, I tried that, but still to no avail. Also tried to remove the timeout option, still nothing changed.

> **nixscripter said:**
> Second, jyou specified a timeout, but not **soft**. Is that implied? I would put it in explicitly just in case.

Sorry, I'm quite new to NFS, so I don't know what this means actually. Could you explain it or can I find it somewhere on the internet?

> **nixscripter said:**
> I would also simply add that NFS is designed for optimizing transfers of many small files (less than 50 MB). Having used it in several capacities, single file transfers are just not efficient. What is "very slowly" in terms of data rate?

Very slowly means that it takes about 40 minutes to transfer a flac album of ~320 MB. First the file transfer dialog gets stuck at about 30 MB and then only slowly proceeds. About 100 kb/s max.

---

### Post by nixscripter on 2008-05-13
In a nutshell, NFS treats the server like a physical device. If a process reads or write, and the server isn't there, the process trying to do the I/O will wait (in an uninterruptable sleep). Hard mounting means the process should wait literally forever. Soft mounting means to give up in failure after a timeout. In this situation, I assume you want soft.

When I have done sustained transfers over NFS, such as copying a single backup tarball, I have found that NFS caching just causes "bursty" traffic patterns. It will dump a large chunk at full speed down the network, and then totally lock up (that uninterruptable sleep I mentioned); then dump another chunk, and lock up. These chunks are probably 50 to 100 MB each, and the lockups are between 10 and 30 seconds. It is quite disconcerting to look at, because the process will not listen to anything, but is in fact normal as far as I can tell.

If this pattern is similar to what you're getting, don't worry about it. If not, please describe what happens over time in greater detail.

---

### Post by daanemanz on 2008-05-13
Hi nixscripter,

thanks for the reply. I already managed to speed things up a little - by adding async,rw,no_root_squash,**no_wdelay**,subtree_check to my /etc/exports file. Particularly the no_wdelay option seemed to speed the transfers up (from ~100kb/s to ~2MB/s).

The bursty pattern that you described is exactly what I see when I do a **write** file transfer to my server. However, when I transfer from the server to my laptop, it goes very smooth. But as this is normal, I won't worry any more.

Thanks for the help!

P.S. I won't use the *soft* option, as I don't know how to use it. Could you tell me how this is done?

---

### Post by nixscripter on 2008-05-14
To use soft, you don't put it in /etc/exports. Instead, you have the client machine mount it soft.

Add it either to the mount command: ```
mount -t nfs -o **any-other-opts**,soft server:/mnt/dir /local/dir
``` or if you mount the filesystem at boot, put it in the /etc/fstab file:
```

# <file system>     <mount point>   <type>  <options>         <dump>  <pass>
server:/remote/dir  /local/dir      nfs     **other-opts**,soft   0       0

```

Hope this helps.

---

### Post by trash on 2008-09-02
> **daanemanz said:**
> Hi nixscripter,

thanks for the reply. I already managed to speed things up a little - by adding async,rw,no_root_squash,**no_wdelay**,subtree_check to my /etc/exports file. Particularly the no_wdelay option seemed to speed the transfers up (from ~100kb/s to ~2MB/s).

The bursty pattern that you described is exactly what I see when I do a **write** file transfer to my server. However, when I transfer from the server to my laptop, it goes very smooth. But as this is normal, I won't worry any more.

Thanks for the help!

P.S. I won't use the *soft* option, as I don't know how to use it. Could you tell me how this is done?

no_wdelay really helps with speed however freeze ups still happen, anybody figured it out yet?
I watched a whole movie lastnight over NFS and aside from 5-6 very minor 1-2 second pauses it worked flawlessly.
Could older hardware being used as a server be a factor in this issue? My clients are all newer/faster machines than the server which is a P3 666mhz/384ram

---

