---
title: "Can I tar massive amounts of files togther?"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by ankspo71 on 2009-12-20
Hello,
I plan to download rocks-n-diamonds and all of the extra level sets for my wife to use on her windows XP, so that we have a more recent version for her. I did this a couple of times before, but what I did last time is I extracted everthing, then combined the folders together, and created a large 7zip archive to make installing easier. Otherwise it takes me a half hour to install it... extracting one folder after another and trying to figure if I installed each level set correctly. I used a 7zip archive because windows zip folders wasn't up for the job, as it failed to create the zip and made some undeleteable files on the hard drive. 

The finished archive isn't that large in size when compressed (probably between 100mb to 200mb), but it contains 66,000 tiny files with all the level sets she wanted... at least that's what it says now in her /program files/rnd/ directory. It could be more now since it was a couple of years ago.

So I was wondering, will I run into any trouble compressing that many files in a single tar archive? Is it possible to get any type of data corruption such as undeleteable files in Ubuntu? 
Thanks

---

### Post by Barriehie on 2009-12-20
I've used tar for my backup and it was genarating an archive of 400,000+ files and approaching 5+ gigs...  After having to restore from it one time I'ld say it works.

Barrie

---

### Post by ikt on 2009-12-20
There isn't an issue with the number of files, the issue is more with the size:

[http://answers.google.com/answers/threadview?id=25116](http://answers.google.com/answers/threadview?id=25116)

> The quick answer is: 2^63-1 for the archive, 68'719'476'735 (8^12-1)
bytes for each file, if your environment permits that.


So you should have zero issues using tar :)

---

### Post by iponeverything on 2009-12-20
The number of files can be an issue when restoring. You have to make sure that the file system that restoring to, has enough inodes.

---

### Post by ankspo71 on 2009-12-20
Hi,
Thanks for the help. I decided I am going to go for it using Ubuntu. I have a feeling I'll run into less problems using linux to do this task, especially after reading your replies. 

In windows... does the amount of inodes have to do with the size of the reserved space in MFT, or the amount of freespace? She has 23gb of freespace left.
Thanks.

---

### Post by iponeverything on 2009-12-20
> **ankspo71 said:**
> Hi,
Thanks for the help. I decided I am going to go for it using Ubuntu. I have a feeling I'll run into less problems using linux to do this task, especially after reading your replies. 

In windows... does the amount of inodes have to do with the size of the reserved space in MFT, or the amount of freespace? She has 23gb of freespace left.
Thanks.

I don't think that inodes are an issue an issue with windows based filesystems. When I read the original post, I didn't notice that windows was on the restore side of equation.

---

