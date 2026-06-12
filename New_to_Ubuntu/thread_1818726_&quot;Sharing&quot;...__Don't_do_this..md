---
title: "&quot;Sharing&quot;... : Don't do this."
date: 2011-08-05
forum: New to Ubuntu
---

### Post by scruffyeagle on 2011-08-05
I had a big problem yesterday, and I thought I should share that it happened, as advice that others shouldn't try what I tried; i.e., what caused the problem.

I have a 1 TB external HD I use as backup storage. I have 4 partitions on it for Ubuntu to notice: 3 NTFS, & 1 FAT32. I'd read advice online that a Linux user should NEVER try to write to a NTFS partition - so, to make sure I wouldn't try that, I tried to dismount one.

I chose "Safely remove" from the menu. The result was definitely NOT what I was after! All of the partitions on the external HD were removed from the desktop except the one I'd chosen to "safely remove". AND, the computer locked up. Both the keyboard and the mouse were completely dead. Even Ctrl/Alt/Sysreq-REISUB didn't have any effect. Eventually, I had to admit defeat and fall back to the last resort: Push & hold the power button till the computer cut off the power entirely.

Doing this with an active OS is just begging for a HD crash & damage, but I had no choice. I think, though, that I lucked out. I plugged the external HD into a XP system, and powered it up. It took a long time to boot, but when it did my external HD's file system seemed undamaged. Switching back to Ubuntu laptop, I powered up there. Seemingly, no damage... (WHEW!)

So, as a piece of advice: Don't trust the "safely remove" option. If you don't want it there, disconnect the drive while the computer is off.

---

### Post by Matt__ on 2011-08-05
A lucky escape, but there must be some other underlying problem that caused this.

I've connected literally tens of dozens of different external storage devices and never had a problem with safely remove.

I think about 3 times it has said device busy and cannot be removed, but even then you can still unmount the device in the nautilus menu in home.

---

### Post by coffeecat on 2011-08-05
@scruffyeagle, I can support what Matt__ says. I have used "safely remove" countless times on external drives/partitions and never seen this. There must have been a co-incidental issue causing your lockup. The fact that the magic key sequence didn't work suggests that the kernel had seized up. Out of interest, what chipset is your USB controller? There is a bug that causes external drives to be remounted after safely removing when you have a nvidia USB controller chipset. This is an inconvenience - you simply "safely remove" a second time - but it doesn't cause the system to freeze.

> **scruffyeagle said:**
> I'd read advice online that a Linux user should NEVER try to write to a NTFS partition

Amazing, isn't it, the amount of misinformed, dated or just plain **bad** advice there is floating out there on the big wide web? :) Unless the advice was not to write to your Windows C: partition (which is not what you said), in which case the advice has some merit, but I would NEVER be so dogmatic as to say "NEVER". :wink:

---

### Post by HermanAB on 2011-08-05
Hmm, the NTFS device driver has been working fine for many years.  You can read and write with it without fear.

All that the 'safely remove' function does is a umount command.  There is nothing wrong with that one either, it's been working fine for almost half a century.  You likely have a weird hardware problem.

---

### Post by Wim Sturkenboom on 2011-08-05
> **coffeecat said:**
> 
Amazing, isn't it, the amount of misinformed, dated or just plain **bad** advice there is floating out there on the big wide web? :) Unless the advice was not to write to your Windows C: partition (which is not what you said), in which case the advice has some merit, but I would NEVER be so dogmatic as to say "NEVER". :wink:

I think it's just **dated** advise. In the days, it was not bad advise. Tja, and it keeps on floating on the web forever.

---

### Post by walt.smith1960 on 2011-08-05
I've never had an issue "safetly removing". It WILL unmount ALL partitions on the drive though, not just the one you're using. I can't remember writing to a Windows partition.  I've copied from a few though :).

---

### Post by d2btoo on 2011-08-05
If on Ubuntu 10.04 then perhaps this [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/811745](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/811745)

