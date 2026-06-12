---
title: "New Install - Will not boot!"
date: 2010-06-28
forum: New to Ubuntu
---

### Post by sunrex on 2010-06-28
[IMG]http://filesmelt.com/dl/imsad.JPG[/IMG]

Help! Please?

---

### Post by rykel on 2010-06-28
Mine is NOT a new install, but I just installed Mac4Lin with Cairo-Dock.

And now, my laptop cannot boot into any desktop environment. (just a black screen with a few white lines at the top of the screen)

I cannot even access other screens using Ctrl-F1 to F8.

However, I can turn off the PC using Alt-SysReq+REISUB.

Please help?

---

### Post by sunrex on 2010-06-28
Bumping

---

### Post by TeoBigusGeekus on 2010-06-28
Have you checked the cd before installing?

---

### Post by sunrex on 2010-06-28
Yes.

---

### Post by rykel on 2010-06-28
OK, for some reasons unknown to me, I can now boot in AND surf the internet.

My boot up "black screen" took place just before the login screen, and pressing ENTER turned up the login screen.

Indeed, I had a whole day of internet downtime after installing Mac4Lin... both wifi and ethernet refused to work! (not even in Windows XP)

Now it seems like things are working again, and I hope it was just a one-off problem!

---

### Post by sunrex on 2010-06-28
Come on, it's been over a hour now and no real response? I can't even boot into the default installation.

---

### Post by lkjoel on 2010-06-28
Ok, try typing this in
```
help
echo hello
exit
```
Don't worry about "help" and "echo hello"
For some reason, you just can't type "exit" without typing something else in.

---

### Post by sunrex on 2010-06-28
> **lkjoel said:**
> Ok, try typing this in
```
help
echo hello
exit
```
Don't worry about "help" and "echo hello"
For some reason, you just can't type "exit" without typing something else in.

Cant open /root/dev/console no such file kernel panic - not syncing: Attempted to kill init!.

That helped loads.

---

### Post by sunrex on 2010-06-28
Seven hours?

Bumping.

---

### Post by QIII on 2010-06-29
It looks to me like it is possible you have a partition problem with your  xfs file system.

Could you run 

```
sudo fdisk -l
```

from the LiveCD and post the results?

While I understand that you are frustrated, please be courteous and  remember that when you bump, you push others down in the queue.  Most  consider 24 hours to be sporting.
 
 Remember that we are all here on our own time, voluntarily, and we don't  see every post right away.  Sometimes the person who has exactly the  answer for you is in Bangalore, and may not even be awake when you  post.  He may want to sleep for a full eight hours, grab a cup of tea  and go to work, play with the kids when he gets home,  read the news and  finally, with his wife brow beating him for goofing off, he'll come  here to help.

---

### Post by anewguy on 2010-06-29
Not only is 24 hours considered sporting, it's actually a forum rule.

However.....I understand your frustrations - we've all been there in some way at 1 time or another.  As already mentioned, this is an all volunteer forum so there are a couple of things to keep in mind:

- it might take a while before someone sees your post

- it might take even longer to get a response.  Issues like you are having are not common, and therefore a lot of the people on this forum can't answer it.  You'll need to wait for someone with more experience to see the post and reply.

That being said, even I am guilty of bumping sometimes before 24 hours, and I know better!

I'm one of the users who don't know the answer, but I'll try searching the net for hints.  In the mean time, hang in there!

Dave ;)

---

### Post by lkjoel on 2010-07-03
What version of Ubuntu did you install?
Try installing 10.04, and we will guide you through the install process.
Does it have any important data inside?

---

### Post by rykel on 2010-07-03
I solved my own problem!

Simply purge 3rd party drive managers (eg. Storage Device Manager), comment out all the NTFS lines in /etc/fstab, do a "sudo blkid", reboot, plug in the devices and let Ubuntu auto-detect/auto-setup the UUID of the devices. I hope this solves your problems too!

The problem seems to be due to the fact that Lucid does NOT use /dev to identify devices anymore, and uses UUID instead.

That blank screen was the one which will ask the user to "press S to skip" a missing NTFS partition.

I am STILL getting the blank screen, but at least it does not hang at that screen anymore and will proceed to the Users' Login Screen!

---

### Post by lkjoel on 2010-07-03
What is the make/model of your machine, and what is it, a laptop or a desktop?

---

### Post by Oldieone56 on 2010-07-05
Each time I get stuck on the black screen I have to hold the power off button in until the pc powers off. Try this and re-boot. Then Ctrl-alt-f2 should get you to a command prompt.

---

