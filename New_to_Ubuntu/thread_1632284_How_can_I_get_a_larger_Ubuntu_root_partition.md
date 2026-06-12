---
title: "How can I get a larger Ubuntu root partition?"
date: 2010-11-27
forum: New to Ubuntu
---

### Post by bthomson100 on 2010-11-27
I have an Acer Aspire 3104 laptop running Windows Vista and Ubuntu 10.4. I installed Ubuntu using something called Wubi.exe from Windows. It installed Ubuntu and offers a boot menu that give preference (1st place in a menu) to Windows Vista, then Ubuntu.

The hard drive is about 120 GB, with partition C using about 51 GB and partition D using about 51 GB. I don't know where the rest is, probably in some invisible boot partitions.

It appears that Ubuntu is running on the D partition of my hard drive. When I type "df" in a Ubuntu terminal/console, I get a listing for two sda3 partitions. See below.

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/loop0             6797452   6023124    429036  94% /
none                    734628       348    734280   1% /dev
none                    739000       256    738744   1% /dev/shm
none                    739000       324    738676   1% /var/run
none                    739000         0    739000   0% /var/lock
none                    739000         0    739000   0% /lib/init/rw
/dev/sda3             53849876  28565636  25284240  54% /host
/dev/sda3             53849876  28565636  25284240  54% /media/sda3
/dev/sda2             54155112  48370428   5784684  90% /media/sda2
/dev/sdb1            244196000 205916972  38279028  85% /media/FreeAgent Drive
/dev/sdc1              3917024   1807536   2109488  47% /media/DC3A-A808

I have 21 gigabytes free on partition D when I look at it under Windows. However, when running Ubuntu, it tells me that my root directory only has 419 MG free. This isn't much and on a number of occasions, Ubuntu on booting has given me an "error" message saying my root drive disk space is very low and I should delete some files. At one point, it actually went to almost 0 space on the root drive and Ubuntu wouldn't boot at all. I solved that problem after 2 days and MUCH grief via other threads in this forum.

Now I'd like to give more space to my Ubuntu root drive so I don't have to face the possibility of a debilitating crash if someone sends me a big file via email. Eventually (sooner than later I hope), I plan to delete Windows. But that depends on my getting Ubuntu to recognize my laptop's internal microphone so I can use Skype. That's a different subject however, than what I hope to get from this thread.

There are probably programmes that I don't need in Ubuntu that I could delete. There are backups and a 1.7 GB Windows pagefile.sys file on drive D that I could get rid of as they are backed up up on external drives and DVDs.

I'm very new to Linux but used to be quite familiar with DOS back in the 80s and 90s.

Can anyone give me some tips on adding say 10 GB to my Ubuntu root partition? Simple explanations that don't assume I know what all Linux commands mean or do would be appreciated.

Bob Thomson
Ottawa, Canada

---

### Post by charlie_b on 2010-11-27
The starting point for your problem will be to use gparted, I think. Try running sudo gparted in a terminal to see if it's installed. If not, it's easy enough to install via the synaptic package manager.
I have used it myself to resize partitions, it works very well. However - I've only used it for Linux partitions.
I don't know what issues may be involved with using it on Windows partitions, so you will need someone more familiar than I am to guide you in that regard.

---

### Post by wilee-nilee on 2010-11-27
> **charlie_b said:**
> The starting point for your problem will be to use gparted, I think. Try running sudo gparted in a terminal to see if it's installed. If not, it's easy enough to install via the synaptic package manager.
I have used it myself to resize partitions, it works very well. However - I've only used it for Linux partitions.
I don't know what issues may be involved with using it on Windows partitions, so you will need someone more familiar than I am to guide you in that regard.
[B]
No this is a wubi install, there is no partition to change with gparted.
[/B]

Actually OP your stuck you have your HD to full already, and I believe you can't expand the wubi, but wait fro more info on this part I may be incorrect on the expansion part.

Do yourself a favor get a external and dump some of that stuff on the HD to it then dual boot with either moving the wubi to a regular partition, there is a tutorial on this on the forum, or just make a dual boot set up the old fashioned way partition and install.

---

