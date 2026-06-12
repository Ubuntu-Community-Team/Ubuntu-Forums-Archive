---
title: "Resizing partition"
date: 2009-10-17
forum: New to Ubuntu
---

### Post by Sisyphus48 on 2009-10-17
I recently installed a new 500 GB Western Digital HD in my computer to replace my 80 GB HD.  I used the DD command to copy the old drive contents to the new had drive, planning to resize the partition after I did the transfer of everything from the old to the new.  That turned out great, really better than I expected.  However, the resizing has not turned out so great.  The DD command copied everything, including the partition from the old on to the new.  The old partition was the whole drive.  According to everything I've read I should be able to resize the new partition to include the whole new hard drive.
Yet I cannot using Gparted.  It does not give me that option.  When I say I want to resize the partition it doesn't give me the option to include the whole drive.  I've included a snapshots to elucidate what I'm talking about.  Damn I can't get the snapshot pasted on here.  Suggestions anyone??

---

### Post by oboedad55 on 2009-10-17
> **Sisyphus48 said:**
> I recently installed a new 500 GB Western Digital HD in my computer to replace my 80 GB HD.  I used the DD command to copy the old drive contents to the new had drive, planning to resize the partition after I did the transfer of everything from the old to the new.  That turned out great, really better than I expected.  However, the resizing has not turned out so great.  The DD command copied everything, including the partition from the old on to the new.  The old partition was the whole drive.  According to everything I've read I should be able to resize the new partition to include the whole new hard drive.
Yet I cannot using Gparted.  It does not give me that option.  When I say I want to resize the partition it doesn't give me the option to include the whole drive.  I've included a snapshots to elucidate what I'm talking about.  Damn I can't get the snapshot pasted on here.  Suggestions anyone??

Are you trying to resize the mounted drive? If so, boot from the LiveCD and use gparted.

---

### Post by Sisyphus48 on 2009-10-17
> **oboedad55 said:**
> Are you trying to resize the mounted drive? If so, boot from the LiveCD and use gparted.


I tried that and gparted didn't give me that option.  When I booted from a LiveCD and used gparted a screen opens that lets you adjust the size of the partition you want but it doesn't let you enlarge it to include the whole disk. It is like it believes that the copy of the old disk I made with the DD command is all there is to the disk.  Having said that it does show the 400 GB space that is free on the disk. I wish I knew how to paste a screen-shot on this pages because I believe that would make what I am trying to say clearer.  Thanks for your reply.

---

### Post by LewRockwell on 2009-10-17
to attach screenshots to your posts just scroll down on the "reply to thread" page to the "additional options" area where you will see "attach files" and just click on **"Manage Attachments"** and follow the instructions found there

.

---

### Post by LewRockwell on 2009-10-17
when you use gparted partition editor via the LiveCD does gparted show your current partition as locked?

(normally this is shown by "keys" or a "padlock" symbol)

the drive must be unmounted to successfully perform alterations/adjustments/etc.

.

---

### Post by gdonwallace on 2009-10-17
This may be caused by the dd command.  dd is a low-level copy program.  It is intended to do what you where wanting, copy the entire partition for backup.  However; the draw back to dd is that when you go to "restore" that backup, it does not matter the size of the driver your going to.  It only sees what you have backed up.  Thats the way dd works.  dd is designed to "backup / restore" to drives that are the same size.  Any thing bigger than what you use dd on is basically lost.  Because part of what dd backs up is the partition information.  If that information reads a 60 gig hard drive and you are copying to a 200 gig hard drive, you only get that 60 gig.

What you really need to do is a actual backup to cd/DVD and restore that to the new hard drive.  That will fix your problems.

---

### Post by oldfred on 2009-10-17
There was another thread with exactly this problem. In the MBR is the partition info as well as boot info. The dd copied the partition info and most programs depend on that partition info for knowing how your drive is set up.

I looked but could not find the previous thread, but he tried a lot of things and the one that finally worked was something from the drive mfg. that reset the drive size so then gparted worked.

---

### Post by Sisyphus48 on 2009-10-18
> **LewRockwell said:**
> to attach screenshots to your posts just scroll down on the "reply to thread" page to the "additional options" area where you will see "attach files" and just click on **"Manage Attachments"** and follow the instructions found there

.

Thanks, LewRockwell I will try this.

---

### Post by Sisyphus48 on 2009-10-18
[QUOTE=LewRockwell;8119390]when you use gparted partition editor via the LiveCD does gparted show your current partition as locked?

(normally this is shown by "keys" or a "padlock" symbol)

the drive must be unmounted to successfully perform alterations/adjustments/etc.

OK, here is what I get when using a LiveCD:

---

### Post by Sisyphus48 on 2009-10-18
> **gdonwallace said:**
> This may be caused by the dd command.  dd is a low-level copy program.  It is intended to do what you where wanting, copy the entire partition for backup.  However; the draw back to dd is that when you go to "restore" that backup, it does not matter the size of the driver your going to.  It only sees what you have backed up.  Thats the way dd works.  dd is designed to "backup / restore" to drives that are the same size.  Any thing bigger than what you use dd on is basically lost.  Because part of what dd backs up is the partition information.  If that information reads a 60 gig hard drive and you are copying to a 200 gig hard drive, you only get that 60 gig.

