---
title: "how to extract files from another computer?"
date: 2010-08-11
forum: New to Ubuntu
---

### Post by StuSchu on 2010-08-11
I'm using ubuntu 9.10 installed via wubi on a dell inspiron mini 10.  I've used Windows my whole life, am very inexperienced using Terminal, and tars, grubs, and sudos are greek to me.

I recently started having [boot problems]("http://ubuntuforums.org/showthread.php?t=1532557&highlight=stuschu") with 9.10 and haven't been able to boot since.  It seems like the simplest fix is to reload the operating system, but I'd like to get some pictures off the harddisk first, as well as some files on the Desktop.  Everything else can go.  I've put the harddisk into an enclosure and tried opening it on a computer also running 9.10 but I can't find anything resembling a Photos or Desktop folder.  

How do I get my pictures and files off the harddisk?  Should I follow the instructions for backing up listed [here]("http://ubuntuforums.org/showthread.php?t=35087&highlight=backup+booting")?  If so, how do I access them once I've created the tar file?

Molto grazie.

---

### Post by StuSchu on 2010-08-11
Another piece of information:

When I plug the enclosure into another computer and open it up, the folders listed are:

BAT, BIN, IMG, SRC1, SRC2, SRC3, SRC4, SRC5

and the files listed are:

COMMAND.COM, AUTOEXEC.BAT, CONFIG.SYS, DELLBIO.BIN, DELLRMK.BIN

---

### Post by bcbc on 2010-08-11
> **StuSchu said:**
> I'm using ubuntu 9.10 installed via wubi on a dell inspiron mini 10.  I've used Windows my whole life, am very inexperienced using Terminal, and tars, grubs, and sudos are greek to me.

I recently started having [boot problems]("http://ubuntuforums.org/showthread.php?t=1532557&highlight=stuschu") with 9.10 and haven't been able to boot since.  It seems like the simplest fix is to reload the operating system, but I'd like to get some pictures off the harddisk first, as well as some files on the Desktop.  Everything else can go.  I've put the harddisk into an enclosure and tried opening it on a computer also running 9.10 but I can't find anything resembling a Photos or Desktop folder.  

How do I get my pictures and files off the harddisk?  Should I follow the instructions for backing up listed [here]("http://ubuntuforums.org/showthread.php?t=35087&highlight=backup+booting")?  If so, how do I access them once I've created the tar file?

Molto grazie.
If you are trying to access data from your wubi installation of ubuntu, you need to locate and loop mount the root.disk (virtual drive that wubi uses). It contains the ubuntu os and all your ubuntu data.

Usually it's in c:\ubuntu\disks\root.disk. Since you're looking from ubuntu, you'll need to mount each partition and look for /ubuntu/disks/root.disk. 

So let's assume your root.disk is on /dev/sdb1. First thing you need to do is mount /dev/sdb1 (if you haven't already) and then after that mount the root.disk:
```
sudo mkdir /media/win
sudo mount /dev/sdb1 /media/win
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
```

Then you have access to your wubi installation under /mnt and can copy your data e.g. /mnt/home contains your wubi /home directory.

---

### Post by StuSchu on 2010-08-11
Thanks, bcbc.

A couple questions about command lines:

1) What do I enter to mount /dev/sdb1 ?

2) What do I enter to copy my data?

---

### Post by dv3500ea on 2010-08-11
The Wubi hard disk file can be found in Windows at ```
c:/ubuntu/disks/root.disk
```
Your best bet to access your files is to boot form an Ubuntu live CD and then follow these instructions:

First open your windows drive from the Places menu and check this file exists.
You need to note down the file path that Ubuntu sees it as, eg.
```
/media/windows/ubuntu/disks/root.disk
```
I will assume this is the path, but in the following instructions you will need to replace it with the path on your system.

Run Applications -> Accessories -> Terminal.
Type the following command and press enter. If you are prompted for your password; enter it. Don't worry that there is no visual clue that you are typing.

