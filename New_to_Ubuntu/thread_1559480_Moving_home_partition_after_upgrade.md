---
title: "Moving /home partition after upgrade"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by nu2u904 on 2010-08-23
> **forestpiskie said:**
> Boot the livecd - go to gparted. Right click swap (sda6) turn off swap.
 
Expand sda2, then the unallocated space will be inside the extended.
 
You can now try expanding sda5 - it may be that sda5 needs moving to the left hand side of sda2 beforehand.
 
Once done right click sda6 turn on swap.
 
I believe my situation falls in the same class to continue this thread.
 
I have upgraded from 9.04 to 9.10 to 10.04. 
Since the upgrades were by update manager there was no opportunity to make changes to my partitions .
 
I now have the problem that I have only 300MB disk space am unsure what big files I could delete. To make room for 10.04 I had deleted 3 iso files. Xp is running on a 500GB hard drive from which I had carved out 10GB for ubuntu. I would like to carve out another 20GB for ubuntu and create separate partitions for home and perhaps other key directores. My problem is how do I assign another partition as /home while /home is still assigned to /. I have  checked the site tomcmd recommended, but  this required a clean install. I just did a cat /etc/lsb-release and got this:
ID=Ubuntu;release=10.04;codename=lucid;description =Ubuntu 10.04.1 LTS. Thank you for giving me something to think about.

---

### Post by Elfy on 2010-08-23
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

[http://www.google.com/cse?cx=012285703143635244993:i9yr8qlpb18&q=moving+home](http://www.google.com/cse?cx=012285703143635244993:i9yr8qlpb18&q=moving+home)

I only did it once and used psychocat's tutorial which is no longer supported.

You might get yourself some space cleaning the apt cache 

```
sudo apt-get autoclean
```

---

### Post by mapes12 on 2010-08-23
This one worked for me:-

[http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)

---

