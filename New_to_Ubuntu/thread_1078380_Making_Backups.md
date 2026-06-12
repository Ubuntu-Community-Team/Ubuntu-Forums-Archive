---
title: "Making Backups"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by mistypotato on 2009-02-23
Hi,

I only have command line access.

How would I copy files from my ubuntu 8.10 box to CD ?

---

### Post by Le-Dart on 2009-02-23
You can use cdrecord
[http://cdrecord.berlios.de/private/cdrecord.html](http://cdrecord.berlios.de/private/cdrecord.html)
[http://ubuntuguide.org/wiki/Ubuntu:Feisty/CDDVDBurning](http://ubuntuguide.org/wiki/Ubuntu:Feisty/CDDVDBurning)

---

### Post by mistypotato on 2009-02-23
Thanks :)

But I'm in a situation where I cannot get my system started and I'm running from the recovery disk...I never installed that program

---

### Post by echo314 on 2009-02-23
If you are using a LiveCD, and have Internet access, you can indeed just install it with the usual apt-get install.

---

### Post by theozzlives on 2009-02-23
try this [http://ubuntuforums.org/showthread.php?t=35087]("http://ubuntuforums.org/showthread.php?t=35087")

---

### Post by mistypotato on 2009-02-23
thx echo.  installed.

Now, I looked over the how=tos. man pages and searched elsewhere but what I could not find is a simple "How To" to copy files from a source on the hard drive to the CD?

thx

---

### Post by echo314 on 2009-02-23
I can see how this might be confusing. I've read some stuff on cdrecord, including [here]("http://ccrma.stanford.edu/guides/planetccrma/cdrecord.html").

From what I can tell, its a two step process. First, use the mkisofs command to create the iso image of the data you want to burn. Next, use the cdrecord command to burn that iso to a disc. I hope this was helpful! Let us know how it goes.

First, I think it would be something like```
mkisofs -J -v -o image.iso /dir/here/
```

Looks like you would need to get all the data you wanted to backup in one folder, as long as it was not larger then the CD capacity. You can use the 'mv' command to move files and folders around, the help options should show you how to use it. Then, you would use ```
 		 cdrecord -v dev=0,0,0 speed=16 -data image.iso
``` to burn the iso. As the link i posted says, check the dev= option by using the ```
 cdrecord -scanbus
``` command, to tell you where the drive is.

---

