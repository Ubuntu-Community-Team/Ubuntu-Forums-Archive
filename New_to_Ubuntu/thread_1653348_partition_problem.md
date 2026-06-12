---
title: "partition problem?"
date: 2010-12-26
forum: New to Ubuntu
---

### Post by rs87424 on 2010-12-26
So I recently had to re install maverick because I had an additional problem with the home partition not loading which caused great frustration and not having any way of using ubuntu. I am running it along side vista and when I was in the process of installing ubuntu I wanted to manually pick and choose partitions. when I finished with that I found out that my home folder is not mounted on start up..so I need to mount a 85GB space, which I didn't expect to happen. Also, when I try to download something it doesn't go anywhere really and when I click on "show in folder" it takes me straight to rhythmbox. So there is a problem with how my partitions are organized and I am not sure how I should fix it..any additional information I am not sure how to check... Help would be much appreciated!

---

### Post by oldfred on 2010-12-26
When you reinstall you want to choose the partitions and what format. If you have an existing /home you choose that but specify DO NOT format. Then it will automatically add /home to fstab and you will be using it.

You really need to add the /home to fstab. But you can look at directions for moving /home and just do the last couple steps.

To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)

---

### Post by rs87424 on 2010-12-26
oh ok thank you... I will let you know what happens as soon as I can get a chance to work on it

---

### Post by rs87424 on 2010-12-26
ok.. I have a few questions before I start this home move. I looked at the properties of the 85GB partition that seems to have all of my original ubuntu settings and folders. It indicates that it is ext3/ext4 type file system and the type of folder is inode/directory. how would I know I am picking this particular partition as my home? I would hate to make the mistake of picking the wrong one.

---

### Post by -kg- on 2010-12-26
> **rs87424 said:**
> ok.. I have a few questions before I start this home move. I looked at the properties of the 85GB partition that seems to have all of my original ubuntu settings and folders. It indicates that it is ext3/ext4 type file system and the type of folder is inode/directory. how would I know I am picking this particular partition as my home? I would hate to make the mistake of picking the wrong one.

How large is your root?  Do you have any other Linux OSes on the drive?  If you have a smaller root (and I would think you would have) and no other Linux OSes, and the partition size is right, it would be a no-brainer.  There's no mistaking the Windows partition...wrong format. But....

Browse it from a Live CD and make sure that all the files and directories are right.

Oh, and to make sure it auto-mounts through FSTAB, you'll need to mark the mount point during the partitioning step.  Be sure to mark "/home" in the mount point box.

---

### Post by rs87424 on 2010-12-27
ok.. I did what was mentioned in the first link (rsync) and it seems as though everything is back to normal but I am not sure yet. So is it optional to Remove old_home or should I just do that whenever? Also, when I click on "downloads" or "home" folders under "Places" Rythmbox still comes up and I can't see the folders. There was an error message when I was performing the switch which said something like "file Vanished...error" and then something about Google Chrome Stable... I am not sure what that meant. But anyways, I think I found the right partition as my home, just not sure if its working or not because of Rythmbox

---

### Post by oldfred on 2010-12-27
Not sure what error messages you are getting.

Sometimes you have permission issues. This link discusses some of them and at the end summarizes commands to make sure permissions are correct.

Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

---

### Post by rs87424 on 2010-12-28
would this fix the rythbox issue I am having? that seems to be the main problem I am having right now

---

### Post by rs87424 on 2010-12-28
ok nevermind I found out why I can't open anything in places. I just needed to right click and open with other application (file browser)

Thanks, if there are anymore problems I will be sure to ask again

---

