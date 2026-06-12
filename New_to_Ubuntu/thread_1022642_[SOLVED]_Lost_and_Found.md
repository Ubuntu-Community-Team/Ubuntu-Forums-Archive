---
title: "[SOLVED] Lost and Found ???"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by loseby on 2008-12-27
Have a hard drive that has the one folder and that is unreadable. It is called lost and found . The hard drive is 500gb and has 432gb free space so I assume the file is 68gb. Now any way I can view what this  is or what is contained in it.

I want to format this drive so I can back all my data up on it but first I want to find out what is on it .

Any suggestions

---

### Post by ELF_O8 on 2008-12-27
The Lost+found is where all the trash goes, even after it is deleted.
It's used so you can recover anything you may have accidently deleted.

If you want to format, format away!

---

### Post by nhasian on 2008-12-27
thats where fsck puts the files it has recovered that were corrupted in the filesystem:

[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html)

---

### Post by ELF_O8 on 2008-12-27
Well, I look like an idiot.
Thanks for correcting my stupid error nhasian.
Almost led OP astray with misinformation.
Might as well kill myself now.

---

### Post by jerome1232 on 2008-12-27
Since trash was mentioned I'd thought I'd say where the trash actually is on removable drives.

Usually the trash on removable disks is .trash-(users uuid here) and is somehow linked to the users trash. If you empty your trash, then .trash-<uuid> get's emptied as well.

It will also ask you when you unmount the filesystem whether you want the drive's trash emptied.

---

### Post by Herman on 2008-12-27
From the command line you should be able to get a list of whatever's in there, but it will probably not make any sense because the files won't have any file names, only inode numbers.
```
sudo ls -l /lost+found/ | less
```
(Press your 'q' key to go back to your normal terminal again).

Another way you can take a look around in your /lost+found is to open nautilus,
```
gksudo nautilus
```
Be careful what you do, that gives you a GUI with root priveleges, it can be dangerous!
(Not for everyday general purpose browsing).
You should be able to navigate to your /lost+found directory in nautilus and take a look and see what files are there. I am told you can copy them to some other media and rename the files you can identify.

Please let me know what happens, I'm curious and I might be able to use the information to help someone in the future. 
confused57 told me about using nautilus for recovering files from the lost+found.
It's hard to find good information on that.

---

### Post by loseby on 2008-12-27
Well it shows nothing in there but properties show volume as 500.1 gb and free space as 438.7gb.

I think I will format the drive and move all my files to there before I do a complete reinstallation of Ubuntu ( this time it will be 8.10 intrepid )

---

### Post by Miljet on 2008-12-27
There probably isn't anything in there to see. The space that is showing as used is probably "overhead" used by the file system.

---

### Post by Herman on 2008-12-27
Another thing that can cause similar symptoms is when the file system doesn't fill the partition.
The partition is just a set of numbers in the MBR which tells the software which sector your partition starts at and what sector it finishes at.
The file system is something completely different and is controlled by code in the first few blocks of the partition,plus more located at strategic points throughout the partition, and it remembers where all your files are, (basically). Sometimes it happens that the partition is  resized and nobody tells the file system it's allowed to spread out a bit now.
Another way that can happen is when the file system is backed up with Partimage or a dd command. It can only be restored to a partition that's equal or bigger than the partition it came from, usually bigger. If no-one does anything, the file system doesn't know it's in a bigger partition.
Some software reports the partition size, and other software tells you the size of the file system.
There are programs that come with each fle system for resizing them to fill up the whole partition. For ext2 and ext3, we can run 'sudo resize2fs' [What to do if your file system doesn't fit your partition]("http://users.bigpond.net.au/hermanzone/p10.htm#What_to_do_if_your_file_system_doesnt").

If you're going to format it anyway, it doesn't matter. 

Thanks for letting us know how you got along with checking your /lost+found.

Regards, Herman )

---

### Post by loseby on 2008-12-28
thanks to all for the help

---

