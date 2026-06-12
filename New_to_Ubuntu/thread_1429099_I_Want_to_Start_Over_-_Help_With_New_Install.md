---
title: "I Want to Start Over - Help With New Install"
date: 2010-03-13
forum: New to Ubuntu
---

### Post by Michael Kaiser on 2010-03-13
I'm frustrated. Not so frustrated that I will give up on Ubuntu; I'm too tenacious for that!

I would like to start over with a fresh install of 9.10. I'm dual booting with Windows XP (I have to have that to run certain programs).

Please keep in mind that I am a total knuckle-head when it comes to understanding Linux. I need things spelled out.

What should I do to unistall and start fresh?

According to GParted (I'm booted to the Live CD right now), I have a 20.03GB partition called /dev/sda3, File System = extended. When I expand that it shows /dev/sda5, File System = ext4. Also /dev/sda6, File System = linux-swap.

Do, I need to boot from my Windows recovery discs and reformat? Can I just delete the Ubuntu partition(s) in GParted and keep Grub? What should I do to start over?

Thanking you in advance, etc.

---

### Post by Michael Kaiser on 2010-03-13
Also, I went to copy my Home folder to an External HD (while in the LiveCD - I can't boot into Ubuntu after installing updates the other day - that's why I'm wanting to start fresh) and it wouldn't copy certain files due to permissions issues. Will I have a problem in restoring my setting in a new install because of this?

---

### Post by werecatomega on 2010-03-13
the easiest way is to install over XP and Ubuntu and then put XP back on.

---

### Post by Michael Kaiser on 2010-03-13
> **werecatomega said:**
> the easiest way is to install over XP and Ubuntu and then put XP back on.

Forgive me, but I find that a confusing recommendation.

---

### Post by OldMerovingian on 2010-03-13
> **Michael Kaiser said:**
> Forgive me, but I find that a confusing recommendation.

I wouldn't do that because then you will need to reconfigure grub and such. The easiest way would be to boot to the live disk, then format your /sda3 and create a partition for your / then one for /home. If you post the size of your disks, someone might be able to help you with a proper partion table

---

### Post by Michael Kaiser on 2010-03-13
> **OldMerovingian said:**
> I wouldn't do that because then you will need to reconfigure grub and such. The easiest way would be to boot to the live disk, then format your /sda3 and create a partition for your / then one for /home. If you post the size of your disks, someone might be able to help you with a proper partion table

Thank you for your reply!

Do you think the advice in [this tutorial]("http://sites.google.com/site/easylinuxtipsproject/reinstallation") is sound? It seems pretty simple. If so, how would I restore my programs from the copy of the Home folder I made, just install it over the Home folder in the new installation?

---

### Post by The Real Dave on 2010-03-13
Can you please post the output of 

```
df -h
```

That'll let use see what's mounted where :)

Good news is that it looks like you have  a seperate /home partition, meaning that you can easily re-install the OS without wiping your data and most of your settings.

You'll need to set the partitions manually, but we can help with that :) You might also need an XP disk to re-install XP's bootloader :)

---

### Post by Michael Kaiser on 2010-03-13
> **The Real Dave said:**
> Can you please post the output of 

```
df -h
```

Thanks, Dave!

Here you go:

```
Filesystem            Size  Used Avail Use% Mounted on
aufs                  498M   60M  438M  12% /
udev                  498M  364K  497M   1% /dev
/dev/sr0              690M  690M     0 100% /cdrom
/dev/loop0            668M  668M     0 100% /rofs
none                  498M  100K  498M   1% /dev/shm
tmpfs                 498M   16K  498M   1% /tmp
none                  498M   92K  498M   1% /var/run
none                  498M     0  498M   0% /var/lock
none                  498M     0  498M   0% /lib/init/rw

```

---

### Post by The Real Dave on 2010-03-13
Oh, your running the Live CD at the moment? I should have guessed :) 

In that case, could you open up Gparted (System>Admin>GParted), and then take a screenshot by pressing the PrintScreen button on your keyboard? Then uploaded it to somewhere like [Omploader]("http://www.omploader.org/"). Sorry about the hassle, I just want to be definate about your partition layout :)

---

### Post by oldfred on 2010-03-13
If you remove the linux partitions grub will not boot from the hard drive as the rest of its boot loader is in the Ubuntu partition. If you are going to immediately reinstall that will not a problem. Or you can reinstall the windows boot loader if you want. If your partitions are set up the way you want you can just use manual reinstall and select the same partitions for root & swap. If home is separate you do NOT reformat that partition. Your /home saves your setting but not all the additional programs you may have installed.

What is the issue preventing you from booting? We solve many boot issues. Sometimes we will take days or weeks solving an issue when reinstalling can take less than an hour.

---

### Post by Michael Kaiser on 2010-03-13
> **The Real Dave said:**
> Oh, your running the Live CD at the moment? I should have guessed :) 

