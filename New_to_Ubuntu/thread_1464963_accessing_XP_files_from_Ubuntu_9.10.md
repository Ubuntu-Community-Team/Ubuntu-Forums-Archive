---
title: "accessing XP files from Ubuntu 9.10"
date: 2010-04-28
forum: New to Ubuntu
---

### Post by maxterbuntu on 2010-04-28
Hi,

I am new to Linux and would appreciate some help on accessing XP text files from my Ubunty terminal. I currently have a dual boot laptop with XP Pro and Ubuntu 9.10 installed. Since I work with large text files I require the power of good text editors like VI to access the files. Can someone please explain how I can access my text files stored in the Windows directory from Ubuntu terminal?

Thanks in advance
max

---

### Post by anewguy on 2010-04-28
I'm not sure yet on the answer to your question, but I am curious as to why you are using terminal mode and VI, instead just running X and using one the good GUI editors?  Is it a restriction where you live, the PC you're on, or does your Ubuntu always go to a terminal logon and never to the GUI logon?  If it's the last, it's possible that we need to help you load a video driver.

Dave ;)

---

### Post by RolandFlagg on 2010-04-29
if u COULD use a GUI some of the time, you can go to Places on the top bar, to the right of Applications.
Under Places, you can mount whichever Windows partition that your file is stored in.
from there you can get back to the terminal, type
 cd /media/[windows_partition_name]

if your partition have a space in it, put quotes around the name, for example, "partition 1"

now that you are in your windows partition, using a few more cd commands should take you to your file, and then simply call vi

---

if you absolutely can't use any gui, then I'm sorry, I'm not sure how to mount partitions directly from the terminal myself, saw a web link, but it seems quite complicated. But here's my 2 cents, hope it helped :)

---

### Post by Cowboybebop79 on 2010-04-29
you could use NANO to edit your fstab config so you can mount your windows partiton or part of it. I used the description of how to do this at this site [http://www.thatsquality.com/articles/mounting-windows-smb-file-shares-using-cifs]("http://www.thatsquality.com/articles/mounting-windows-smb-file-shares-using-cifs") to mount a nas at boot and it has worked fine for me so far.

Hope this helps

---

### Post by maxterbuntu on 2010-04-29
Thank you to all who replied. I do have access to the GUI environment. Its just that I prefer to work with VI. Also my initial impression of gedit is that its not as powerful as VI. I am still not clear on how to access the Windows partition from terminal. I can click the files from the desktop but dont know how to access them from terminal.

---

### Post by cuberts on 2010-04-29
> **maxterbuntu said:**
> Hi,

I am new to Linux and would appreciate some help on accessing XP text files from my Ubunty terminal. I currently have a dual boot laptop with XP Pro and Ubuntu 9.10 installed. Since I work with large text files I require the power of good text editors like VI to access the files. Can someone please explain how I can access my text files stored in the Windows directory from Ubuntu terminal?

Thanks in advance
max
I am not sure about how you can do that, but when you install a new kernel then you should have transfered files. Then that would have let you acess all of the files that was on there

---

### Post by lkraemer on 2010-04-29
OK, Let's assume you have plugged in the IDE drive into a USB to IDE/SATA
Adapter.  At this point I typically use GParted to scan the drive, because
it tells me the Physical Size, the Partition Information, And I can easily
switch from one drive to another with a GUI, and picture of what is used
or unallocated on the drive.  For this example assume my IDE drive shows
up as /dev/sdc and it is a FAT32 Partition.  The first Partition will be
sdc1, and the second will be sdc2, etc....That's why I use GParted......

What you want to do is:
MOUNT the DRIVE
EDIT some Files
UMOUNT the Drive

Open a Terminal Window:
(You will be at your HOME Directory, and you need to get to the 
Root, so you can create a directory to allow mounting the drive.....
or you can mount from the GUI, which is much easier.......and you don't
need to create the directory.....)
```

cd /
cd media
sudo mkdir windrv
sudo mount -t msdos /dev/sdc1 /media/windrv
cd windrv
ls
ls -alt
pwd
cd /path/to/file
/path/to/vi/vi file.txt

```
Then exit the /dev/sdc1 directory so you can umount it by:
```

cd /
umount -t msdos /media/windrv

```
You could copy/move any file to any other mounted drive......
as needed.  You may want to remove the directory windir when finished.
```

cd /
cd /media
ls
sudo rmdir windrv
exit

```

lk

---

### Post by RolandFlagg on 2010-04-30
> **maxterbuntu said:**
>  I can click the files from the desktop but dont know how to access them from terminal.

Since you do have access to the GUI and can click the files from the desktop, you can actually download GVIM or EMACS, that way, you can right-click on the file you want to edit, and can simply use VI under the GUI environment.

On the other hand, if you are set on using the terminal, you'll need to double click on the windows partition on the desktop (simply opening it and then closing it should do the trick). And then do what I said before. Your windows partition should have a name, for example, on my lap top it has the name IBM_PRELOAD, so for me to access that partition from terminal i'd type:

```
cd /media/IBM_PRELOAD
```

From here, say that the file I want to edit is called "test.txt" and is on in "My Documents", i'd do:

```
cd "Documents and Settings"/RolandFlagg/"My Documents"
vi test.txt
```

and then you are all set

---

