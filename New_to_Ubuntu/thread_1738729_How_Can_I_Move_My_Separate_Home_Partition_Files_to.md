---
title: "How Can I Move My Separate /Home Partition Files to a /Data Partition ?"
date: 2011-04-25
forum: New to Ubuntu
---

### Post by mikodo on 2011-04-25
Hi everyone,

I may be too tired to write this, much less follow any commands tonight, but I saw a similar thread and it got me interested. I have a Lucid only OS on my Desktop with a boot & (/) partition (Primary ext4) and an extended partition which holds a /home partition (ext4) and a swap partition in it.

I want to have my data files moved from the /home partition/ to a /media/data partition/ and place the system files from the /home partition/ back in the /home directory of Lucid under (/). I want to be able to dual/triple/quad boot with other distros, and be able to point to the /data partition/ for my stuff, to be able to use it with the distro I am booted into. Each will have to have their own config/system files in their respective /home directories, as they are different between distros.
 
So, I would have a new partition for Ubuntu Lucid that held the boot & (/) with the home directory, all in one partition, and an extended partition that holds the /media/data partition/and a few small 20 gig slave partitions for the other distro's in it (maybe 3). I suppose one swap partition would suffice for them all, don't you think? I know I would have to use something like a live CD to resize and make new partitons, that I know how to do with gparted. I don't know how to move the data from my /home partition to a new /media/data partition and move the old /home partition system and config files back to being in the /home directory under / in Lucid again.

How can I do this without reinstalling Lucid or a new release?

Below is my fdisk -l and df -h:

I am sorry, but I am truly very tired and now must go to bed soon.

Thanks. :)

```
mikodo@mikodo-desktop:~$ sudo fdisk -l

```[sudo] password for mikodo: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002efb7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19530752   83  Linux
/dev/sda2            2432       38914   293038081    5  Extended
/dev/sda5            2432       38119   286658067+  83  Linux
/dev/sda6           38184       38914     5859328   82  Linux swap / Solaris

 
```
mikodo@mikodo-desktop:~$ df -h
```Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              19G  4.1G   14G  24% /
none                  2.0G  304K  2.0G   1% /dev
none                  2.0G  112K  2.0G   1% /dev/shm
none                  2.0G  208K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
none                  2.0G     0  2.0G   0% /lib/init/rw
/dev/sda5             270G   48G  208G  19% /home
mikodo@mikodo-desktop:~$

---

### Post by Dutch70 on 2011-04-25
I'm not sure if I understood you correctly, but if you're going for a multiboot system, you're better off to keep /home in with /. 

Then just symlink your folders in the data prtn to your home folder. To symlink them, just create your folders in data, then middle click & drag them.

One swap prtn is all you need, and you don't even need a /boot prtn.

Have a look at my partitions.

---

### Post by mikodo on 2011-04-25
Thanks for the reply. :)

I was afraid I wasn't going to make a lot of sense, being so tired.

My /home partition is not in with (/), but on its' own partition. So can you tell me how to move it back in with the /root partition?

Thanks!

---

### Post by mikodo on 2011-04-25
Dutch70:

ll I see you have a separate /media/data partition also. That is what I want in my set up too!

Thanks.

See Screenshot of my Gparted window:

---

### Post by Dutch70 on 2011-04-25
I can't tell you how to move /home back to /. One thing you can do though, is shrink /home down to about 60GB *(52GB)*, create your new data prtn & move all of your files to it. Then reinstall Lucid & use that 60GB of free space for your new installs, or maybe that will give you some other ideas.

You can make it smaller by moving your data prtn to the left after you get your files put in it.

ps. I've heard that you can even save your settings by saving your .config folder, but I haven't tried it yet.

---

### Post by mikodo on 2011-04-25
Seems first, I will need to enlarge the /partition.

Then transfer the /home partition contents into the /home directory again.

Then mount a /media/data partition to hold all the data/stuff.

Then move the data out of the /home directory to the new /media/data partition.

Make an extended primary partition.

Then make new smaller slave partitions for more distros to reside and a one for swap


Now just how to do all of this???

---

### Post by mikodo on 2011-04-25
Well, I am off to bed ... 

I'm talking to myself! 

 :P

---

### Post by mikodo on 2011-04-25
> **Dutch70 said:**
> 
ps. I've heard that you can even save your settings by saving your .config folder, but I haven't tried it yet.

