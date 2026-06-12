---
title: "How do I restart a killed process, or reinstall just root?"
date: 2010-03-15
forum: New to Ubuntu
---

### Post by JayRobert on 2010-03-15
I'm running Ubuntu Studio 9.10 Karmic.  While setting up a recording from a new tape to USB device, I was testing different settings in Audacity.  The program froze, and nothing would respond - couldn't get it to force exit, either.

Did a hard reboot, worked OK, but then when I tried to start up Audacity again, got an error message that a copy was already running.  Tried rebooting again a couple of times, same message.  Foolishly decided to try to kill the process that was still running (ala common Wiindows procedure), but stopped something else, apparently.  Lost all commands and the bar.

After much pressing of every F key combination I could think of, I did another hard reboot.  Now it won't launch.  I get the grub screen.  I have encrypted directories.  It runs through the usual password prompts to unlock the directories, but then freezes on the splash screen.

Any solution besides reinstalling everything?  I have separate partitions for /boot, swap, and / (these three on an SSD, swap is encrypted, /boot and / are not encrypted).  I also  have partitions for /home, /tmp, /usr, /var (all encrypted), as well as /srv and /opt (not encrypted) on a RAID5 array.

If it involves using the recovery boot prompt, I will need detailed instructions - got to a command line (was not able to successfully mount all  the encrypted drives, btw), but no idea what to do at that point.

Is there a way to figure out what process is missing and restart it?  I don't remember exactly which process I killed that caused the problem - bad habit of a recovering Windows user.

Or can I just reinstall the program files in / without affecting the other directories, in hopes of reinstalling whatever process is missing?  I do know that  / is located at sda5.

Also, if it matters, this is a dual-boot with XP, which is running fine - it's how I'm able to post this.

Any help is greatly appreciated!

---

### Post by nothingspecial on 2010-03-15
You seem to have gone into partitioning/encrypting overkill.

I`m struggling with this one.

You could try just reinstalling / to your / partition but I don`t know wether it will create a new /var /tmp /usr partitions in the new /.


Maybe if you specify them in the install partitioning dialogue.

I`d like to know, so post back.

Btw, why did you encrypt swap?????

---

### Post by JayRobert on 2010-03-15
Yes, I'll admit to partitioning / encryption overkill.  I'll even admit to spending time on crypto sites just for fun.

Honestly, I did it just because I could.  And maybe I'm paranoid.  Anyway, I encrypted swap to prevent anything that would be normally encrypted from getting swapped out of memory overflow into the clear.

That you can (relatively) easily build encrypted RAID LVM partitions is one of the most appealing things about Ubuntu, frankly.  If not for that, I might have spent the extra time to build my own kernel with Gentoo.

So how do I reinstall just / ?  I have an install iso that I downloaded - it works, it's what I used for the original install.  Won't it ask me about partitions again?

---

### Post by nothingspecial on 2010-03-16
From my vague recollections of the ubuntu installer, you are going to have to specify each partition manually.

When it get`s to the partitioning bit, choose manual advanced. Then select each partition and specify it`s mount point and file system.

[SIZE="5"][COLOR="Red"]BUT[/COLOR][/SIZE]

only check the "format partition" box for your root partition.

That`s what I would do, however, I`m not sure if that would work with your system.

It goes without saying that you will have to identify which /dev/sd?? is which first.

---

### Post by audiomick on 2010-03-16
> **nothingspecial said:**
> From my vague recollections of the ubuntu installer, you are going to have to specify each partition manually.

When it get`s to the partitioning bit, choose manual advanced. Then select each partition and specify it`s mount point and file system.

[SIZE=5][COLOR=Red]BUT[/COLOR][/SIZE]

only check the "format partition" box for your root partition.

That`s what I would do, however, I`m not sure if that would work with your system.

It goes without saying that you will have to identify which /dev/sd?? is which first.
Correct. 
I have no idea about the encryption, or raid if it comes to that, but as far as it goes, any directory that is on it's own partition can be re-mounted during a fresh install.
You just have to specify partition, mount point, and **not format.**

Good luck!!

PS: I would reconsider the encrypted swap. I understand your logic, but swap is supposed to be fast, isn't it?

---

### Post by JayRobert on 2010-03-16
Thanks to both of you for your replies.  I will try again later this evening and let you know how it goes.

As for swap, I think it encrypts whatever is there only when it is unmounted (i.e., when shutting down or logging off).  I could be very wrong about that assumption.  In any event, I haven't noticed any performance impact.

---

### Post by JayRobert on 2010-03-17
Well, I ended up doing a fresh install of the entire thing.  The installer wouldn't let me mount the encrypted directories without reformatting them, so I left those unmounted, thinking I would fix it once I got the basic system up and running, but the installer froze at "Setting up accounts and passwords" 26% - twice.

Also, I remember now why I encrypted swap.  The installer *requires* an encrypted swap if you mount other encrypted directories, stating that otherwise unencrpyted passwords might be swapped out to the clear.  It actually won't let you encrypt any other directory if your swap is either encrypted or unmounted (with swapoff) - but the point is that having an unencrypted swap would likely defeat the purpose of encrypting the other directories.

Thanks again!

---

