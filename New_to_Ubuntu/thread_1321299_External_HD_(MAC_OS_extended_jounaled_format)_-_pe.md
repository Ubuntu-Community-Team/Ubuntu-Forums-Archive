---
title: "External HD (MAC OS extended jounaled format) - permissions issue"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by pixelup on 2009-11-09
Hi there,
Absolutely newbie to the linux world.

I've been searching on this forum for a solution to what it seemeed to me it was going to be a simple issue but none of the answers found solved my problem.

I have installled Ubuntu 8.04 and the Ubuntu Studio package on a acer extensa 4620Z (not such a great quality hardware I might say).

I have an external HD, **MAC OS journaled** format that mount on ubuntu, I can see the content (4 folders) but I cannot access any of the folders on the drive (folder icon X), error message:
The folder contents could not be displayed.
You do not have the permissions necessary to view the contents of "FOLDER NAME".

I am able to access the drive content thru the **sudo nautilus** command line, open folders and files but **cannot write** or copy into or out the drive.

I tried sudo chmod/chown unsuccessfully. permissions error.

I also changed permissions for the drive on a MAC but the issue remains.

This HD is a main back up therefore I do not want to format it, I want to be able to use the drive with my Ubuntu package.

Any help? Let me know if you guys need any other information that since I'm a total newbie I might be forgetting.

Thanks a bunch.

pixelUp

---

### Post by schauerlich on 2009-11-09
In OS X, open the drive, select the folders you want, right click and hit "Get Info". Go down to "Sharing & Permissions" and change "everyone" to "Read & Write".

---

### Post by pixelup on 2009-11-12
Hi there,
Thanks for your reply.

I've done that before (change permissions on HD thru get info) and still not working, I've also dejournalized the HD on a mac.
Now Read is permitted but not write allowed on the disc.

Any other idea?

thanx

pixelUp

---

### Post by schauerlich on 2009-11-12
Try installing hfsutils through Synaptic. You will need to restart.

---

