---
title: "use \ partiton like \home?"
date: 2010-02-25
forum: New to Ubuntu
---

### Post by grobar87 on 2010-02-25
i have free space on my \ partiton,so can i use that for my movies,and how to copy there?
can't create new folder....:S (tnx and sorry for my english :)

---

### Post by Seanuntu on 2010-02-25
The right way to do this would be to boot from the live CD and use Gparted to reallocate space from your root partition to whatever partition contains /home.

The half-assed way to do this is to create a folder in / and then create a link to it within your home directory.

sudo mkdir /extra_space
sudo chown youruser:yourgroup /extra_space
cd ~
ln -s movies /extra_space

Now /your/home/dir/movies will actually point to /extra_space.

You also now risk filling up your root folder which could lead to a non-responsive system.

---

### Post by QIII on 2010-02-25
I would not recommend doing stuff like that in your / partition any more than I would recommend doing it in a Windows system folder.

You risk permissions issues and filling your / partition to the extent that your system will not run (as above) or you will not be able to install new applications.

What is the size of your / partition?  /home?

Typically, it is best to keep your / partition to a reasonable size and make your /home partition as large as possible.  For reasons just like this.

---

### Post by undecim on 2010-02-25
5GB is usally a good size for a root partition.

You can use a livecd with gparted to resize your partitions, but make sure you have any important files backed up, because if something goes wrong during resizing partitions, you can lose your files.

Also, if you get an error from gparted, make sure you save the report somewhere so that the people on the forums can help you fix it. Somewhere like a thumb drive, burn it to a CD... just don't put it on any of the partitions that gparted was messing with.

---

### Post by grobar87 on 2010-02-26
my root partition is 20 GB and i have 12GB free space...and my home partition is 100GB but is full :S
i don't want to loss my files,i just want to move that 12 gb to home partition...
i will try gparted.
thx again :)

---

### Post by 3rdalbum on 2010-02-26
You need to be root to modify anything outside your home directory. You can open up a file browser as root by typing in this command:

```
gksudo nautilus
```

Alternatively, you can add an "Open as Administrator" option to the right-click menu of your file browser by installing the "nautilus-gksu" package from Synaptic.

---

### Post by codemaniac on 2010-02-26
slice out your free space from root using gparte and make it(free sp.) NTFS this way you can use it as data partition, and it will be mounted automatically as a read write file system in ubuntu and various modern distros..

---

### Post by codemaniac on 2010-02-26
your slashes are on wrong way.. ;^)

---

### Post by grobar87 on 2010-02-26
ok i solved the problem
tnx to all ;)

---

### Post by Rayve on 2010-02-26
Glad you got it working!  :)

You can mark the thread as solved by clicking on the "Thread Tools" at the top of this thread and then "Mark Thread as Solved".

---

### Post by profeta81 on 2010-02-26
> **grobar87 said:**
> ok i solved the problem
tnx to all ;)

hi

just out of curiosity, how did you solve it?

and btw... my smallest opinion... you have movies on your \home? if so the best (according to my views) way to really solve the problem is to store films and music in DVDs or on another hdd (externals dhh are very cheap nowadays)

cheers
L

---

