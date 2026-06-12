---
title: "Need help moving home folder to it's own partition"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by chriscross93 on 2009-04-21
I have been trying to move my /home to it's own partition.  I have tried multiple tutorials, but they all end up not working.  Here is what I have done...

Copied entire home folder to directory on another drive, original permissions intact.

(tried) to set new /home to /dev/sdb5 in /etc/fstab 

Please, any pointers would be GREATLY appreciated, I've run out of space of my drive.:(  This is why I need to move /home to it's own!

---

### Post by RetchingRabbit on 2009-04-21
Post the contents of your fstab, and perhaps we can figure it out.

---

### Post by MDSmith2 on 2009-04-21
I have done this by:
1. Creating another partition for my home (keeping a backup!!!).
2. Copied all the data to that partition.
3. Changed my fstab entry from ```
/dev/sda1       /home           jfs      defaults    0    0
to
/dev/sdb1       /home           jfs      defaults    0    0
```(yes, I did put my home directory on another hard drive)
4. Testing my recovery CD in case it didn't work
5. Rebooted and preyed it would work :)

That did it for me. 
Post us your fstab file and lets see what we see.

---

### Post by Gen2ly on 2009-04-22
There's this guide too that might be able tohelp:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by expatCM on 2009-04-22
I have seen a number of similar threads on this subject in the last few days, it is certainly topical.

What I find confusing about the process is in fstab.   I got the idea that the syntax was generally 
UUID / volume, mounted to, options.   

Now where I miss this is that if I look for the original mount point of /home I cannot see it. Everything is mounted to /   

What I had thought the way to proceed was 
/home, UUID / mounted to, options 
but it does not seem to work this way....

No idea why .....  hope this thread will cover that :)

---

### Post by Kobalt on 2009-04-22
If you don't specify a separate partition for /home during the install process, or change it later on, then you don't get a mount point for /home out of an usual install, your /home is contained in /

The syntax for the fstab file is as follows : 
> [Device] [Mount Point] [File System Type] [Options] [Dump] [Pass]

If you need more info regarding fstab : [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

@chriscross93 : please post your fstab 
```
$ cat /etc/fstab
```

---

### Post by expatCM on 2009-04-22
Kobalt ... thank you for your post.  So basically what you are telling me is to pay better attention when the partitioning option is presented during the install process and at that time specify the path for /home?  I cannot remember what it says on screen but I guess this has to be the manual partition option.

Good to discover at this time since I will be making a fresh install in a few days time ..... and I can see value in separating out /home.

---

### Post by philinux on 2009-04-22
> **expatCM said:**
> Kobalt ... thank you for your post.  So basically what you are telling me is to pay better attention when the partitioning option is presented during the install process and at that time specify the path for /home?  I cannot remember what it says on screen but I guess this has to be the manual partition option.

Good to discover at this time since I will be making a fresh install in a few days time ..... and I can see value in separating out /home.

Yes choose manual partition. It's pretty straightforward. 

you need

/
/swap
/home

I've set mine to 12 gig for root. 2 gig for swap and the rest is home.

---

### Post by XubuRoxMySox on 2009-04-22
Most of us are doing a fresh install in a few days anyway. Make your partition then, but be sure and give it the very same name and password you had before, so you can transfer all the stuff from your backup copy back to your new Jaunty installation. You may have to re-install *programs*, but all your documents and pictures and the *settings* for you favorite programs (e-mail settings, bookmarks, that kinda stuff) won't be lost.

Cheers!
-Robin

---

