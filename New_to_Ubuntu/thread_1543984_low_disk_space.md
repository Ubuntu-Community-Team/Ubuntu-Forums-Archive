---
title: "low disk space?"
date: 2010-08-01
forum: New to Ubuntu
---

### Post by pirates712 on 2010-08-01
I did a quick search but couldn't find anything. I'm trying to get my new ubuntu installation up and running but have run into a problem.
When trying to copy my music (60 GB) I come up with a low disk space error. Windows says I have 250 gigs free. What's going on here?

Thanks,

Pirates

---

### Post by hansdown on 2010-08-01
Hi pirates712.

Please click system> administration> system monitor.

Click file systems, and post a screenshot.

---

### Post by corrytonapple on 2010-08-01
When you partioned for ubuntu, you did not include he 60GB of music into the amont of space you would need. Windows reports 250GB because that is how much space is free for the windows partion.

---

### Post by pirates712 on 2010-08-01
Well I can't get the screenshot utility to save the shot, so I will describe the contents of said window (but not through interpretive dance, sorry)

the devices are as follows:
/dev/loop0    directory: /  type: ext4  total: 16.1 GB
/dev/sda1    directory: /host    type" fuseblk   total: 455.9 GB (247 free)

---

### Post by corrytonapple on 2010-08-01
Yes, you don't have enough disc space for all of that music. (That is seen from the partion that is formatted in ext4, your ubuntu partion.) That other device is your hard drive's total capacity and free space. You have to purge the ubuntu partion and install again. I would make the partion about 90-100GB.

---

### Post by pirates712 on 2010-08-01
there is no way to store the files in a partition separate from the os?

---

### Post by hansdown on 2010-08-01
> **pirates712 said:**
> Well I can't get the screenshot utility to save the shot, so I will describe the contents of said window (but not through interpretive dance, sorry)

the devices are as follows:
/dev/loop0    directory: /  type: ext4  total: 16.1 GB
/dev/sda1    directory: /host    type" fuseblk   total: 455.9 GB (247 free)

I love you, man.

No, seriously.

sda1, is most likely your windows install.

To post a screenshot, click applications> accessories> take screenshot.

The default setting is, "grab the whole desktop".

Choose "grab the current window".

Also, change the "grab after a delay of"> to 3 seconds, or more.

To upload, scroll down, past the submit reply/preview post, to attach files.

Click "manage attachments".

Click "browse".

I usually save my screenshots to>>desktop.

In this case, click desktop, and find your screenshot, then click on it, then click open>

---

### Post by pirates712 on 2010-08-01
If that's my windows install, why is it showing up as 455 GB? That's the total capacity of the hdd windows and ubuntu are installed on. 

And can I keep my files in a diff. partition?

---

### Post by jtarin on 2010-08-01
> And can I keep my files in a diff. partition?Linux can read write to Windows....Windows cannot write to Linux and in very rare circumstances can it read....with proper software installed and not all Linux filesystems. I have all my movies and music not only on a differnt partition but a different drive that both OS's can read and write to. To get a differnt look at your disk space from Linux issue the command ```
df -h 
```in a terminal.

---

### Post by 3rdalbum on 2010-08-02
You've used Wubi to install Ubuntu. That actually installs Ubuntu within a file on your NTFS partition. The file is a fixed size - did you miss the option in the installer that lets you choose a size for the installation? The limit is 16 GiB, if I recall correctly.

Also I'm not quite sure why you want your music stored a second time on the same disk - can't you just access it through /host? (go to Places > Computer and double-click on Filesystem and then "host").

If you want to keep Ubuntu, then you should remove it through Windows and do a proper installation by booting your computer from the CD. Wubi is only really intended as a trial of Ubuntu.

---

### Post by hansdown on 2010-08-02
Erm.. nice catch,3rdalbum.

I didn't see that.

---

