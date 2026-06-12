---
title: "Program to completely erase?"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by linkmaster03 on 2008-12-31
I have some files on an external hard drive. I am looking for a Linux program to completely erase some files on it, which leaves absolutely no chance of the data being recovered by a user on any OS. Does anyone know how I could do this, or recommend a program?

---

### Post by jamesrl on 2008-12-31
shred.  Type 'man shred' for options.

---

### Post by solitaire on 2008-12-31
Easiest way to do it is to use the "dd" command

```
 dd if=/dev/urandom of=/dev/sda#
```
if = input file / device
/dev/urandom = randomly generated data
of = output file / device
/dev/sda# = the path to the device / partition or file you wish to securely overwrite

examples:
dd if=/dev/fda0 of=/home/user/copy_of_floppy.img
this saves an exact copy of the disk in the floppy drive to a file called "copy_of_floppy.img"

dd if=/dev/zero of=/home/user/wipe.file
This creates a file called "wipe.file" and fills it with zeros till it runs out of room on the drive.

_**check the "man" pages for the "dd" command before you do anything!! you can totaly bork your sytstem if you get the commands wrong!!!**_

---

### Post by linkmaster03 on 2008-12-31
Wow, thanks for the quick response guys. Those commands look like exactly what I need! :)

---

### Post by fubbleskag on 2008-12-31
> **linkmaster03 said:**
> I have some files on an external hard drive. I am looking for a Linux program to completely erase some files on it, which leaves **absolutely no chance of the data being recovered by a user on any OS**. Does anyone know how I could do this, or recommend a program?if you'll pardon the pedancy... there is no way to **absolutely** guarantee that, but the methods described will certainly make it quite unlikely.

---

### Post by Paqman on 2008-12-31
> **fubbleskag said:**
> if you'll pardon the pedancy... 

Ahem. I think you mean pedantry.

;)

---

### Post by linkmaster03 on 2008-12-31
Well, I'm not dealing with any sort of computer geniuses, so it won't take much for them to have no chance of recovering it.

---

### Post by phantomjoker on 2008-12-31
be careful with dd, i screwed up a external by doing the same thing. Make sure you specify the exact location, and on the correct device.

Its worth double checking - trust me.

---

### Post by Paqman on 2008-12-31
Yeah, probably much safer to use secure-delete or shred.

---

### Post by mkvnmtr on 2008-12-31
There is also a program in the repositories called "wipe". The author of that program warns to be very careful. He also says that depending on the type format on the partition it may be unlikely that you can find all of the information to delete it all. If you want to completely wipe a drive you better do a lot of Googleing.

---

### Post by handydan918 on 2008-12-31
AFAIK, shred won't work on a journalised file system.

---

### Post by solitaire on 2008-12-31
"dd" is so simple to use it's dangerous! 
Other programs are around that will wipe the disk but most just use the "dd" command with a few more things thrown in to the command.

"dd" command is quick and simple to type out. but BE CAREFUL!! you should write the dd command on paper first and check it with the man pages to see what it will do! THEN type it into the terminal! :D

But do a FULL backup of your system first :D just incase...... :D

---

### Post by Paqman on 2008-12-31
> **handydan918 said:**
> AFAIK, shred won't work on a journalised file system.

From man shred:
>        
In  the	case of ext3 file systems, the above disclaimer applies (and shred is thus of limited  effectiveness)  only  in  data=journal  mode, which  journals file  data  in addition to just metadata.  In both the data=ordered (default) and data=writeback modes, shred works as	usual.


In other words, shred works fine on ext3 unless you're mounting it in a funky mode.

As for data destruction in general: for all practical purposes overwriting a file three times renders it unreadable. I doubt many of us here are likely to have people probing their old platters with a scanning electron microscope. Even forensic data recovery normally just uses software tools to recover data.

---

### Post by linkmaster03 on 2009-01-01
Thanks guys, I took out the files using shred. :) It was only two .tar.gz archives, so I didn't need to get too fancy.

---