---

### Post by scruffyeagle on 2011-08-06
> **d2btoo said:**
> If on Ubuntu 10.04 then perhaps this [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/811745](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/811745)

Yes, definitely! My system's kernel _was_ updated to linux-image-2.6.32-33-generic. I found the following advice on the launchpad page you linked to, posted by "Rick":

"You probably still have the older kernel installed. One way to use a different kernel is to use Startup Manager to select the old one to boot from. If you don't already have it installed, install the package "startupmanager" from either Synaptic or the command line, then run it from the System/Administration menu. A window will come up where you can select the default kernel to boot into. Select 2.6.32-32 - the one that DOESN'T end with "recovery mode", close, and reboot."

Now, I see a solution other than turning off the computer when I want to remove the drive. But, what prevents the kernel from being restored to 2.6.32-33 during update/upgrade operations?

---

### Post by d2btoo on 2011-08-06
Well, actually no startup manger needed, you surely have the old kernel installed (unless you manually removed it), so just choose it from the grub menu when you boot till they release the fix. And according to post #46 there, 2.6.32-33.72 contain the fix (hopefully) and that is already in proposed.

PS: I haven't enabled the proposed section and still on 2.6.32-33.71

---

### Post by scorp123 on 2011-08-06
> **scruffyeagle said:**
>  I'd read advice online that a Linux user should NEVER try to write to a NTFS partition ...  There used to be a reverse-engineered "ntfs" kernel module back in the 2.4 kernels. Yes, that's a looooong time ago. Something like around 2000/2001. It was based on reverse-engineering the NTFS driver of Windows NT 4 because back then Microsoft refused to release exact specs on how to handle their super-secret NT filesystem. So this kernel module was very much dangerous, yes. It could really hose your NTFS drives. Those distributions who shipped it per default (e.g. SUSE) only compiled it with the "read-only" option so you couldn't write to NTFS drives at all (if you wanted that you had to reconfigure + recompile your kernel yourself); other distributions such as Red Hat left it turned off completely.

There are a few things that have happened since then:

- kernel 2.6 arrived and it had new rewritten modules
- kernel 2.4 is no longer used these days
- Microsoft lost several lawsuits in the USA and EU and was forced to disclose some of their specifications
- NTFS-3G project arrived, forming the basis for how NTFS is being accessed these days ...

So there was a time where the warning above was valid, e.g. like 10 years ago. But now? Unless you do some really scary stuff modern-day Linux distributions should be able to handle NTFS just fine ...

---

### Post by Gone fishing on 2011-08-06
+1 scorp123

The is no reason not to use ntfs now things have changed a lot since the 2.4 kernel ntfs support is now good. 

ntfsprogs has some good tools, ntfsclone I've used very successfully, and I think even ntfsfix now works? so if ntfs is uncleanly mounted it can be fixed without Windows.

---

### Post by scruffyeagle on 2011-08-06
_**d2btoo**_: The computer in question is a single-boot system, and Grub never displays during startup; i.e., it goes directly to the login screen. I definitely want to keep it this way, since this computer will (when ready) be for my 84 year old mother. She's far from being a computer guru, and the simpler I can keep it, the better.

**_scorp123_**: Thanks for the info. That's reassuring to me. The alternative to simply avoiding using the drive that has those 3 NTFS partitions, would have been to shuffle all the contained data (250 GB?) elsewhere, reformat that storage space to FAT32 (my audio work station for recording & editing is a Windows machine) possibly repartitioning into smaller sections, and then shuffle it all back.

---

### Post by scruffyeagle on 2011-08-06
> **Gone fishing said:**
> +1 scorp123

The is no reason not to use ntfs now things have changed a lot since the 2.4 kernel ntfs support is now good. 

ntfsprogs has some good tools, ntfsclone I've used very successfully, and I think even ntfsfix now works? so if ntfs is uncleanly mounted it can be fixed without Windows.

