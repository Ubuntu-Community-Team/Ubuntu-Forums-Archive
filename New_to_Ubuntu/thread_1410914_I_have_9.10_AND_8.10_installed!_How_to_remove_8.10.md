---
title: "I have 9.10 AND 8.10 installed! How to remove 8.10??"
date: 2010-02-19
forum: New to Ubuntu
---

### Post by pacmanic91 on 2010-02-19
Hello,

I'm kind of new to Ubuntu. Installed 8.10 a while ago and forgot about it, but wanted back in the game so installed 9.10. When GRUB loads on bootup, it takes forever to load the list... I think this may be because i have Windows XP, Ubuntu 8.10 and Ubuntu 9.10 all installed. 

To make GRUB load quicker and to save some space, could anyone tell me how to remove 8.10 without affecting 9.10?

8.10 and 9.10 are both installed on the same partition... i think. Both on an external harddrive.

Thankyou very much and i'd really appreciate your help.

Tom

---

### Post by eltama on 2010-02-19
The time that GRUB takes to load does not depend on the number of systems you have. If it is taking too long it's probably related to the fact that you have the grub list in the external drive.

You cannot have Ubuntu 8.10 and 9.10 in the same partition, in the same way that you cannot have 2 Windows in the same partition. If both are working they must be on separate partitions.

To remove Ubuntu 8.10 I suggest you boot with the livecd and use gparted (System->Administration->GParted) to remove the partition and expand the one of Ubuntu 9.10.

Before removing any partition triple-check that you know what you are doing or you may end up deleting your Windows or 9.10.
Also I suggest that in gparted you do one step at the time. First delete the partition, and once it is finished expand the other partitions or create a new one if you want.

---

### Post by pacmanic91 on 2010-02-21
Hi,

Sorry for the late reply.

I booted with the disc, and am now on gparted. However it looks very confusing:(, and have no idea which partition ubuntu 8.10 may be installed on...

Here's what it looks like:

(/dev/sdb) is my external hardrive, a 'mybook'.

Thanks very much for your help:D

---

### Post by pacmanic91 on 2010-02-21
I have also decided to install 9.10 on the spare partition on /dev/sda therefore should make GRUB load quicker once i've removed ubuntu 8 and 9 off my external drive.

---

### Post by JiuJitsu500 on 2010-02-21
dev/sdb1 is your storage, the FAT32 filesystem isn't linux... but you might have known that and I don't mean to point out the obvious...

dev/sdb5 (sdb6 as it's swap) looks like an install with a bunch of other stuff in it, of either OS... and dev/sdb7 looks like the one you meant to use for 9.10, and is only a little used...

If you installed 9.10 later, then 7 and 8 should be them, but they're not the same partition, you would have had to create them somehow... how did you choose to install it? And by default I want to say 9.10 uses ext4.... 8.10 uses ext3... (someone correct me if I'm wrong).

Oh, if 7 and 8 are them, and you delete the swap space and the space for 8.10, you can't get the sdb5 back for the linux, it'll be unallocated until you put it with the FAT32 (it can't combine unallocated space to the left of the OS)... and the stuff at the end will be more swap space unless you combine it to the other swap, then shrink swappiness to see normalcy there.

---

### Post by JiuJitsu500 on 2010-02-21
> **pacmanic91 said:**
> I have also decided to install 9.10 on the spare partition on /dev/sda therefore should make GRUB load quicker once i've removed ubuntu 8 and 9 off my external drive.

If you have another OS, like windows or Mac, doing this.... you will have to sort out the mess sometimes (others have no issue choosing OS) at boot-up.... GRUB fights with boot.ini and other boot files sometimes...

---

### Post by pacmanic91 on 2010-02-21
Thanks for the reply.

Ok first thing, i have no idea what a swap is! Yes, i am very new to ubuntu and partition stuff. :confused:

You also say that 7 and 8 should be them, do you mean 9.10 is probably installed on 7 and 8? While 8.10 is using 5 and 6? I guess that would make sense... 
Are you sure that 8.10 is on 'ext3' and '/dev/sdb6/', like i said i don't understand what a linux swap is.

I have really screwed my external drive up haven't I? :(

And yes, i knew fat32 couldn't be linux, thanks for pointing it out anyway.
On '/dev/sda/' i have windows installed on the 'C' partition and absolutely nothing on the 'D' partition, therefore i was considering installing 9.10 on D, so on boot up GRUB should just load 9.10 and Windows direct from '/dev/sda/', and nothing from my External Drive (once i've removed ubuntu from it)
Saying that, if i just delete all of '/dev/sdb2/' (on the screenshot), that should just wipe ubuntu from my external hardrive together?

Thanks:)

---

### Post by JiuJitsu500 on 2010-02-21
> **pacmanic91 said:**
> Thanks for the reply.

Ok first thing, i have no idea what a swap is! Yes, i am very new to ubuntu and partition stuff. :confused:

You also say that 7 and 8 should be them, do you mean 9.10 is probably installed on 7 and 8? While 8.10 is using 5 and 6? I guess that would make sense... 
Are you sure that 8.10 is on 'ext3' and '/dev/sdb6/', like i said i don't understand what a linux swap is.

I have really screwed my external drive up haven't I? :(


And yes, i knew fat32 couldn't be linux, thanks for pointing it out anyway.
On '/dev/sda/' i have windows installed on the 'C' partition and absolutely nothing on the 'D' partition, therefore i was considering installing 9.10 on D, so on boot up GRUB should just load 9.10 and Windows direct from '/dev/sda/', and nothing from my External Drive (once i've removed ubuntu from it
Saying that, if i just delete all of '/dev/sdb2/' (on the screenshot), that should just wipe ubuntu from my external hardrive together?

Thanks:)

Don't worry or excuse yourself, linux is harder to learn, but infinately more useful to me (and not to mention, virus free and free of charge :) )

Swap is like RAM, but instead of using your RAM (and thus conserving computer power), it used your hard drives' "swap space" it sets... and if you have over 2GB of RAM, and are a power user from hell, you don't need it, or should shrink it a whole lot. Default is 60, so 10 is cool, but I use 5 just to have some. Shrinking Swap allows the computer to use more RAM, and thus, improve performance (SSD (solid state drives, eg USB stick, RAM, etc) is 100 or so times faster than optical drives).

Ext3 is the file system format that linux uses in some distrobutions, newer versions use ext4, so that's why I am almost positive your 9.10 is on the 7 and 8 partitions.

And no, don't worry, your external is fine, and easily fix-able whenever you're ready to clear it out of linux and get it all back to storage space :) After of course, if you do what you said and put Karmic on your internal drive... and even if not, it's still okay...

A "D" partition in Windows is usually recovery, so unless you're planning on wiping windows out, don't mess with it (but I would suggest as a linux fan, do it, then virtualize windows if you do need it, like for my stupid Zune I have it).

If you delete everything after the FAT32 you will remove linux, it'll just become unallocated space. Then you can extend the FAT32 partition to fill up the whole hard drive and you'll be totally bueno (though a lot of time the disk utility will say you have bad sectors... don't worry, usually that's just a sign of "age").

Whatever you're ready and willing to do, we're here :) Just know though if you've never used linux, it will impress you like nothing else can, and piss you off genuinely sometimes (until you learn it's an easy fix, like I do all the time, and happens 99% of the time I've found). But in the end, the ends do a whole hell of a lot more than justify the means.

