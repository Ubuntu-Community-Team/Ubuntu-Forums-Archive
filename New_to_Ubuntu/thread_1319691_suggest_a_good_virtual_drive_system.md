---
title: "suggest a good virtual drive system?"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by ChubbySauce on 2009-11-08
for reading iso and junk?

---

### Post by noelvh on 2009-11-08
Virtual box. I use the VB fro the sun's web site not the one from the repos. I think it is better.

Very easy to setup and use.

Noel

---

### Post by ajgreeny on 2009-11-08
> **noelvh said:**
> Virtual box. I use the VB fro the sun's web site not the one from the repos. I think it is better.

Very easy to setup and use.

Noel
+1
The only one I've ever used, but it certainly works well.

---

### Post by falconindy on 2009-11-08
Virtual **drive**, not virtual machine. Linux doesn't require extra software to read an iso like windows does. Just create a directory somewhere convenient and mount your image to it, e.g.

```
mkdir -p $HOME/isomount
sudo mount -t iso9660 /path/to/image.iso $HOME/isomount
```

---

### Post by ajgreeny on 2009-11-08
On my machine iso files, eg the ubuntu iso or other disk images are opened by archive-manager or mounted by archive-mounter without the need for any further action on my part.
Is that what you want?  If so, just right click on the iso file and choose what you want to use.

---

### Post by ChubbySauce on 2009-11-11
I cant find virtual box in synaptic and iso files wont open on their own :c

---

### Post by bodhi.zazen on 2009-11-11
> **falconindy said:**
> virtual **drive**, not virtual machine. Linux doesn't require extra software to read an iso like windows does. Just create a directory somewhere convenient and mount your image to it, e.g.

```
mkdir -p $home/isomount
sudo mount -t iso9660 /path/to/image.iso $home/isomount
```

+1

---

### Post by peacen1k on 2009-11-27
fujisan@fujisan-laptop:/$ sudo mount -t iso9660 /home/fujisan/Desktop/pup-431.iso /media/iso
mount: /home/fujisan/Desktop/pup-431.iso is not a block device (maybe try `-o loop'?)


uh oh- I'm hacking away at the command line without the faintest understanding of the most basic commands.

Why doesn't that line work??

Any help appreciated.

---

### Post by NickJones on 2009-11-27
> **ChubbySauce said:**
> I cant find virtual box in synaptic and iso files wont open on their own :c
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