I've heard that too, don't know how to do it though.

Thanks for your thoughts.

:)

---

### Post by Dutch70 on 2011-04-25
I believe you can just copy/paste it into your data partition then put it back in your file system after you install. Of course you wouldn't want 2 of them. 

You don't have to move your files and /home around like you're talking about if you do it the way I suggested.

---

### Post by Elfy on 2011-04-25
There's a lot of writing in this thread ... 

Personally, I moved from a seperate /home a fair while ago. When I first did it I just copied those files and folders I wanted into the new non-seperate /home.

The media and data I'd collected in the /home got moved to it's new place then I reinstalled.

As long as it's backed up it's fairly straightforward - that said it is also probably one of those tasks you can make as complicated as you want to :)

If you have good backups of all you need to move about you might be in a position to repartition so you have a sensible base to work with in future.

I've sort of got a setup like
/
data
music
parrtition to install and delete trials from 
unallocated space

Symlinks will be your friend.

---

### Post by mikodo on 2011-04-25
Thanks for the responses,

I am trying to find a way to do this without doing the whole install thing again.

It's OK when you have your config and sytem files in place for the reinstall, but I don't because I'd be messing with my /home ...

Oh well ....

:confused:

---

### Post by Elfy on 2011-04-25
Right - so what all this really is about is adding /home to an install then. 

If your / is big enough you might be able to do this by copying your seperate home - removing the /home entry in fstab and then copying the old stuff into the /home in the /

I'd certainly wait for someone else to pitch in.

There are lots of threads here of people doing the move to seperate - you in effect want to do the opposite.

I'd hazard a guess that it'd be quicker to reinstall.

> It's OK when you have your config and sytem files in place for the reinstall, but if I don't because of messing with my /home ...What have you done to them?


Edit - [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
[http://forums.opensuse.org/english/get-technical-help-here/install-boot-login/438581-move-separate-home-partition-back.html](http://forums.opensuse.org/english/get-technical-help-here/install-boot-login/438581-move-separate-home-partition-back.html) 

Give you some idea. There will be pitfalls.

---

### Post by mikodo on 2011-04-25
Thanks FP:

I think you figured it out!

I. Repartition to enlarge /

2. Remove the /home entry in fstab from /

3. Copying the the separate /home partition into / and add a new fstab entry reflecting the new /home directory.

4. Delete the old /home partition.

5. Mount a /media/data partitions with perms and stuff.

6. Copy my data files from the /home directory to the /media/data partition.

7. Downsize the / partition to about 20 gigs.

8. Sym link /home directory to the/media/data partition.

9. Repartition my HDD to satisfaction for multiple distro booting.

10. Re-install Lucid, with boot / on the same partition.

11. Set up all configurations as before on desktop and apps.

12. install other distros in new partitions sym linking their /home config/system files with 
      their /media/data directories.

13. Check permissions for the new distros.

Thanks.

Do you know anyone who can tell me how to do this correctly?

 :P

---

### Post by Elfy on 2011-04-25
> 4. Delete the /home partition.Make sure that everything is working correctly first.
> 
Do you know anyone who can tell me how to do this correctly?Afraid not - you could try searching - it's likely you'll find what I did - there are hundreds of move /home to a seperate partition - not much the other way.

I suggest you have a good look at the wiki page I linked above - you're doing the opposite.

Have fun.


Edit - actually I'm a tad confused as to the order you intend on doing things in that last post of yours. 

Effectively if your are reinstalling at 10 then you don't need to do anything other than backup what is in the current /home - create the new data partition - install - move the old home data either to the data or to the new /home.

---

### Post by mikodo on 2011-04-25
This link you provided may be the CLI answer FP:

 [http://forums.opensuse.org/english/get-technical-help-here/install-boot-login/438581-move-separate-home-partition-back.html](http://forums.opensuse.org/english/get-technical-help-here/install-boot-login/438581-move-separate-home-partition-back.html)

I am too tired to study it. 

I be sure to read this backwards, as you suggest::P

- [https://help.ubuntu.com/community/Pa...ng/Home/Moving]("https://help.ubuntu.com/community/Partitioning/Home/Moving")

Thanks for all your help.

:)

---

### Post by Elfy on 2011-04-25
If you're too tired to read then I suggest you do no more today :)

---