What you really need to do is a actual backup to cd/DVD and restore that to the new hard drive.  That will fix your problems.

Thanks, gdonwallace,. I included a couple of snap shots of what I get when I try to use Gparted to clarify what I had said earlier.  If I end up doing what you suggest can I make the backup to DVD from the DD copy I'm using now or would I have to use the original disk??

---

### Post by Sisyphus48 on 2009-10-18
> **oldfred said:**
> There was another thread with exactly this problem. In the MBR is the partition info as well as boot info. The dd copied the partition info and most programs depend on that partition info for knowing how your drive is set up.

I looked but could not find the previous thread, but he tried a lot of things and the one that finally worked was something from the drive mfg. that reset the drive size so then gparted worked.

Thanks, OldFred.  The reason that I used the dd command was that I had read on some forum that you could easily resize the partition after making the copy but the advice to do the resizing hasn't worked so far.
I went to Western Digital's web site but it seemed like they offered little support for a Linux system 
.

---

### Post by egalvan on 2009-10-18
Your screenshot show that your drive is "full", you only have approx 20mb un-allocated.
You have no un-allocated space to "grow" sda1 into.

you basically have three partitions

sda1 is a primary partition, formated as ext3, and mounted as root "/", and locked

sda2 is an extended partition, with "swap" fully using it. swap is locked

sda3 is a primary partition, formated as ext3. This is un-locked.

So, question time:

Is sda1 an existing *nix install?

Are you booting from sda1?

or are you booting from a LiveD?

Is sda3 the space you want to use?



You need to use a LiveCD to actually make changes to partitions.
They need to be un-mounted in order for changes to be allowed.

You can use almost any LiveCD for this...
I recommend PartedMagic LiveCD, an excellent "mini-distro" with a good selection of partition tools, and they keep gparted up to date.


And if sda3 actually is the space you want to use,
then make sure you have no data you want/need on it,
use gparted  to un-allocate the space (delete the partition)
then move the other partition to the end of the drive,
and "grow" sda1 into the un-allocated space.

I'll be back on Monday morning, I have a shift starting at the firehouse.

Hopefully the others posting here can further help.

---

### Post by hopelessone on 2009-10-18
While you're movin stuff around you might wanna shrink that SWAP partition to say 1Gb, gives you more space...My computer hardly uses swap...

Nowdays gone are the SWAP = Double your memory..

And stick it at the very end of the drive too!

just a thought..

---

### Post by Sisyphus48 on 2009-10-18
> **egalvan said:**
> Your screenshot show that your drive is "full", you only have approx 20mb un-allocated.
You have no un-allocated space to "grow" sda1 into.

you basically have three partitions

sda1 is a primary partition, formated as ext3, and mounted as root "/", and locked

sda2 is an extended partition, with "swap" fully using it. swap is locked

sda3 is a primary partition, formated as ext3. This is un-locked.

So, question time:

Is sda1 an existing *nix install?

Are you booting from sda1?

or are you booting from a LiveD?

Is sda3 the space you want to use?



You need to use a LiveCD to actually make changes to partitions.
They need to be un-mounted in order for changes to be allowed.

You can use almost any LiveCD for this...
I recommend PartedMagic LiveCD, an excellent "mini-distro" with a good selection of partition tools, and they keep gparted up to date.


And if sda3 actually is the space you want to use,
then make sure you have no data you want/need on it,
use gparted  to un-allocate the space (delete the partition)
then move the other partition to the end of the drive,
and "grow" sda1 into the un-allocated space.

I'll be back on Monday morning, I have a shift starting at the firehouse.

Hopefully the others posting here can further help.

OK, did what you said and it still won't let me resize the partition.  I've included two snap shots that show me what Gparted says. The 73363 (?) on the partition window is all it allows me to resize the partition even though I deleted the large partition.  I have no idea why but it keeps telling me the second screen shot I try to add is wrong even though it is listed on the acceptable list and well below the maximun size.  That screen shot show the large partition deleted, the drives unmounted.

---

### Post by oldfred on 2009-10-19
I found this for the same issue:

