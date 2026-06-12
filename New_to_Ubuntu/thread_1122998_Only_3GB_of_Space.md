---
title: "Only 3GB of Space?"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by SLaCK3r on 2009-04-11
Hi. I just installed Ubuntu and deleted Windows Vista Home Edition (piece of junk). Might've been a bad idea, but it's only partially deleted. I saved my "Users" file because I want to put some videos of a vacation I had in the Caribbean on Ubuntu. Video files are very large (these ones being about 20GB total) and Ubuntu won't let me "Drag N' Drop" it on my desktop.

It also says I only have 1.7GB of space left...I don't see how that's true, as I have a 60GB C: and a 60GB D:

I need someone to help me get my hard drive space back and videos.

---

### Post by drs305 on 2009-04-11
Did you delete the files from inside ubuntu? If so, you may still have files in Trash taking up space.

Empty your user trash by right clicking the trash bin and selecting "Empty trash".

You can also have trash in root's Trash, which isn't emptied when you empty yours. Open nautilus or another file browser as root and use SHIFT-DELETE to remove the *Trash* folder or info and files subfolder. Be careful with sudo and SHIFT-DELETE - the files are not recoverable when you do this.
```

gksudo nautilus /root/.local/share

```

---

### Post by SLaCK3r on 2009-04-11
My trash bin is empty. When I goto "Places>Computer>Home" It says: 2.3 GB available at the bottom. I deleted the files in Ubuntu from Filesystem. Windows and Program Files.

---

### Post by drs305 on 2009-04-11
Take a look at your system with baobab/Disk Usage Analyzer. Open it with root privileges so you see all the files (some of which would be hidden as a normal user):
```

gksudo baobab /

```

Note: I've submitted a tutorial that covers finding and recovering lost disk space and am awaiting approval. It should show up in the Tutorials section once the mods have looked it over.

---

### Post by RetchingRabbit on 2009-04-11
> **SLaCK3r said:**
> 

It also says I only have 1.7GB of space left...I don't see how that's true, as I have a 60GB C: and a 60GB D:

I need someone to help me get my hard drive space back and videos.

Let me guess....


Another Wubi victim...---err, install?

):P

---

### Post by SLaCK3r on 2009-04-11
"/" Usage is 100% with 12.6 GB, "host" is about 50% with 7.2GB , "Home" is 20% with 2.6 GB, and "usr" is 15% with 1.9 GB.




EDIT: Yes, a Wubi installer :p

---

### Post by SLaCK3r on 2009-04-11
> **RetchingRabbit said:**
> Let me guess....


Another Wubi victim...---err, install?

):P


Is it bad to install with Wubi?

---

### Post by drs305 on 2009-04-11
> **SLaCK3r said:**
> Is it bad to install with Wubi?

With a wubi install you set the maximum file size when you set it up. It doesn't matter how much space you have on the partition - at least that is the way it was when wubi first came out. Data within the installation can't expand beyond the limits you set when you installed it. There are a few ways around this limitation using LVPM. Here is a link that might prove useful on converting a wubi install into a normal one.

[http://ubuntuforums.org/showthread.php?t=438591]("http://ubuntuforums.org/showthread.php?t=438591")

---

### Post by RetchingRabbit on 2009-04-11
> **SLaCK3r said:**
> Is it bad to install with Wubi?

No...as long as you don't intend for that installation to be a permanent solution. wubi is intended for testing purposes, and while it's neat for that, it is NOT suited to use as a permanent installation.
The whole idea of expecting performance and stability out of a linux system installed in a ntfs environment...
Laughable, really.


:rolleyes:

---

### Post by SLaCK3r on 2009-04-11
Alright, well I had to re-install windows because I restarted my PC and it wouldn't boot anything. If I want to install Linux as a stable and permanent OS, I have to burn it's ISO to a disk and then boot my PC from the disk? That will give me my real amount of hard drive space?

---

### Post by drs305 on 2009-04-11
> **SLaCK3r said:**
> Alright, well I had to re-install windows because I restarted my PC and it wouldn't boot anything. If I want to install Linux as a stable and permanent OS, I have to burn it's ISO to a disk and then boot my PC from the disk? That will give me my real amount of hard drive space?

Yes, you boot from the LiveCD and you will be given several different options for partitioning, including wiping the entire disk, choosing the largest contiguous free space, and manually selecting the partitions.

These 3 links are good for help in the installation process:
[https://help.ubuntu.com/community/Installation]("https://help.ubuntu.com/community/Installation")

[http://news.softpedia.com/news/Installing-Ubuntu-8-04-LTS-84314.shtml]("http://news.softpedia.com/news/Installing-Ubuntu-8-04-LTS-84314.shtml")

[http://www.psychocats.net/ubuntu/index]("http://www.psychocats.net/ubuntu/index")

---

### Post by SLaCK3r on 2009-04-11
> **drs305 said:**
> Yes, you boot from the LiveCD and you will be given several different options for partitioning, including wiping the entire disk, choosing the largest contiguous free space, and manually selecting the partitions.

These 3 links are good for help in the installation process:
[https://help.ubuntu.com/community/Installation]("https://help.ubuntu.com/community/Installation")

[http://news.softpedia.com/news/Installing-Ubuntu-8-04-LTS-84314.shtml]("http://news.softpedia.com/news/Installing-Ubuntu-8-04-LTS-84314.shtml")

[http://www.psychocats.net/ubuntu/index]("http://www.psychocats.net/ubuntu/index")


Alrighty, thanks. Just need to clear this up. My "LiveCD" is the disk that I burned my ISO to, correct?

---

### Post by drs305 on 2009-04-11
> **SLaCK3r said:**
> Alrighty, thanks. Just need to clear this up. My "LiveCD" is the disk that I burned my ISO to, correct?

Yes it is. You should be able to stick it into your machine, reboot, and it will give you options to run ubuntu from the cd or install it.

---

### Post by SLaCK3r on 2009-04-11
New install works fabulous. Thank you.

---

