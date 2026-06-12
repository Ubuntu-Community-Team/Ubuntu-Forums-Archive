---
title: "4 Main Partitions"
date: 2011-07-08
forum: New to Ubuntu
---

### Post by Damarch on 2011-07-08
I've been considering trying out ubuntu for years and years now. A couple weeks ago I made a boot disk and just today I decided to use it. Unfortunately I'm getting a problem.

I'm trying to dual boot on an hp laptop that I use for school. I was told to first free some space in windows and then boot up the liveCD and use GParted to partition the drive and then install ubuntu. However, I'm prevented from partitions because it says, "You cannot have more than 4 main partitions on a disk", or something to that effect. It seems HP felt the need to create 4 partitions on the harddrive, one for use, another for backup, another for "HP_TOOLS"...whatever that is, and one more...think it says "system".

So here's my question: Is there a way around the 4 partition rule? If not do you guys think I can get rid of a partition?...like the hp tool one? Is there any other recourse? If not I'm tempted to simply do a clean install. Though that might take another couple weeks for me to decide on.

---

### Post by Blasphemist on 2011-07-08
There is a limit of 4 primary partitions on a disk. It seems you already have 4 and therefore GParted can't create an extended partition to put Ubuntu in. An extended partition is considered a primary partition itself. You can have all the logical partitions you want in the extended partition. So yes, you do need to remove a partition. And yes the HP Tools partition is a good one to remove. You can see this thread where HP tells someone to go ahead and there is a link to how to get them back should you somehow ever need it.
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

I also recommend using this site as reference for installing dual boot the first time. [http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

### Post by Damarch on 2011-07-08
Wow, that was super helpful. Thanks for the quick reply, most forums I post on for this sort of information are completely useless (don't get me started on the Asus forums).

---

### Post by Blasphemist on 2011-07-08
Thanks but I didn't notice this was your first post. I should have welcomed you! So welcome and I hope you do have nothing but good experiences here. This is a great community!

---

### Post by Damarch on 2011-07-08
Mind if I coopt the thread for another question?

I installed ubuntu (thank you Blasphemist) but I noticed before I was able to actually use it (after install, prior to first bootup) it took a long time doing who knows what while the screen was black. After a while I came to the screen and pressed a couple buttons and it booted.

Then it asked to update some things (I think it was less than a meg worth of stuff) and it's doing the same thing, taking forever with a black screen. Only this time it's been like 10-20 minutes (don't remember, I went to do other things) and it still is in a black screen and pressing buttons don't help.

So I looked up this problem and I noticed some people were saying they had a similar issue with their computer and it was the fault of the nvidia drivers and they just pressed control + alt + f1 to get into command line mode and then logged in that way. Well, my graphics card is amd but I thought I'd try it out anyway, I did install the driver after all...it didn't do anything.

Is there something wrong or am I just being impatient? Seems like something is wrong.

---

### Post by wildmanne39 on 2011-07-08
> **Damarch said:**
> Mind if I coopt the thread for another question?

I installed ubuntu (thank you Blasphemist) but I noticed before I was able to actually use it (after install, prior to first bootup) it took a long time doing who knows what while the screen was black. After a while I came to the screen and pressed a couple buttons and it booted.

Then it asked to update some things (I think it was less than a meg worth of stuff) and it's doing the same thing, taking forever with a black screen. Only this time it's been like 10-20 minutes (don't remember, I went to do other things) and it still is in a black screen and pressing buttons don't help.

So I looked up this problem and I noticed some people were saying they had a similar issue with their computer and it was the fault of the nvidia drivers and they just pressed control + alt + f1 to get into command line mode and then logged in that way. Well, my graphics card is amd but I thought I'd try it out anyway, I did install the driver after all...it didn't do anything.

Is there something wrong or am I just being impatient? Seems like something is wrong.
Hi, so are you stuck at a black screen or does it eventually boot? If it does not boot have a look at this link.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Damarch on 2011-07-09
Oh my, lots of reading and code. Thanks for the link, it looks like it will help but I'm too lazy tonight...I'll have to get to it tomorrow.

---

### Post by wildmanne39 on 2011-07-09
> **Damarch said:**
> Oh my, lots of reading and code. Thanks for the link, it looks like it will help but I'm too lazy tonight...I'll have to get to it tomorrow.
Hi, ok I will check on these thread tomorrow.

---

### Post by Blasphemist on 2011-07-09
This sticky thread is really long but it's the first 3 posts that you use to trouble shoot graphics issues. [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Try looking at those first 3 posts and using them. Let us know if you have any questions or continued issues. You could also post in that thread as it is active and the OP is very good with graphics issues. I'm not sure that is your issue though. If it isn't, try to give us as detailed a description as possible.

---