```
sudo mkdir /media/wubi && mount /media/windows/ubuntu/disks/root.disk /media/wubi -o loop
```

Then use the file manager to go to /media/wubi/home.
You should see a folder with your username. Double click this folder and you should be able to access your files.

Note that a proper dual boot (or just Ubuntu) install is much more robust than a Wubi install, so if you reinstall Ubuntu, I would suggest not using Wubi.

---

### Post by StuSchu on 2010-08-11
It turns out that the file path is /media/OS/ubuntu/disks/root.disk

> **dv3500ea said:**
> Run Applications -> Accessories -> Terminal.
Type the following command and press enter. If you are prompted for your password; enter it. Don't worry that there is no visual clue that you are typing.

```
sudo mkdir /media/wubi && mount /media/windows/ubuntu/disks/root.disk /media/wubi -o loop
```Then use the file manager to go to /media/wubi/home.
You should see a folder with your username. Double click this folder and you should be able to access your files.

When I enter this command, I get the following message: 

```
mkdir: cannot create the directory <</media/wubi>>: The file already exists
```

Any suggestions?

---

### Post by bcbc on 2010-08-11
> **StuSchu said:**
> It turns out that the file path is /media/OS/ubuntu/disks/root.disk



When I enter this command, I get the following message: 

```
mkdir: cannot create the directory <</media/wubi>>: The file already exists
```

Any suggestions?

Just loop mount the file (drop the first command string that creates the directory and add a sudo to the second that loop mounts the file)
i.e. sudo mount -o loop /media/OS/ubuntu/disks/root.disk /media/wubi

(This assumes you already created the directory and you are running the same command twice. If /media/wubi is in use, you'll want to replace this with another directory or unmount it first "sudo umount /media/wubi" )

---

### Post by bcbc on 2010-08-11
> **StuSchu said:**
> Thanks, bcbc.

...

2) What do I enter to copy my data?

What are you planning to do: just recover data or are you planning to reinstall ubuntu? If reinstalling, how do you plan to do this?

---

### Post by StuSchu on 2010-08-11
> **bcbc said:**
> What are you planning to do: just recover data or are you planning to reinstall ubuntu? If reinstalling, how do you plan to do this?

Just recover data.

---

### Post by bcbc on 2010-08-11
> **StuSchu said:**
> Just recover data.

OK so if you want to extract your data from the root.disk to the same drive, I'd just open up two windows in Nautilus and copy the folders from one location to the other.

You can do this from the desktop or from command line:
```
gksudo nautilus /media/wubi/home &
gksudo nautilus /media/OS

```
Then look for your data within /media/wubi/home under your username (e.g. Documents, Downloads, Pictures etc.) and copy the folders direct to /media/OS 

that's probably the simplest. Keep the root.disk until you are sure you got everything.

---

### Post by StuSchu on 2010-08-11
> **bcbc said:**
> OK so if you want to extract your data from the root.disk to the same drive, I'd just open up two windows in Nautilus and copy the folders from one location to the other.

You can do this from the desktop or from command line:
```
gksudo nautilus /media/wubi/home &
gksudo nautilus /media/OS

```Then look for your data within /media/wubi/home under your username (e.g. Documents, Downloads, Pictures etc.) and copy the folders direct to /media/OS 

that's probably the simplest. Keep the root.disk until you are sure you got everything.

I don't have a /media/wubi file, which makes me think I've been explaining my setup wrong.

When I used to be able to boot ubuntu 9.10, I chose it from a dual boot.

Does this change things?  Thanks for your patience.

---

### Post by bcbc on 2010-08-11
> **StuSchu said:**
> I don't have a /media/wubi file, which makes me think I've been explaining my setup wrong.

When I used to be able to boot ubuntu 9.10, I chose it from a dual boot.

Does this change things?  Thanks for your patience.

No, before you had a /home folder (your root.disk was mounted as '/'). But now you've mounted your root.disk to /media/wubi. So that just means /home is under /media/wubi/home.