[http://swiss.ubuntuforums.org/showpost.php?p=7529107&postcount=9](http://swiss.ubuntuforums.org/showpost.php?p=7529107&postcount=9)

[http://www.hdat2.com/](http://www.hdat2.com/)

---

### Post by oldfred on 2009-10-19
Also found this on:
[http://www.pcreview.co.uk/forums/thread-3865829.php](http://www.pcreview.co.uk/forums/thread-3865829.php)

Many disk manufacturer provide tools to do lower level testing and repairs
to their disks.

For example, Hatachi offer a "Drive Fitness Test" tool that can, among other
things, erase the master boot record.  (See page 21 of the PDF maual for
thier software.)

[http://www.hitachigst.com/hdd/support/download.htm](http://www.hitachigst.com/hdd/support/download.htm)

Other disk makers probably offer similar tools for their hardware.

---

### Post by egalvan on 2009-10-19
> **egalvan said:**
> 
So, question time:

Is sda1 an existing *nix install?

Are you booting from sda1?

or are you booting from a LiveD?

Is sda3 the space you want to use?



OK, but the questions above remain un-answered.


Further, are you aware that operations in gparted are a two-step process?

First you pick the operation you want,
and then you "apply" them.

For instance, to delete a partition, you first highlight the paritition, then pick "delete partition", then you tell gparted to "apply" the change.
You can do several operations in a row, but untill you apply the changes, NOTHING WILL BE WRITTEN TO THE HARD DRIVE.

Sorry if the above is something you are aware of, but too many folks who are unfamiliar with gparted are tripped up by this.

Try posting the gparted screenshot again.

---

### Post by Sisyphus48 on 2009-10-20
> **egalvan said:**
> OK, but the questions above remain un-answered.


Further, are you aware that operations in gparted are a two-step process?

First you pick the operation you want,
and then you "apply" them.

For instance, to delete a partition, you first highlight the paritition, then pick "delete partition", then you tell gparted to "apply" the change.
You can do several operations in a row, but untill you apply the changes, NOTHING WILL BE WRITTEN TO THE HARD DRIVE.

Sorry if the above is something you are aware of, but too many folks who are unfamiliar with gparted are tripped up by this.

P.S.  I hope you can make this out the uploader keeps changing it from a .PNG file to a .jpeg and reducing the size also.  Now see I don't get that as it was originally 103 kb which it says is well below the maximum for a .png file.

Try posting the gparted screenshot again.

Ok here are the questions and answers;
Is sda1 an existing *nix install?YES

Are you booting from sda1?

or are you booting from a LiveD?LIVECD, I REALIZED THAT THE DRIVE COULDN'T  BE UNMOUNTED IF YOU WERE USING IT.

Is sda3 the space you want to use? YES.  NOW IN THE SCREEN SHOT I'M POSTING, IT IS NO LONGER sda3 BECAUSE I DELETED THE PARTITION AS PER YOUR INSTRUCTIONS.

Absolutely no offense taken with you making sure of what I know.  All the above knowledge I've learned in the last week.  Been using Ubuntu for 2 years now and I love it!  However, I never feel like I know enough.  That being said I would never go back to Windows because I'm overwhelmed at how good Linux/Ubuntu are.

---

### Post by mikechant on 2009-10-20
Your screenshot is unreadable even when zoomed in.

---

### Post by Sisyphus48 on 2009-10-20
> **mikechant said:**
> Your screenshot is unreadable even when zoomed in.

I'm sorry, I don't uderstand what the deal is with this screenshot. It is a PNG image (image/png)that is 101.3 KB (103703 bytes) yet when I upload it the Ubuntu forums software changes it to a .jpeg file with less KBs making it unreadable.  
Any suggestions??

---

### Post by LewRockwell on 2009-10-20
back-up/clone/safely-store any/all valuable data and then you can really get that drive partitioned the way you want it and then install the distro(s) that you like

You can check out a couple of our daily beaters at these links:

[http://ubuntuforums.org/showthread.php?t=1222961](http://ubuntuforums.org/showthread.php?t=1222961)

[http://ubuntuforums.org/showthread.php?t=1252042](http://ubuntuforums.org/showthread.php?t=1252042)

.

---

### Post by Sisyphus48 on 2009-10-20
> **LewRockwell said:**
> back-up/clone/safely-store any/all valuable data and then you can really get that drive partitioned the way you want it and then install the distro(s) that you like

You can check out a couple of our daily beaters at these links:

[http://ubuntuforums.org/showthread.php?t=1222961](http://ubuntuforums.org/showthread.php?t=1222961)

[http://ubuntuforums.org/showthread.php?t=1252042](http://ubuntuforums.org/showthread.php?t=1252042)

.

Thanks LewRockwell I think I'm going to go the route you suggest rather than messing around with it.

---

### Post by mikechant on 2009-10-21
> when I upload it the Ubuntu forums software changes it to a .jpeg file with less KBs making it unreadable. 
Any suggestions??

Looks like you're taking another route now but just for reference I would suggest opening the png with any image editor (e.g The Gimp) and then doing a 'save as' to jpeg with the quality set to 100%/max/whatever the option is.

I guess the forum upload process is maybe doing a lower quality conversion or something.

---

### Post by Sisyphus48 on 2009-10-21
> **mikechant said:**
> Looks like you're taking another route now but just for reference I would suggest opening the png with any image editor (e.g The Gimp) and then doing a 'save as' to jpeg with the quality set to 100%/max/whatever the option is.

I guess the forum upload process is maybe doing a lower quality conversion or something.

Thanks, mikechant, good suggestion!

---

