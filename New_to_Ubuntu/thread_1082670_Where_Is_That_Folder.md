---
title: "Where Is That Folder?"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by djmoore on 2009-02-28
From both a command line and in GNOME, how do I determine what partition a given file or folder is on?

I have Ubuntu Ibex on the hard drive and am currently booting from a Heron LiveCD.

The LiveCD complicates things, because it creates its own file system parallel to the "real" FS on the hard drive.

Another way of asking this: I boot off a LiveCD, and find the several hard drives in the system have been divided up into numerous partitions. Since I booted from the LiveCD, of course, the usual mount points have been hijacked. 

How can I browse through the partitions to see what folders and files are in each one? 

I really want this answered both ways:
Grab a file, see what partition it lives on.
Grab a partition, see what files it contains.

===


Related:

I have a partition, /dev/sda2, which the LiveCD mounts as a subfolder of /home -- not the /home that the LiveCD creates, mind, but the "real" /home on the hard drive. (The LiveCD path is /media/home/public.)

I've manually mounted that same partition as the folder /DATA. The browser reports /DATA to be empty except for lost+found. /media/home/public has my data in it.

Why is /DATA empty?

---

### Post by Ms_Angel_D on 2009-02-28
This looks like it might be of some help to you. [http://kb.iu.edu/data/afiy.html](http://kb.iu.edu/data/afiy.html)

---

### Post by djmoore on 2009-02-28
I admit, I don't immediately see how. I don't know the command that will yield the information grep can search through.

What command will simultaneously display folder and partition info?

---

### Post by Ms_Angel_D on 2009-02-28
I wish I could be of more assistence to you unfortunatly I'm just learning the CLI myself. Hopefully somebody will be along soon who can help you, better than I.

Angel

---

### Post by apmcd47 on 2009-02-28
df tells you the size of your partitions and also where they are mounted. YOu can also find out which partiton you are currently on:```
df .
```
So, ```
df /path/to/file
```will tell you which partition your file/directory is on. You don't know where it is at all?```
find / -name xxx -print0 | xargs -0 df
``` The -print0 and xargs -0 (that is a zero) will allow special characters (eg spaces) in the filenames, otherwise xargs cannot handle then properly.

Andrew

---

### Post by rburkartjo on 2009-02-28
dj, you can try this open a terminaland type whereis (one word) space and then what you want to find. okay very easy way open search for files type in what you are looking for change 
look in folder to file system. then when you find what you are looking for click on open when you open it the location is given/cheesemaker

---

### Post by djmoore on 2009-02-28
apmcd47/Andrew: Excellent answer, thank you very much. That worked exactly as I hoped.

Now, is it possible to go the other way, that is, knowing a device name, such /dev/sda2, can I find all the folders it contains?

===

rburkartjo/cheesemaker: Thank you for your suggestions; I appreciate your effort.

whereis seems to work best to find information on commands. For instance ```
whereis ls
```results in
```
ls: /bin/ls /usr/share/man/man1/ls.1.gz
```

I've found that when running the LiveCD, the File Browser Search function only finds things in the temporary Ubuntu file system. I can't find anything anywhere else -- even when I've navigated to the appropriate folder and can see the [test file] I'm [pretending to] look for.

In any event, this function does not return the /dev name of the partition the file or folder is on.

---

### Post by amauk on 2009-02-28
> **djmoore said:**
> Now, is it possible to go the other way, that is, knowing a device name, such /dev/sda2, can I find all the folders it contains?
Using tree, if you don't have it installed
```
sudo apt-get install tree
```
this will list (recursively) all directories under your device
```
df | grep '/dev/sda2' | sed 's/ [ ]*/ /g' | cut -d' ' -f 6 | tree -d > ~/sda2_dirs.txt
```

---

### Post by ad_267 on 2009-02-28
Another useful command is "mount", which will list all partitions and their mount points when called with no arguments.

---

