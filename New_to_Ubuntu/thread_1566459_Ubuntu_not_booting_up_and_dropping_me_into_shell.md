---
title: "Ubuntu not booting up and dropping me into shell"
date: 2010-09-02
forum: New to Ubuntu
---

### Post by parham-d on 2010-09-02
Hi,

I have already searched on this forum and have been unable to find a solution that works for me. Basically, the same thing you have already guessed happens: I get told something Pardon me for not copying the exact message, I am blind and there is no one to read it for me right now, and the font size in that screen is quite small, so that doesn't help either.

The only difference with the other threads I have read that this "alert!" line is the very first one, there is nothing about waiting for the root and etc. Let me tell you when this happened:

like, alert! [a long string here] does not exist. Dropping back to shell.

I was reading a book with Orca(the Gnome screen reader)and the computer hanged. I didn't want to just reboot, since alt+ctrl+f1 didn't work either, so I held down alt, pressed print screen, r, e, u, and when that didn't work, I practically pressed i, o, and etc,to make it work. When this too failed, I held down alt+ctrl,pressed printscreen, then released it (still holding alt+ctrl) and pressed the same keys(r, e, i, s, u,b, i, etc). When I rebooted, I got presented with this (cursed!)window.

I have tried changing the,

set root = ("hd1,5");

to everything I could think of (I don't remember which partition my Ubuntu installation is on).

Any ideas?

Thanks!

---

### Post by Jammerton on 2010-09-02
(caveman solution)......back up your files with puppy linux or your ubuntu live cd.....reinstall, reconfigure....if it happens again then you have a real problem

you'll save time this way I bet.

---

### Post by parham-d on 2010-09-02
Hi,

The problem is, the live CD won't boot either!:)

---

### Post by parham-d on 2010-09-03
So, any way I could fix this, given that, for some reason, the bootable CDs won't boot?

And, I can boot into Windows on the same machine, just not Ubuntu.

---

### Post by bcbc on 2010-09-03
Have you tried booting a previous kernel? Or do you not even see the grub menu?

EDIT:
i guess you have to see the grub menu, if you can boot windows, just not Ubuntu.

---

### Post by linux18 on 2010-09-03
try typing xinit at the prompt

---

### Post by parham-d on 2010-09-04
> **linux18 said:**
> try typing xinit at the prompt
Hi,

I typed xinit, and got told by /bin/sh that nothing called "xinit" is found. Oh, and I've also found that the alert goes something like,

"Alert! The disk/object [the string here] does not exist."

and then the line that talks about dropping me back to shell.

---

### Post by Silent Warrior on 2010-09-04
How's about startx, then, rather than xinit? They're supposed to be one and the same, I've been told, so, if one exists, you should be able to find the other, but...
Another thing to try might be fsck-ing your HD. If hd(1,5) is your boot partition, I guess the invocation would be something like 'fsck /dev/sda4', unless the partition-enumeration is the same as in GRUB (meaning 'fsck /dev/sda5' instead of 4). Can you boot into recovery-mode?

---

### Post by parham-d on 2010-09-05
Hi,

I'll try 'startx'. However, I thought hd(1,5) means sdb5? I read somewhere that hd(0,1) would be sda1, so probably if you change it to 1, it'd be sdb1.

I'll tell you the results soon!

Thanks.

---

### Post by parham-d on 2010-09-05
I tried 'startx' and the same thing happens. It appears Busybox has only enough to fix problems, no startx or anything. It's probably a low-level Unix shell. I didn't try fsck since no one is here to read the output for me, but I'll try that, too, later on.

Oh, and to maybe aid the solving of this problem, this happened after I upgraded to the latest Linux headers and image. Also, once before when I had left my computer and later came back, Linux didn't recognize my root device any more, and whatever I typed, I was told that the file /usr/bin/[whatever] does not exist and such. Restarting fixed it at the time, but maybe somehow my harddrive is not being normal or something?

---

### Post by linux18 on 2010-09-05
-connect to an ethernet
chroot / 
dhclient eth0
apt-get update && apt-get clean && apt-get -f install && apt-get --fix-broken upgrade

---

### Post by Legendary_Bibo on 2010-09-05
If live CDs aren't working then either the CD isn't working or the CD drive isn't

---

### Post by cogier on 2010-09-05
Try this: -

At the Terminal prompt type FSCK and press enter. If you get "don't do this" type warnings you will need to unmount the drive first.

When the command has finished reboot the computer.

---

### Post by bcbc on 2010-09-05
> **parham-d said:**
> ...It appears Busybox has only enough to fix problems, no startx or anything. 

If you're at a busybox prompt, likely you have this problem.
 [http://ubuntuforums.org/showthread.php?t=1565714&highlight=busybox](http://ubuntuforums.org/showthread.php?t=1565714&highlight=busybox)

Solution is to boot a previous kernel, or to use live CD to rebuild the initrd.img.

---

### Post by parham-d on 2010-09-06
Hi,

I tried the solution given in this link, but that didn't work. I have kernels 2.6.3-24, 22, and 21. The 24 one comes up with just "Alert! /dev/disk/by-uuid/[UUID] odes not exist.". The 22 claims there is a missing module, something like /proc/[something?]. The 21 kernel says that it gave up waiting for the root device. When I tried the 22 kernel again, this time it told me that no init was found and I should specify init = bootargs, but I hadn't done anything at all!

When I insert in the Linux CD/DVD, Grub comes up.

Oh, and when I held down shift the first time so I could enter Grub, since then I have to enter a password (my Ubuntu password I think) so Grub window would appear. Any way I could remove this?

Thankies!

---

### Post by parham-d on 2010-09-07
Bump? :)

---

### Post by parham-d on 2010-09-07
Hi,

I have also tried the help command. It seems there is very few commands that could help me there. I have also verified that my disk has the uuid set correctly, by checking it with blkid.

Any other ideas? Let me remind you that I'm using kernel 2.6.3-24, I'm being dropped into Busybox with this prompt (I've tried booting to previous kernels (I.E. 2.6.3-22 and 2.6.3-21), but that didn't work. The disk works fine though, I can boot into Windows 7 on the same disk, but a different partition):

initramfs

Thanks!

---

### Post by Chewable on 2010-09-09
I got stuck on the **initramfs** shell as well after a reboot (it times out looking for the boot drive and dumps out). Trying to get to recovery mode made no difference except that I could choose which drive to boot from - the result was the same. I couldn't edit anything, move any files, or mount any drives. 

Booting from a Live CD didn't fare any better either -- everything was read-only and I couldn't mount any other drives to dump files that I hadn't already backed up (like my bookmarks which I regularly cram stuff in).

So perusing the forums, someone said **type "exit" to see if it can resume booting**. Well, odd as it seems, it _worked_ at least for me. Now I'm religiously backing up stuff again and plan for a reinstall fairly soon. I wonder if I can replicate what caused the bootfail...

Thanks to gaodan for the solution. ):P

---

