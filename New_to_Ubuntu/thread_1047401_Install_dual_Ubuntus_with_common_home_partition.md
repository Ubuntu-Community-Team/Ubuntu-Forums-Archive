---
title: "Install dual Ubuntus with common /home partition?"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by 2CV67 on 2009-01-22
Hi guys!

I currently have Hardy running with a separate /home partition.
I am interested in having 2 versions of Ubuntu on the same PC, preferably sharing a common /home partition.
On several sites (Illustrated Dual Boot Site, Psychocats, etc) I have seen this scheme presented as OK - good even.
But I have not seen how to get there.

If I try to install another Ubuntu to a new partition (from a live CD or a Remastersys live DVD) is it not going to automatically create its own new /home inside that partition? (sorry - its been a while since I did any of that...).
How do I get it to not create a new /home?
How do I get both Ubuntus to use the same /home?

Or is it a bad idea anyway?

Thanks for any advice!

---

### Post by dorkdork777 on 2009-01-22
I've had /home across versions with relatively no hitches. The only thing is you'll need to make sure your own settings work for both versions - for example, if you install an app that goes on your panel, it needs to be installed on both. Also, themes can be a problem - just make sure you're using a theme that's installed on both.

After that, it's pretty easy. You'll need to select manual partitioning in the installer. Make a partition to use as /, then make one to use as /home (if you haven't already). However, it won't know that you want to use it as /home, so click it, go on "Edit partition", and select "mount point" as "/home".

Use the same /home partition for both installs, obviously. And you'll probably want the same username as well.

Good luck :)

---

### Post by mjheagle8 on 2009-01-22
i would recommend using different usernames and just copying over settings so you do not screw up files with different software versions etc. and if you decide to remove one os you can also remove that account.

---

### Post by ComputerHQ-UK on 2009-01-22
Does this not cause issues with user permissions?  I would think that the user accounts of each version might have different numeric IDs and that would cause issues.

---

### Post by dorkdork777 on 2009-01-22
Different usernames is more of a safety measure, that requires quite a bit of work on the user's part. Keeping all the right settings in sync, and not the rest can get tiring.

I've had no problems with sharing /home between versions, but that's just my experience. If you're doing mission-critical work, then for safety's sake I'd have to agree with mjheagle8 and suggest different usernames.

But I'm intrigued; why have two different versions installed at once? I'd like to hear your reasoning :)

EDIT: @ComputerHQ-UK: as far as I'm aware the IDs are the same for every version. The only problems you'd get from that is if you were sharing one /home folder across two different distros which use different IDs, like (I think) Fedora and Ubuntu.

---

### Post by 2CV67 on 2009-01-22
Thanks for all those good comments so far!

> **dorkdork777 said:**
> 
But I'm intrigued; why have two different versions installed at once? I'd like to hear your reasoning :)
To quote the [Illustrated Dual Boot Site]("http://mywebsite.bigpond.net.au/dfelderh/linuxmaniac/p23.html")
> Multiple booting is as easy as dual booting, and it avoids the problem of having something go wrong during an upgrade. Many people upgrade from an older version of Ubuntu to a newer version when it is released, but a few don't make it or decide they'd rather go back to the older version. It's too late, they can't go back.

My experience has been that even kernel updates bring new problems (sometimes severe like freezing & no wireless) & version upgrades even more so.
I don't want to be stuck with Intrepid belly-up & no way to work or go back.
So I want to get started gently with Intrepid while keeping Hardy available for vital work & looking for fixes.

I discussed this generally in another thread [http://ubuntuforums.org/showthread.php?t=1038213](http://ubuntuforums.org/showthread.php?t=1038213)
but I wanted a clear answer to this one point about sharing /home.

Thanks again for all comments!

---

### Post by 2CV67 on 2009-01-23
The attached detail from the Illustrated Dual Boot site shows about what I am aiming to do:
XP on one partition
FAT32 share partition
Existing Ubuntu with separate root, home & swap partitions
New Ubuntu to be inserted in new partition but using existing home, swap & share partitions.

So I still hope & assume that is reasonable.

What I need to know is - how, in installing the new Ubuntu from a live CD/DVD do I just install the root bit & get it to work with the existing home, swap & share bits?

I don't want to just go & try it, in case I screw something up too badly!

Thanks for any tips, or pointers to tutorials or how-to's.
I think I looked all through the usual tutorials, without seeing this point mentioned.

---

### Post by Bölvaður on 2009-01-23
like they said above there can be problems sharing /home if you do not know what you are doing. thats why I normally make for me and others /data partition that is shared and the bookmarks are just redirected into /data from /home, or you could also just make a link from /home/Documents that points to /data/Documents

that way you will not get into trouble with programs sharing config.

---

### Post by 2CV67 on 2009-01-23
I certainly still have at least one foot in the "do not know what you are doing" camp, so I am listening to the warnings & will probably end up not sharing my /home.

But I would still like to know, as I said above:> how, in installing the new Ubuntu from a live CD/DVD do I just install the root bit & get it to work with the existing home, swap & share bits?

Can anybody clear that up for me - even if I end up not daring to do it?

Thanks!

---

