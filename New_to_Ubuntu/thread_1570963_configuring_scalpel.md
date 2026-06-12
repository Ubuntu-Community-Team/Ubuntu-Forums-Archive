---
title: "configuring scalpel"
date: 2010-09-08
forum: New to Ubuntu
---

### Post by duceduc on 2010-09-08
I wanted to see if I can recover a file that I have deleted in Ubuntu. I installed Scalpel and have issued the following command.
```
sudo scalpel /dev/sda1 -o ouput
```

I also uncomment out this line in the conf file.
```
NONE y 10000 FOREMOST
```

I run the search and it ended with 90 files found. I try to open the output folder but it says 'Error listing directory /etc/scalpal/output'. Server returned empty listing for directory /etc/scalpel/output.

Am I suppose to configure something else? Also I am abit confuse as to what I need to edit for the line I uncommented in the conf file. I know the exact name of the file in which I want to recover. Do I replace the name like so?
```
NONE y 10000 myfilename
```

---

### Post by jtarin on 2010-09-08
An alternative software would be "PhotoRec"(or known as testdisk in the repositories.)

---

### Post by egalvan on 2010-09-09
First, you should NOT be running the system that holds the file you want to recover.
The more you use it, the greater the chance that the ``empty``
sectors will be used, and there goes your file!

Scalpel is more of a ``data carver`` tool than a file recovery tool.
The main difference being

file recover tries to find files based on the header information.
This is information inside the file itself that tells the system what kind of file it is;
 for example, a jpeg image file, or an OpenOffice document, etc.
Linux-based ones also use the inode information, if available.
These basically try to find the beginning of the file, and follow it to it´s end.
These are usually used first, to see what can be easily recovered.

file carver tries to find pieces of the original file, when header and/or inode info is not present.
This basically finds pieces and leaves it to the user to put it back together again.
they ``carve out`` the data, piece by piece.
These are usually ``last-resort`` utilities, due to their greater work-load.


Take **jtarin** advice (post 2) and try photorec first.

Note, you should be working from a liveCD, with ALL HARD DRIVE PARTIIONS UNMOUNTED.
Use an external hard drive or USB thumb drive to store your found files.
Re-read my first point at the start of this post.

---

### Post by duceduc on 2010-09-09
Thanks for the info. That makes more sense than the info I have gathered on the net. I may just let go that one file I have deleted than take a chance of wiping my live system. 

I found one tutorial about photorec, but it is a bit over my head.

---

### Post by egalvan on 2010-09-09
> **duceduc said:**
> Thanks for the info. That makes more sense than the info I have gathered on the net.

Google can be a good source of information. Of course, it can also oveload a person with too much...


>  I may just let go that one file I have deleted than take a chance of wiping my live system.

Sorry if I gave the impression of these things ``carving`` your systems to pieces, like a turkey ;)

Most all of these types of programs will attempt to mount the file-system as **read-only**.

They should not be run ``from´´ the file system that contains the information you need to recover.

There are many LiveCD versions of these utilities, and some LiveCD distros contain them.
Knoppix is one example (rather large download)
PartedMagic LiveCD is another (small download)

That said, they will not write to the drive until the ``write`` or ``commit`` command is picked.
Even then, they usually write the data to another partition.


> I found one tutorial about photorec, but it is a bit over my head.

Well, to be honest, if photorec is over your head, then data carving is really out there.


And lastly, what some folks do, is obtain another equal-sized drive and make a bit-by-bit copy of the original (using `dd`for example),
then work on the copy, thus leaving the original alone.
Forensics folks (law enforcement for example) use this method all the time...
the original is ``un-touched``.
Beleive it or not, ``dd`` is recognized by the US courts as a tool that can make legal copies of evidence that stand up in court.

``dd`` is one way, but there are far more user-friendly versions out there,
PartedMagic has several choices for ``cloning`` a drive.

Obviously, buying another drive may be more than you want to spend.
But with 1TB drives going for unde $80, you have to balance your own scales...
is the file worth it?
also, if you screw up, you can try mutliple times, as long as the original has not been used.

And remember, when you are done, you have a new drive to use a a back-up, or to load more Linux distros! ):P

---

