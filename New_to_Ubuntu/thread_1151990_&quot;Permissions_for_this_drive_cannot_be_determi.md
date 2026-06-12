---
title: "&quot;Permissions for this drive cannot be determined&quot;"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by newbpanda on 2009-05-07
Long post! Question on the bottom.

**I have a DELL dual core E520 which is dual-booted with Windows XP and Ubuntu.** My Windows portion of the computer is currently virused up. :( You see I let AVG 7 go for awhile without renewing my license (about three months). It wasn't until the middle of the third month that I realized something I'd forgotten: Grisoft (makers of AVG) accepts Paypal. Yada yada.

Needless to say I can't even get Windows XP to boot... anyway my problem is that the C: drive (called "61.9GB Media" by Ubuntu) won't let me delete files on it. (My C: drive is where I have XP installed.)

**A gump pops up telling me it is READ ONLY mounted.**

**I checked the Permissions of the drive & it said this: "Permissions for this drive cannot be determined."**

My question is: How do I instruct Ubuntu to mount the C: drive (aka "61.9GB Media") as Read/ Write?

---

### Post by Niniel on 2009-05-07
This happens to me occasionally; it seems to come from an improper shutdown of Windows. In other words, all you may need to do is boot up Windows and do a proper shutdown.

---

### Post by newbpanda on 2009-05-07
Haha. The thing is when I boot XP, it goes to the login screen, right? I push the button for the login I wanna use...

Then it says "Logging out" beneath the button and returns to the login screen without bothering to go to my Windows desktop for that login. Uh, actually I mean I can't get past the login screen.

And the computer also refuses to go into Safe Mode for XP. Uh, you're supposed to press & hold F8 when that screen with "Windows" pops up on the screen with the scroll bar, right?

---

### Post by lukeinvancouver on 2009-05-07
> Needless to say I can't even get Windows XP to boot.

Maybe this will turn out to be a dumb question or maybe you just forgot: Did you not make a start-up disks for AVG because if you have a set (and forgot) you can repair/start Windows.

I'm just trying to help.

:)

---

### Post by newbpanda on 2009-05-07
> **lukeinvancouver said:**
> Maybe this will turn out to be a dumb question or maybe you just forgot: Did you not make a start-up disks for AVG because if you have a set (and forgot) you can repair/start Windows.

I'm just trying to help.

:)



Argh! No. :( I didn't know I could do that.

I have AVG 8 on my older computer for some reason but the newer computer (the one I'm having problems with) uses AVG 7 so I guess I can't use AV6 8 to make a start up disk for AVG 7...

EDIT: I'm looking at the menu for AVG 8 on my older computer... there is no option to make a boot disk. :(

---

### Post by lukeinvancouver on 2009-05-07
> **newbpanda said:**
>  I'm looking at the menu for AVG 8 on my older computer... there is no option to make a boot disk. :(

I'm using AVG 7 Free on my old Win 98 clunker. (The only reason I keep that lousy OS is because I have some nifty audio software that came with my Soundblaster Value Plus and which will not work with anything else.) I'm sure I have some emergency startup disk somewhere for that machine. It gave me the choice when I installed it and it has saved my butt several times.

Alas, that's no help to you.

Do you really need Win XP? If not you could get out of the pickle by installing Ubuntu on a partition taking up the whole drive.

Btw, if you reinstall XP DISABLE restore because it will reinstall the virus over and over again. Yeah, the wonderful world of Microsoft! (I'm so glad I'm in the process of getting away from it ... or almost.)

Good luck is the only thing I can add.

---

### Post by lukeinvancouver on 2009-05-07
Or install Ubuntu and leave another partition large enough to install XP on. I know it's a pain in the neck to install XP. But ....

I know next to nothing about Linux. So maybe you should not rush into reinstalling XP because somebody else might be able to help you solve the problem without all that hassle.

Good luck!

---

### Post by newbpanda on 2009-05-09
I get paranoid sometimes... not going to say what I get paranoid about, but sometimes I think the some of the less reputable manufacturers of computer virus protection software actually MAKE viruses just to increase their business potential! :D

At this moment I have ZERO interest in subscribing to Cedega (just saying that before someone tries to advertise it in a PM to me) and have even less interest in backing up my hard drive. I have an external drive I can use... but right now I want to delete a bunch of superfluous files from my computer... which I can't because I don't have "permission" to delete stuff from my own computer.

---

### Post by mkvnmtr on 2009-05-09
If you are only going to delete some files the Ubuntu live disk should let you do that. If you plan to delete the whole system learn how to repair grub before you do it.

---

### Post by Niniel on 2009-05-11
No, it won't. The NTFS partitions are flagged as "dirty" due to improper shutdown of Windows, so in order to not damage anything, the ntfs-3g driver won't access them.
[Here's a guide]("http://www.swerdna.net.au/linhowtontfs.html") that gives instructions on how to deal with such a situation.
You may also want to read [this]("http://forums.opensuse.org/install-boot-login/408510-how-access-windows-ntfs-partitions-2.html"), and [this]("http://ubuntuforums.org/archive/index.php/t-661051.html"). 

Actually, I suggest you try the last link first, then the second one, and only if none of those work try the first one with the "force" option.

---

### Post by newbpanda on 2009-05-11
> **lukeinvancouver said:**
> 

Btw, if you reinstall XP DISABLE restore because it will reinstall the virus over and over again. Yeah, the wonderful world of Microsoft! (I'm so glad I'm in the process of getting away from it ... or almost.)

Good luck is the only thing I can add.

How do you do that?

Anyhow, I've gotten fed up with old installation the way it was. I bought a virtual machine for Ubuntu that runs Windows as a VM or whatever you call that. My hard drive has a primary bootable partition for Ubuntu & that's it. No more stupid dual booting for me. 

I cost thirty bucks, but it was worth it to simplify things. I also backed up my old files. Hrm. They probably are still infected with a virus... well I'll scan everything before I put it on the VM. 

Any precautions I should take? (Notice I'm not plugging the name of the VM because they ain't paying me to!)

EGAD!!!!


[I][B]From the official webpage:
Does (the virtual machine) run the latest Windows games?

No, (the virtual machine) is not a gaming platform and does not support the latest 3D/DirectX games.[/B][/I]

I shouldn't be surprised, I guess.

---

