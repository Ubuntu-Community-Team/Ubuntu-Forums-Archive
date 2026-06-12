---
title: "Memory usage/Memory hole? fix, or am I a nervous Nellie?"
date: 2011-03-30
forum: New to Ubuntu
---

### Post by Jedcurtis on 2011-03-30
Hello everyone!
Quick NOOB question here.  I've done some searching first, so I'll finally post a question at you all.
I've  noticed my RAM usage ends up being around 96 percent after being up and  running for a while. (i.e. Anywhere from say 24 to 72 hours)  Things  still seem to run OK and I haven't exactly been able to pinpoint the  'process', though after killing a couple of them I can bring the mem  usage down to about 50 percent.
Is there a way to do a cron job that reclaims the memory?  This is the physical Ram not the swap.
Also  from startup when I get into the System Monitor it shows that right  after boot-up I'm utilizing about 500 mb, or 5 percent of the physical  Ram.  (I have 8 Gb of ddr3)  I am no longer using MS's OS and boot only  Ubuntu.  It looks as if the Ram never stops increasing in usage.  (as in  a 'memory hole' so-to-speak?)
My system is screaming fast! I just  want to keep it that way!  Any help or info would be great.  It is NOT  an emergency!  The Ubuntu Forums have been a tremendous help to me  personally in the past and I appreciate ahead of time any help...

Thanks,
Jed

---

### Post by Dutch70 on 2011-03-30
Can you open system monitor, go to processes and see what's using all of your memory. That may help you find your memory leak.

---

### Post by Ocxic on 2011-03-30
Thats normal, Ubuntu will use any memory not in use by programs as cache to improve loading times. The system will automatically allocate memory to applications you open when needed. Any good OS will always try and use ALL of your memory to improve system performance and loading times for frequently used applications.

---

### Post by Dutch70 on 2011-03-30
> **Ocxic said:**
> Thats normal, Ubuntu will use any memory not in use by programs as cache to improve loading times. The system will automatically allocate memory to applications you open when needed. Any good OS will always try and use ALL of your memory to improve system performance and loading times for frequently used applications.

That may be true, but I have several OS's installed with half the RAM he has and I've never seen mine use over 40% of my physical RAM. 
It usually runs less than 25%

Jed, are you using 32-bit or 64-bit Ubuntu? 
To take advantage of all your RAM you would have to be using 64-bit.

---

### Post by lloyd_b on 2011-03-30
> **Jedcurtis said:**
> Hello everyone!
Quick NOOB question here.  I've done some searching first, so I'll finally post a question at you all.
I've  noticed my RAM usage ends up being around 96 percent after being up and  running for a while. (i.e. Anywhere from say 24 to 72 hours)  Things  still seem to run OK and I haven't exactly been able to pinpoint the  'process', though after killing a couple of them I can bring the mem  usage down to about 50 percent.
Is there a way to do a cron job that reclaims the memory?  This is the physical Ram not the swap.
Also  from startup when I get into the System Monitor it shows that right  after boot-up I'm utilizing about 500 mb, or 5 percent of the physical  Ram.  (I have 8 Gb of ddr3)  I am no longer using MS's OS and boot only  Ubuntu.  It looks as if the Ram never stops increasing in usage.  (as in  a 'memory hole' so-to-speak?)
My system is screaming fast! I just  want to keep it that way!  Any help or info would be great.  It is NOT  an emergency!  The Ubuntu Forums have been a tremendous help to me  personally in the past and I appreciate ahead of time any help...

Thanks,
Jed

Open a terminal window, and type "free -m" - what is that telling you?  Here's an example:```
lloyd@dell:~/stuff$ free -m
             total       used       free     shared    buffers     cached