Thanks for the tip. I upgraded my NTFS stuff via Synaptic, after reading this. I found the ntfsprogs program, but didn't find ntfsfix & ntfsclone in either the SPM or the Ubuntu Software Center. Is there any good reason to go chasing them down? And, if yes, where would I find them?

---

### Post by coffeecat on 2011-08-06
> **Gone fishing said:**
> I think even ntfsfix now works? so if ntfs is uncleanly mounted it can be fixed without Windows.

Have another look at man ntfsfix, particularly this bit:

>  ntfsfix  is a utility that fixes some common NTFS problems. **ntfsfix is NOT a Linux version of chkdsk.**  It only repairs some  fundamental  NTFS inconsistencies,  resets  the  NTFS  journal file and schedules an NTFS consistency check for the first boot into Windows.

> **scruffyeagle said:**
> I found the ntfsprogs program, but didn't find ntfsfix & ntfsclone

ntfsprogs includes ntfsfix and ntfsclone, among others.

[quote="ntfsprogs package description"]This is a set of tools targeted for people interested in working
with the NTFS support in the Linux kernel and using it.  The
following utilities are included:

ntfsfix - Fix common filesystem errors and force Windows to check NTFS.

mkntfs - Format a partition with an NTFS filesystem, optionally bootable.

ntfsinfo - Show some information about an NTFS partition or one of the
files or directories within it.

ntfslabel - Show, or set, an NTFS partition's volume label.

ntfsresize - Resize an NTFS partition without losing data.

ntfsundelete - Recover deleted files from an NTFS partition.

ntfscluster - Locate the owner of any given sector or cluster on an NTFS
partition.

ntfscat - Concatenate files and print them on the standard output
(without mounting the partition).

ntfsls - List directory contents on an NTFS filesystem (without
mounting).

ntfscp - Overwrite files on an NTFS partition.

ntfsclone - Efficiently clone an NTFS filesystem or a part of it.

ntfsmount - Mount an NTFS partition from user-space using libntfs and FUSE.

ntfsdecrypt - Decrypt NTFS-encrypted files (NOT INCLUDED).

ntfscmp - Compare two NTFS volumes and tell the differences.[/quote]

---

### Post by Gone fishing on 2011-08-06
> ntfsfix is a utility that fixes some common NTFS problems. ntfsfix is NOT a Linux version of chkdsk. It only repairs some fundamental NTFS inconsistencies, resets the NTFS journal file and schedules an NTFS consistency check for the first boot into Windows. 

So it should be able to fix a basic unclean dismount assuming there is no substantial damage? It was alway a pain if you needed chkdsk just to fix an unclean dismount because the power went out.

---

### Post by scruffyeagle on 2011-08-06
> **coffeecat said:**
> <snipped>

ntfsprogs includes ntfsfix and ntfsclone, among others.

Thanks, coffeecat! I hadn't dug into it yet; simply came back here to reply & inquire. Now, I know! ("Enquiring minds", & all that...)

By the way, that's a great tagline on your post. Doctors used to have to swear to it. And now, they don't. But, moral people attempt to adhere to it anyway.

---

### Post by coffeecat on 2011-08-06
> **Gone fishing said:**
> So it should be able to fix a basic unclean dismount assuming there is no substantial damage?

I don't know. I've certainly come across threads where the OP cannot mount an ntfs filesystem in Ubuntu because it is unclean following an unclean dismount. The error message in such a case always tells the user to use chkdsk. Common advice is only to use NTFS in internal partitions or external drives if you have access to Windows in case you need chkdsk. That being said, I agree with everyone who says that is safe to write to NTFS from Ubuntu. But, for myself, I would choose to use Windows chkdsk if one of my NTFS partitions was damaged.

---

### Post by scorp123 on 2011-08-06
If you have serious damage on your NTFS drive it would be better to use Windows-native programs to repair the damage.

I always keep a Windows live CD around just for these cases. URL for instructions on how to build your own Windows live CD:
[http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/)

---

