---
title: "Is it possible to clear space from your hard drive using the live cd?"
date: 2011-05-07
forum: New to Ubuntu
---

### Post by sprogmeister on 2011-05-07
I upgraded to the latest Ubuntu release but it will not boot up. The live CD works and will run updates on the hard drive  but there is not enough space to do this. I try to clear space but am told I do not have permissions. I do not want to fdisk the drive, is there a way I can clear space to run the updates?

---

### Post by andrewthomas on 2011-05-07
How are you trying to create space?

Try using sudo rm in the terminal

---

### Post by Linux_junkie on 2011-05-07
If your booting up from the live CD your not using the hard drive.  The Live CD does not use the hard drive.  What its using instead is part of the computers memory (RAM) as a drive this is why its running out of space on the RAM drive.

---

### Post by Not unique on 2011-05-07
Try copying  "   sudo nautilus   "   (without the quotes) into your terminal and this will open Nautilus (your file manager) in ROOT mode so you can copy,edit or delete anything no matter the permissions.
Hope this helps should be easier than using just terminal.
Try NOT to delete any thing important only files in Home would be best.

---

### Post by sprogmeister on 2011-05-08
I had accessed the hard drive through places and computer. The idea of sudo nautilus will not allow to change the hard drive just the mounted live cd. Anyone any ideas?

---

### Post by powerpleb on 2011-05-08
> **sprogmeister said:**
> I had accessed the hard drive through places and computer. The idea of sudo nautilus will not allow to change the hard drive just the mounted live cd. Anyone any ideas?
Yes, you won't have the permissions to make changes to the drive. You'll need to use chroot.

Follow cariboo's advice in this thread: [http://ubuntuforums.org/showthread.php?t=1656497](http://ubuntuforums.org/showthread.php?t=1656497)

---

### Post by sprogmeister on 2011-05-08
Powerpleb, thanks but I do not quite understand how to use chroot.

---

### Post by powerpleb on 2011-05-08
> **sprogmeister said:**
> Powerpleb, thanks but I do not quite understand how to use chroot.

Just follow the instructions. Chroot will allow you to run commands from the LiveCD as if you are running them from your Ubuntu install.

> **cariboo907 said:**
> I would suggest you make some empty space on the hard drive. What a lot of people forget is that all the packages you install are archived in /var/cache/apt/archives. The quick way to remove them is to open a terminal and type:

```
sudo apt-get clean
```

Even though you can't boot from your hard drive, you should still be able to mount it and and chroot it. Follow these instructions:

Boot from the Live CD, and once at the desktop, open a terminal, at the prompt type the following commands, pressing Enter after each one:

[LIST=1]
[*]sudo mount /dev/sda1 /mnt
[*]sudo mount -o bind /dev /mnt/dev
[*]sudo mount -o bind /sys /mnt/sys
[*]sudo mount -o bind /proc /mnt/proc
[*]sudo chroot /mnt
[/LIST]

now at the prompt you should be able to run the first command I gave you, without the sudo.

Once you are finished with the above, you can umount your hard drive by pressing Ctrl-D and then at the prompt type:

[LIST=1]
[*]sudo umount /mnt/proc
[*]sudo umount /mnt/sys
[*]sudo umount /mnt/dev
[*]sudo umount /mnt
[/LIST]

P.S. You might have to change "/dev/sda1" to the location of the drive you want to free space from. Best way to find out which drive it is is to run "sudo fdisk -l".

---

### Post by sprogmeister on 2011-05-08
Thanks Poerpleb, tried it and still get the error message that I need to clear at lease 243mb from \. Any ideas?

---

### Post by gandaran on 2011-05-08
> **sprogmeister said:**
> Thanks Poerpleb, tried it and still get the error message that I need to clear at lease 243mb from \. Any ideas?
what are those files you want to clear

---

### Post by sprogmeister on 2011-05-08
Gandaran, I am trying to free some of the files containing films to clear space to run the updates in the hope this will clear another issue. I just don't know how to do it

---

### Post by powerpleb on 2011-05-08
No probs. Go through same instructions but instead of running "sudo apt-get clean", navigate to where the files are (cd /path/to/files) and delete them with "rm" (rm file.name).

---

### Post by gandaran on 2011-05-08
> **sprogmeister said:**
> Gandaran, I am trying to free some of the files containing films to clear space to run the updates in the hope this will clear another issue. I just don't know how to do it
the space you need for updates is in the root file system not the user home where you keep your films, deleting the films wont fix it.
what you have to delete is the downloaded cache in /var/cache/apt/archives, boot the live cd first then open terminal and type
```
sudo -i nautilus
```
this opens a root nautilus window then navigate to your ubuntu drive install, go to /var/cache/apt/archives and delete all or at least some of the downloaded programs archives (.deb).
when running ubuntu from the hardrive you can keep the system clean of downloaded cache running this command
```
sudo apt-get clean
```

---

### Post by sprogmeister on 2011-05-08
Gandaran, how do I get to /var/cache/apt/archives from terminal ?

---

