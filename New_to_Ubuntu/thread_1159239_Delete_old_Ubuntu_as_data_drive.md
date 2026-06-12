---
title: "Delete old Ubuntu as data drive"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by MaxVK on 2009-05-14
Hi there. Iv just installed Jaunty (with some help from Didius Falco) and I am left with two hard disks:

sda:
sda1: Jaunty (root)
sda5: Jaunty (Home)
sda6: Jaunty (Swap)

sdb:
sdb1: Old Gutsy (Root)
sdb2: NTFS Storage drive
sdb3: Old Gutsy (Home)

The old Gutsy install no longer works because the swap partition that it was using is now gone. I have no real need to have it running, however I would like the space back.

I do not want to lose the data that is on sdb3 and sdb3 (and I don't have the space right now to back it all up), but I would like to free up sdb1, which is the old root drive.

Is simply formatting sdb1 with the partition editor the best thing to do? All I want it for is a storage area.

Also, sdb1, which is the old Gutsy install is still showing in the GRUB menu. Will this be a problem if I format the drive? (Its not that I'm going to try and boot from it)

cheers

Max

---

### Post by sir_nasty on 2009-05-14
if you're now using grub on the new drive with the new install then just formatting sdb1 should free up the space just fine.  Just use the partion manager in Jaunty is what I would do

---

### Post by whoop on 2009-05-14
You can use gparted to remove the partitions. You could even resize the existing ntfs partition to take up the entire drive, or create new partitions.
The entry in grub should be gone as soon as grub gets updated.
```

sudo update-grub

```

---

### Post by MaxVK on 2009-05-15
Thanks guys - I thought it would be quite simple, although I didn't know that 'update-grub' would work like that.

Cheers

Max

---

### Post by MaxVK on 2009-05-15
Well, Iv formatted the drive as ext3, and everything went okay, however, now that I have a nice empty storage area I cant use it because there are no permissions set.

What do I need to do to make this a simple storage drive?

Cheers

Max

---

### Post by Didius Falco on 2009-05-15
> **MaxVK said:**
> Well, Iv formatted the drive as ext3, and everything went okay, however, now that I have a nice empty storage area I cant use it because there are no permissions set.

What do I need to do to make this a simple storage drive?

Cheers

Max

Hi Max,

You'll need to add it to your fstab file. To edit the fstab, open a Terminal and type ```
gksudo gedit /etc/fstab
``` Then add a line for that partition. Here is the line from mine that links my Data partition:

```
# EXT3 Data on /dev/sda12  (hd0,11)
/dev/sda12                                 /media/Data         ext3         defaults                    0  0  
```Make something similar to that, but reflecting the location on your PC. Yours would be sdb1, for example, if it's the first partition on the second drive. Note the mount point in mine - the part that says /media/Data. By adding that it will make it possible to automatically mount the drive when you log in. Save the fstab file and exit.

Next, type this in the terminal:

```
gksudo nautilus
```Navigate to /media and create a folder with the *exact* same name as your mount point in fstab, including any capitalization - linux is case-sensitive.Don't use any spaces either - if you need to separate two words, either use a dash or a period.

Reboot and it should mount the drive with full read/write permissions. If it doesn't allow you to read/write to the drive, post again and you'll get instructions on how to change the file permissions.

Regards,

Didius

---

### Post by MaxVK on 2009-05-15
Hey Didius. Thanks for that. The drive is now mounting nicely when I start the machine, but there are a couple of problems:

Firstly, I formatted this drive (sdb1) and it showed as empty. It has now mounted okay thanks to your instruction, but suddenly it seems that it still contains the data that was there before the format. All of it.

Secondly I am unable to do anything with any of the files there. Should I try to format it again? 

I wonder why was it reported empty when I first formatted it, and now its full up again? Most odd! Is this something that is supposed to happen?

cheers

Max

---

### Post by Didius Falco on 2009-05-15
> **MaxVK said:**
> Hey Didius. Thanks for that. The drive is now mounting nicely when I start the machine, but there are a couple of problems:

Firstly, I formatted this drive (sdb1) and it showed as empty. It has now mounted okay thanks to your instruction, but suddenly it seems that it still contains the data that was there before the format. All of it.

Secondly I am unable to do anything with any of the files there. Should I try to format it again? 

I wonder why was it reported empty when I first formatted it, and now its full up again? Most odd! Is this something that is supposed to happen?

cheers

Max

Max,

I'm not sure why it didn't format. Did you use Gparted to do so? If so, it could be that while you set it up to format it, you never actually "pulled the trigger" by hitting the "apply" button. I've done that myself...

The easiest way to do it is by using Gparted. If you don't have it installed you can install it from Synaptic. Make sure you select all the "Mark Suggested For Install" packages at the bottom of the menu that comes up when you right click it.

Then just format as either ext3 or ext4 - whichever you are using. Be sure and hit the "apply" button. ;)

Label it the same, and you won't have to fiddle around with your mount point settings.

If you are still having troubles accessing the drive for read/write after you reformat it and reboot, run these two commands:

```
sudo chown -R max:max /media/max
sudo chmod -R 777 /media/max
```

Substitute your user:group names and the name of the mount point you created in those examples.

The first command changes the owner of the drive to you, and the second one gives every account on your installation read/write access.

Regards,

Didius

---

### Post by MaxVK on 2009-05-15
Thanks Didius, but I still have a problem:

I reformatted the drive (You are most likely right and I did not click apply) and gave the drive the label "StorageData".

I used the codes you posted like this:

```
sudo chown -R max:max /media/StorageData
sudo chmod -R 777 /media/StorageData
```

Everything seemed to go okay and when I restarted the drive was mounted nicely on the desktop as 'StorageData' but I still have no permissions on it.

If I try to unmount the drive I get this message:
> **Cannot unmount volume**
You are not privileged to unmount the volume 'StorageData'.

Details
umount: only root can unmount dev/sdb1 from /media/StorageData

A similar message is shown if I unmount the volume as root (I tried this in the partition editor), and then try to remount it again from anywhere else (In other words, not as root).

I'm thinking that I typed a command in wrong perhaps? Any ideas?

cheers

Max

---

### Post by Didius Falco on 2009-05-15
> **MaxVK said:**
> Thanks Didius, but I still have a problem:

I reformatted the drive (You are most likely right and I did not click apply) and gave the drive the label "StorageData".

I used the codes you posted like this:

```
sudo chown -R max:max /media/StorageData
sudo chmod -R 777 /media/StorageData
```Everything seemed to go okay and when I restarted the drive was mounted nicely on the desktop as 'StorageData' but I still have no permissions on it.

If I try to unmount the drive I get this message:


A similar message is shown if I unmount the volume as root (I tried this in the partition editor), and then try to remount it again from anywhere else (In other words, not as root).

I'm thinking that I typed a command in wrong perhaps? Any ideas?

cheers

Max

When you say you have no permissions on it, does that mean that you've tried writing to it and reading from it without success? Please do so and let us know. 

You can change the setting in fstab (I won't insult you by telling you how to open it or where to find it - you are probably dreaming about it at this stage!) from "defaults" to "user". If you also want to be able to run executables from that drive, you'll need to make it "user,exec".

Just out of curiosity (and feel free to tell me to mind my own business), why do you want to unmount it? I leave my data drive mounted all the time, so I can get to my data. <G>

Regards,

Didius

---

### Post by MaxVK on 2009-05-16
I don't want to unmount the drive in the ordinary way of things, but thats about the only thing that was available to for to see if it worked.

This morning however, I have just booted up, the drive has been correctly mounted on the desktop, and I am now able to read/write the drive, so I don't really know what was going on last night.

Which means that everything is working as it should, so once again, thanks for all your help and patience.

regards

Max

---

### Post by Didius Falco on 2009-05-16
My pleasure. I learn new things all the time, even helping out with things I *thought* I already knew.

When my brain still works at age 80, You'll get some of the credit.<G>

Regards,

Didius

---

### Post by MaxVK on 2009-05-16
> **Didius Falco said:**
> When my brain still works at age 80, You'll get some of the credit.<G>

;) Glad to be of some assistance with that - I'm over halfway there already and learning new things all the time, so I'm not doing *too* badly myself!

So, on with my mission to help your brain at 80, Iv another question, which I *think* I know the answer to...

I have now successfully formatted the original root partition (sdb1) for use as a storage area. It has been given a name (StorageData) and it now auto-mounts when I start up.

My next objective is to get the original home partition to auto-mount with a nice label, but of course, without destroying any of the data that is still on it. I am assuming that I will need to do something like this:

```
Create a folder: /media/OldHome

Edit fstab:
/dev/sdb3     /media/OldHome     ext3 user,exec 0  0

Change Permissions: (although maybe not - I already have full permissions)
sudo chown -R max:max /media/OldHome
sudo chmod -R 777 /media/OldHome

Restart
```

Am I correct in my thinking or have I missed something or got things mixed up?

Cheers

Max

---

### Post by Didius Falco on 2009-05-16
> **MaxVK said:**
> ;) Glad to be of some assistance with that - I'm over halfway there already and learning new things all the time, so I'm not doing *too* badly myself!

So, on with my mission to help your brain at 80, Iv another question, which I *think* I know the answer to...

I have now successfully formatted the original root partition (sdb1) for use as a storage area. It has been given a name (StorageData) and it now auto-mounts when I start up.

My next objective is to get the original home partition to auto-mount with a nice label, but of course, without destroying any of the data that is still on it. I am assuming that I will need to do something like this:

```
Create a folder: /media/OldHome

Edit fstab:
/dev/sdb3     /media/OldHome     ext3 user,exec 0  0

Change Permissions: (although maybe not - I already have full permissions)
sudo chown -R max:max /media/OldHome
sudo chmod -R 777 /media/OldHome

Restart
```Am I correct in my thinking or have I missed something or got things mixed up?

Cheers

Max

I'd try it with just "defaults" instead of the "user,exec" option in the fstab file. I'd also hold off on the chown and chmod commands until you test it out.

All my ext3 drives are read/writable with just the basic 

```
/dev/sdb3     /media/OldHome     ext3 defaults 0  0
```setup. But either way will do - as long as it's doing what you want it to, that's the main thing.

I'm more than 1/2 way to 80 myself - I'll be 50 in December.

You'll probably find that partition already has an entry in the fstab - what you may want to do is label it. You can do that in Gparted, just make sure it isn't mounted. That's not required, but it makes it nice when you do a ```
sudo blkid
``` because then you get the labels and the UUID numbers in the output. Helps keep track of what's what.

Regards,

Didius

---

### Post by MaxVK on 2009-05-17
> I'm more than 1/2 way to 80 myself - I'll be 50 in December.

You old devil, you're even older than me, by about 4 years! ;) Almost makes me feel young again!:lol:

Anyway, once again thanks for your help. The old home partition is now mounting nicely as well, so I'm pretty much where I wanted to be with Jaunty.

Once I work out how to stop the system speaker from beeping when I close Jaunty, or work out why the auto-updates don't auto-tell-me that there is an update ready, I'll be finished, now doubt just in time for 9.10 to be released so I can start all over!

thanks again

Max

---

### Post by Didius Falco on 2009-05-17
> **MaxVK said:**
> You old devil, you're even older than me, by about 4 years! ;) Almost makes me feel young again!:lol:

Anyway, once again thanks for your help. The old home partition is now mounting nicely as well, so I'm pretty much where I wanted to be with Jaunty.

Once I work out how to stop the system speaker from beeping when I close Jaunty, or work out why the auto-updates don't auto-tell-me that there is an update ready, I'll be finished, now doubt just in time for 9.10 to be released so I can start all over!

thanks again

Max

They say you are only as old as the one you feel, so with a wife a decade younger than myself, I'm actually younger than you.  :tongue:

To turn off the PC Speaker, you have a couple of options. To turn it off just for that session, you can open a Terminal and type:

```
sudo rmmod pcspkr
```

But to get rid of it for good, type:

```
gksudo gedit /etc/modprobe.d/blacklist.conf

```

Scroll to the bottom of the file and add > #PC Speaker Off
blacklist pcspkr

To never hear that awful sound again, do both the above. I let it squawk one last time, while I made rude noises back at it. =P~

For the Updates, go to** System/Administration/Software Sources**, then to the Updates tab and set up your options. I have mine set to: check daily, only notify about updates (I like to look them over before I install them) and Normal Releases. I also have all four radio buttons enabled at the top.

Regards,

Didius

---

### Post by MaxVK on 2009-05-17
That speaker trick I might try, but I'm a bit peeved that it still beeps rather than play the sound file that I have specified. I'm not sure if this is a specific issue or not, because Iv read a few things where people are complaining about the same thing.

This also goes for the update. I have my settings exactly the same as you, but I never get informed about updates, in fact the only time that I ever saw the notification was immediately after installation.

As it is I have to remember to check for updates, which is not really an issue, but sometimes, especially when my mind is on my latest bit of python code etc, I forget.

As for how old we may feel: I'm a single parent with two kids so Id reckon on feeling about 60 most days!

---

