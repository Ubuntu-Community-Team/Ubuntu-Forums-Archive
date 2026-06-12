---
title: "new extern HD 160 gig"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by freykatt on 2009-05-12
Hi all, I just formated and partitioned a WD 160 gig external HD ext3.  I will use it for storage only.  Whenever I try to cut and paste, I get a warning that I am not the owner.  I have perused the forum and have tried a couple of things having to do with using the terminal, sorry, but everything I do or try does not accomplish anything.  Ubuntu 9.04 upgrade.  I have clicked on everything on this puutor for the answer, but unable to make sense of or find an answer.  I would appreciate any help please, thank you     dick

---

### Post by unutbu on 2009-05-12
This is a very good guide: [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
If you run into any problems, post back here with a copy of the terminal output.

---

### Post by freykatt on 2009-05-12
Hi unutbu, thank you for your quick reply.  I checked it out and tried it, but, no luck, it seems to be what I need, but, not having worked with a terminal (complete newby) I am lost.  will try it again later.  Also, it is recognized by the distro and I have formated and partitioned it as ext3, just won't let me cut and paste.  Frustrating.   Thanks again   Dick

---

### Post by MrWES on 2009-05-12
> **freykatt said:**
> Hi unutbu, thank you for your quick reply.  I checked it out and tried it, but, no luck, it seems to be what I need, but, not having worked with a terminal (complete newby) I am lost.  will try it again later.  Also, it is recognized by the distro and I have formated and partitioned it as ext3, just won't let me cut and paste.  Frustrating.   Thanks again   Dick


you need to change the ownership and/or permissions of the mount point; I'm assuming it's /media/something, so from the terminal:

```
sudo chown -R youusername:yourusername /media/something
```

you might also need to change the read/write permission too:
```
sudo chmod -R 755 /media/something
```

Bill

---

### Post by freykatt on 2009-05-12
Yes, exactly what I am trying to do, just not getting it done.  Question? what is "something" represent.????        Dick

---

### Post by Jazzy_Jeff on 2009-05-12
An easy way to get around this is just to format it fat32 if it is just for storage. That is what my external harddrive is formated to.

---

### Post by theozzlives on 2009-05-12
> **freykatt said:**
> Yes, exactly what I am trying to do, just not getting it done.  Question? what is "something" represent.????        Dick

"something" represents the mount point. If it has no label it'd prolly be "disk"

---

### Post by freykatt on 2009-05-12
Hi Jazzy Jeff.  Thanks for your reply. I shall reformat the drive as Fat32 as it is only for storage then try it again.  Your appreciated.  Dick

---

### Post by freykatt on 2009-05-12
Hi Ozz,  thanks for replying.  Ok, yeah, it is "mynewdrive" so just left it that way. If I keep this up, I might just get a little familiar with CL, right now I am struggling with it.   Thank again,      Dick

---

