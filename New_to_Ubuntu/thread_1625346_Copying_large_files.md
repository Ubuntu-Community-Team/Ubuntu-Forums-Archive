---
title: "Copying large files"
date: 2010-11-18
forum: New to Ubuntu
---

### Post by echo314 on 2010-11-18
cp and rsync seem to choke when I try to copy a 75 GB virtual hard disk. Period freezing of Fx and nautilus. Is there a program better suited to making a copy of a large file, or can I change some parameters to get the system to copy gracefully?

---

### Post by psusi on 2010-11-18
Ummm... it's going to take quite a while to copy that much data.  You just have to wait it out.

---

### Post by echo314 on 2010-11-18
I'm not concerned at all about it taking a good amount of time. I am concerned that the one copy operation seems to freeze the system. Even with a big file, I would expect this to work "slow and steady" and get the job done without impacting other work, since this is not a time critical operation.

---

### Post by amauk on 2010-11-19
Depending on your disk setup (inc. which filesystem your using), this could be an IOwait issue
(basically disk is so busy writing stuff, that reads get delayed and applications stall for a second or two until a read can be completed)

run top, then start copying the file,  and see if the IOwait changes significantly

*edit*
Btw, the IOwait is the "wa" in the CPU line of top

---

### Post by iponeverything on 2010-11-19
This is known issue. Big copies brings the system to it knees until the copy finishes. A 75 Gig copy will take a while finish, a terminal with top running will let you see it chugging away..

---

### Post by asmoore82 on 2010-11-19
Are you copying over Wireless?

You could use the `--bwlimit` option of rsync to enforce "slow and steady"

---

### Post by echo314 on 2010-11-19
Not copying over wireless, just from one folder to another on the same partition. Would the rsync option mentioned still be useful?

---

### Post by asmoore82 on 2010-11-19
Aha, copying on the same partition involves lots of rapid reading and
writing to the same physical disk - that can get ugly.

Do you really need 2 copies of the same file?

If not, you can just move them. Moving files on the same partition is always instant.
You could also hard link them, this gives the file 2 names on the file system
mapping to the same physical file.

---

### Post by echo314 on 2010-11-19
Is saving an image through the VirtualBox interface different from my copying the harddisk image in nautilus/bash? My goal is to have a clean copy so that I can revert, and I figured that copying the image was the way to do it.

---

### Post by asmoore82 on 2010-11-19
Why not use snapshots, they are great!!

You can even "collapse" them later into the core image
if you are happy with all of your changes.

---

### Post by matt_symes on 2010-11-19
Hi

> Why not use snapshots, they are great!!

You can even "collapse" them later into the core image
if you are happy with all of your changes.!Hear, hear. That is what they were designed for.

Kind regards

---

