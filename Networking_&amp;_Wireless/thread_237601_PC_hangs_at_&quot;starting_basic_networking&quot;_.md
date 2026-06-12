---
title: "PC hangs at &quot;starting basic networking&quot; on startup after kernel upgrade."
date: 2006-08-16
forum: Networking &amp; Wireless
---

### Post by dyoung66 on 2006-08-16
Howdy all,

Everytime I start my PC it hangs at "starting basic networking" (at the splash screen).
This problem has only started to happen since I updated my kernel from 2.6.15.25-686 (which worked fine) to 2.6.15.26-686 which causes the freeze. 

Has anyone else had a similar problem or know of a fix??

Cheers.

---

### Post by lenux- on 2006-08-16
Same here..

---

### Post by mpvano on 2006-08-16
Try interrupting the boot process by

1. Hitting escape at the Grub countdown prompt to get a grub menu

2. Selecting the first kernel entry and typing "e"

3. Selecting the first line of the boot stanza and typing "e" again

3. Editing out the words "quiet" and "splash" from that boot entry and then hitting return

4. Typing "b"


If I got that all correctly explained (!) It should let you boot once in verbose mode so that you can see exactly where it's hanging up when you boot.

Unfortunately, the fancy boot screen only displays the high points of the process. There are lots more steps in between the ones it displays.

Once you can see what the last line it printed before hanging up is, someone here can help.

Also, does it continue the boot process if you type control-C when it's hung up?

Mario

---

### Post by dyoung66 on 2006-08-17
Hi Mario,
 thanks for the help, I'm about to give it a try now, it does proceed when I hit ctrl-C, but then hangs at the next step...

I'll let you know how it goes, thanks.

---

### Post by dyoung66 on 2006-08-17
ok, I followed the instructions above to get more verbose output at startup , although I got extra information, it just stopped at "starting basic networking"(no error message info was displayed). 

I then hit Ctrl-C and it went to "loading hardware drivers" and then froze. Once again it didnt give me any extra error message.

Any other suggestions?

(maybe unrelated)
I booted into a previous kernel and checked my boot log for any errors, but it said the file for my boot log didn't exist. Can I just create a text file for this boot log to work??

---

### Post by mpvano on 2006-08-17
Unfortunately, I don't think there's currently a way to get the kind of bootlog your looking for.

Tell me about your pc and your networking hardware. Do you have any devices at all whose drivers weren't automaticlaly installed by Ubuntu? Examples are proprietary video drivers (like ATI's or nVidia's), smartmodem or winmodem drivers, custom ndiswrapper installations built from source, custom network card drivers built from source, etc?

If so, you do know that anything built from source has to be reinstalled after every kernel update, don't you?

I noticed a change in the device system after the last kernel update myself. It seems to have changed the way some network devices are named. I had to lock the names down using iftab entries to get my network configuration working reliably again. Normally this won't cause a crash, however - only long delays at startup while things time out. You might want to see if you can tell if any network drivers were preloaded (as occurs if they are listed in /etc/modules) and if they got the right names (if the machines not totally frozen). Is there something else more complicated going on in your networking?

Also, what version is the kernel that works and the one that doesn't? I spent a long time earlier this week troubleshooting for someone who didn't tell me he was trying to use a kernel from breezy (which won't always work properly).

Mario

---

### Post by dyoung66 on 2006-08-18
I think I've got an idea now from those (big)hints you've given, I was using ndiswrapper a while ago, but replaced it with the bcm43xx native wireless driver, which worked well. I was sure I had removed ndiswrapper, both the package and other files.

But evidently this is not the case, as I just located a bunch of ndiswrapper files :

/home/dyoung/wireless/ndiswrapper-utils_1.8-0ubuntu2_i386.deb
/lib/modules/2.6.15-23-386/kernel/drivers/net/ndiswrapper
/lib/modules/2.6.15-23-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
/lib/modules/2.6.15-25-386/kernel/drivers/net/ndiswrapper
/lib/modules/2.6.15-25-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
/lib/modules/2.6.15-25-686/kernel/drivers/net/ndiswrapper
/lib/modules/2.6.15-25-686/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
/lib/modules/2.6.15-26-686/kernel/drivers/net/ndiswrapper
/lib/modules/2.6.15-26-686/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
/usr/src/linux-headers-2.6.15-26-686/include/config/ndiswrapper
/usr/src/linux-headers-2.6.15-26-686/include/config/ndiswrapper/module.h
/usr/src/linux-headers-2.6.15-26/include/config/ndiswrapper.h
/usr/src/linux-headers-2.6.15-26/drivers/net/ndiswrapper
/usr/src/linux-headers-2.6.15-26/drivers/net/ndiswrapper/Makefile
/usr/src/linux-headers-2.6.15-25-686/include/config/ndiswrapper
/usr/src/linux-headers-2.6.15-25-686/include/config/ndiswrapper/module.h
/usr/src/linux-headers-2.6.15-25/include/config/ndiswrapper.h
/usr/src/linux-headers-2.6.15-25/drivers/net/ndiswrapper
/usr/src/linux-headers-2.6.15-25/drivers/net/ndiswrapper/Makefile

My 2.6.15-25-686 kernel works fine.
The 2.6.15-26-686 kernel is when it hangs.

I thought by installing the linux-headers and linux 686 packages I would not have to recompile source after a kernel upgrade, but I could be wrong(?).

I'm thinking I now need to remove the 2.6.15-26
kernel, remove ndiswrapper thoroughly (I followed a tute on this but obviously it didnt work(or I made a mistake)), and reinstall the 2.6.15-26 kernel.

This is the only thing I can think of that would break my networking. Or Ive gone off on a tangent...

Thanks for taking the time to help, I'll get onto this tonight and let you know the outcome.

---

### Post by dyoung66 on 2006-08-18
I deleted all ndiswrapper files, and reinstalled the 2.6.15.26-686 kernel, but that didnt solve anything.

Also, some ndiswrapper files are back again. ??

Totally lost now. Might just stay with the 2.6.15.25-686 kernel.

---

### Post by mpvano on 2006-08-19
I think you've lost me as well.

Try giving it a rest for a few days and then coming back at it fresh.

You might want to review what you've "removed". One problem with FAQ instructions and forum advice is that it's quite hard sometimes for anyone else to tell what exactly you have done later.

When you do get back to it, you also might want to note that while some parts of the boot process are selective about which version's device files are used, other parts are always the same.

I'd try preventing ndiswrapper from loading (by removing what you think is loading it) to confirm that it's the problem.

By the way - I've had terrible troubleshooting problems with drivers sometimes due to a stupid thing I often forget - the backup file created by editors! Many text editors create a backup file by renaming the old file and leaving it in the same directory as the edited file. Unfortunately most of the debian/ubuntu enumerated directories used at startup don't look at the file extension at all. This means that if you have a backup file in any of the ".d" style enumerated directories, it may ALSO be read and used as well as the edited version. The order is sometimes unpredictable depending on the names of the files and the algorithm the editor uses for renaming. The bottom line is: MAKE SURE YOU REMOVE ANY BACKUP FILES RESULTING FROM EDITS!! Failure to do so will definitely make you old before your time!

I'll keep my eye on the thread in case you need more help if you get back to it, but at this point some fresh insight might be useful.

Mario

---

