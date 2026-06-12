---
title: "Remove Corrupt Folder on Ectaco jetBook Lite"
date: 2010-06-04
forum: New to Ubuntu
---

### Post by lhb1142 on 2010-06-04
I have an Ectaco jetBook Lite e-book reader. Somehow I have created a corrupt folder which is named 553741206.

It contains nothing.

It is contained within the 'Books' folder. Even when logged in as 'root' on my Acer Extensa 5620-6419 computer running 'Lucid' connected to the jetBook,

I cannot delete this folder. The error message names the folder 553741206/1903662969. I have tried rm -rf * and sudo rm -rf * while logged in as root and with the 'Books' folder opened in the Terminal but nothing I have tried works so far.

Does anyone know how to positively delete an errant folder from this or another external drive?

Thanks for any help.

---

### Post by Jeroensum on 2010-06-05
Can you post an *ls -l* of the folder, maybe it will help us determine what's wrong with it.

---

### Post by lhb1142 on 2010-06-06
> **Jeroensum said:**
> Can you post an *ls -l* of the folder, maybe it will help us determine what's wrong with it.

I'm sorry but I haven't the foggiest idea of what an < ls -l > is.

When I connect the e-book reader to my computer, it appears to be just another drive, much like a Western Digital external hard drive. I can add, move, manipulate, and even delete files and folders on it. But somehow this one folder became corrupted.

Though I can certainly "live with" having it remain (it is on the reader's main drive and I now have all of my books on a removable SD card - there are no books on the main drive other than the jetBook's operating manual), I would really like to know how, in general, to remove a corrupted folder or file. I have tried changing the "permissions" under root (starting with sudo nautilus) but so far nothing has worked.

Thanks for replying.

Lawrence

---

### Post by Jeroensum on 2010-06-07
I was already in terminal-land ;) No worries I'll explain.

First, fire up a terminal: Applications -> Accessoiries -> Terminal
Next, we need to check where your book has been mounted, type: *mount*
You will now see a list of all the devices (internal disks and partitions) and also a name that would resemble your jetBook. Now the line will probably look something like this:
*/dev/sdb1 on /media/jetbook type usbfs (rw)*
Values may vary, but the important part here is the second column, this is where your jetBook is mounted on the system. Instead of mounted you could also read connected.
You can navigate to this directory by entering:
*cd /media/jetbook* (replace with your values)
Now enter: *ls -l*  and you should get a file listing of the files on the device, including the corrupt folder. Please copy/paste that listing here (you can use your mouse to select and rightclick to copy the text)

---

### Post by lhb1142 on 2010-06-10
> **Jeroensum said:**
> I was already in terminal-land ;) No worries I'll explain.

First, fire up a terminal: Applications -> Accessories -> Terminal
Next, we need to check where your book has been mounted, type: *mount*
You will now see a list of all the devices (internal disks and partitions) and also a name that would resemble your jetBook. Now the line will probably look something like this:
*/dev/sdb1 on /media/jetbook type usbfs (rw)*
Values may vary, but the important part here is the second column, this is where your jetBook is mounted on the system. Instead of mounted you could also read connected.
You can navigate to this directory by entering:
*cd /media/jetbook* (replace with your values)
Now enter: *ls -l*  and you should get a file listing of the files on the device, including the corrupt folder. Please copy/paste that listing here (you can use your mouse to select and rightclick to copy the text)

Thanks for trying but your instructions do not work. When I try them with the jetBook attached (connected), this is what I get in the Terminal:

<name>@Acer-Extensa-5620-6419-2:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /var/lib/ureadahead/debugfs type debugfs (rw,relatime)
gvfs-fuse-daemon on /home/lhbulk/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=lhbulk)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdb on /media/4A9F-6405 type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
<name>@Acer-Extensa-5620-6419-2:~$ 

As you can see, nothing actually reads "jetBook" but the indication 4A9F-6405 is the jetBook

but, if I try to access (cd) < media/4A9F-6405 > or < media/4A9F-6405 type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush) > I get either < bash: cd: media/4A9F-6405: No such file or directory > or < bash: syntax error near unexpected token `(' >

It looks as though I'm just going to have to "live with" that corrupted file.

Thanks for trying anyway.

Lawrence

---

### Post by Jeroensum on 2010-06-12
We're not quite there yet. The reason for the bash errors are simple. The second command (including the vfat values, etc) doesn't work because the directory isn't named like that. The first command doesn't work either since you don't seem to provide the whole path, this would be including the /
Your command should be:
cd /media/4A9F-6405

---

### Post by lhb1142 on 2010-06-12
> **Jeroensum said:**
> We're not quite there yet. The reason for the bash errors are simple. The second command (including the vfat values, etc) doesn't work because the directory isn't named like that. The first command doesn't work either since you don't seem to provide the whole path, this would be including the /
Your command should be:
cd /media/4A9F-6405

Dear Jeroensum,

You've been very patient with me - and I thank you. The above command did work but I don't know if the results will be very helpful.

Here is what shows:

myname@Acer-Extensa-5620-6419-2:~$ cd /media/4A9F-6405
myname@Acer-Extensa-5620-6419-2:/media/4A9F-6405$ ls -l
total 4
drwx------ 3 myname myname 2048 2010-05-04 14:09 Books
drwx------ 2 myname myname 2048 1999-12-31 23:12 Pictures
myname@Acer-Extensa-5620-6419-2:/media/4A9F-6405$

The "Books" and "Pictures" appear in blue.

The corrupt folder is within the Books folder; as you can see, it doesn't show when I enter the ls -l command. It is named 553741206 and it contains nothing.

For simplicity, I removed the SD card on which I have all of my books (my wife has her own separate card). The corrupt folder is present whether or not a card is inserted; in other words, the corrupt folder is always included in the Books folder. (With the Ectaco, the instructions warn against trying to delete either the Books or the Pictures folders which are the main folders on the machine.)

Is the above of any help to you in determining what is wrong?

By the way, I have read that the Ectaco jetBook Lite uses a Linux operating system but I do not know for sure that that is correct.

Thank you again for your efforts.

Lawrence H. Bulk

---

### Post by Jeroensum on 2010-06-14
When working in the IT business as I have been for almost 10 years, patience becomes second nature. I've waited ages for some systems to install or corrupt drives to be scanned, checking a forum every few days is peanuts ;)

I'm becomming more curious to your problem every minute, the folder is all numbers and would suggest an auto-generated folder, however I still need some output from you te get down to what this folder is and why you can't touch it.

Try:
ls -l /media/4A9F-6405/Books
or
ls -l Books

The folder should be in the output and should state something like you have seen with the Books and Pictues folders like so:

drwx------ 3 myname myname 2048 2010-05-04 14:09 Books


The 'd' at the beginning of the line states that it is a directory. In linuxland there are several other system files which can act as a directory but are something different like for instance a symlink )which would start the line with an 'l'). A symlink by the way, is kind of the same thing as a shortcut in windows.

So, still curious and patient here   ;)

---

