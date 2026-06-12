---
title: "Can I just replace the home folder with a backup?"
date: 2010-10-15
forum: New to Ubuntu
---

### Post by kapi on 2010-10-15
I want to upgrade to 10.10 and have backed up a copy of my home folder to an external hardrive, do you know that if I install 10.10, can I simply replace the home folder with the backed up version?

cheers

---

### Post by k3lt01 on 2010-10-15
Short answer is yes.

Long answer is, next time set up your PC with a / and a /home partition. That way you wont have to do this again.

---

### Post by sanderd17 on 2010-10-15
> **k3lt01 said:**
> Short answer is yes.

Long answer is, next time set up your PC with a / and a /home partition. That way you wont have to do this again.

yes, but if you want to have a completely new system and only have your documents in it, you should only copy the visible folders to your new home, not the folders which start with a "." (you can see those by pressing ctrl+H in nautilus). If you want the settings too, copy the *.folders* too.

---

### Post by k3lt01 on 2010-10-15
Taking into consideration the OPs other thread it appears, to me anyway, that they want their settings as well. Thus my answer.

---

### Post by kapi on 2010-10-15
> **k3lt01 said:**
> Short answer is yes.

Long answer is, next time set up your PC with a / and a /home partition. That way you wont have to do this again.

any documentation to show how

---

### Post by Black Hawk on 2010-10-15
For information on how to create a separate /home partition during installation:
[http://www.psychocats.net/ubuntu/installseparatehome]("http://www.psychocats.net/ubuntu/installseparatehome")

For information on how to move a /home partition after the installation of ubuntu:
[https://help.ubuntu.com/community/Partitioning/Home/Moving]("https://help.ubuntu.com/community/Partitioning/Home/Moving")

---

### Post by migs73 on 2010-10-15
Assuming you do not dual boot bu tare doing a clean install;

Select the Advanced Install
Give yourself 3 Partitions;
Swap (size about 1.5x your RAM)
/ (root, Minimum size about 10GB for OS and software)
/home (for the rest of the drive)

Proceed with install.

Next time you want to install your OS you only have to format and write to the / partition. Name the /home parition but don't format it.
Low and behold new OS, old settings/docs etc.



EDIT: too late, or do as described above, probably a better how to than mine :)

EDIT EDIT: Definately a better how to than mine ;)

---

### Post by baddnady23 on 2010-10-15
> **kapi said:**
> any documentation to show how

The next time you reformat, backup your /home to an external hard drive.  That way all your personal stuff is saved.  When you install ubuntu then, you can wipe out the old hard drive and tell it in the installer to make different partitions.  For example, you can set up a 20 GB partition, 100 GB partition and a 5 GB partition all on the same disk.  Then you can tell it to install / in the 20 GB, install /home in the 100 GB and SWAP in the 5 GB spots respectively.  Then you could copy everything on the external hard drive back over to /home once you boot up and all your documents and settings will be right as they were.  You will only then have to reinstall programs that you want.

This way in the future, you would only have to reinstall / to the 20 GB partition and you /home would always be untouched.  This makes life so much easier down the road.  

The way of doing this is while in the installer for ubuntu from the Live CD,  when it comes time to telling it where to install, select advanced set up.  Then select the partition you want for / and tell it to format it.  Then select the partition you want for /home and **do not select format.**  Doing so will erase everything in /home.  Just select it and tell it to mount /home there.  Do the same for swap.  Be careful, double check your work, and make sure you have your stuff **backed up.**  It can be tricky here for a beginner and checking a wrong box(i.e. format /home) will erase all your personal stuff.
I included a picture of my current partition table to show you visually what I mean.  All on the same disk I have a:

23 GB /
16 GB NTFS (for file sharing with windows if need be)
11 GB SWAP
880 GB /home

---

### Post by kapi on 2010-10-15
You are such a great help, thanks so much. I appreciate your time

Regards

Kapi

---

### Post by k3lt01 on 2010-10-15
I hope you haven't done it yet. It was night here so that is why I haven't replied.

All of the above info is good but partitioning, as you can probably see from the different answers, is personal choice. There is no right or wrong way.

My setups are all 10GB /, 2GB SWAP, and the rest /home.

Why I do it like this is 10 GB / is plenty for most standard setups including Edubuntu which has alot of extra applications. 2GB for SWAP I found to be ideal for me because the general consensus of 1.5 times your RAM just wont work when you only have 256MB of RAM. My little old machine just would not function without the 2GB of SWAP. The rest being /home is just logical for standard setups. in my 2 main cases the rest is approximately 230GB for the laptop and 980GB for the desktop.

---

