---
title: "Disk Space on root Partition in Use"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by foogo on 2011-02-15
Hi whenever I log onto my computer now, my computer tells me "99 % of disk space on the root partition is in use." Today it says 100 % and my computer is barely functioning. I can go online, but I can not log into anything that you have to enter a username and password for. I am using a different computer now.

This happened when I first got the computer, and I called someone for help. By writing sudo apt-autoclean in the terminal, the whole problem was fixed. However, I have tried that and sudo apt-get clean, and it does absolutely nothing to fix the problem. Please help me out. I am not very literate in the terminal commands. 

I only have about 5 pictures on the computer and 25 word documents. So there should not be much stuff taking up memory.

Thanks.

---

### Post by TeoBigusGeekus on 2011-02-15
Can you post us the output of
```
df -h
```
?

---

### Post by foogo on 2011-02-15
I'll have to type it since I can not log into the ubuntu forum account from that computer, but it says:

Filesystem  Size  Used  Avail  Use%  Mounted on
/dev/sda2   3.4G  3.3G    0     100        /
varrum       501M  100K  501M  1%      /var/run
varlock       501M   0      501M   0%     /var/lock
udev           501M  36K   501M   1%     /dev
devshm      501M   48K   501M   1%     /dev/shm
lrm             501M  1.9M  499M   1%     /lib/modules/2,624-24-lpia/volatile
overflow     1.0M   20K   1004K  2%     /tmp
gvgs-fuse-  3.4G   3.3G    0      100%    /home/username/.gvfs
daemon

---

### Post by TeoBigusGeekus on 2011-02-15
```
/dev/sda2 3.4G 3.3G 0 100 /
```
Your root partition is indeed full.
Boot up with a live cd and use gparted to give it some more space.

PS:It's not bloated - 3.3g for root is a completely normal space usage for root.

---

### Post by foogo on 2011-02-15
Well I have an 8.5 inch dell, so I'll have to find a cd rom to connect to it. I was hoping i could just type something in, clear everything out, and then just be working with a clean slate. I literally have nothing on my computer, so i don't feel like i need to obtain any more space. 

What I don't understand is why it is full all the sudden or what that means. I If i haven't added any programs or any videos, why isn't my computer exactly the same as it was last month. What has changed that ll the sudden something is full? 
Maybe i should look up what root means...

---

### Post by TeoBigusGeekus on 2011-02-15
An alternative would be to install bleachbit (something like ccleaner)
```
sudo apt-get install bleachbit
```
and run it both as user
```
bleachbit
```
and root
```
gksu bleachbit
```

3.4 gbs for your whole linux system (apparently you don't have a separate home partition) is too little. A couple of updates and it's full.

---

### Post by foogo on 2011-02-15
~$ sudo apt-get install bleachbit
[sudo] p: 
Reading package lists... 0%
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package bleachbit

Hm so this is what happened...

By removing some of the programs that came with the computer though, i am at least able to sign into accounts again. I am almost content with this, but it seems that in a couple days my computer will get full again without me saving or downloading everything.

---

### Post by TeoBigusGeekus on 2011-02-15
Can't be...
Try from the Software Centre; search for bleachbit.
If you still can't find it, go to its [site]("http://bleachbit.sourceforge.net/download/linux") and install it from the deb file provided there.

---

### Post by foogo on 2011-02-15
Thanks. Have to run, but going to try that this evening.

---

### Post by mcduck on 2011-02-16
With only 3,4GB for Linux, you are definitely going to run out of space, again and again, no matter what you do.

The only thing that will solve the problem, instead of being just a temporary fix, is resizing your root partition to get more space.

You haven't mentioned your hard drive's size, but if you are really that short on space then you probably just should buy a larger drive, they are rather cheap. But new drive or not, 3,4GB just isn't going to do it. Even if you keep on cleaning the system all the time, and remove some programs, you'll still have hardly any space for any of your personal files.

---

### Post by foogo on 2011-02-16
Could you direct me to any information about resizing root partition?

And as a general question, is this a difficult job for a novice/ is it something you have to pay for?

I have  a work computer, and I am just surviving on the personal computer for another year or so when i am going to invest in something much nicer. Still, I would like it to be able to save a few more personal files and not come to a complete halt when i am watching videos.

---

