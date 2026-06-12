---
title: "Trash disabled on internal HD?"
date: 2011-05-27
forum: New to Ubuntu
---

### Post by nosehat on 2011-05-27
Hi--

I'm having a problem with deleting files.

**My Setup**

I have a dual boot machine with two drives, one drive for the operating systems and one drive for data.  The operating system drive at /dev/sda has Ubuntu 10.04 on one partition (ext4) and Windows XP SP3 on another (NTFS).

The data drive at /dev/sdb is a 1TB internal SATA drive with one big NTFS volume.  I chose NTFS for the shared data drive because I want both OSes to be able to access it, and I need the option of big files.  The line in /etc/fstab that mounts this drive is:

```
UUID=227910DE427D0C49 /media/Datadrive ntfs defaults 0 0
```

**My Problem**

The trash can function on the data drive seems to be disabled.  There is a .Trash-1000 folder at the root of the data drive (as well as a Windows RECYCLER folder), but every time I try to delete a file when I'm booted to Ubuntu, I get this message:  "Cannot move file to trash, do you want to delete immediately?"  Unfortunately, I don't remember if this has been a problem since I installed the data drive (the existence of the .Trash-1000 folder suggests it was working at one point).  

Help?

Thanks!

---

### Post by wildmanne39 on 2011-05-27
> **nosehat said:**
> Hi--

I'm having a problem with deleting files.

**My Setup**

I have a dual boot machine with two drives, one drive for the operating systems and one drive for data.  The operating system drive at /dev/sda has Ubuntu 10.04 on one partition (ext4) and Windows XP SP3 on another (NTFS).

The data drive at /dev/sdb is a 1TB internal SATA drive with one big NTFS volume.  I chose NTFS for the shared data drive because I want both OSes to be able to access it, and I need the option of big files.  The line in /etc/fstab that mounts this drive is:

```
UUID=227910DE427D0C49 /media/Datadrive ntfs defaults 0 0
```

**My Problem**

The trash can function on the data drive seems to be disabled.  There is a .Trash-1000 folder at the root of the data drive (as well as a Windows RECYCLER folder), but every time I try to delete a file when I'm booted to Ubuntu, I get this message:  "Cannot move file to trash, do you want to delete immediately?"  Unfortunately, I don't remember if this has been a problem since I installed the data drive (the existence of the .Trash-1000 folder suggests it was working at one point).  

Help?

Thanks!
Hi, that is a message that I have been getting for 2 years now so I just delete instead of moving to the trash bin, I just assumed that was the way it was setup,I never thought of it as a porblem, but there might be a fix for it.

---

### Post by audiomick on 2011-05-27
I've seen that message a lot too. I always assumed it had something to do with the medium or the way it was mounted. From memory, I think I see it when I am accessing stuff on my NAS device. At any rate, I have also always just told it to delete and never really considered it to be a fault. Maybe I am not critical enough... ;)

---

### Post by nosehat on 2011-05-27
Thanks for the replies.

Unfortunately, I do see this as a problem, since this is the primary drive that has all my documents/work/etc on it.  I've accidentally deleted things in the past, and I love the functionality of a trash/recycling bin as an added buffer for mistakes.

My guess is that it's something about the way the drive is mounted, or else something got corrupt with the original .Trash-1000 folder.  Usually Gnome's trash feature works just fine on other installs, and on other media with this install.  NTFS isn't usually a problem.

Any clues for finding out what might be wrong, and how to fix it?  I'd hate to have to boot to Windows for file management!

---

### Post by drs305 on 2011-05-27
The problem stems from the fact that it is a non-linux file system. If you add the partition to your /etc/fstab file and include your UID in the options section, it should allow you to 'own' the .Trash-1000 folder and let you to delete files. The deleted files will be moved into the .Trash-1000 folder.

Here is a sample fstab entry, although you should preferably use UUIDs:
```
/dev/sdb3 /mnt/temp ntfs  defaults,uid=1000 0 0
```

The first user is UID 1000. If you aren't sure of your's, type "id" in a terminal.

If it's owned by you the .Trash-1000 bin will be emptied when you empty your normal Ubuntu trash bin.

This is a very basic fstab entry. There are more complex entries which offer more options and security (if needed). For more information about fstab entries, here is a good link:
[http://ubuntuforums.org/showthread.php?t=283131]("http://ubuntuforums.org/showthread.php?t=283131")

---

### Post by nosehat on 2011-05-27
Thank you, drs305!

Adding uid=1000 to my existing fstab entry completely solved the problem!

The reason the trash folder was there, but non-functional, is because when I first put the new drive into the case, I mounted it manually as user to check it out and make sure it worked.  In the process I must have made and deleted files, etc.

The problem only started after I'd added a line to fstab to auto mount the drive at boot up, and in that case it was root mounting the drive, not me.

Thanks again!

---

### Post by audiomick on 2011-05-28
> **nosehat said:**
> Thank you, drs305!
  In the process I must have made and deleted files, etc.

Not necessarily. I've noticed that a .trash appears automatically on every thing that gets mounted on a linux (or mac) machine. I noticed it first on things like USB sticks that I was using on linux and on windows machines.

---

### Post by drs305 on 2011-05-28
Glad it's working for you. Under normal circumstances, Ubuntu will handle NTFS partitions without the need for an fstab entry and the user will be able to delete trash. But once you have created an fstab entry unless you designate yourself as the owner the issues you saw arise.

The reason is that once it's listed in fstab without additional mounting options, the files 'belong' to root (NTFS doesn't actually support ownership designations). So if you try to delete something, Linux isn't going to let you access root's trash bin, which is just another folder. To allow the user some control over the files, it allows to you delete them permanently but you don't get access to root's trash bin.

---