---

### Post by Paddy Landau on 2010-02-21
> **pacmanic91 said:**
> I have also decided to install 9.10 on the spare partition on /dev/sda therefore should make GRUB load quicker once i've removed ubuntu 8 and 9 off my external drive.
In this case...

[LIST]
[*]Delete all the partitions sdb5, 6, 7, 8 and 2. (You'll have to right-click sdb6 and 8 and choose "Swapoff" before it will allow you to delete them.) **Warning: Back up any data from the external drive, first!**
[*]Expand your sdb1 partition, if you want, or create a new sdb partition, perhaps as NTFS.
[*]Install Ubuntu on your spare sda partition. It will reinstall grub for you. **Warnings: Back up any data from the spare partition, first. Check -- and recheck -- that you don't accidentally overwrite your Windows partition. Back up any important data from your Windows partition, just in case.**
[/LIST]

---

### Post by JiuJitsu500 on 2010-02-21
Definately should have added to make backups.... for sure :)

---

### Post by pacmanic91 on 2010-02-21
JiuJitsu and Paddy,

Thankyou both so so much for helping me out with this. I pretty certain i know what to do now. This morning i had no idea about any of this, so thankyou for letting me pick your brains. :D

What you said about the SWAPs i found interesting (JiuJitsu) , i have 3gb of RAM so ill definately minimize the swap space. I'll back up everything and start this mini project tonight.
Only had Ubuntu 9.10 for a few days and i'm absolutely loving it. So fast and light, and havent had a single hang, crash or error!! Also it's free, and seems much easier to get free advice from people who know what theyre talking about, instead of reffering you to some troubleshoot program!

So once again thankyou very much for your help, i really appreciate it.

Kind regards,

Tom

---

### Post by JiuJitsu500 on 2010-02-21
Have you tried Kubuntu at all? Most people find it a little easier to start with, but I like GNOME so I stay with Ubuntu... Fedora, Mandriva, SUSE, there's a lot of distros out there but I think Ubuntu is the most well-rounded and easiest to go with for near everything... plus if you don't like you can always change anything... Try Kubuntu though to see if you like the KDE desktop better than GNOME... you never know :)

Glad to help man and a quick tip... before posting anything new, (just for future reference :) ) try google or searching the forums, answers are probably already there for you. There's a lot of great forums and sites too, [linuxquestions.org]("http://www.linuxquestions.org") is another of my favorites.

---

### Post by Paddy Landau on 2010-02-21
> **pacmanic91 said:**
> ... ill definately minimize the swap space.
If you ever want to hibernate, you need at least as much swap space as your RAM. 3Gb is hardly a lot in today's world, so make your swap a full 3Gb to match your RAM.

> **pacmanic91 said:**
> ... seems much easier to get free advice from people who know what theyre talking about
Well, I don't always know what I'm talking about, but I do my best! But you're right, this Ubuntu forum is the possibly the best and friendliest I've ever joined!

---

### Post by lotharmat on 2010-02-21
It is probably the friendliest forum since

[www.friendly-friends.fr/friend](www.friendly-friends.fr/friend)

---

### Post by Paddy Landau on 2010-02-21
> **lotharmat said:**
> It is probably the friendliest forum since [www.friendly-friends.fr/friend]("http://www.friendly-friends.fr/friend")
"Address Not Found"

---