Mem:          2004        721       1282          0        112        391
-/+ buffers/cache:        217       1786
Swap:          956          0        956
```
The thing to note above is that the "Mem:" line reports 721Mb used, but if you look at the "-/+ buffers/cache:" line, it's only actually using 217Mb of that for programs - the rest is just Linux trying to optimize things by using free RAM for buffers and caching.

If that shows that your system is actually using all that RAM (not just for buffers), then run the "top" command, and then hit "M" (must be uppercase) to sort by how much memory the various programs are actually using.  Does that show any single process with an unusual amount of memory?

Lloyd B.

---

### Post by matt_symes on 2011-03-30
Hi

> The thing to note above is that the "Mem:" line reports 721Mb used, but if you look at the "-/+ buffers/cache:" line, it's only actually using 217Mb of that for programs - the rest is just Linux trying to optimize things by using free RAM for buffers and caching.

Not much more to say really.

> My system is screaming fast!

And that is why your Linux is so blindingly fast :D

Great explanation lloyd_b.

Kind regards

---

### Post by Jedcurtis on 2011-03-30
Here is my 'free -m' from the terminal;

              total       used       free     shared    buffers     cached
Mem:          7994       4643       3351          0        292       1297
-/+ buffers/cache:       3053       4941
Swap:        19337          0      19337

Like I said in the first post it's not causing anything to slow down, It was more or less for my own curiosity.  In the past working with that "other" OS the more memory in use meant the guarantee of a crash or blue screen at best.  In my experience in the old days letting the OS do its thing was kind of alien in nature.  You could never trust it.  Not so with Linux eh?  I've been on an Ubuntu only system now for almost a year and I dont remember one crash yet!  And I'm still accidentaly learning stuff as well. Gotta love Linux!
Jed

---

### Post by lloyd_b on 2011-03-30
> **Jedcurtis said:**
> Here is my 'free -m' from the terminal;

              total       used       free     shared    buffers     cached
Mem:          7994       4643       3351          0        292       1297
-/+ buffers/cache:       3053       4941
Swap:        19337          0      19337

Like I said in the first post it's not causing anything to slow down, It was more or less for my own curiosity.  In the past working with that "other" OS the more memory in use meant the guarantee of a crash or blue screen at best.  In my experience in the old days letting the OS do its thing was kind of alien in nature.  You could never trust it.  Not so with Linux eh?  I've been on an Ubuntu only system now for almost a year and I dont remember one crash yet!  And I'm still accidentaly learning stuff as well. Gotta love Linux!
Jed

Based on those numbers, you were actually using 3Gb of memory for programs at the time that was run.  Which is higher than I've ever seen on typical desktop machines, but not too outrageous for some servers.  Without a better idea of what you're using that machine for it's kinda hard to tell what to expect.  Also - what kind of graphics does that machine have?  If it's one of those that uses system RAM instead of having its own on-board RAM, then it may account for that seemingly high memory usage.

Wait until it gets back up to that 90%+ point, and run "free -m" again to confirm that something is actually eating up your RAM.  Then use the "top" method I mentioned before to identify what it is that's using it.

Even if one of your programs *does* have a "memory leak", it won't crash Linux - at some point, it'll ask for more than Linux can deliver, and Linux will kill it.  So the worst case you'd see (except the case of a memory leak in the kernel or a device driver) would be one program that crashes, not the whole system.

Lloyd B.

---

### Post by Jedcurtis on 2011-04-01
Lloyd, (and all the rest that have replied here the past few days!) here is the results of my laptop being up and running for a couple of days...

```
root@jed-dv6:/# free -m
             total       used       free     shared    buffers     cached
Mem:          7994       7191        803          0        320       1546
-/+ buffers/cache:       5324       2670
Swap:        19337          0      19337
root@jed-dv6:/# uptime
 01:30:02 up 2 days,  2:27,  2 users,  load average: 0.01, 0.04, 0.05

```So right now, not fully utilizing "all" the ram, but around 65%...  Just wondering if this is normal for a laptop or should I be concerned?  Never runs hot, fans don't run excessively, all seems fine.
Below is a screen grab of my sys mon;

[IMG]http://www.jedsdesk.com/tmp/Screenshot.png[/IMG]

So there you have it.  Hope this all helps.  Like I've said, I just want to learn whats best practice and proceed accordingly.  This is by far the best OS I've ever had, and when you add in for free, well, It don't get no better than that.  This forum has been incredibly helpful, and I certainly appreciate it.  It adds tremendous value to a superb free product that I'm amazed hasn't finally put MS down.
Any advice on the ram issue (if it is an issue, of which I'm still a bit uncertain) is appreciated of course.  Almost 30 years in the computer industry and I can still be a NOOB again!  Life is grand...
Jed

BTW Lloyd it is an nvidia 1gb on board video ram.  Not part of the system ram.

---

### Post by lloyd_b on 2011-04-01
That does *not* look good.  You still have plenty of reserve (it's using close to 2Gb for buffers and such), but usage shouldn't have climbed from around 3Gb to 5Gb over that period of time.

Looking at that process list - those top two really jump out at me.  Nothing called an "applet" should be using up 2Gb of memory, especially "nm-applet", which is for Network Manager.  I have no clue what "indicator-applet" is, but that 490Mb looks extremely high for it.  Those two combined account for over half of memory used...

What Ubuntu version are you using?  You may be a victim of [this bug]("https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/684599").

Lloyd B.

---

### Post by Jedcurtis on 2011-04-03
Lloyd, I am indeed victimized!  By the time I got to this, the free m command in terminal was telling me my 8Gb of ram was fully engaged.  I immediately followed some of the advice in your link and voila, I'm thinking this is resolved!
Once again the Ubuntu Forums come to the rescue.  What a great OS eh?

Anyone else experiencing this "Memory Leak" should immediately check the launchpad site for '***Bug #684599***'.
Jed

---

### Post by Jedcurtis on 2011-04-05
This is after doing the downgrade on the nm-applet.

```
root@jed-dv6:/home/jed# free m
             total       used       free     shared    buffers     cached
