---
title: "&quot;Corrupted&quot; Hard Disk"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by Pauho on 2009-03-08
Ok, I haven't got a clue on what to do with this problem, so I'll just lay it out:

I've got Ubuntu installed through WUBI on my Windows D:\ drive. I can access everything on this HD using the /host directory in Ubuntu. However, when I try to access the drive in Windows, it informs me that "This file or directory is corrupted and unreadable".

Clearly, that isn't the case or I wouldn't even be able to run Ubuntu, never mind access the rest of the drive through Ubuntu.

So, if anyone can shed light on this problem I'd be very grateful.

---

### Post by lindsay7 on 2009-03-08
Window will not see the partition for ubuntu, if installed Ubuntu under window it will just show up as a program running under windows. you can see it in the control panal, add remove progams, for example.

---

### Post by howefield on 2009-03-08
Windows can't read ext partitions without third party software installed.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

How can I access the Wubi files from Windows?

There are a few Windows applications that can mount ext2-based file systems. See for instance:

    *      [http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)
    *      [http://www.fs-driver.org/](http://www.fs-driver.org/) 

The relevant Wubi files you need to access are located under C:\ubuntu\disks\

---

### Post by Pauho on 2009-03-08
But until this problem occured, I had been able to use my D:\ drive in Windows, Ubuntu was installed to a directory on that drive through Wubi. The D:\ drive is in NTFS format. Does that mean that the ext partition only applies to that directory (in this case, D:\ubuntu).

---

### Post by lindsay7 on 2009-03-08
I could be wrong but I thought that Wubi only installed under windows and you would not see a partion for Ubnutu under windows on any drive. The Wube Ubuntu installation would be on the same drive as windows.

---

### Post by Pauho on 2009-03-08
No, I installed it on my data drive (D:\). Windows is on my C:\ drive. I could access everything through Ubuntu, but couldn't access Ubuntu stuff through Windows.

The problem now is that while I can still access the whole drive through Ubuntu (/host), I cannot access the same drive (D:\) through Windows.

---

### Post by lindsay7 on 2009-03-08
Ok, I not sure what is going on but if you did install Ubuntu with Wubi you should be able to uninstall it under windows. control panel, add remove program. I would uninstall it (make sure you take off and save anything you need) and then reinstall it with Wubi under windows in the same drive  as windows. I have used wubi before but I did not remember it giving you a choice as to where you wanted to install.  Anyway here is the web site if you need it.

[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by halitech on 2009-03-08
Boot into Ubuntu, open a terminal and post the output of 
```
sudo fdisk -l
```

that should tell us whats going on with your D:\ drive

---

### Post by Pauho on 2009-03-08
I appreciate the help, but I'm not sure that would solve the problem to be honest. I don't think reinstalling Ubuntu through Wubi would let me access a drive through Windows.

But then again, I don't have a clue how to go about sorting this problem.

---

### Post by halitech on 2009-03-08
I agree but having the info of fdisk in Ubuntu might give us a clue as to whats going on. Also, can you go into Disk Management in Windows and take a screen shot of your partitions?

---

### Post by Pauho on 2009-03-29
Apologies for my delay,

Here is the information that was asked for, the disk management screenshot and the fdisk screenshot.


Again, thanks in advance for any help you can offer.

Paul.

---

### Post by halitech on 2009-03-29
ok, based on the info you provided, Ubuntu was definately installed using WUBI which means its not a seperate OS but a program running in a quosi-virtual file system. 

I'm not sure but it could cause issues when trying to mount the NTFS file system as it technically is mounted when you are running Ubuntu.

---

### Post by Pauho on 2009-04-03
That's right, it was installed through WUBI. 

Not sure I understand the second part of your message. I'm not running the two OS's simultaniously if that's what you mean.

---

### Post by halitech on 2009-04-03
because you install Ubuntu using WUBI, it is basically installed in a file on the NTFS file system so the drive is already mounted when you boot into Ubuntu. If you had installed to a true linux partition, the NTFS file system would not be in use when you are running Ubuntu. I don't know if this is causing the issues you are having or not. You might want to check in the WUBI subforums to see if they have any ideas for you.

---

### Post by syronth on 2009-05-04
@Pauho

Some time has been passed but I found this thread just now...

I've got the same problem (Ubuntu 9.04) and I believe the ntfs-driver is corrupting the partition/ntfs data structure in some very subtle way if you move, create and delete large chunks of data. Perhaps moving gigs from the disk-image to /host might cause this all alone.

Well, the Wubi-Homepage ([http://wubi-installer.org/](http://wubi-installer.org/)) just tells you that your Ubuntu disk-image might get corrupted, it is not as safe/stable as installing it natively on a real ext3 partition. And in the wiki ([https://wiki.ubuntu.com/WubiGuide#Corrupted](https://wiki.ubuntu.com/WubiGuide#Corrupted) NTFS filesystem) they tell you not to hard reboot. I didn't but just before I was downloading gigs of data, first into the home dir, than copied the stuff to /host and dl'ed another few things directly to /host and deleted a few gigs. I guess this was just to much for Wubi/ntfs-driver.

Side note: TestDisk (a windows tool) as well as chkdsk did not find any error, everything seemed perfect and Ubuntu was starting without any problems indeed. But still Vista wasn't able to read the ntfs-partition anymore. With TestDisk I was able to read the data and to copy the whole /ubuntu dir to a working partition. After that I formatted the corrupt partition and copied back the /ubuntu dir - this was the only way for me.

So, the moral of this story is I guess: if you really want to use Ubuntu, better make room for a native ext3-partition. Wubi might work flawlessly for the most nevertheless as long as they don't do hard reboots and download/move/delete huge .iso-Files.

---

