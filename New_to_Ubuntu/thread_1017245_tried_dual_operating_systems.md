---
title: "tried dual operating systems"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by libihero on 2008-12-20
i partitioned my hard drive, and i tried to download ubuntu 8.10
i wanted to do the "guided: use largest continuous free space" but it showed that ubuntu would result in 100% after
and i tried the first guided that showed ubuntu to result in 60%, but there was an error
soo im jus wondering what i have to do exactly to have both operating systems when installing ubuntu 8.10

---

### Post by infinitejones on 2008-12-20
What was the error?

---

### Post by Zeedok on 2008-12-20
Did you partition your hard drive before trying to install Ubuntu?

You don't need to, but no matter, if you already have a partition ready to go, just select the "manual" option when selecting where to install Ubuntu (ie not the "Guided") select your new partition (ie the one you want to put Ubuntu on, everything there will be wiped) and off you go. Choose carefully . . . once you format a partition the info on it is gone - don't actually reformat your Windows partition by mistake . . .

---

### Post by noerrorsfound on 2008-12-20
Have you thought about using the manual option? I'm not sure how the other options set up your hard disk, but with manual, you can create a separate home partition so you can easily reinstall Ubuntu or switch Linux distributions, while keeping all your files.

[Some information about partitioning here]("http://www.cyberciti.biz/tips/the-importance-of-linux-partitions.html"), including advantages of dividing your system into more partitions than necessary.

---

### Post by presence1960 on 2008-12-20
I found out that it is best to use the manual option when installing. I was helping a friend install Linux Mint on his PC. Good thing I had the foresight to tell him to back up his important files. I used the guided install and it didn't work as intended. To make a long story short I had to reinstall windows and Mint on that one. Besides the manual option gives you great flexibility in choosing the partitions sizes and you can make an extra partition for /home or a partition for storage if you so desire. Of course this is my preference only and as in most cases there is more than one way to accomplish the same objective.

---

### Post by libihero on 2008-12-20
i partitioned my hard drive, and the error it gave me during the guided was something about being unable to partition
i'm not too computer code savy, so how would i recognize my free space created on the manual?

---

### Post by Bölvaður on 2008-12-20
I would need to urge you to manually do the partitions before you install.

It is the wise way.

Then when installing choose manual partitioning and just select the partitions you already made.
There are very good tutorials on this if you use google with the correct keywords.

---

### Post by bodhi.zazen on 2008-12-21
> **libihero said:**
> i partitioned my hard drive, and i tried to download ubuntu 8.10
i wanted to do the "guided: use largest continuous free space" but it showed that ubuntu would result in 100% after
and i tried the first guided that showed ubuntu to result in 60%, but there was an error
soo im jus wondering what i have to do exactly to have both operating systems when installing ubuntu 8.10

That is a bug in the installer (and a nasty one at that). The first screen shows Ubuntu will use 100 % but if you continue it will update and show the actual usage.

I agree, I always partition prior to and separate from installing.

---

### Post by sofasurfer on 2008-12-21
I worried about the same thing when I tried to install 2 Linux os's. It seemed to indicate that the new os would use the whole disk. But it did not. After the dual install, the partition information showed the individual os's. So just ignore the worry about using the whole disk. Its ok as long as you choose, "use largest continuous free space".

---

### Post by libihero on 2008-12-21
ok i tried manual, and what i did was clicked on the free space
then it gave me a whole bunch of partition options, such as logical or primary, and things like mount root.... and i dont know what to do :(

---

### Post by mkvnmtr on 2008-12-21
For a first time installer the manual option appears very complicated. I remember my first time . I got to the point of formating 6 or 8 times and backed out. Post a picture of Gparted on your partitions and somebody will probably be abel to lead you through it.

---

### Post by bodhi.zazen on 2008-12-21
> **libihero said:**
> ok i tried manual, and what i did was clicked on the free space
then it gave me a whole bunch of partition options, such as logical or primary, and things like mount root.... and i dont know what to do :(

See this thread : 

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018")

---

### Post by tad1073 on 2008-12-21
What you need to do at that point is select extended partition, create, inside the extended partition create a swap partition of 1gb=1024mb, then create the ext3 partition and set the mount point as "/".

An extended partition is needed if you have more than 3 partitions on one hdd. I Think!!!

The extened partition will allow you to add other partitions in the future once you learn more about linux and ubuntu.

---

### Post by libihero on 2008-12-21
wow i think i just got a little more confused with that link.......
i'll try to post a pic of what i got so far
like i REALLY dont wanna mess this part up... cuz then it'll screw up my whole comp haha

---

### Post by tad1073 on 2008-12-21
here...

---

### Post by libihero on 2008-12-21
here is what comes up with me, i dont know how to make it look like yours

---

### Post by tad1073 on 2008-12-21
Edit the partition and from the mount point dropdown menu select "/".

Also, make it primary.



My partition are setup with:

Ubuntu 8.04 on /dev/sda5 and Ubuntu 8.10 x86_64 on /dev/sda7 with the swap shared between the two.
I guess I got lucky on that one, as I did not create a swap partition when I installed 8.10 x86_64.

---

