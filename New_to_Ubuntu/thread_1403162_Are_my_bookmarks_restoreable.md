---
title: "Are my bookmarks restoreable ?"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by Innernet on 2010-02-09
Hi all.
Saved "Home folder" to an external USB hard drive. And it is safely there.  

Upgraded to 9.10 

I already restored my 'desktop' contents; all fine. Cannot find where are the old bookmarks. 

Where are they or are they lost forever?
If they are somewhere and you tell me how to locate them, how do I drag/restore them to where they are supposed to reside ?

---

### Post by golanbatrac on 2010-02-09
This thread should get you going:

[http://ubuntuforums.org/archive/index.php/t-1016719.html](http://ubuntuforums.org/archive/index.php/t-1016719.html)

(the ~/.mozilla directory is a hidden directory.  while in your home directory in nautilus, hit CTRL + h to view hidden files and directories.)

---

### Post by Innernet on 2010-02-09
Thanks for responding.  Found your link not simple to follow.
Any idiotproof guidance please ?

---

### Post by HappyFeet on 2010-02-09
Just insert your usb hard drive. Open it and do Ctrl-H. Then Ctrl-A will highlight everything. Then Ctrl-C to copy everything. Next, on the new installation, go to the new home folder and Ctrl-V to paste. It will ask if you want to replace some things, say yes. Enjoy.

---

### Post by golanbatrac on 2010-02-10
> **HappyFeet said:**
> Just insert your usb hard drive. Open it and do Ctrl-H. Then Ctrl-A will highlight everything. Then Ctrl-C to copy everything. Next, on the new installation, go to the new home folder and Ctrl-V to paste. It will ask if you want to replace some things, say yes. Enjoy.

If that works, that's a lot easier than the way I do it.

OP: If you have permission troubles (and I think you will), open a terminal and type:
```
gksudo nautilus
```and then follow hf's instructions.

---

### Post by golanbatrac on 2010-02-10
> **Innernet said:**
>   Found your link not simple to follow.

Sorry about that.  I scanned the thread and saw that it had all of the relevant information, but you're right, it is overcomplicated and a bit confusing.

---

### Post by HappyFeet on 2010-02-10
> **golanbatrac said:**
> If that works, that's a lot easier than the way I do it.
It works.

> **golanbatrac said:**
> OP: If you have permission troubles (and I think you will), open a terminal and type:
```
gksudo nautilus
```and then follow hf's instructions.

There won't be any permission problems.

---

### Post by Innernet on 2010-02-10
Thanks.
The restoration is done as needed, at this point only the bookmarks are missing, should be a couple of MByte.
The only 'Bookmarks' item is not the actual bookmarks, it is a 6KB html link and cannot find another anywhere else.  Snapshot attached

---

### Post by lovinglinux on 2010-02-10
> **Innernet said:**
> Thanks.
The restoration is done as needed, at this point only the bookmarks are missing, should be a couple of MByte.
The only 'Bookmarks' item is not the actual bookmarks, it is a 6KB html link and cannot find another anywhere else.  Snapshot attached

Bookmarks are stored in *places.sqlite* and backups are stored under the *bookmarkbackups* folder, as json files. See the Backup section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by Megaptera on 2010-02-10
I use Xmarks (online) to backup & sync my bookmarks. Really useful and simple to use this quote from the website "Install Xmarks on each computer you use, and it seamlessly integrates with your web browser and keeps your bookmarks in sync."

Link: [http://www.xmarks.com/](http://www.xmarks.com/)

Works with _buntu, XP, Vista etc.

Hope this is of interest as a different approach?

---

### Post by HappyFeet on 2010-02-10
> **lovinglinux said:**
> Bookmarks are stored in *places.sqlite* and backups are stored under the *bookmarkbackups* folder, as json files. See the Backup section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

Copying and pasting the .mozilla dir to a pendrive works for me. The only 3 config files I save are .mozilla/.opera/.thunderbird I actually like most things to start off fresh when I reinstall. Since I keep all my docs/pics/music/etc on separate drives, I have next to nothing to backup before I install the latest ubuntu. I like to keep things simple and straight forward.

---

