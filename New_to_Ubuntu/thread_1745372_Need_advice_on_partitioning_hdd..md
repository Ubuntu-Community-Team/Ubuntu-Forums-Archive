---
title: "Need advice on partitioning hdd."
date: 2011-05-01
forum: New to Ubuntu
---

### Post by StarZtorm on 2011-05-01
So i have this master plan for partitioning my harddrive. The one in question is a 74.4 GB raptor disc and i want to install both Ubuntu and windows xp.. These will be in a dual boot setup. 

Now, to the plan! 40 gb goes to xp, 30 gb goes to Ubuntu, and then theres (i have 2 gb ram) 2.5 gb to swap (since people say u should have double the ram for swap, or the same as ram, or a little more than ram. So im going for compensation here) 

From what i have learnt by installing only ubuntu on my Notebook, i find that when letting ubuntu choose the partitioning it set off 1.1 GB to swap (makes sence because it only has 1 GB of ram) and theres an extended partition of 1.1 GB, described as a "container for logical partitions". Frankly, i cant tell if this is doing anything useful other than being there for later usage. Or can it be root?

Anyway, back to the raptor disc. If i take the 40GB and format it as NTFS, then windows should find this partition right? (Im installing xp after installing Ubuntu) Then when i format the 30GB to ext4 for Ubuntu, and the 2.5 for swap. Am i forgetting something then? Will root and grub go to the same partition as ubuntu? And, when i install xp to the 40 gb partition, will grub update itself and let me dual boot? 

And last but not least, where can i find a history of my posts in the ubuntuforums?


Alot of text, i know. Sorry, but bear with me.

---

### Post by Quackers on 2011-05-01
Normally it causes less problems to install XP before Ubuntu. This is because both systems fight for the mbr of the drive. If XP is last in you need to re-install grub after. If Grub is last in you can just update grub to pick up the Windows Loader.
Your partititioning sounds ok.

To find all your threads or all your posts go to the first buff coloured bar near the top of the page and click on "search", (not "search this forum") and the choices are obvious.

---

### Post by MollyWop on 2011-05-01
> **Quackers said:**
> Normally it causes less problems to install XP before Ubuntu. This is because both systems fight for the mbr of the drive. If XP is last in you need to re-install grub after. If Grub is last in you can just update grub to pick up the Windows Loader.
Your partititioning sounds ok.

To find all your threads or all your posts go to the first buff coloured bar near the top of the page and click on "search", (not "search this forum") and the choices are obvious.
Or if you want the better looking MBR, you can install easyBCD in windows and add Ubuntu to the MBR.

---

### Post by StarZtorm on 2011-05-01
Thanks Quackers :) MollyWop, MBR?

---

### Post by Hedgehog1 on 2011-05-01
MBR (**M**aster **B**oot **R**ecord), the partition table method we have to use so Windows will be happy.

***The Hedge***


[IMG]http://img97.imageshack.us/img97/8240/deathparionshishdd.png[/IMG]

---

### Post by wizard10000 on 2011-05-01
> **MollyWop said:**
> Or if you want the better looking MBR, you can install easyBCD in windows and add Ubuntu to the MBR.

EasyBCD is the way I'd go but it doesn't work in Windows XP, only Vista and later.  What you want for NT/2k/XP is bootpart

[http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm)

or to just do it manually with dd.

I don't build dual boot machines any more but my personal preference is to use a Windows bootloader to chainload grub rather than the other way around - as this allows you to reinstall either OS without disturbing the other one.  You do have to **remember to install grub on the first Linux partition rather than on the MBR** but it works pretty well.

On partitioning - your swap partition needs to be slightly larger than installed RAM *if you intend to hibernate the machine*, otherwise swap partition size needs to at least equal swap space used.

Let's say for example you have a 64-bit machine with 8GB RAM.  If you never suspend to disk you most likely won't need an 8GB swap partition.  On my own desktop PC (6GB RAM) I've never seen the swap partition used at all, but swap size is 6.1GB just in case I ever decide to hibernate the machine.

Also, I'd give some thought to creating a partition for a home directory.

cheers -

---

### Post by srs5694 on 2011-05-01
> **Hedgehog1 said:**
> MBR (**M**aster **B**oot **R**ecord), the partition table method we have to use so Windows will be happy.

***The Hedge***


[IMG]http://img97.imageshack.us/img97/8240/deathparionshishdd.png[/IMG]

ROTFL! The cartoonist for that is Samuel Marcus, who attended the same college I did ([Oberlin College,](http://www.oberlin.edu) in northern Ohio), but a few years later. I picked up a poster with his Death cartoons at one of my reunions. The original caption for that one, BTW, was "Death uninstalls Windows." You can see them all at [Death Gets a Website.](http://www.deathgetsawebsite.com)

I now return you to your regularly-scheduled discussion....

---

### Post by StarZtorm on 2011-05-01
Thanks alot for all the input here guys! appreciate it! will get to work on the computer tommorrow hopefully.

---

