---
title: "128 inode vs. 256 inode"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by phreaknite on 2009-04-08
Sorry if this has been posted.  I did a search here and on google and the results are so unclear that I think it would just be easier if I posted...

I installed Ubuntu 8.1 last night and I wanted to set up my Vista to read from my Ext3 (ubuntu) drive.  However, one tool, ext2FSD, needs Vista in test mode to run properly (or turn off driver signing which just seems dangerous..).  I would like to be able to use my drive seamlessly on Vista, if possible...not have to pick and choose times when I can access my ext3 data...

With that in mind I decided to use ext2IFS.  However, ext2IFS requires me to reformat my Ubuntu drive and reformat it with an obsolete inode configuration - 256 vs. 128.  This would make accessing the drive much more seamless on Vista.

My main question is "Is this worth it?"  What exactly am I giving up with a smaller inode size?  It doesn't seem like the impact is worth mentioning, but i just want to be sure.

Thanks in advance!

---

### Post by cariboo on 2009-04-08
When I had Vista on my hard drive I used [Linux reader]("http://www.diskinternals.com/linux-reader/"), it worked quite well until I formatted my Linux partition as ext4. None of the utilities can read ext4 yet. I now have Vista in a vm as I was tired of dual booting. It works just as well or better.

Jim

---

