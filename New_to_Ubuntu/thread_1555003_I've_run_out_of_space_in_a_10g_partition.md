---
title: "I've run out of space in a 10g partition"
date: 2010-08-17
forum: New to Ubuntu
---

### Post by sumoboy98 on 2010-08-17
Hi Folks
 
First off, thank you for such a great site. A big hats off to all of the folks that help it be as great as it is.
 
I am nu to Ubuntu and find the program is fantastic. As a Windoze user, Ubuntu comes off as a breath of fresh air. I have installed Ubuntu, using Wubi, into a seperate 10gig patrtition. The triple boot setup with Windoze Xp, 7 and Ubuntu works flawlessly, but here is my problem.
 
I am trying to add a few new games / apps to Ubuntu using the installer and I am being told I have no free disk space. A check of space shows 2.9gb used and 6.8gb is free under the partition Ubuntu is installed in.
 
I have read about swap files but don't believe one was set up by Wubi. My pc has 3 gigs of ram so I don't think memory is an issue. I am thinking of installing Ubuntu without using Wubi and manually creating seperate partitions, but I think that is overkill to what must be a simple problem.
 
Any advice will be greatly appreciated and thanks in advance for your support.
 
Sumo.
 
Do you think

---

### Post by proxyofsocks on 2010-08-17
If you like Ubuntu you should install it on a dedicated partition.

When I first began using Ubuntu I liked it so much I spent hours learning, customizing, installing and playing. It was great. Then for some reason the wubi installation became corrupted and I could no longer boot my wubi. I was devastated. So I decided to install it on it's on partition and dual boot.

Now I don't even have a Windows partition anymore. If I need Windows for anything I run it in a VM. 

Freedom is nice.

---

### Post by neilms on 2010-08-17
My advice would be to sit down and plan how much space you want to allocate to linux. The manual says that a swap space is needed, so your existing installation is not correct in any event.

As far as I know,  new programs are installed under /usr - the size of your /usr partition will determine how much space you have for new programs. I would guess that the 6gb is allocated to /home.

I imagine you can try to resize the partitions using a partition program, but i would recommend a new install.

Also IMHO, 10gb is probably way too small for a fully functional ubuntu desktop. Maybe you should consider giving it more space.

---

### Post by sumoboy98 on 2010-08-17
Thanks for the reply. My Ubuntu is installed , via Wubi, on a seperate 10g partition. I am wondering if it thinks it is part of the XP partition and that is why it is saying "running out of space"?
 
I have no problem removing the Wubi install and re-installing, but would still be curious about the space issue.
 
Sumo

---

### Post by neilms on 2010-08-17
> **sumoboy98 said:**
> Thanks for the reply. My Ubuntu is installed , via Wubi, on a seperate 10g partition. I am wondering if it thinks it is part of the XP partition and that is why it is saying "running out of space"?
 
I have no problem removing the Wubi install and re-installing, but would still be curious about the space issue.
 
Sumo
It is because programs are typically installed under a /usr partition - that is the most likely reason you are running out of space. What do you get when you type at the terminal 'df -a'?
That should show the partitions you have and space used by each.

---

### Post by sumoboy98 on 2010-08-17
> **neilms said:**
> My advice would be to sit down and plan how much space you want to allocate to linux. The manual says that a swap space is needed, so your existing installation is not correct in any event.
 
As far as I know, new programs are installed under /usr - the size of your /usr partition will determine how much space you have for new programs. I would guess that the 6gb is allocated to /home.
 
I imagine you can try to resize the partitions using a partition program, but i would recommend a new install.
 
Also IMHO, 10gb is probably way too small for a fully functional ubuntu desktop. Maybe you should consider giving it more space.
 
 
Thanks for the reply. I can increase my partition to 30gb if need be. If I re-install without Wubi, will the included partition program set up the usr / home and swap sections automatically, or will I need to do it manually?
 
Sumo

---

### Post by bcbc on 2010-08-17
wubi installs to a virtual disk, not a partition. So even though you installed it on a 10GB partition, there will be a root.disk file there (/ubuntu/disks/root.disk) and that will be the same size you allocated when you installed wubi (if you don't remember selecting a size then wubi would have defaulted the size based on what it feels reasonable based on the partition size and free space).

It doesn't matter how much space is left on the partition, wubi will never use it after the root.disk size is set. 
Now there are some options to increase the space available to wubi installs, but since you are planning to reinstall direct, I wouldn't bother.

If you do "df -h" it will tell you how much space that "/" is using  and how much is free. This is the virtual disk, not the partition.

---

### Post by sumoboy98 on 2010-08-17
> **bcbc said:**
> wubi installs to a virtual disk, not a partition. So even though you installed it on a 10GB partition, there will be a root.disk file there (/ubuntu/disks/root.disk) and that will be the same size you allocated when you installed wubi (if you don't remember selecting a size then wubi would have defaulted the size based on what it feels reasonable based on the partition size and free space).
 
It doesn't matter how much space is left on the partition, wubi will never use it after the root.disk size is set. 
Now there are some options to increase the space available to wubi installs, but since you are planning to reinstall direct, I wouldn't bother.
 
If you do "df -h" it will tell you how much space that "/" is using and how much is free. This is the virtual disk, not the partition.
 
Thanks for your reply. I will check the space with the mentioned commands and let you know what I find. It is sure looking more like a direct install will be the path to take.
 
Sumo

---

### Post by bcbc on 2010-08-17
> **sumoboy98 said:**
> Thanks for your reply. I will check the space with the mentioned commands and let you know what I find. It is sure looking more like a direct install will be the path to take.
 
Sumo

If you're OK setting up the partitions manually, then you can use the following Howto to migrate your wubi install: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by sumoboy98 on 2010-08-18
Well I have jumped in and did a direct install of 10.04. Wubi blew itself away in Windoze flawlessly but did not appear to create a swap file when it installed. Perhaps the virtual drive version uses Windowz swap settings? I have marked the thread as solved and  offer many thanks to everyone for their help with my problem.
 
Until the next question ...
 
Sumo

---

