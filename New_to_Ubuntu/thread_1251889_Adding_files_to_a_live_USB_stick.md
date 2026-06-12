---
title: "Adding files to a live USB stick"
date: 2009-08-28
forum: New to Ubuntu
---

### Post by darkmast2 on 2009-08-28
Hi all, I would just like to point out I know very little about Ubuntu/Linux in general hence why I'm here.

I won't go into the reason why here but I created a LiveUSB stick with Ubuntu on it to get access to the hdd in a laptop as it wouldn't boot into Vista. I've had success with that and gotten off files that was needed on it.

Now that I've gotten the files off I wanted to try and salvage the laptop, it was dropped while turned on. I download a program called TestDisk and extracted the folder to the LiveUSB stick thinking I could access the program from within Ubuntu but I couldn't find out how to access the USB stick from within Ubunut, not being familiar with commands/locations etc.

If anyone can help I would be really grateful. If you need clarification of anything just let me know and I'll do my best to explain.

---

### Post by Paqman on 2009-08-28
Testdisk is available in the Ubuntu repositories. While you're running from your LiveUSb just go to System > Admin > Synaptic package manager and install it.

Good luck with your data recovery! 

However, if you've had a bigtime head crash on the laptop's hard drive then the easiest thing to do is simply get a new hard drive and slap it in. If you've got the cash you could get a solid-state drive, as they're much more drop-resistant than old-fashioned spinning drives.

---

### Post by darkmast2 on 2009-08-28
> **Paqman said:**
> Testdisk is available in the Ubuntu repositories. While you're running from your LiveUSb just go to System > Admin > Synaptic package manager and install it.

Good luck with your data recovery! 

However, if you've had a bigtime head crash on the laptop's hard drive then the easiest thing to do is simply get a new hard drive and slap it in. If you've got the cash you could get a solid-state drive, as they're much more drop-resistant than old-fashioned spinning drives.

Thanks for the reply.

Is this something that is already in the distro ? or does it go off to a website to download ? I haven't tried connecting it to the internet yet.

It would probably be easier to install a new hdd in the long run but I was hoping to see if I could save the current one first as the laptop belongs to my cousin who is a single mother and doesn't want to splash out on new hardware if it isn't necessary.

The other problem is that although the Vista key is on the bottom of the laptop there was no reinstall discs supplied, the restore data is on a partition on the hard drive i.e. Vista/drivers etc, so I would have to try and source a Vista disc to install the OS and then manually find and install the drivers as the manufacturer would probably charge for sending out a restore disc. There's nothing really valuable or needed left on the hdd so data loss isn't significant.

---

### Post by Paqman on 2009-08-28
> **darkmast2 said:**
> 
Is this something that is already in the distro ? or does it go off to a website to download ? I haven't tried connecting it to the internet yet.


The repositories (or repos) are online software libraries. Downloading from them is the normal (and easiest) way to get software on Linux. So go ahead and connect to the internet from your LiveUSB. Open Synaptic, go to Settings > Repositories, make sure the "Universe" repo is checked, let it reload then search for and install testdisk. Synaptic will install the app and bits and pieces it needs automatically.

New hard drives don't have to be expensive, you can get them off eBay pretty cheaply. Not having the install disks could be a problem though.

---

### Post by LewRockwell on 2009-08-28
> **darkmast2 said:**
> Is this something that is already in the distro ? or does it go off to a website to download ? I haven't tried connecting it to the internet yet.

Synaptic requires internet access to complete this task.

> **darkmast2 said:**
> It would probably be easier to install a new hdd in the long run but I was hoping to see if I could save the current one first as the laptop belongs to my cousin who is a single mother and doesn't want to splash out on new hardware if it isn't necessary.

If hard drive replacement is necessary a used drive can be found for minimal expense.

> **darkmast2 said:**
> The other problem is that although the Vista key is on the bottom of the laptop there was no reinstall discs supplied, the restore data is on a partition on the hard drive i.e. Vista/drivers etc, so I would have to try and source a Vista disc to install the OS and then manually find and install the drivers as the manufacturer would probably charge for sending out a restore disc. There's nothing really valuable or needed left on the hdd so data loss isn't significant.

Some OEMs shipped machines without disks, however if they did so then during the initial usage of the equipment, the operating system would request that the user complete the disk creation utility. This was only available as a one-time recovery-disk-writing-procedure so as to prevent multiple disks from being written.

It should also be noted that disks from other machines will probably not work with other equipment(unless those disks are from a "full-version" stand-alone non-OEM issue of the operating system, perhaps).

What happens / happened when you attempt to boot the machine into Vista normally?

.

---

### Post by darkmast2 on 2009-08-28
> What happens / happened when you attempt to boot the machine into Vista normally?

The boot starts up fine but when it gets to the Windows loading bar it either just sits there with the bar bit going forever or occasionally it will go to a blank screen, it never reaches the desktop.

---