In that case, could you open up Gparted (System>Admin>GParted), and then take a screenshot

Here she is:

[IMG]http://i6.photobucket.com/albums/y244/pfinkrat/Anything%20Goes/Screenshot-1.png[/IMG]

---

### Post by Michael Kaiser on 2010-03-13
> **oldfred said:**
> 

What is the issue preventing you from booting? We solve many boot issues. Sometimes we will take days or weeks solving an issue when reinstalling can take less than an hour.

After running the new updates the other day (including Kernel 2.6.31-20) Ubuntu will not boot. It won't boot from any previous Kernel, either. After the splash screen I just get the loading/working icon, and it goes no further. I started a couple threads about it, actually. I wasn't getting anywhere, so I decided maybe starting over would do the trick.

---

### Post by The Real Dave on 2010-03-13
Ok, you havn't got a seperate partition, so were going to have to backup your data, and do a clean re-install :) 

Go to Places and click "20Gb Partition" or similar. That will mount your Ubuntu partition, and should open it up in Nautilus. At this stage, attach and open your external drive too :)

You mentioned earlier that not all your files could be copied, due to permission errors, and this is to be expected. To get around this, start a Nautilus window as root (super-user) by hitting Alt+F2 and running

> gksudo nautilus

Give it your password, and it'll open another window. In the location bar type /media and hit enter. Then navigate into whichever folder holds your Ubuntu install. Then click home, followed by the folder with the same name as your username. 

Press Ctrl+H to un-hide hidden folders, and then copy everything to your external drive for safe keeping :)

---

### Post by Michael Kaiser on 2010-03-13
> **The Real Dave said:**
> 

Give it your password

Its not asking for my password. :(

---

### Post by ajgreeny on 2010-03-13
I am a little concerned, to see from your gparted screenshot that the winxp partition sda2, appears to be unused, containing nothing at all.  Have you removed everything from windows, including the OS itself?

Before you do anything, I think you need to be sure about what has happened to that XP install.

PS:
**gksudo nautilus** in the live CD will not ask for a password, as there is no user password set.  It will still work with root permissions, so just go ahead with that way of copying to the external disk.

---

### Post by Michael Kaiser on 2010-03-13
> **ajgreeny said:**
> I am a little concerned, to see from your gparted screenshot that the winxp partition sda2, appears to be unused, containing nothing at all.  Have you removed everything from windows, including the OS itself?

Before you do anything, I think you need to be sure about what has happened to that XP install.

No. XP is working just fine.

---

### Post by The Real Dave on 2010-03-13
> **ajgreeny said:**
> I am a little concerned, to see from your gparted screenshot that the winxp partition sda2, appears to be unused, containing nothing at all.  Have you removed everything from windows, including the OS itself?

Before you do anything, I think you need to be sure about what has happened to that XP install.

Notice the little warning sign next to the XP partition. That's there because GParted can't read the partition correctly, because the ntfs-3g package isn't installed on the LiveCD. The XP install is there, GParted just can't modify it.

> **Michael Kaiser said:**
> Its not asking for my password. :(

That's ok, seeing as it's the LiveCD. Did the window open? Is it letting you copy your files over?

---

### Post by Michael Kaiser on 2010-03-13
> **The Real Dave said:**
> Did the window open? Is it letting you copy your files over?

Yes. I copied everything that I could. Things like .adobe ect. wouldn't copy, but the main things did. :)

---

### Post by The Real Dave on 2010-03-13
> **Michael Kaiser said:**
> Yes. I copied everything that I could. Things like .adobe ect. wouldn't copy, but the main things did. :)

They still wouldn't copy? Well, most of those hidden folders are just your programs config files. Most things should have copied over though :) 

Next up, the re-install. You'll want to go back into Gparted, and right click on any mounted partition, including your external drive, and click unmount. After that, remove your external drive, close GParted, and run the Install shortcut on the Desktop :)

---

### Post by Michael Kaiser on 2010-03-13
> **The Real Dave said:**
>  and run the Install shortcut on the Desktop :)

Just run the Install? Will that delete the original and get me all set-up the way I want to be? :)

---

### Post by The Real Dave on 2010-03-13
> **Michael Kaiser said:**
> Just run the Install? Will that delete the original and get me all set-up the way I want to be? :)

Were gonna make it that way :) Go through the Install as normal until you get to the Partition Editor. Then, click the last option, Manual Partitioning. 

You then need to go down to /dev/sda5 and delete that partition. In the Un-partitioned space left behind, create a new partition, around 8Gb (8000Mb), by selecting the space and clicking Add. Let this as ext4, and it's mount point as "/". You'll then have ~12Gb left, in which you create another partition, again ext4, with the mount point as "/home". 


After that, click Forward, and agree to writing the changes :) Make sure you double check that everything is as it should be, once you write the changes, it's nigh on impossible to go back :( After all that, continue the install as normal :)