---

### Post by StuSchu on 2010-08-11
> **bcbc said:**
> OK so if you want to extract your data from the root.disk to the same drive, I'd just open up two windows in Nautilus and copy the folders from one location to the other.

You can do this from the desktop or from command line:
```
gksudo nautilus /media/wubi/home &
gksudo nautilus /media/OS

```Then look for your data within /media/wubi/home under your username (e.g. Documents, Downloads, Pictures etc.) and copy the folders direct to /media/OS 

that's probably the simplest. Keep the root.disk until you are sure you got everything.

there aren't any files at all in the wubi folder.

---

### Post by StuSchu on 2010-08-11
> **bcbc said:**
> Just loop mount the file (drop the first command string that creates the directory and add a sudo to the second that loop mounts the file)
i.e. sudo mount -o loop /media/OS/ubuntu/disks/root.disk /media/wubi

(This assumes you already created the directory and you are running the same command twice. If /media/wubi is in use, you'll want to replace this with another directory or unmount it first "sudo umount /media/wubi" )

It tells me I must specify the type of file system.

---

### Post by bcbc on 2010-08-11
> **StuSchu said:**
> It tells me I must specify the type of file system.

That doesn't sound good. It should pick that up automatically. This might explain why you were having problems booting.
You could try supplying -t ext3 i.e. ```
sudo mount -o loop -t ext3 /media/OS/ubuntu/disks/root.disk /media/wubi
```

The [wubi guide]("https://wiki.ubuntu.com/WubiGuide#How can I access my Wubi install and repair my install if it won't boot?") reckons you can run an fsck on it.
i.e. sudo fsck /media/OS/ubuntu/disks/root.disk
I would recommend backing up the root.disk file before doing this.

If you still had your drive in the original computer I'd also suggest running a chkdsk on the computer (from windows).

EDIT: I see from your other thread you were able to mount the root.disk before. It looks like you needed to reinstall the windows bootloader. I don't know what has happened in the subsequent 3 weeks, so not sure why it can't be mounted now.

---

### Post by StuSchu on 2010-08-11
> **bcbc said:**
> That doesn't sound good. It should pick that up automatically. This might explain why you were having problems booting.
You could try supplying -t ext3 i.e. ```
sudo mount -o loop -t ext3 /media/OS/ubuntu/disks/root.disk /media/wubi
```

This worked- I was able to get into wubi/home.  The new problem is that *all* the files are there *except* for my freakin pictures.  The conclusion seems to be that I deleted these, but I have absolutely no recollection of doing so and doubt that I did.  Could the computer not be recognizing certain file types for some reason?  Seems improbable.

---

### Post by bcbc on 2010-08-11
> **StuSchu said:**
> This worked- I was able to get into wubi/home.  The new problem is that *all* the files are there *except* for my freakin pictures.  The conclusion seems to be that I deleted these, but I have absolutely no recollection of doing so and doubt that I did.  Could the computer not be recognizing certain file types for some reason?  Seems improbable.

It does seem improbable. You could do a find command to pick up any jpgs. I'd have to look up the format for you.

try 
```
find /media/wubi/home/ -name "*.jpg"
```

---

### Post by StuSchu on 2010-08-11
Thanks for spending all day  on this.  I'd label the thread [SOLVED] but I don't know how to do that post hoc.

---

### Post by AlphaLexman on 2010-08-11
> **StuSchu said:**
> I'd label the thread [SOLVED] but I don't know how to do that post hoc.
Click on the red underlined text: [COLOR=Red]_Thread Tools_[/COLOR] at the top of the page, and select Mark as Solved.

---

### Post by bcbc on 2010-08-11
> **StuSchu said:**
> Thanks for spending all day  on this.  I'd label the thread [SOLVED] but I don't know how to do that post hoc.
No prob. :) Did you get your pics? I hope it worked out.

---