Mem:       8186816    1413008    6773808          0      92556     506988
-/+ buffers/cache:     813464    7373352
Swap:     19802108          0   19802108
root@jed-dv6:/home/jed# uptime
 21:00:45 up 55 min,  2 users,  load average: 0.05, 0.09, 0.07
root@jed-dv6:/home/jed# free m
             total       used       free     shared    buffers     cached
Mem:       8186816    1443392    6743424          0      95968     514000
-/+ buffers/cache:     833424    7353392
Swap:     19802108          0   19802108
root@jed-dv6:/home/jed# uptime
 21:15:37 up  1:10,  2 users,  load average: 0.24, 0.20, 0.12
root@jed-dv6:/home/jed# free m
             total       used       free     shared    buffers     cached
Mem:       8186816    1546880    6639936          0      98580     572540
-/+ buffers/cache:     875760    7311056
Swap:     19802108          0   19802108
root@jed-dv6:/home/jed# free m
             total       used       free     shared    buffers     cached
Mem:       8186816    1546968    6639848          0      98580     572540
-/+ buffers/cache:     875848    7310968
Swap:     19802108          0   19802108
root@jed-dv6:/home/jed# free m
             total       used       free     shared    buffers     cached
Mem:       8186816    1546968    6639848          0      98580     572540
-/+ buffers/cache:     875848    7310968
Swap:     19802108          0   19802108
root@jed-dv6:/home/jed# uptime
 22:04:14 up  1:58,  2 users,  load average: 0.00, 0.01, 0.05
root@jed-dv6:/home/jed# free m
             total       used       free     shared    buffers     cached
Mem:       8186816    1555760    6631056          0     101220     573212
-/+ buffers/cache:     881328    7305488
Swap:     19802108          0   19802108
root@jed-dv6:/home/jed# uptime
 23:50:11 up  3:44,  2 users,  load average: 0.00, 0.03, 0.05
root@jed-dv6:/home/jed# free m
             total       used       free     shared    buffers     cached
Mem:       8186816    2006676    6180140          0     218324     787092
-/+ buffers/cache:    1001260    7185556
Swap:     19802108          0   19802108
root@jed-dv6:/home/jed# uptime
 18:49:55 up 1 day, 22:44,  2 users,  load average: 0.01, 0.04, 0.05

```

And there you have it.  After almost 48 hours, with no other alterations to anything else on the laptop, the memory leak is apparently plugged.  Anyone else want any info on how to easily fix this let me know.  Or just follow the link in one of Lloyd's posts.  Before the downgrade it was using almost 100% of Ram after only 24 hours.  I was using a version of the nm-applet that downloaded from the elementaryart ppa.  Went back to Ubuntu version and it looks like all is well so far.  Thanks for all the help.
Jed

---

### Post by Jedcurtis on 2011-04-06
Another shot of it from today.  I'll go ahead and mark this as resolved.  Sys Mon says I'm utilizing 1.5 Gb of ram as I type this.  This is a vast improvement over the last few days or weeks.  May still be a small issue with indicator-applet leaking some as well?  We'll see.  As for nm-applet it seems ok now.

```
root@jed-dv6:/home/jed# free m
             total       used       free     shared    buffers     cached
Mem:       8186816    2545320    5641496          0     303772    1016984
-/+ buffers/cache:    1224564    6962252
Swap:     19802108          0   19802108
root@jed-dv6:/home/jed# uptime
 22:34:20 up 3 days,  2:28,  2 users,  load average: 0.02, 0.07, 0.05

```

Thanks to all the kind posters who helped out.  It's nice to know I'll at least learn something while visiting here at the forums.  You guys are great!
Jed

---

