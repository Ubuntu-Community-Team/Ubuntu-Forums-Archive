---
title: "Ubuntu reinstall"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by lover_of_sc on 2009-08-26
Hi threre,

Does a re-installation from the live Ubuntu 9.04 64bit clear all my exsisting files in my home/ folder? My second computer seem to have crashed big time - the screen goes all black after the ubuntu logo and before the logon screen normally appear... Id there a way I can save my old files? Cheers.

---

### Post by snakeman21 on 2009-08-26
Yes, you can save your files.  You need someplace to copy them to, such as an external hard drive or a large thumb drive.  

Boot your computer from the live CD and you can access the computer's hard drive from there.  Click on "places" and you should see your hard drive.  Let's say you have a 200GB hard drive.  It will say "200GB media."  Click that, and navigate to your home folder.  Copy all the files you want to save to your external media, and when you're done, go ahead and reinstall.  After reinstalling, you can copy your files back to your new installation. Good luck!

---

### Post by gali98 on 2009-08-26
You might also be interested in this:
[http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)
Kory

---

### Post by tarps87 on 2009-08-26
Alternatively to could use the live cd to install 9.04 **along side** your original install, copy the data across, delete the old installs partition and resize the new one. This should be simple as long as you have enough disk space. If you do have an external hard drive that would be better

---

### Post by Bucky Ball on 2009-08-26
You need to make sure you choose 'Manual Partition' and DON'T create another home. Your existing /home you will see there. Check to make sure it is not set to format the partition (along with any other partitions you want to keep) and away you go. 

I've recently been checking about this on another thread. I see if I can find it for you. 

Main thing; if you don't do a manual partition, there is no way of keeping your current /home.

** Starting from post #5 here:

[http://ubuntuforums.org/showthread.php?t=1244420](http://ubuntuforums.org/showthread.php?t=1244420)

Vastone has done what I describe.

---

### Post by gali98 on 2009-08-27
Note on Bucky Ball's post. The Home directory partition will only be there if you already have your home on a separate partition.
Kory

---

### Post by nikhilbhardwaj on 2009-08-27
personally
i'd recommend that you have the /home on a separate partition

---

### Post by Bucky Ball on 2009-08-27
> **lover_of_sc said:**
> Hi threre,

Does a re-installation from the live Ubuntu 9.04 64bit clear all my** exsisting files in my home/ folder?** 

Gali98, this is from OP's original post.

nikhilbhardwaj, same/same. That is what we are talking about. PLEASE read posts carefully before posting. :)

---

### Post by tarps87 on 2009-08-28
> **Bucky Ball said:**
> Gali98, this is from OP's original post.

nikhilbhardwaj, same/same. That is what we are talking about. PLEASE read posts carefully before posting. :)

> **lover_of_sc said:**
> Hi threre,

Does a re-installation from the live Ubuntu 9.04 64bit clear all my exsisting files in my home/ **folder**?


From the OP it is not clear if home is just a folder or it is a separate partition, this needs to be confirmed. Not being picky just need confirming before the op tries to attempt it

---

