---
title: "Problems with Dual Boot Hardy and Vista"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by InvaZimm on 2009-01-21
Hi everyone,

Been searching around trying to to troubleshoot this problem I am having.  I had an HP Pavilion laptop that crapped out on me a few months back unfortunately.  As grabbing a new one isn't very likely just yet, I decided that I would see about putting the 2.5" SATA harddrive from the laptop into an old workstation of mine so I can at least use some of my work for now.
The harddrive had been dual booted with Vista and Hardy Heron.  Both working fine together in the laptop.  I placed the harddrive into my workstation set a quick raid to load it.  I received the GRUB loader and selected Heron to run.  After a quick check over of the new components, Heron started up fine and has worked relatively well since.
Seeing that Heron worked, I restarted the machine and chose Vista from the loader.  After viewing the loading screen Vista flashed the BSoD and restarted.  From some of the information I gathered, Vista is just having a difficulty readjusting to the new hardware and that the boot is not functioning well.  After searching around some I discovered on this form a quick tutorial/tip that appeared to be what I am looking for:
[http://ubuntuforums.org/showthread.php?t=828862]("http://ubuntuforums.org/showthread.php?t=828862")

After getting into the repair console, it does not recognize the SATA harddrive being attached so I am unable to see if these instructions are what I am looking for.  I am pretty sure they are, but just having difficulties getting a chance to use them.
If anyone has any idea what's going on or can at least point me in the right direction I'd be greatly appreciative.  There's a ton of stuff, work and programs that I need sitting on that partition of the harddrive that makes reformatting and reinstalling Vista a very very last ditch effort.

Thanks.

---

### Post by AegisTalons on 2009-01-21
I'm not sure if I completely understand your problem. Can you currently boot into Linux? Additionally, I'm assuming the you have multiple partitions setup (at least 2, one for Vista and one for Ubuntu). If you can boot into Ubuntu, can you see the Vista partition? If you see the Vista partition, can you copy everything over to either the Linux partition or a backup drive?

After just reading your post again, could it be that Vista has no clue how to handle your SATA drive? If I'm not mistaken, with Windows you need special drivers to let it know how to handle the SATA drive. If this is the case, most SATA drives can be put into a "simple" mode. The drawback to this mode is that its just slower, but you should get access to it.

To set it to "simple" mode, you need to go into your BIOS and search for how to change it. It varies from manufacturer where they hide this feature. I would definiately recommend googling your laptop name and something like "SATA BIOS".

Keep us updated.

---

### Post by northern lights on 2009-01-21
That booting an installed Vista on completely different hardware would be a real hassle is no surprise. I'd rather recommend backing up data from Ubuntu and reinstalling Vista, if needed.
If you can boot your Ubuntu, please post the output of ```
sudo fdisk -l
``` to verify the validity of the following:

Your Vista should be on the drive's first partition. If so, do the following:

Open a Terminal (Applications > Accessories) and run```
gksu gedit /etc/fstab
```add the following line to the file```
/dev/sda1	/media/windows	 ntfs    noatime,uid=1000	0       0
```Save and quit. Subsequently run```
sudo mkdir /media/windows
```and```
sudo mount -a
```The Windows partition should now be available from the Places menu or manually from /media/windows/

---

### Post by InvaZimm on 2009-01-23
Hi Guys,

Thanks for the replies, honestly.  Sorry for the difficult post before, wrote it too quickly and didn't really re-read it.

Yes, the SATA drive is in 2 partitions, the larger side being the Vista side, a little less than 98 gigs, while the smaller side is Linux, about 20ish gigs including swap.  I am able to get into Linux fine, the only problems I have in there are just newbie issues of still trying to get used to something of the Linux/Unix environment.

I'm not sure if there's something in the current bios, workstation has Phoenix Bios V2.02 an older version than what I believe is currently out there.  Which I definitely would like to upgrade when I get a chance, though many of the scan programs online are Windows based and seem to fail the few times I've run them in Wine.  SATA wasn't within this Bios, there was a separate one called FastBuild in which I setup the quick raid.  In Phoenix, there is no hard drive listed as the Primary Master, not sure if that is a reason for why I'm having difficulties with Windows Repair seeing it or not.  But also wondered if the Primary Master slot in Phoenix was only for IDE drives, could be wrong.  I'm trying to remember what Bios was used on the laptop, I think it was Phoenix, but not entirely sure.

From day one of putting this hard drive into the workstation I've been actually able to see the Vista partition as you described Northern.  Listed in my places.  I was definitely relieved about that since I required at least some documents at that exact moment.

There is a possibility of grabbing everything from the Vista drive and then either reinstalling Vista or using a backup that I had made with Acronis of Vista, though that was unfortunately back at the end of September. Thought I had a more recent one, but oh well.  The one thing I do wonder though is whether it is the correct sized partition, since I believe I made it before I created the partition for Ubuntu.  Or would that matter, do you think?

The thing is I would rather not have to reinstall everything all over again if able.  Time being one of the factors.

---

