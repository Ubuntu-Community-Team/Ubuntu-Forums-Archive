---
title: "complete newbie to multibooting linux"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by jonnny_j22 on 2010-05-13
Hi all,

I'm a recent linux convert and I've been getting on with my ubuntu pretty wel i think, I managed (with much help) to get all the bugs i had after install sorted and have picked up a fair bit and now it's my standard OS.

Before I started using ubuntu, i downloaded live cds from fedora, linux mint, mandriva and open suse. I went with ubuntu because it was the most welcoming as a novice. now I'm all settled, I'd quite like to install the others just to learn a bit more about linux, and also not have to keep using the cds as this gets a bit annoying.

Prior to going linux, i had used online tutorials to get windows 7, xp and os x triple booting on my computer, and i'd quite like to keep them (especially as getting that osx disc installed was a nightmare). As i understand it this means that my new distros will have to go into the extended partition ubuntu made itself under logical partitions. This is the part I'm ok at and have used gparted to create four aditional logical ext4 partitions as i read online that the new distros can share the swap partition?

My problem comes when i try to install the new distro(s), I feel i'm hitting a knowledge wall that is probably quite basic, but that i can't seem to find the answer to (possibly because it's so basic). When I installed ubuntu, I came across a step i've never been asked before... 'select a mount point for this instilation', so that got 'googled' and i tryed again having been told to mount it at '/'. the instilation ran fine and we've got on ever since. So when I poped in the mandriva disc and it said 'select a mount point' I thought 'i know this' and selected '/' only to be told that dev/sda5 is mounted there'.. ah. This time googling said to go with /home, so i did that and it installed, and it'ts grub loader over wrote ubuntu's. Which was doubly annoying as it now doesn't recognise ubuntu or mac.

I think therefore this is a two part quesion:
1)could someone please explain to me, or point me in the direction of an idiot-proof guid to mount points? I keep comming up with sites about sharing home between distros and as far as i know i don't want to do this, i just want to add a couple of extra distros to act as independant os?

2)Help with setting up grub. It seems that the routes are either install the new distros,then re-install ubuntu as it's grub loader will then recognise everything (result of googling) or install them, run live cd and edit the grub loader through code. That sounds more likely to me (simply because it sounds more difficult and easy fixes seldom work) but the online guides i have found have been way over my head and presumed quite a bit of extra knowledge leading me into an endless search tree.

If anyone can help, or point me in the direction of 'multiple distros for dummies' it'd be a huge help! Thank you in advance!

---

### Post by moep on 2010-05-13
Can you boot Ubuntu using your current setup? If so, what version of Ubuntu do you have installed?

10.04 uses grub2 which can automatically detect the various operating systems on your available disk(s) and sets up the grub entries accordingly. You can do so by typing ```
sudo update-grub
``` in the terminal.

If one of the other distributions overwrote your ubuntu bootloader, consider following this guide to restore it:

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by jonnny_j22 on 2010-05-13
Cheers for this, I have 10.04 so that looks the way to go there, and much less stressful than i thought!. Any ideas about where I should be mounting instilations?

---

### Post by jonnny_j22 on 2010-05-13
Update! typically now i pot it, i find out what happened. It was pretty stupid of me, but i figure ill put it up incase any other newbies fall foul of this!

when you install linux, to put the os in a partition, you use mount point '/'  you can then put other 'bits' of it, like home directory in other partitions. now i knew this when i installed ubuntu. but where i got caught out was when installing the new distro

It'd been 3 weeks and it was no longer fresh in my mind, not that it's a defence, now i realised what i did, this was dumb! when mandriva gets to the partition selection, it put the little '/' in dev/sda5 because it was the first partition formatted 'linux style'. so when I looked at it i thought 'thats normal, when i was in gparted a min ago,dev/sda5 had a'/' in it.... *because that's where ubuntu was installed*. So when i selected dev/sda7 which is where i wanted it to go, the message 'you already have '/' mounted in dev/sda5 had nothing to do with ubuntu, i just couldnt install into two partitions... dah

then i google, get confused and set dev/sda7 to /home.... guessed what i did yet?

yup i installed mandriva over ubuntu, which probably explains why the mandriva bootloader couldn't find ubuntu!

fortunatly i had all my data on a shared partition, and have been able to laugh at this one, but i thought id put it up for newbies just as a warning - RTFQ!

still big thanks to moep, one less thing to mess up!

---

### Post by fly-by-night on 2010-05-13
Hi, if you have at least 2GB of memory you might want to take a look at Virtualbox.  You can test (and use) all the OSes you want within Ubuntu and don't run the risk of messing up the grub etc.

[www.virtualbox.org](www.virtualbox.org)

---

