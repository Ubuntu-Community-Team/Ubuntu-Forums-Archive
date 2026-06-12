---
title: "No free space"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by Shenachie on 2009-07-17
I am brand new to Ubantu and Linux. (I can hear the sniggers already *got to love newbies eh?*)

Not so sure with that attitude already on the thread how this is going to be received.

I down loaded the OS from the main site and burnt it to CD. I installed it from said CD.

I tried to update the system and it says not enough space, 2 gig used of 2.3. Seems a lot of space for Linux to be using but that is what the Disc Usage Analyser reports.

I created a partition for Ubantu to go onto but got very confused by the installation process so have no no idea where it actually is. (Yeah I know laugh here) How can I firstly find out where it has taken up lodgings and 2ndly give it more space as there is  50g available.

Thanks

Shenachie

---

### Post by Tibuda on 2009-07-17
The [System Requirements]("https://help.ubuntu.com/community/Installation/SystemRequirements#Desktop%20installation") of the default desktop installtion says 4GB for bare minimum and 8GB recommended.

EDIT: There's a link for that page in [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by Elfy on 2009-07-17
Hi - I'ved moved your post to a new thread. 

Can you open a terminal from the Apps>Accessories menu. You will need to use your password for the first command - it will not be visible as you type - this is normal.

Please run these commands and post the outputs you get here - it makes it easier to read if you use code tags, to do that put [noparse]```
[/noparse] at the beginning of the paste and [noparse]
```[/noparse]

The commands I want you to run are

```
sudo fdisk -l
df -h
```

That is a lower case L not a 1.

Once you've done that - reboot with the livecd and we can look at getting you some more space.

---

### Post by raymondh on 2009-07-17
> **Shenachie said:**
> I am brand new to Ubantu and Linux. (I can hear the sniggers already *got to love newbies eh?*)

Not so sure with that attitude already on the thread how this is going to be received.

I down loaded the OS from the main site and burnt it to CD. I installed it from said CD.

I tried to update the system and it says not enough space, 2 gig used of 2.3. Seems a lot of space for Linux to be using but that is what the Disc Usage Analyser reports.

I created a partition for Ubantu to go onto but got very confused by the installation process so have no no idea where it actually is. (Yeah I know laugh here) How can I firstly find out where it has taken up lodgings and 2ndly give it more space as there is  50g available.

Thanks

Shenachie

Hi Shenachie,

Welcome.  

The 2.3GB install is a common mistake/problem.  But, the forum is here to help.

Here's what I suggest.  Create a new thread with an appropriate title and in your first post, be decriptive of what you installed (wubi or staright-up Ubuntu), your install procedures and the output of

```
df -h
```

To make that output, go to terminal (applications > accessories) and type/copy&paste the above command.  You will be asked for your password which when you type, will not be shown on the terminal.  With the output, just hightlight it and paste back in your thread.

Also, if you can (while you are at the terminal)

```
sudo fdisk -l
```  (small L, not 1 nor i)

We'll go from there.

EDIT : sorry ForestPixie .... I type so slow.

---

### Post by Shenachie on 2009-07-17
I do not understand this code matter , but have tried it as well as a straight copy and paste. 

```

pete@pete-laptop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06d8cc68

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1402    11261533+  12  Compaq diagnostics
/dev/sda2   *        1403       10446    72638464    6  FAT16
/dev/sda3           10446       19457    72387584    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06d8cc6a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19131   153669726    7  HPFS/NTFS
/dev/sdb2           19132       19457     2618595    5  Extended
/dev/sdb5           19132       19435     2441848+  83  Linux
/dev/sdb6           19436       19457      176683+  82  Linux swap / Solaris
pete@pete-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb5             2.3G  2.1G  148M  94% /
tmpfs                1006M     0 1006M   0% /lib/init/rw
varrun               1006M  104K 1006M   1% /var/run
varlock              1006M     0 1006M   0% /var/lock
udev                 1006M  176K 1006M   1% /dev
tmpfs                1006M  484K 1006M   1% /dev/shm
lrm                  1006M  2.4M 1004M   1% /lib/modules/2.6.28-11-generic/volatile
pete@pete-laptop:~$ 

```