### Post by powerpleb on 2011-05-08
> **gandaran said:**
> the space you need for updates is in the root file system not the user home where you keep your films, deleting the films wont fix it.
That's only going to be the case if he put the home dir in a different partition. Isn't it?

---

### Post by gandaran on 2011-05-08
> **sprogmeister said:**
> Gandaran, how do I get to /var/cache/apt/archives from terminal ?
type in terminal
```
sudo -i nautilus
```
then go with the root nautilus file browser that opens with the terminal commad

---

### Post by sprogmeister on 2011-05-08
Powerpleb, I am confused by what I have to do to follow your advice.

---

### Post by sprogmeister on 2011-05-08
> **gandaran said:**
> type in terminal
```
sudo -i nautilus
```
then go with the root nautilus file browser that opens with the terminal commad

Sorry Gandaran, I am still having issues with this. The only folder I see is called Desktop. Am I doing something wrong?

---

### Post by gandaran on 2011-05-08
> **powerpleb said:**
> That's only going to be the case if he put the home dir in a different partition. Isn't it?
well, I don't know, I have always used a separate home partition so I have never seen a ubuntu setup in the same partition but either way removing the cache should make the necessary space.

---

### Post by gandaran on 2011-05-08
> **sprogmeister said:**
> Sorry Gandaran, I am still having issues with this. The only folder I see is called Desktop. Am I doing something wrong?
don't you see the the mounted hardrive partitions in the nautilus left bar?

---

### Post by sprogmeister on 2011-05-08
No I cannot see the partitions or hard drives

---

### Post by sprogmeister on 2011-05-08
Found it. But where is the trash folder held? Then I can empty that to ensure the space is freed up.

---

### Post by Not unique on 2011-05-08
Just to refer to my earlier post:
If it is a permissions problem sudo nautilus would of sorted that out that's how I move stuff around and such without messing around to much.

---

### Post by gandaran on 2011-05-08
> **sprogmeister said:**
> Found it. But where is the trash folder held? Then I can empty that to ensure the space is freed up.
select the file then use the delete key or enable the delete option in nautilus preferences, don't send to root trash, you may find problems emptying the root trash.

---

### Post by madjr on 2011-05-08
> **gandaran said:**
> select the file then use the delete key or enable the delete option in nautilus preferences, don't send to root trash, you may find problems emptying the root trash.

**shift + delete** to permanent delete


------

@sprogmeister

can you attach here a pic of your nautilus or the folders you are navigating?

press the **PrtSc** key to capture the screen.

---

### Post by sprogmeister on 2011-05-08
Thanks. I have deleted it all and it still says it need space

---

### Post by sprogmeister on 2011-05-08
Basically I am trying to run the updates in order to repair the grub that keeps failing if I try and boot from the hard drive.

---

### Post by Lateralis on 2011-05-08
I'm now really confused as to what your problem is.  You said that you cannot boot, but I have to ask you: at what point does the boot fail?  You've mentioned just now that you need to update grub, which suggests to me your boot problems are related to grub and nothing else.  Is that the case?  

You also said you've upgraded to 11.04 - did that process go OK, or did you run out of disc space during that upgrade?  

If the problem is with Grub, then you could try simply chroot into your hard disc-installed Ubuntu from a live CD and issuing 

```

sudo update grub

```

If the problem with your boot is not with grub then what error do you get?  Do you see a message which specifically says you have run out of disc space?  Or another way, why do you think a lack of disc space is preventing your computer from booting properly?  

I apologise entirely if I've missed anything you've said or if I am being dense, but I'm having a hard time correlating your boot issues with your lack of hard drive space.

---

### Post by sprogmeister on 2011-05-08
Lateralis. I have a problem with the Grub and booting up. I have tried to reinstall the grub but still get the prompt about grub rescue. I thought I might get round the problem by updating via the live disk. It seems the update did not work either as the upgrade to the new distro is offered. I am desperately trying to get the computer working without wiping it

---

### Post by Lateralis on 2011-05-08
OK, well, lets try and get your computer booting up.  

Firstly, it might be of use if you could download and run in a Live session [this boot info script]("http://sourceforge.net/projects/bootinfoscript/").  This will tell us exactly how your hard drive is partitioned, how much space you have, where your boot files are etc... It might provide clues as to why Grub is falling over.  

You may also want to read the [Grub Wiki]("https://help.ubuntu.com/community/Grub2#Command Line and Rescue Mode") on Grub rescue and recovery.  If you get the recovery console you may be able to boot manually.  Not ideal, but if you can get into your install then you can do anything you need to in order to get things straight again.

---

### Post by sprogmeister on 2011-05-08
Thanks for your patience. I have got it to boot up now. Thanks for all the help and education, I'll try not to be a pain again

---

### Post by Lateralis on 2011-05-08
Excellent!  I wouldn't say you were a pain at all.  We've all had boot problems!   

Anyway, if the problem is solved, would you mind marking the thread as such, using the thread tools menu found at the top of the thread?

Edit: Out of interest, what did you do in order to boot back into Ubuntu?

---

### Post by sprogmeister on 2011-05-08
I ended up upgrading the grub. I got it right in the end!

---

