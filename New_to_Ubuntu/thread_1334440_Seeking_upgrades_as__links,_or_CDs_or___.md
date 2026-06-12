---
title: "Seeking upgrades as:  links, or CDs or___"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by flywelder on 2009-11-22
I need to upgrade my Ubuntu  from 7.4 to newer versions.  yes, i missed the cutoff date for support,  because I am a new user of Ubuntu. SO I am hoping to avoid the hassles associated with ( as I have personally experienced) installing operating systems.

I am hoping to avoid having to back up files, as i do not have a back up program or additional hard drive, upon which to do back ups with.  So I am in hope to find copies of older versions of Ubuntu  that can be mailed to me or emailed, or etc.  so I can install them and move on up 'with in days' to a still supported version  which from that i can get the very latest updates from Ubuntu .com  ;)

I hope I explained myself well, and i hope this request falls on compassionate  ears.
 Thank you.
11-22-09

---

### Post by overdrank on 2009-11-22
Hi, this link should help [EOLUpgrades]("https://help.ubuntu.com/community/EOLUpgrades")

---

### Post by ibizatunes on 2009-11-22
Why dont you download 9.10, and do a clean install, it will save you time in the long run, upgrading like that is a recipe for trouble
 and ext4 filesystem will make your system quicker
And if you do a clean install create / and /home on separate partition you wont need to back up your data next new version just install over the / partition

---

### Post by flywelder on 2009-11-24
ibizatunes, your reply  has my curiosity stirred, when you wrote: And if you do a clean install create / and /home on separate partition you wont need to back up your data next new version just install over the / partition

ibizatunes......  do I follow you correctly when I say, "are you telling me I can split my current hard drive into two? and then move all the items I want to save to one half,  and then when I install the latest ubuntu,  it will only erase / format the one half of my hard drive leaving the half with the items i saved, entirely alone?...and ready to easily  move back to the other half, if I wanted? .... if this is true, I'll try it,!@!! ....... but first ibizatunes, tell me how do I split my hard drive?

 Thanks a bunch!!

---

### Post by darkstaar on 2009-11-24
> **flywelder said:**
> ...I can split my current hard drive into two? and then move all the items I want to save to one half,  and then when I install the latest ubuntu,  it will only erase / format the one half of my hard drive leaving the half with the items i saved, entirely alone?...and ready to easily  move back to the other half, if I wanted?

Yes, exactly. Not that anyone here would recommend not backing up first (just to be safe) but it can be done successfully just as ibizatunes has described.

> **flywelder said:**
> ... but first ibizatunes, tell me how do I split my hard drive?

Great info on that at [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Cheesemill on 2009-11-24
+1 for the clean install.

You can only upgrade 1 release at a time so to get to 9.10 you would have to upgrade 5 times.
7.04-7.10 then 7.10-8.04 then 8.04-8.10 etc...... Making it 5x more likely that you will have serious problems (especially with the amount of problems people have had just from 9.04-9.10).

---

### Post by flywelder on 2009-11-29
great information every one, thank you all!  I  made some attempts over the holiday, but  I have determined I need some additional instructions form all of you.
 Instructions needed for: Backing up  in Ubuntu......... i think i  successfully split my hard drive into two half's, but not 100% sure, now, I want to back up everything, and copy it to the other side of my hard drive.   
Plus, i w do not know the steps  to move the saved items and programs back over, once I have successfully upgraded to a newer version of Ubuntu.

I read and printed the info at the link provided for doing the backing up.....I think I should use rsync........I need instructions on performing this backing up and copying ....stay with me... and I do not know where  the so called 'terminal'  is located?     or how to access it,.... and once I know, .....I still do not know where to type the instructions such as:
rsync -av  /path/to/source/directory /path/to/target/directory



....Note:  keep in mind I am using Ubuntu 7.04

And wanting to upgrade to a newer version of Ubuntu
Does nay one  remember how one would do this  with Ubuntu 7.04??...I hope so!

 thanks all! :)
11-29-09

---

### Post by darkstaar on 2009-11-30
If you simply want to simply backup your files to "the other side" of your drive and you have the space to do this, you only need to copy them over with your file manager (Nautilus).

And, again, you should do a fresh install of the version you wish to use rather than use the upgrade path.

---

### Post by flywelder on 2009-12-04
Forgive my delay  in responding, for I have been sick.

My hard drive is partitioned...I hope.
I have tried to copy files over and I am not able  to , for when i do, a window appears that says:
error accord while copying to media/disk-1 you do not have permissions to write to this folder

I should have permissions. i don't understand why it says i do not when i own this computer, and it is in my house right now.????
I have included some screen shots that might help.

I tried to copy files to the new partition using  the terminal and typing rsync..as you can see in the screen shots I have included....... yet this failed and I do not know why?..............So you know, I named my partitions /media/disk-1 and media/disk-2...............I was only able to  include one screen shot here.i don't know why?  so i have pasted the results of my  attempts to use rsync below:

flywelder@flywelder-desktop:~$ rsync - av /path/to/source/directory /path/to/target/directory
rsync: -: unknown option
rsync error: syntax or usage error (code 1) at main.c(1318) [client=2.6.9]
flywelder@flywelder-desktop:~$ rsync-av/home/flywelder/media/disk-1
bash: rsync-av/home/flywelder/media/disk-1: No such file or directory
flywelder@flywelder-desktop:~$ rsync-av/homefolder/media/disk-1
bash: rsync-av/homefolder/media/disk-1: No such file or directory
flywelder@flywelder-desktop:~$ rsync-av/home/flywelder/media/disk-1
bash: rsync-av/home/flywelder/media/disk-1: No such file or directory
flywelder@flywelder-desktop:~$ rsync-av/home/media/disk-1
bash: rsync-av/home/media/disk-1: No such file or directory
flywelder@flywelder-desktop:~$

---

### Post by flywelder on 2009-12-04
Here is a screen print.i hope your able to see it.....
 this is showing my partitions...........apparently that wish will not work...for it seems the image is too large...crazy!!  ...and worse , i do not know how to make it smaller!!!  rrrrrrrrrrrrggggggggg!  help please.
 Thanking  you all in advance.
 flywelder
12-04-09

---

### Post by sandyd on 2009-12-04
run
```

gksudo nautilus

```
that window that opens will now have ultimate permissions (root) and will be able to write to anywhere.

---

### Post by flywelder on 2009-12-06
Thank you Carlee!

I am still not doing something correct.  I would like to propose a different approach, seeing how I have been attempting this upgrade for 4 weeks now.

 My proposal, is to ask  if any of you  who have helped wouldn't mind talking to me on the phone  so that I can better and quicker relate what I see on my screen. I will happily pay for the call or calls,  All I need is a number and a time to call. I am on the east coast of the USA............otherwise I think this could drag on for weeks, before I understand what I am doing  and what I should be doing. Email me, send me a private message, anything.
 Thanks so much every one. :)

---

### Post by flywelder on 2009-12-08
...mmmmmm no replies yet???? I will guess / assume that means no one wants to,  that is saddening.   SO I'll continue fumble along,.
 I need to ask this:
 when you replied with : run 
code 
gksudo nautilus


Please explain  to me this:   where do i type this?

Secondly:   where can I print   a list of Ubuntu terminology with explanations and their locations with in Ububtu?

Flywelder
 a very green beginner with Ubuntu
12-08-09

---