Having your /home dir separate makes it much easier to re-install your OS, without having to backup your data. It's also reassuring that if you screw up Ubuntu, your data is probably still safe :)

---

### Post by Michael Kaiser on 2010-03-13
Ok, then. Here goes nothin'!

---

### Post by The Real Dave on 2010-03-13
> **Michael Kaiser said:**
> Ok, then. Here goes nothin'!

If there's anything your not sure about, or think looks wrong, stop and ask :) We don't want to format your whole harddrive by mistake lol ;)

---

### Post by Michael Kaiser on 2010-03-13
Well, the install is hung up at 46%. That's just my luck!

---

### Post by The Real Dave on 2010-03-13
> **Michael Kaiser said:**
> Well, the install is hung up at 46%. That's just my luck!

Have you used the disk before? Is it one from Ship-IT or did you burn an ISO? :)

---

### Post by Michael Kaiser on 2010-03-13
> **The Real Dave said:**
> Have you used the disk before? Is it one from Ship-IT or did you burn an ISO? :)

Yeah, it's a burned ISO. I've installed a couple time from it.

---

### Post by The Real Dave on 2010-03-13
> **Michael Kaiser said:**
> Yeah, it's a burned ISO. I've installed a couple time from it.

Hmmm. Try giving the installer a while, to see if it continues. 

If it doesn't, restart the computer, and instead of booting into the LiveCD, select the "Check Disk Integrity" option. If it returns an error, re-burn the disk, at a slower rate. Then check the disk again. 

If it again returns an error, check the MD5sum of the ISO against the one supplied on the download site for that ISO. Your burning software in Windows should be able to do this, or you can probably find some free little program to do it. 

If the sums are any bit different, you'll have to re-download the ISO. Consider downloading it with a torrent, that'll give a lower chance of getting a corrupt ISO.

Of course, if the disk check comes back ok, simply retry the install process again. It's quite possible that the partitions you created may be listed as damaged, but don't worry about that. You can just delete them, and begin again. Make sure that when you set up the partitions, that the mount points are correct, and that both partitions are marked to be formatted. If it stalls again, check the CPU and RAM usage in System>Admin>System Monitor

And if *all* that fails, it possible that it wasn't the update that spoiled your Ubuntu install, or some hardware issue like a bad sector or something. But as to go about fixing that, I simply don't know :( 

Best of Luck mate, I'll be heading to bed in a while. I hope this works out ok for you.

---

### Post by Michael Kaiser on 2010-03-13
Woo Hoo! I'm back with a brand new, fresh for today installation of Ubuntu 9.10!!

Dave, you are THE MAN!

Now, how do I get my backed-up Home Folder into the new install?

---

### Post by oldfred on 2010-03-13
You should be able to just copy them back, but it may depend on the file system you have used to back them up onto. I just copied some files using Samba and lost ownership so I had to go back and reset it.

This talks about moving /home. You only need last several commands - the cp command and possibly the chown and chmod commands to make you owner and give you rights. If you do not want to copy everything you can just copy whatever you want just remember that most system setting are in the hidden (.) folders and files.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by The Real Dave on 2010-03-14
> **Michael Kaiser said:**
> Woo Hoo! I'm back with a brand new, fresh for today installation of Ubuntu 9.10!!

Dave, you are THE MAN!

Now, how do I get my backed-up Home Folder into the new install?

You copy them back the same way you copied them over, mount your external drive and the /home dir from a LiveCD and run

```
gksudo nautilus
```

After that, just navigate to where you have them like before and copy and paste :)

The one part that could catch you are the permissions, but we'll face that if we get to it :)

---

### Post by unknowndude on 2010-03-14
what I do is using gparted give ubuntu full space.Delete windows.And then reinstall windows and  follow this thread.

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

---

### Post by yeats on 2010-03-14
> Now, how do I get my backed-up Home Folder into the new install?

Realizing that you've probably done this already, but it's probably better to move the specific files/folders you need from the old /home to the new /home, rather than trying to drop the entire old /home into place in the new install (hoping that makes sense :-) ).

All of your GNOME, Firefox, etc. configurations are in the old /home and may not necessarily play well with the new install (especially since it sounds like some files didn't want to copy over cleanly).  Just FYI :-), speaking from personal experience.

---

### Post by rafita on 2010-03-15
> **Michael Kaiser said:**
> Well, the install is hung up at 46%. That's just my luck!

I'm glad it eventually worked out for you, but could you please confirm the installation actually continued after 46%?

I'm about to do the same in one of my computers, and so it will help me to know what to expect. ;)

---

### Post by Michael Kaiser on 2010-03-15
> **rafita said:**
> I'm glad it eventually worked out for you, but could you please confirm the installation actually continued after 46%?

I'm about to do the same in one of my computers, and so it will help me to know what to expect. ;)

I did a hard shut-down... twice. The 3rd time it completed the install. I'm suspecting the problem is with my old HP Pavilion; you'll probably have no problem. :)

---

