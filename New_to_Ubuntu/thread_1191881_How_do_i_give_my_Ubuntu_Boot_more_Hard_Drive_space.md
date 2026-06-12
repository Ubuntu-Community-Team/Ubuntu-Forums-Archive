---
title: "How do i give my Ubuntu Boot more Hard Drive space?"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by SamR09 on 2009-06-19
Title really explains it all, i currently have 11.5GB of space on my Ubuntu boot, and i think i actually have about 70GB of space left on my 250GB HD, so how can i allow Ubuntu to use up more space?

---

### Post by philinux on 2009-06-19
You need to boot use your livecd to alter the partitions, using the app gparted. Shrink one expand the another. Not without risk and it takes a long time for the machine to perform.

Backup, backup, backup any important stuff before you attempt this.

---

### Post by SamR09 on 2009-06-19
Which option to i select? 

I put in my disk, rebooted my computer, pressed F12 whilst starting, booted the CD, and then i was at a loss for which option to choose. 

Which one?

---

### Post by starcraft.man on 2009-06-19
When you log in to the live CD open a terminal. Applications > Accessories > Terminal. Then type in "sudo aptitude install gparted". Unfortunately due to space constraints, gparted isn't installed by default on Ubuntu.

I alternatively recommend the [gparted live CD]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779") Just download the ISO and burn it to a CD or DVD and then boot to it. It comes with a bare bones environment with gparted.

Either path will lead to the gparted program. If you install it on a live CD, simply go to system > administration > gparted. If you boot the live CD, your in it at the start. After that you will see the gui and can select any hard drive or partition and manipulate as you like. Right clicking brings up most options, rest are in the menus.

I give you fair warning. BACK UP! You never know when something bad might happen during partition editing, normally nothing goes wrong but there's always the exception.

Any other questions, post back.

---

### Post by Idefix82 on 2009-06-19
> **SamR09 said:**
> Title really explains it all, i currently have 11.5GB of space on my Ubuntu boot, and i think i actually have about 70GB of space left on my 250GB HD, so how can i allow Ubuntu to use up more space?

To add to what others have said: if the other OS on the drive is Windows and you are going to resize it then before you do the resizing, defragment the windows partition a couple of times. If the space that you are adding to Ubuntu is unallocated space, then you don't need to worry about any of that.

---

### Post by SamR09 on 2009-06-19
I don't get it, the liveCD is the CD you use to install Ubuntu? And when you mean login to liveCD it means i should open a session without changing any of my settings or whatever it is?

---

### Post by starcraft.man on 2009-06-19
> **SamR09 said:**
> I don't get it, the liveCD is the CD you use to install Ubuntu? And when you mean login to liveCD it means i should open a session without changing any of my settings or whatever it is?

Yes, the liveCD is the one you used to install. I am assuming you installed using the desktop x86 or 64 version. When you boot up the disk, you should see the "try ubuntu without changing..." select that option and it logs you into a live session. That's what we are talking about. The session is loaded into RAM and so won't affect your system unless you specifically modify the hard drives by using gparted. Once your logged in, just follow the steps I outlined in the terminal and open gparted. It's pretty intuitive after that, just resize the free diskspace into the partition you want to expand. 

If you have any trouble in the live session, just boot up firefox and post back here.

---

### Post by SamR09 on 2009-06-19
Right, im on the LiveCD now, and i've got up to opening GPARTED, anyhow, it says i  need Root permissions to do anything. 


How do i give myself root permissions? 

(Sorry for all these stupid questions.)

---

### Post by SamR09 on 2009-06-19
Bumpety Bump.

---

### Post by starcraft.man on 2009-06-19
> **SamR09 said:**
> Right, im on the LiveCD now, and i've got up to opening GPARTED, anyhow, it says i  need Root permissions to do anything. 


How do i give myself root permissions? 

(Sorry for all these stupid questions.)

No question is stupid my friend! Questions lead to knowledge, and knowledge is the key to the universe... ok, maybe that's a bit over the top. :)

Anyway, by default, I'm pretty sure there's no password for the root account. To open gparted with root priveledges just go back to the terminal and type in "gksudo gparted". Alternatively, you can push alt + F2 to get the run dialog, it basically can run any simple command like "gksudo gparted", I use it when I just need one or two commands run quick.

I forgot to mention this before, without root privileges gparted can't really function.

---

### Post by SamR09 on 2009-06-19
Now i've got this screen.



[IMG]http://i39.tinypic.com/dq3fpw.png[/IMG]



What do i do on it? I'm confused.

---

### Post by Idefix82 on 2009-06-19
Have you got several hard drives in the computer? The one you are looking at now doesn't have a Ubuntu installation. In the top right corner of this window is a drop down box where you can switch between the hard drives (at the moment it says "/dev/sda (232.83 GiB)"). Choose the drive on which Ubuntu is installed, you will recognise the partition as being formatted as ext3 (probably) rather than ntfs.

---

### Post by SamR09 on 2009-06-19
Also, just so you know, the only reason i'm doing this is so i can install WoW on my Ubuntu boot instead of loading it from my Vista boot in /host 

I think it'll run better, because at the moment, it's glitchy and laggy. I haven't even got into the select a character screen yet.

---

### Post by SamR09 on 2009-06-19
No, i have both Ubuntu and Vista installed on this Hard Drive, i don't have any others.

---

### Post by starcraft.man on 2009-06-19
[http://gparted.sourceforge.net/documentation.php]("http://gparted.sourceforge.net/documentation.php")

The above link takes you to the partition manual, select general information and then resizing. Use the html links under the UK flag (english). The nice thing is they put pictures for new people like yourself. A quick read will turn you into an expert.

If you have multiple drives, you'll notice in the top right /dev/sda. You can click here and select from your different hard drives. The one you displayed in the picture is completely formatted with ntfs (I assume it's Windows), I assume that isn't the one you installed linux on.

Just curious but you didn't use Wubi to install Linux into Windows did you? If so, this process won't help you. You didn't mention it before so I assumed you installed to hard drive. Best of luck.

And remember, please back up important data on the drive you plan on modifying, I can't be responsible if something goes wrong and data goes poof!

---

### Post by SamR09 on 2009-06-19
I put the disc in my computer while i was on Windows, and i clicked the middle one, it installed, and i get the choice which OS i want to boot when i start my computer. This any help?


EDIT: Tell you what i'll do, i'm just going to Uninstall Ubuntu, go back on my Windows OS, and see what options i have. 


-back soon.

---

### Post by philinux on 2009-06-19
Have you perchance installed ubuntu using the wubi installer? That would explain what gparted is seeing.

---

