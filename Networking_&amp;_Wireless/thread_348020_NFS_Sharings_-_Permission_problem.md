---
title: "NFS Sharings - Permission problem?"
date: 2007-01-28
forum: Networking &amp; Wireless
---

### Post by juan_kerr on 2007-01-28
Hi,

I'm using Kubuntu 6.10 on one PC and Ubuntu 6.10 on another. Both are my first ventures into Linux, which has been rather interesting over the last month. 

I have set up NFS file sharing between both machines and can happily see and access files on each (thanks to some excellent how to's on this site). 

However, I cannot seem to copy/cut and past between machines and it is really starting to annoy me now. I thought I had set permission correctly on both machines. I have basically set the root, user and others all to be able to create and delete files and read and write.

My fstab entries for mounting the network drives also has 'rw' in the options. 

What am I doing wrong? A morons guide would be great if anyone has the time. 

Thanks,

Fraser

---

### Post by kidders on 2007-01-28
Hi there,

I recently responded to a similar thread at [http://www.ubuntuforums.org/showthread.php?t=347203](http://www.ubuntuforums.org/showthread.php?t=347203) that might be of interest to you.

---

### Post by RandomJoe on 2007-01-28
I can think of two possibilities right off from my experiences - 

Do you have (rw) permissions in /etc/exports on the server?  An example from mine:
```
/raid           192.168.144.0/255.255.255.0(rw)
```

And are you trying to write to the actual directory you shared?  I've not been able to get that working either, I always have to create a subdir of the shared dir and I can write to that.  (Obviously, making the subdir ON the server since I can't do that via NFS.)  So the above share for me has a few different subdirs, /raid/archive /raid/mmedia /raid/isos so forth and I can put things in those directories, but NOT right into /raid.

I have no idea why, I just got it working and went on... :rolleyes:

---

### Post by kidders on 2007-01-28
> **RandomJoe said:**
> I have no idea why, I just got it working and went on... :rolleyes:That probably has to do with the way you're mounting your NFS shares. To be sure, try comparing who owns things you can & can't write to ... You may be mounting your NFS shares as root.

As I mentioned in my other post, you can explicitly instruct your NFS server not to squash attempts to write to shares as root. A better alternative might be to use a different account to mount the share, though.

---

### Post by juan_kerr on 2007-01-28
Thanks for your replies, I now have it working using the techniques you described. 

Took a bit of messing about, but that's just down to inexperience and general messing about. 

It does what I want now at least, which is a huge step forward. I'll start worrying about security and best practice once I understand how this all goes together. I don't just now to be honest.

Thanks again.

---

