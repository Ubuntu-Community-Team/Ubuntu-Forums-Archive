---
title: "Opening files in a hidden partition, how?"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by Makaaveli on 2009-06-11
How do i open up files in a hidden partition? I cannot see the partition at all on my ACER laptop.

So i wanted to be able to access the files within this hidden partition using UBUNTU live CD.

The hidden partition is called PQSERVICE. And the file i need to access is called "aimsdrs.dat" - i want to open that with a text editor.

Please can someone help me with this simple request.

---

### Post by muteXe on 2009-06-11
You have to mount the partition first.  Google "ubuntu partition mounting" or something like that.
What filesystem is it as well?

---

### Post by Makaaveli on 2009-06-11
The file system is ntfs

The hardrive is called PQSERVICE.

And under Partition it says - /dev/sda1

^^ i got that info from GParted.

Btw i'm a real beginner and i dont want to make any irriversable mistakes =/

---

### Post by bruno9779 on 2009-06-11
```
sudo mount /dev/sda1
```

should do

---

### Post by Makaaveli on 2009-06-11
it says;

mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab

---

### Post by muteXe on 2009-06-11
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

read that.

---

### Post by Makaaveli on 2009-06-11
Then i typed in;

**sudo mount /dev/sda1 /mnt**

and i think it did something, but nothing was showing. So i tried again and it said;
[B]
fuse: mount failed: Device or resource busy[/B]

---

### Post by muteXe on 2009-06-11
Ideally you should create your own folder to mount to (/mnt already exists in the filesystem), but that should work.
Navigate to /mnt, can you see your drive now?

---

### Post by Makaaveli on 2009-06-11
> **muteXe said:**
> Ideally you should create your own folder to mount to (/mnt already exists in the filesystem), but that should work.
Navigate to /mnt, can you see your drive now?

if you mean can i see my hidden partition in "file browser" then the answer is no.

In GParted it says /mnt under "mount point" column.

What does this mean? And how can i see my hidden partition files from this.

---

### Post by Makaaveli on 2009-06-11
OMG IT WORKED! THANKS ALOT muteXe!

Now that i've read the file i wanted to know, do i need to unmount anything or can i just leave it? It's a live cd afterall, so no data gets saved right?

---

### Post by muteXe on 2009-06-11
Make a folder in your home directory and mount it there.
Good info here: [http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/mnt.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/mnt.html)

Something like:
```

mkdir pqserviceDrive
```
in your home folder, then:
```

sudo mount /dev/sda1 ~/pqserviceDrive
```

---