---

### Post by drs305 on 2009-07-17
> **Shenachie said:**
> I do not understand this code matter , but have tried it as well as a straight copy and paste. 

```


pete@pete-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
**/dev/sdb5             2.3G  2.1G  148M  94% /**

```

What the code is telling you is that your system partition is 2.3GB and the installation is already taking up 2.1GB of space. You simply do not have a large enough partition allocated to / to run properly.

Your options are to take some space from Windows and give it to Ubuntu by manually repartitioning your hard drive or reinstalling and allowing Ubuntu to do it for you.

If you decide to repartition the drive yourself, you should backup your data, run defrag at least once, and then shrink your Windows partition (sdb1). You will then have to expand the "extended partition" (sdb2) to incorporate the free space, then expand your Ubuntu partition (sdb5). If you have the space give Ubuntu a *minimum* of 10GB.

Repartitioning Windows is probably best done from within Windows, but the application "gparted" when used from the LiveCD can also accomplish these tasks.

---

### Post by Shenachie on 2009-07-17
I think I can do that but how do I tell the distro (hey techie talk!) where to take up residence as this is where I fell foul already.

Pete

---

### Post by earthpigg on 2009-07-17
hi pete,

at this point, it looks like you will want to resize the ubuntu partition from 2.3 gigs to at least 8. that means ~6 gigs less for windows. make sure you have that much free space in windows!

please read all directions prior to doing anything, so you have a grasp of what we will be doing.

if the power goes out or there is an earthquake or something while resizing partitions, you could potentially lose all the data on your hard drive. get a good backup before we start resizing partitions. 

it also can't hurt to defrag windows first.

boot from the live cd.

applications -> accessories -> terminal

```
sudo gparted
```

right click on your ubuntu and windows partitions and select 'unmount'. if this is greyed out, that means it is already done, no big deal.

to resize, you will first need to shrink the windows partition.

right click -> resize. adjust the little slider thingie to free up as much space as you desire (6 gigs minimum, as we established earlier). make sure you move the slider from the correct side -- the graphical picture of the boxes should show you which side you need to move inward.

once that is done, resize the ubuntu partition to take up the newly-freed space.


make sure the dog/baby/terrorist/cookie-monster is locked up so as not to attack the power chord while this is going on, and hit apply.


this will take a while.


EDIT: the poster above me is correct, it is best to shrink the windows partition using a windows tool and not gparted, *especially* if it is windows _*vista*_.

---

### Post by Elfy on 2009-07-17
Ok - whle you might not understand the code thing - you have done it :)

What you will need to do is - resize the ntfs partition, resize the extended then resize the partition with the install on - this sounds much worse than it actually is.

Boot the livecd - in the Sys Admin menu - open Partition Editor. Once it has opened, in the top right corner you should see sda - change that from the drop down to sdb

Now - right click the swap partition and turn it off.

Now right click on the ntfs partition - resize - move the slider to the left so that there is enough space for the linux install - this is up to you, but I would be looking to have at least 10Gb in total once you have finished. 

It depends on how much free space there is on the ntfs drive.

Once that has finished resizing. Right click on the extended and resize it top take up the unallocated space. 

Once that has finished - you need to move the install partition all the way to the left then resize it to take up the unallocated space.

It is likely to take a long time to do, do not assume that gparted has hung.

If there is data on sdb1 - the NTFS partition you cannot afford to lose make sure you have suitable backups.

---

### Post by raymondh on 2009-07-17
> **Shenachie said:**
> I think I can do that but how do I tell the distro (hey techie talk!) where to take up residence as this is where I fell foul already.

Pete

Hi Pete.

Just want to be clear here.

Are you going to re-install..... or..... Are you planning to "shrink-windows-and-then-enlarge-existing-ubuntu-to-take-up-the-freed-space"?

EDIT : oops. did not see forestpixie's post.  I do type so slow.

---

### Post by Tibuda on 2009-07-17
Remember to backup your important files before resizing a partition. Just to be safe.

---

### Post by Shenachie on 2009-07-17
Problem here. No sdb5 I can see. 

