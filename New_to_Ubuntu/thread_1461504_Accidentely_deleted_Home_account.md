---
title: "Accidentely deleted Home account"
date: 2010-04-24
forum: New to Ubuntu
---

### Post by userub on 2010-04-24
Hello, I'm hoping you can help me...

I had installed a second user, so that there were two Users.

I then wanted to delete the second user, so I used the User and Group options to disable the account. The files of the account were still there, though, so I tried to delete them manually by selecting the folders and hitting delete. It said I had no permission, so I went online to try and find a code.

The code I found was something like, sudo rr -r /home//

I don't remember exactly, and I don't have access to my Firefox history to look it up. Anyway, I typed that code into the terminal, as sudo rr -r /home// other (other being the name of the second group).

Unfortunately, I wound up deleting my MAIN user account. All of my files, like Desktop, Downloads, Documents, etc are GONE. Is there any way I can recover those files? Trash bin has nothing in it.

---

### Post by byStanderone on 2010-04-24
...first thing to do: refrain from doing anything on that pc....use another box for your research on what to do next!

---

### Post by carrarin on 2010-04-24
Yes, first thing is to shut down the computer.
Get a live cd.

Boot into a live cd.
install sleuth kit

use the following commands 
mkdir ~/recovery
$ sudo fls -f ext -d -r -p /dev/sdb1 >\ ~/recovery/deleted_files.txt

and then...

$ sudo icat -f ext -r -s /dev/sdb1 910452 \
              >~/recovery/may_lj_article.txt

Note. 910452 needs to be replaced with all the inode numbers that were output from fls command

for more information man the commands

---

### Post by userub on 2010-04-24
> **carrarin said:**
> Yes, first thing is to shut down the computer.
Get a live cd.

Boot into a live cd.
install sleuth kit

use the following commands 
mkdir ~/recovery
$ sudo fls -f ext -d -r -p /dev/sdb1 >\ ~/recovery/deleted_files.txt

and then...

$ sudo icat -f ext -r -s /dev/sdb1 910452 \
              >~/recovery/may_lj_article.txt

Note. 910452 needs to be replaced with all the inode numbers that were output from fls command

for more information man the commands


I'm afraid I'm very confused.

1) Is a Live CD the same as the CD I use to install Ubuntu with?

2) Do I boot into this same computer (I don't have access to another one, so I have to use this one)?

3) Is the first set of commands to install Sleuth Kit? Do I type that in the terminal of the Ubuntu or Live CD (or are they the same thing?). I tried typing that into this terminal and it says: bash:  ~/recovery/deleted_files.txt: No such file or directory

---

### Post by sisco311 on 2010-04-24
Try this:
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

---

### Post by userub on 2010-04-24
> **sisco311 said:**
> Try this:
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

Thanks for the link, but I got lost here:

You can use an external hard drive or even internal second hard drive for backup.  For an internal second hard drive, you can access it the same way you accessed the internal first hard drive (the one you’re trying to recover data from). 
 If the backup location is an external hard drive, you should be able to plug it in and have it automatically appear on the desktop as an icon. 





I'm not sure what it means. Can I have the backup location be a folder on my desktop? Will this backup location be where the files are backed up?

---

### Post by userub on 2010-04-24
Okay, I'm running Photorec, and I'm trying to set it up to save on my dual-booted Vista partition. But it says I can't save there: Cannot create file in current directory.

I think it's because Ubuntu asks me for my password when I want to access the Vista partition from Ubuntu. Is there a way to unlock the Vista partition so Photorec can use it for backup? Thanks.

By the way, I tried saving the backup to recovery, one of the folders that comes up after hitting the back button when in Home (along with bin, media, etc). Photorec seemed to run fine, listing the numbers of files being recovered and so on, but when I clicked on the recovery folder, there was nothing there. How can that be? Photorec itself said the contents from the last backup software I used are in the, yet I can't see it with Ubuntu's file exploration system.

---

### Post by carrarin on 2010-04-24
it might be hidden 

try pressing ctr-h

---

