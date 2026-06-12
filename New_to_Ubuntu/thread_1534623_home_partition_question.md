---
title: "/home partition question"
date: 2010-07-19
forum: New to Ubuntu
---

### Post by Joe Ker1086 on 2010-07-19
Getting ready to do some "spring cleaning" with operation systems. I am going to reinstall ubuntu and try a couple other distros as well... my concern is I have seen a lot of conflicting opinions on the /home partition. Some say "always make a /home partition so that you can share your files with multiple other distros" but I have also heard that a /home partion shared by multiple distros causes permissions conflicts as well as other problems. I actually encountered a problem b/c I had the same user name on 2 distros sharing a home partion.... Did I just do something wrong or should I just keep separate /home partitions and make a separate storage partion......any comments would be appriciated.

---

### Post by Zorgoth on 2010-07-19
Having a /home partition and the same usernames on different distros is probably not a good idea in my opinion.  However there is a different advantage to having the separate /home partition which is that if your system partition(s) is(are) corrupted your /home partition might come out just fine, preserving your data.

---

### Post by mike555 on 2010-07-19
Better to have a separate partition for backup IMHO , just backup your /home to it (so make it big enough)

---

### Post by Bucky Ball on 2010-07-19
+1. The other thing is of course that when you want to reinstall the OS, if you don't have a separate /home PARTITION you're /home DIRECTORY will be on the same partition as your OS, which means backing it up then plopping it back onto the new /home when you're done.

---

### Post by Joe Ker1086 on 2010-07-19
I have also heard that i could have a separate partition and have my /home directory link to that other partition, thus alieviating the permissions problems. I just dont know how to do that....has anyone else heard of doing that?

---

### Post by ubunterooster on 2010-07-19
You would not have a problem unless you had several distros all using the same partition for home

---

### Post by Joe Ker1086 on 2010-07-19
Two was enough to cause problems......

---

### Post by k3lt01 on 2010-07-19
There are many ways to do this. Personally, after having run two separate versions of Ubuntu (9.10 and 10.04 when it was being developed), I would run a separate /home for each OS. You are able to share files across them you just need to mount the relevant /home if you want to share files across.

Another way to do it is to keep your /home as part of the / partition but have a /data that each OS can see. Your settings etc stay with your / (/home being within /) but your personal file etc are placed in the separate /data partition.

---

### Post by Joe Ker1086 on 2010-07-19
I do understand the benefits of 2 home folders but with a laptop that has "semi-limited" storage I just wanted to make it as easy as possible....I suppose the /data partition is the best answer to what I want to accomplish...

---

### Post by k3lt01 on 2010-07-19
> **Joe Ker1086 said:**
> I do understand the benefits of 2 home folders but with a laptop that has "semi-limited" storage I just wanted to make it as easy as possible....I suppose the /data partition is the best answer to what I want to accomplish...Semi-limited? how big is your hard-drive?

---

### Post by Joe Ker1086 on 2010-07-19
250.....i know that seems like plenty but once i start partitioning for 2 systems (/boot, /, /home) I end up getting down to less space than I want....I use my laptop for work and my wife uses it too....I guess 2 /home wouldnt be the end of the world...just like everything being in one spot..

---

### Post by k3lt01 on 2010-07-19
> **Joe Ker1086 said:**
> 250.....i know that seems like plenty but once i start partitioning for 2 systems (/boot, /, /home) I end up getting down to less space than I want....I use my laptop for work and my wife uses it too....I guess 2 /home wouldnt be the end of the world...just like everything being in one spot..
Mine is 250 as well, check my signature for details of my laptop. I ran Ubuntu 9.10 and 10.04 development at the same time. Both had 10gb for their own /, a shared SWAP, 9.10 had 165gb for /home and 10.04 had 44gb for /home. Now 9.10 is gone and 10.04 is where 9.10 used to be. I am planning on putting 10.10 where 10.04 used to be.

---

### Post by Joe Ker1086 on 2010-07-28
I suppose my question has been answered.....just wish i could use one central home...must be a way to do it....marking resolved.

---

### Post by Bucky Ball on 2010-07-29
> **Joe Ker1086 said:**
> Getting ready to do some "spring cleaning" with operation systems. I am going to reinstall ubuntu and try a couple other distros as well... my concern is I have seen a lot of conflicting opinions on the /home partition. Some say "always make a /home partition so that you can share your files with multiple other distros" but I have also heard that a /home partion shared by multiple distros causes permissions conflicts as well as other problems. I actually encountered a problem b/c I had the same user name on 2 distros sharing a home partion.... Did I just do something wrong or should I just keep separate /home partitions and make a separate storage partion......any comments would be appriciated.

Why bother with /home then? You can name it whatever. My wife and I have a folder on the admin machine called 'Ourstuff'. In there we have a folder each and things pertaining to both of us are in the 'Ourstuff' folder. Easy. Ourstuff = household files + a folder each. /his /hers if you like.

ps: things all being in the one place is never good if a drive dies. ;)

---

### Post by Paqman on 2010-07-29
> **ubunterooster said:**
> You would not have a problem unless you had several distros all using the same partition for home

You can have as many distros as you like sharing one home partition. Just create a different account for each distro. Since each account gets it's own separate folder within /home there's no risk of conflicts.

---

### Post by ubunterooster on 2010-07-29
> **Paqman said:**
> You can have as many distros as you like sharing one home partition. Just create a different account for each distro. Since each account gets it's own separate folder within /home there's no risk of conflicts.
That's a brilliant Idea! thanks! :D

---

