---
title: "I gave /var a 1GB partition and i have 295MB left."
date: 2009-03-07
forum: New to Ubuntu
---

### Post by Arazu on 2009-03-07
Should I be concerned about this? Will it stay this size or do I need more space?

---

### Post by thtrgremlin on 2009-03-07
I would not recommend using multiple partitions for different parts of your system unless you really know what you are doing. Typically, breaking up partitions are for auditing or for security purposes. If you are not certain of /var's behavior or purpose, then I see you getting into quite an unnecessary mess.

Typical partitionaholics will have a different partition for /boot, /home. /boot does not need to be mounted after startup, so that keeps it protected. /home on its own partition means that you can do a clean install / upgrade and not worry about backing up your personal files more than normal.

Beyond that, it is most practical to use auditing tools to see how much space different things are taking up. limiting things through partitioning is not a good way to go. If you are splitting things, know what functionality you are gaining, like the above examples.

---

### Post by Arazu on 2009-03-07
Where were you when I installed this? =)

It was suggested that I create the following:
/
/home
/swp
/var
/tmp

So that's what I did. Where would you suggest I go from here?

---

### Post by thtrgremlin on 2009-03-07
well, there should be no '/swp', but just a 'swap' partition. If you just installed, and you are a beginner, I would recommend starting over and just following the guided setup that will set your root and swap. If you are looking forward to upgrading to 9.04 and don't want to backup everything in your home directory that you want to save, then create a /home partition. Personally, I don't do this because not all settings roll over from version to version, so I only save what I need.

While you could go the route of adjusting the size of the partitions and reconfigure everything's mount point, that is quite a bit of work for nothing other than a learning experience / masochism / headache. A clean install is MUCH faster, and a jot less to go wrong.

The idea with partitioning var and tmp away from the system is that they fill up over time. Ubuntu handles this well, not to mention that this was much more of an issue when hard drives were a LOT smaller. I do not know where you found your info, and while I commend you for the research, it must have been quite a few years old. It is too bad they did not explain what that kind of setup was for or how to utilize it.

I'll be around if you have more questions.

---

### Post by Arazu on 2009-03-07
Thanks for the advise but you haven't answered the OP. Should I be concerned? I'd just assume let the configuration stand until I upgrade. Then I will reconsider partitions.

---

### Post by cariboo on 2009-03-07
To gain some free space in /var, open a Applications-->Accessories-->Terminal and type:

```
sudo apt-get clean
```

The above command will clean out archived packages in /var/cache/apt/archives. Every time you update or install new programs the package files are stored in /var/cache/apt/archives, you usually don't need these packages after updates or installation, so it is safe to remove them.

Jim

---

### Post by kpatz on 2009-03-07
There's nothing wrong with running /var in its own partition, I did just that on one of my boxes.  I would have made it bigger than 1GB though.

If your root partition is big enough, just leave /var in there.  How big is your drive and all your partitions?

---

### Post by Kareeser on 2009-03-07
We're a bit unclear as to what you were asking. Did you mean to say that you had 295 MB of unpartitioned space left over?

If so, then assuming the rest of your partitions have enough space to work comfortably, you have nothing to worry about. Unpartitioned space is just extra space that is unused.

---

### Post by Arazu on 2009-03-07
> **cariboo907 said:**
> To gain some free space in /var, open a Applications-->Accessories-->Terminal and type:

```
sudo apt-get clean
```

The above command will clean out archived packages in /var/cache/apt/archives. Every time you update or install new programs the package files are stored in /var/cache/apt/archives, you usually don't need these packages after updates or installation, so it is safe to remove them.

Jim
Thank you! That is exactly what I needed to know.

Edit: I meant that I only have that amount left in /var. Sorry I missed your question. My partitions are:
/ 40
/home 250
swap 4
/tmp 1
/var 1

---

### Post by thtrgremlin on 2009-03-07
As far as the original post, yes, it can grow. The purpose of the partitioning is to STOP it from growing. As mentioned above, 'apt-get clean' can clear some space out, but as mentioned before, the only problem you can run into is the same any time the computer runs out of space. Anything that uses /var won't be able to do what it does. If you don't know what /var does or how programs use it, then it really isn't very useful. I could imagine necessity for hard limits, but that is really beyond the appropriate scope.

One example, apt-get stores all the packages it downloads into /var, so assuming the other 705MB are necessary, you are limited to 295MB updates at a time. That could be a big problem when doing a distribution upgrade.

Further, all your system logs are in /var/log. If you run out of space, the logs stop. This can be necessary with high traffic web servers where you NEED to know that some issue creating tons of logs isn't going to kill other necessary disk space. Logs are not more important than uptime. If you use 'dmesg', that is really the same as running 'cat /var/log/dmesg', so no space in /var, no dmesg.

So in my opinion, yes, 1G for /var is too little, and 295MB free is a problem. I am not in a situation where a limit on /var is going to solve more problems than it could make, and I believe that would also apply to most all desktop users, especially those that may be a bit new still to system audits and maintenance.

Hope that is useful.

---

### Post by Syed_Muhammad_Shahbaz on 2009-03-08
Well i only create 3 partitions viz., swap, root (/), and /home on my 70 GB disk space(10 GB for some data on fat32 partition) and it works just fine:

Swap about three times the size of my RAM;
Root (/) of about 15 GB; and 
/home.. rest of the space left which is normally 54 GB. 

I never gave any space to /tmp or /var.

---

### Post by thtrgremlin on 2009-03-10
whatever you don't give its own partition just goes in the same space as root. That should work well. Enjoy!

---

### Post by adult swim on 2009-03-10
look in /var/log for some huge log files.  sometimes they run away and you will have some logs that are well over 100mb, which should not be the case.

---

