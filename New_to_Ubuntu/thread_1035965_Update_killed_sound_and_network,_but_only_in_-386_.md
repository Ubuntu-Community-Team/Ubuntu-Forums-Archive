---
title: "Update killed sound and network, but only in -386 version not in -generic"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by susanw on 2009-01-10
I updated, installing all the updates given by Update manager a few days ago, was then asked to restart my system which I did. I now find wireless network doesn't work and neither does the sound.

What I don't understand is that when I choose a different option in the Grub menu - 'Ubuntu 8.04 kernel 2.6.24-23-generic' instead of '....-386' it all works. Can anyone tell the the difference please? I am assuming that the Grub menu, which now has about 10 different Ubuntu choices available, allows boot from many different versions of 8.04, from different updates I have done?

When I run the -386 version the network manager tool says it's state is unconnected, which it isn't in -generic version. This thus seems a simple? thing to change but I don't know how. Also sound (I'm running Alsa) still has unknown problems.

I would like a way to 'undo' this update and wonder if dpkg could help in this case but don't know where to start. Also I don't know what effect changing one version would do to the other version and don't want to kill the one working version I have!

This is also posted as [http://ubuntuforums.org/showthread.php?t=1035900](http://ubuntuforums.org/showthread.php?t=1035900) but I thought this forum might be more useful.

Thank you for reading.

---

### Post by jojo21 on 2009-01-12
I have the exact same problem. No sound or wireless after the update last Thursday. If not for this cheap second laptop I fixed up with XP a few weeks ago I would have gone mental. After all, I can't search for help without internet.

---

### Post by susanw on 2009-01-12
jojo21,

Have you tried choosing a different version in the grub menu? I just wondered if your computer had the same pattern mine does - working in the -generic version but not the -386 version. Finding it was fantastic as, as you say, finding help without the internet is really hard!

---

### Post by jojo21 on 2009-01-12
> **susanw said:**
> jojo21,

Have you tried choosing a different version in the grub menu? I just wondered if your computer had the same pattern mine does - working in the -generic version but not the -386 version. Finding it was fantastic as, as you say, finding help without the internet is really hard!

Yes, I did the same thing you did. When I go back to the same version of the kernel as you it works fine, but obviously its quite annoying as everytime you reboot it boots to the new one unless you're standing there to press Esc and choose the new one.

I also made a thread, but noones replied yet.

---

### Post by susanw on 2009-01-12
Kind of glad that someone had the same experience. Have you had any luck undoing the install? I can't figure out how to find what installs have been made - where they are stored and such like, a log would do. I wouldn't mind manually going through synaptic package manager and reverted to previous versions of packages but can't find one.

Also I've been trying to find out what the difference is between -386 and -generic to no avail.

s

---

### Post by navidson on 2009-01-12
i too am having very similiar issues. no sound...slow internet. i however reinstalled off a disk i got with my laptop so the options of kernel to choose from in the menu are not that many. i posted a thread as well so far no luck with how to get the kernel before the last update and how to make it stick when i reboot.

---

### Post by jojo21 on 2009-01-12
> **susanw said:**
> Kind of glad that someone had the same experience. Have you had any luck undoing the install? I can't figure out how to find what installs have been made - where they are stored and such like, a log would do. I wouldn't mind manually going through synaptic package manager and reverted to previous versions of packages but can't find one.

Also I've been trying to find out what the difference is between -386 and -generic to no avail.

s
I'm still a Linux newbie, I've no idea how to undo any updates. I don't understand why there's no option to set it to automatically boot the generic instead of the i386 version though. Right now I'm just glad I can go back to the older version at all. Pity there's nothing like System Restore for Linux though.

---

### Post by susanw on 2009-01-12
Navidson,

sorry you've had the same problem, it's infuriating me so I imagine it must be you too. Do you have any other kernel versions that work? - I ask because this puts a twist on my idea that the -generic version of the kernel I'm using is from the same update.




jojo21,

I bet there is a way of choosing grub to automatically choose the version you want .... but I don't know it yet!

I too want the easy system restore, I've wanted it loads of times during my use of linux, especially when I've killed the touchpad, mouse, sound, video playing ability screen resolution, .... etc.!! I've experimented with system backup programs and saved xorg files but to no clear end yet.

---

### Post by 73ckn797 on 2009-01-12
You would need to provide the info in grub in order for someone to help. If there is a specific kernel that does work you can make that the default.

To provide a copy of the last section of your grub menu.lst you will need to do one of 2 things.

1. Under Places/Computer, go to File System. Then select /boot/grub/menu.lst. to open with text editor. Do not fear, opening it this way will not allow you to save any changes you may intentionally or accidentally make.

Look for the section at the bottom similar to this:

```
## ## End Default Options ##

title        Ubuntu 32bit 8.10, kernel 2.6.27-9-generic
root        (hd1,0)
uuid        33b41abc-de92-4925-aeb3-815844a1cf66
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=33b41abc-de92-4925-aeb3-815844a1cf66 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-9-generic
quiet

title        Ubuntu 32bit 8.10, kernel 2.6.27-9-generic (recovery mode)
root        (hd1,0)
uuid        33b41abc-de92-4925-aeb3-815844a1cf66
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=33b41abc-de92-4925-aeb3-815844a1cf66 ro  single
initrd        /boot/initrd.img-2.6.27-9-generic

title        Ubuntu 32bit 8.10, memtest86+
root        (hd1,0)
uuid        33b41abc-de92-4925-aeb3-815844a1cf66
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems: Intrepid Ibez 64bit & MS Windows XP
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Ubuntu 64bit 8.10, kernel 2.6.27-9-generic (on /dev/sdb1)
root        (hd2,0)
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=55b390fb-cc36-4d8b-91c6-fc1ac0af0766 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-9-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Ubuntu 64bit 8.10, kernel 2.6.27-9-generic (recovery mode) (on /dev/sdb1)
root        (hd2,0)
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=55b390fb-cc36-4d8b-91c6-fc1ac0af0766 ro single 
initrd        /boot/initrd.img-2.6.27-9-generic
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Ubuntu 64bit 8.10, memtest86+ (on /dev/sdb1)
root        (hd2,0)
kernel        /boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title        Microsoft Windows XP Home Edition sp3
root        (hd0,0)
savedefault
makeactive
chainloader    +1
```Copy that section and post it in a reply. Remember to also highlight the info once you paste it in the reply and click on the "#" option on the reply menu bar. That will make it appear  like what I have shown you. The above are my grub choices, your's would be different but similar.

Make note of which kernel is the good one.

Step #2 will follow if needed.

---

### Post by 73ckn797 on 2009-01-12
You can also go to System/Administration/Synaptic Package Manager. Click on File/History and view what updates have been installed. It would also show programs you may have installed. That will at least let you see what has been installed. I do not know immediately how to un-do updates but if you will search the forums you ought to find the info you need. I know, I have seen similar questions relating to your issue.

---

### Post by jojo21 on 2009-01-12
Here it is:

```
## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-23-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-386 root=UUID=34b56014-ae7b-4956-a900-db3261a0841e ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-386
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-23-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-386 root=UUID=34b56014-ae7b-4956-a900-db3261a0841e ro single
initrd		/boot/initrd.img-2.6.24-23-386

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=34b56014-ae7b-4956-a900-db3261a0841e ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=34b56014-ae7b-4956-a900-db3261a0841e ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=34b56014-ae7b-4956-a900-db3261a0841e ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=34b56014-ae7b-4956-a900-db3261a0841e ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, kernel 2.6.24-21-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-386 root=UUID=34b56014-ae7b-4956-a900-db3261a0841e ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-386
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-386 root=UUID=34b56014-ae7b-4956-a900-db3261a0841e ro single
initrd		/boot/initrd.img-2.6.24-21-386

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=34b56014-ae7b-4956-a900-db3261a0841e ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=34b56014-ae7b-4956-a900-db3261a0841e ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=34b56014-ae7b-4956-a900-db3261a0841e ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=34b56014-ae7b-4956-a900-db3261a0841e ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-18-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-386 root=UUID=34b56014-ae7b-4956-a900-db3261a0841e ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-386
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-18-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-386 root=UUID=34b56014-ae7b-4956-a900-db3261a0841e ro single
initrd		/boot/initrd.img-2.6.24-18-386

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=34b56014-ae7b-4956-a900-db3261a0841e ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=34b56014-ae7b-4956-a900-db3261a0841e ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-386 root=UUID=34b56014-ae7b-4956-a900-db3261a0841e ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-386
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-386 root=UUID=34b56014-ae7b-4956-a900-db3261a0841e ro single
initrd		/boot/initrd.img-2.6.24-16-386

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=34b56014-ae7b-4956-a900-db3261a0841e ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=34b56014-ae7b-4956-a900-db3261a0841e ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

The one that works for both Susan and I is 2.6.24-23-generic, but we have to manually select it as the default boot is 386.

Thanks.

---

### Post by WitchCraft on 2009-01-12
That looks like a sudden driver problem...

Now probably an update installed a new kernel.

That means that usually your sound and network drivers do no longer work.

For sound, you need to recompile the latest ALSA drivers.

For network, you need to run:
```

lspci | grep "Ethernet controller"
lspci | grep "Network controller"

```

02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)


This tells you your hardware, you then have to search with google for the appropriate drivers...

since your new kernel has been added to grub, **and the old is there, too (not just a coincidence, you see why now)**, boot into generic, search and download there, then boot in 386 and install the new drivers.
Afterwards it will run flawlessly.

See
[http://ubuntuforums.org/showthread.php?t=638146](http://ubuntuforums.org/showthread.php?t=638146)
for closer information on how to do that.
[SIZE="7"]
**!PLEASE! don't mess with your configuration files [COLOR="Red"](for heaven's sake)[/COLOR], you need to install the latest drivers.**[/SIZE]

---

### Post by navidson on 2009-01-13
this is the information i was told to get in one of the earlier posts.  i have read through so many threads my brain feels fried and nothing even the simplest of steps seems coherent. 

## ## End Default Options ##

splashimage=(hd0,2)/boot/grub/splash.xpm.gz

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=b669f247-7d40-4239-8633-a71186925d2b ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=b669f247-7d40-4239-8633-a71186925d2b ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=b669f247-7d40-4239-8633-a71186925d2b ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=b669f247-7d40-4239-8633-a71186925d2b ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


the sound works on the 2.6.24-16 generic one but i don't know how to make it so i don't have to manually get it to boot from it each time...i'm beginning to feel there are no simple solutions to some of these linux problems. perhaps my computer knowledge is that slim that what should be simple isn't....i truly do not want to spend money on an xp disk...i'd rather get things working on linux but the time i'm spending is becoming ridiculous...thanks for any help given...

---

### Post by 73ckn797 on 2009-01-13
> **navidson said:**
> 
title        Ubuntu 8.04.1, kernel 2.6.24-23-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=b669f247-7d40-4239-8633-a71186925d2b ro quiet splash
initrd        /boot/initrd.img-2.6.24-23-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-23-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=b669f247-7d40-4239-8633-a71186925d2b ro single
initrd        /boot/initrd.img-2.6.24-23-generic

title        Ubuntu 8.04.1, kernel 2.6.24-16-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=b669f247-7d40-4239-8633-a71186925d2b ro quiet splash
initrd        /boot/initrd.img-2.6.24-16-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=b669f247-7d40-4239-8633-a71186925d2b ro single
initrd        /boot/initrd.img-2.6.24-16-generic

title        Ubuntu 8.04.1, memtest86+
root        (hd0,2)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


As a temporary fix, so you can boot into the kernel that you have sound with, you will have to make a small edit to the "menu.lst" file to make the "16" kernel boot by default. It sounds like the menu displays and you have to manually select it, this will work until you can follow other measures to fix the latest kernel sound issue.

Make a copy of the menu.lst prior to editing in case something goes wrong.

Open terminal and enter:
```
gksudo gedit /boot/grub/menu.lst
```It will prompt you for your password.

The "menu.lst" will open in text editor but will allow changes that can be saved.

At the very top of the file you will see the following:
```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

```The "0" at the end is the default selection written by grub. Looking at your boot order, you want to change the "0" to "2". That will make the "16" kernel the default boot selection. Save the file and reboot to see if it works. You may have to tweak the number but I doubt it. I boot with a number "4" because the version of Ubuntu that I use, the 64bit, is the 5th in the grub menu boot order. Do not be confused here. The boot order begins with "0" as the first one. Each section in the boot order that is a paragraph counts as one selection.

Try that and let me know how it goes.

You could also cut and paste the selections into a different order in grub (the info you provided before) but the edit above is easier.

---

### Post by navidson on 2009-01-13
Thank you so much 73ckn797  i know it doesn't completely make the newest kernel a dream but i now have sound and it loads from that older kernel...you are a saint. i have been having issues and i've been able to put up with them but the no sound thing....that disheartened me...do you think that is something they would fix in the updates or is manual fixing just something i am going to have to learn? either way i'm very grateful and as i become more linux literate i'm sure my comfort level and understanding will increase...until now i've been all about the point and click...i'm trying not to give up on linux though haha...maybe i'll take a course or something...

---

### Post by 73ckn797 on 2009-01-14
> **navidson said:**
> Thank you so much 73ckn797  i know it doesn't completely make the newest kernel a dream but i now have sound and it loads from that older kernel...you are a saint. i have been having issues and i've been able to put up with them but the no sound thing....that disheartened me...do you think that is something they would fix in the updates or is manual fixing just something i am going to have to learn? either way i'm very grateful and as i become more linux literate i'm sure my comfort level and understanding will increase...until now i've been all about the point and click...i'm trying not to give up on linux though haha...maybe i'll take a course or something...


I am not familiar with the -386 kernel you use so I do not know what to tell you to fix the sound. I have had many updates where the kernel was replaced but have never seen the one you have. Is your's a derivative flavor of Ubuntu?

---

### Post by WitchCraft on 2009-01-14
> **73ckn797 said:**
> i am not familiar with the -386 kernel you use so i do not know what to tell you to fix the sound. I have had many updates where the kernel was replaced but have never seen the one you have. Is your's a derivative flavor of ubuntu?

he - can - fix - the - sound - and - drivers - by - installing - the - latest - drivers. The - old -ones - are - broken - because - the - new -kernel - has - different - interfaces - and - offsets.

---

### Post by 73ckn797 on 2009-01-14
> **WitchCraft said:**
> he - can - fix - the - sound - and - drivers - by - installing - the - latest - drivers. The - old -ones - are - broken - because - the - new -kernel - has - different - interfaces - and - offsets.


They were wanting to be able to default into the earlier kernel. [SIZE=7]
[/SIZE]What is with all of the dashes?

---

### Post by navidson on 2009-01-14
> **WitchCraft said:**
> he - can - fix - the - sound - and - drivers - by - installing - the - latest - drivers. The - old -ones - are - broken - because - the - new -kernel - has - different - interfaces - and - offsets.

i did read the link but there were some steps in that installation guide that was supposed to come up that confused me with some things i didn't understand and at this point i have spent so much time trying to read and fix things instead of working. so I just wanted to get it working and i'll go back when my mind has recovered from the onslaught of computer talk. there are some significantly smarter people on here than me...you have all been a great help and the only reason i still have linux on my computer.  things are working as i need them to be for now...


in regards to what kind of kernel i have. i ordered my computer with linux on it and they gave me an ubuntu 8.04 full time supported and i ran into some problems so i reinstalled and started new...so far i'm still having slow download speeds but i'm not gonna lie i'm pretty tired and apparently there is a person in the town i'm in who will help me set things up smoothly.........i hope....i'm going to bookmark this page though so i can learn some of these things..thanks so much again.

---

### Post by WitchCraft on 2009-01-14
> **73ckn797 said:**
> They were wanting to be able to default into the earlier kernel.


Yes, but because the drivers on the new one didn't work.
Even though it works, you can't always reside with the old, for the same reason why you don't drive around in an old-timer if you have to travel far and fast (and secure).


> 
What is with all of the dashes?

It was all capitalized. 

He should not mess up his system by editing his config files, they are ok. And it's not a solution to boot into the old kernel by default. Grub takes the latest kernel for default, and offers you the choice to use old versions for a reason. He should fix his system, not keep using an old kernel.

Of course, **temporarely **using the old kernel is ok.

---

### Post by 73ckn797 on 2009-01-14
> **WitchCraft said:**
> He should not mess up his system by editing his config files, they are ok. And it's not a solution to boot into the old kernel by default. Grub takes the latest kernel for default, and offers you the choice to use old versions for a reason. He should fix his system, not keep using an old kernel.

Of course, **temporarely **using the old kernel is ok.

I agree but they wanted what I gave them. As an auto tech I fully understand the need to fix things right. I am also not going to avoid situations that need a temp fix, though prefer correct remedies be made. It is better in the long run.

---

### Post by navidson on 2009-01-14
I do plan on fixing things. I just need a break from it...just temporary. all the fixes and computer lingo got a bit much for a newbie and eventually little, even simple things made sense...i'm going to go back to things again just in a few days. it seems as though even some step by step instructions are not step by step enough and after reading so much nothing seems to process...i'm hopefully going to be able to meet with someone here where i live who supposedly is quite the linux guy so hopefully he'll be able to help me learn some things i'm not processing. i like the one on one where i can ask immediate questions...an actual chat would work too i guess.

---

