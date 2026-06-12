---
title: "How Much Space Do I Need?"
date: 2010-03-10
forum: New to Ubuntu
---

### Post by terrybennett on 2010-03-10
I had 9.04 on 7GB with no problems.  I clean installed 9.1 on a partition of 8.3GB space.  My Home is on a separate partition.   Now I keep getting a warning message that I am running out of space.   What is the minimum recommended space for Ubuntu?

What can I remove that will free up some space?  During install there was an option about importing Windows settings and making documents available.  Did I import copies of  everything?

I am running on a dual boot Vista and 9.1.  Only been using Ubunutu a short while.

---

### Post by jonabyte on 2010-03-10
I use wubi to dual boot and always use the 30gig partition and still don't think its enough for me.
It really depends on what you are using the machine for? Don't need gimp or evolution? Uninstall them, etc.

---

### Post by r-senior on 2010-03-10
My root filesystem (separate /home) on my 9.10 laptop has only used 4.3G and I've added a few things to the base without taking anything away.

If you go to a terminal and type

$ df -h

it will show you how much space is used overall.

You can use Applications -> Accessories -> Disk Usage Analyzer to scan your root filesystem and see graphically where the space is being used.

---

### Post by ChildOfMana on 2010-03-10
Try using the following command to remove temporary packages of former installations:

```
sudo apt-get clean
```

This may or may not clear up a lot of space, depending on how much and in what way you've been using your system since the initial installation.

---

### Post by terrybennett on 2010-03-10
I am mostly using it to learn about Linux.  Do a lot of web browsing.  I need Windows for Quicken and Netflix so can't really do away with Vista right now.  I tried Wine but Quicken just will not run.  Nefflix will not run with Linux.

I have used Gimp once and really liked it.  I can uninstall Evolution.

Tried the apt-clean thing and did not gain anything there.

Is 9.1 that much larger than 9.04.  I had 9.04 on for a couple of month and never had a problem.  I tried to upgrade and it has not been the same since.  I was able to format and do a clean install of 9.1.  Now I get low space warnings.

---

### Post by albert s on 2010-03-10
I have my /root on a 14G partition and its only using 3.8G at the moment,
have quite a few things installed.

---

### Post by kleskjr on 2010-03-10
my Linux partition is 11GB and it is quite enough for me, but I have another 1 GB swap partition. It could be that your slap should share place with ur system, maybe there is a way to control it.
good luck

---

### Post by r-senior on 2010-03-10
> **terrybennett said:**
> Is 9.1 that much larger than 9.04.  I had 9.04 on for a couple of month and never had a problem.  I tried to upgrade and it has not been the same since.  I was able to format and do a clean install of 9.1.  Now I get low space warnings.
Not significantly. Did you try the Disk Usage Analyzer? 

Something else ... but you've probably tried it ... emptying your wastebasket?

Anything else unusual, like attempts to install virtual machines, and perhaps left virtual disks sitting around?

kleskjr's suggestion is a good one ... did you perhaps create a swap file in your partition?

$ cat /proc/swaps

should tell you.

---

### Post by terrybennett on 2010-03-10
Here is a screenshot of my disk usage.

Does anyone see anything out of sorts.   It just does not look like that much disk space should be used.

---

### Post by era86 on 2010-03-10
I just did a 7gb partition for root, 1g for swap, and 32 for home.  Haven't run into any problems yet.  Strange...

---

### Post by r-senior on 2010-03-10
> **terrybennett said:**
> Here is a screenshot of my disk usage.

Does anyone see anything out of sorts.   It just does not look like that much disk space should be used.
That's odd. The numbers don't add up. It looks like only 2.5G is used and almost 0.5G is your /home partition. Could you run that again, but go to Edit -> Preferences and untick /home so that we can just see the root filesystem.

Could you also post the output from:

$ cat /proc/swaps

---

### Post by Running_Dualboot on 2010-03-10
> **jonabyte said:**
> I use wubi to dual boot and always use the 30gig partition and still don't think its enough for me.
It really depends on what you are using the machine for? Don't need gimp or evolution? Uninstall them, etc.

i did the same and I only used 10-30GB.

---

### Post by terrybennett on 2010-03-11
Well I went to log on tonight and could not.  It kept going back to the login screen.    I just started a new install and format of the partition.  I will see how much space I have after this fresh install before doing anything else.   

Will left everyone know.

---

### Post by terrybennett on 2010-03-11
Okay after the new install I have 5.8 GB of free space.  Yaay!!

This time I made sure to format with ext4 journaling file system and I did not import Windows settings.  

Must have been one of these things. 

Thanks to all for suggestions and help.

---

