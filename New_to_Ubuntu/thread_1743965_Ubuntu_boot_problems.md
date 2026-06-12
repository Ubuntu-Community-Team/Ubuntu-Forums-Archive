---
title: "Ubuntu boot problems"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by djm777 on 2011-04-29
Greetings guys i'm new to forums and fairly new to ubuntu and dont know any terminal commands etc, i'm cheesed of as i had UBUNTU 10.10 INSTALLED on my dual booted pc however i started it up then upgraded to UBUNTU 11.04 via update manager NOW THIS FREAKING THING IS telling me :

ININIT:UNDEVMONITOR MAIN PROCESS (432) KILLED BY TERM SIGNAL
the disk drive for/ is not ready yet or present
Continue to wait; or press S to skip mounting or M for manual recovery

i have about 320 gigs of info dear to me on this partition  and would hate to loose it any professional or general help please tx angelo
:confused:

---

### Post by scott-ian on 2011-04-29
Do you have an external hard drive you can backup your files onto?  If so, it would be as simple as booting off the live CD, copying the files, and then you can do a clean install.  Otherwise you might be able to recover your system... but that will not be easy, at least as far as I know.  Hopefully I'm wrong and it is as simple as editing the file that tells where drives are mounted.  If only I could remember what that was called...

---

### Post by cariboo on 2011-04-29
I had a Seagate 750GiB drive give me the same message the other day, it is toast, and on it's way to Seagate for yet another replacement. That being said, you may be able to access the drive from a Live CD. Boot from the Live CD (it doesn't matter what version) and once you are at the desktop open a terminal and type:

```
sudo fdisk -l
```

to determine what drive label it has, once you have found this out, you can mount it manually using the following command:

```
sudo mount /dev/sdxX /mnt
```

where /dev/sdxX = your drive.

Once you have the drive mounted, you can access it from Nautilus. You may need to run Nautilus as root, so press alt-F2 and type:

```
gksudo nautilus
```

---

