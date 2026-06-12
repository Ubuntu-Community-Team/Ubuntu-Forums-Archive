---
title: "Ubuntu on my brother's comp"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by Xarver on 2009-01-23
Hello, my brother wants Linux on his computer so I installed Wubi.
he rebooted the computer, and we go to the "partition editor" and click forward and we get this error: [http://img407.imageshack.us/img407/1895/screenshotfh0.png](http://img407.imageshack.us/img407/1895/screenshotfh0.png)

Any help appreciated, We both want Ubuntu on this computer with Windows dual boot! :)

P.S. It's a hp pavilion a630n
EDIT: Ubuntu 8.10 using Wubi 8.10 Installer

---

### Post by handydan918 on 2009-01-23
The error seems to say "No root file system is defined"

So, define a root file system. 

You have to tell the installer where root (or /) is going to go.

---

### Post by Xarver on 2009-01-23
Sorry, I've been using linux for a while although can you please tell me how to do that? Thanks for your reply. :)

---

### Post by avtolle on 2009-01-23
> **handydan918 said:**
> The error seems to say "No root file system is defined"

So, define a root file system. 

You have to tell the installer where root (or /) is going to go.
That's normally true; but not on a Wubi install, as I recall.

To the OP: I've a feeling that the way to resolve the problems is to uninstall whatever of Ubuntu has been installed by Wubi, and then defrag the HDD on your brother's computer (maybe more than once) then reinstall. The partitioning problem under Wubi generally arises in situations where the HDD is badly fragmented. Give that a try and see how it goes.

---

### Post by Xarver on 2009-01-23
How do I defrag a hard drive?
And is their alternative with out re-installing Ubuntu?

---

### Post by avtolle on 2009-01-23
You defrag a hard drive by using the defragmenter under Windows. If you don't remove Ubuntu as installed by Wubi, from what I can gather the defragmenting of the HDD will mess up the Ubuntu install and create even bigger problems for you. So, use the "Add/Remove" program feature under Windows (Control Panel, I believe) to remove Ubuntu; then run the defragmenter; and reinstall using Wubi. I gather your reluctance is due to the download time for the iso using wubi.exe. Unless you have a CD of 8.10 from which you may install via wubi, it will need to be downloaded and installed as before.

---

### Post by Xarver on 2009-01-23
Okay, so remove ubuntu, defrag the hard drive, and reinstall?
I also want to know if this is safe because I don't want to do anything bad to the computer. I don't want to remove Windows XP, any files (only temporary/unimportant), and keep Windows XP as it is. 

So is it safe???
Thanks for everything! :)

---

### Post by avtolle on 2009-01-23
Take a look at [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide) which may help answer some questions and give additional information. You might also visit the Wubi sub-forum on this forum to see if anyone else has had your problem (generally, the problem with partitioning comes up with the swap partition, but a badly fragmented HDD would logically cause problems with partitioning the virtual drive Wubi creates for Ubuntu over the NFTS formatted drive on the HDD).

---