In Gparted there are:

/dev/sda1  ntfs PQSERVICE 10.75 Gib Used 9.16 Gib Unused 1.58Gib

/dev/sda2 (warning triangle) nfts ACER 69.27 Gib Used .... Unused .... Flags boot

/dev/sda3 ntfs New Volume 69.03 Gib Used 3 Gib unused 66.03 gib

Looks to my innocent eye as if Ubantu is on sda3? If so there is lods of space. A further 66gig.

Pete

---

### Post by Elfy on 2009-07-17
You're looking at the wrong drive - change to sdb in the top right of the editor.

---

### Post by Shenachie on 2009-07-17
I am looking at shrinking windows. 

However having moved the slider to move it down to 108.16 gig there is now a grey area at  unallocated 38.39 gig which I cannot do anything with. the linux area will not drag into it. 

Hmm

Pete

---

### Post by Elfy on 2009-07-17
Assuming that you are using the livecd have you turned off the swap - you will not be able to do anything with the linux partitions while swap is being used.

---

### Post by Shenachie on 2009-07-17
I have no idea what swap is let alone know if it is running. Newbie here...... Live cd is running.

Pete

---

### Post by drs305 on 2009-07-17
> **Shenachie said:**
> I am looking at shrinking windows. 

However having moved the slider to move it down to 108.16 gig there is now a grey area at  unallocated 38.39 gig which I cannot do anything with. the linux area will not drag into it. 

Hmm

Pete

Your swap is sdb6. It should be listed as "linux-swap". Highlight it in the top section, then select Partition, Swapoff. If it is grayed out or says Swapon, it is unmounted. 

After you shink the Windows partition, you have to expand the extended partition next. You have to select the extended partition from the bottom section (still sdb2?). Drag the border to the left to touch Windows to expand it. Then you should be able to expand the ubuntu partition to the right (if you turned off swap as forestpixie asked you to).

To be able to expand Ubuntu into the extended partition, there can be no light blue line/border between the dark gray area and the Ubuntu partition. The light blue border is the boundary of the extended partition.

---

### Post by Shenachie on 2009-07-17
And how do I turn of swap? If that knowledge is essential then please pass it this way. :)

Pete

---

### Post by Elfy on 2009-07-17
> **Shenachie said:**
> I have no idea what swap is let alone know if it is running. Newbie here...... Live cd is running.

Pete
Heh - I understand that - that is why post9 gives you all the right clicks and choose options :)

Basically swap is similar to pagefile on win.

The most important thing to know while you are trying to resize your partitions is that if any have a lock symbol next to them you will not be able to do anything with that partition.

---

### Post by Shenachie on 2009-07-17
Never heard of pagefile either... sorry. and used win since 1998

Right the story now.

Ican shrink win to 99.36 gig.

I have unallocated 47.19 gig.

I can move /dev/sdb2 to the left and grow it from 2.5 gig to 49.69gig and I can do nothing else.

Early start in the morning so I am going to do nothing tonight and see if there is any more info here in the morning. thanks for your help.

Pete

---

### Post by Elfy on 2009-07-17
If you can move and grow sdb2 you should be able to move and grow sdb5 to fill the extended.

If not please post a screenshot - the PrtSc key should do that if not - Apps > Accessories > Take Screenshot

---

### Post by Shenachie on 2009-07-18
Ok. I ha[IMG]file:///tmp/moz-screenshot-1.jpg[/IMG]ve shrunk the Windows partition. I am unable to move the Linux one.[IMG]file:///tmp/moz-screenshot-2.jpg[/IMG]

I have attached the screen shot.

Pete







[IMG]file:///tmp/moz-screenshot.jpg[/IMG]

---

### Post by Elfy on 2009-07-18
You have to resize the extended partition (sdb2) first - then move sdb5 all the way to the left and _then_ resize it to take up all the unallocated space.

---

### Post by Shenachie on 2009-07-18
You are quite right, I did. And so I did. 

I can report success, and I have now d/l my updates and am a happy beekeeper now. :)

Many thanks to those who helped. Much appreciated. 

No doubt I will be back..LOL

Pete

---

