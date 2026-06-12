---
title: "Freeing Partion Space For New Install"
date: 2011-06-29
forum: New to Ubuntu
---

### Post by rs321 on 2011-06-29
Folks,

I'm want to install 10.04 over 11.04 but I'm only given the options of installing it next to Windows or formatting the entire disk.  It isn't giving me the option to install it in the partition where 11.04 resides, which would cost me half my disk space.  How do I get it to utilize that space?

-Randy

---

### Post by andrewthomas on 2011-06-29
You should also be able to select:

Advanced or manual partitioning.

---

### Post by Elfy on 2011-06-29
Which I think is now called "Something Else"

---

### Post by amjjawad on 2011-06-29
> **rs321 said:**
> Folks,

I'm want to install 10.04 over 11.04 but I'm only given the options of installing it next to Windows or formatting the entire disk.  It isn't giving me the option to install it in the partition where 11.04 resides, which would cost me half my disk space.  How do I get it to utilize that space?

-Randy

If I were you, I would use GParted from LiveCD/USB

System > Administration > GParted

and prepare the HDD "before" installation. Pre-planning is much better IMHO :)

---

### Post by rs321 on 2011-06-30
Folks,

At the beginning of the installation I chose to use the previous partitioning and Ubuntu warned me that changing the partition size would take a lot of time and I couldn't go back  and change it.  I quit the installation at that point because I didn't ask it to change anything.  What gives?

-Randy

---

### Post by dFlyer on 2011-06-30
Start the live cd to a live desktop. Use disk utilities to format your current ext4 partition, than from the live desktop run install.

---

### Post by rs321 on 2011-06-30
Gary,

Thanks for the response, but I'm confused.  By "live" CD do you mean the Ubuntu installation disk?  I didn't see an option for anything other than time zone and keyboard on it at the point I mentioned.  If you mean using Windows disk utilities I can't run the Installation CD from anywhere in Windows.

I'm confused and hate to ask a question that reflects a thorough lack of knowledge but the only thing I understood about what you said was "ext4 partition".  Sorry.

-Randy

---

### Post by dFlyer on 2011-06-30
When you boot the live cd choose try it and boot into live desktop, from there you should be able to start disk utility which will allow you to delete your old ext4 partition that contains 11.04. Than when you click the install icon on the desktop itself. From there you can manual configure your partition by selecting the old partition where 11.04 was installed and install 10.04 or 10.10 the choice is yours.

---

### Post by Alver on 2011-06-30
> **dFlyer said:**
> When you boot the live cd choose try it and boot into live desktop, from there you should be able to start disk utility which will allow you to delete your old ext4 partition that contains 11.04. Than when you click the install icon on the desktop itself. From there you can manual configure your partition by selecting the old partition where 11.04 was installed and install 10.04 or 10.10 the choice is yours.
I'm in the same condition as the thread starter. Although I understand the general rationale behind your explanation I see nothing on the fate of the GRUB or of the MBR in general. How are these influenced when I attempt to delete the existing ext4 partition? 
Thx for a possible reply.

Alver

---

### Post by dFlyer on 2011-06-30
When you reinstall it will update your grub to the new install, It will find windows if you dual boot and then the new linux install.

---

### Post by rs321 on 2011-06-30
Gary,

Okay, got it, thanks.  I missed the part about "try it" and was thinking only of the "install" option.

-Randy

---

### Post by Alver on 2011-06-30
> **dFlyer said:**
> When you reinstall it will update your grub to the new install, It will find windows if you dual boot and then the new linux install.
Thx, it is reasonably clear now. I have indeed a dual boot with W7 64b/U 10.10 64b. When I delete the Linux partition I assume it will produce "unallocated space". Will the install program give me the choice of "Use the largest available free space" (or something along these lines-I'm running a Dutch language version) or will I have to dive into the "Advanced" install settings? This is something I have never attempted before and I dread ending up with an unbootable system. Please forgive my ignorance in these matters.

---

### Post by rs321 on 2011-06-30
Gary,

Did just what you explained and was able to format ext4.  In fact, once it finished the format that partition was already labeled 10.04.2 and the dual mount button was already highlighted.  Smiling that I'd learned something else about Ubuntu I pressed the Install button and the very next thing that happened was Ubuntu started formatting the entire disk.  By the time I got that stopped and the computer restarted Windows was trashed and I got a little line that asked something about a GRUB, whatever in Hell a grub is.  I now have no operating system (I'm writing this from my wife's computer) and am wondering if I really want to use a computer at all or if I should just invest in an abacus.

If I were to install Ubuntu and format the entire hard drive for it would I then be able to create a partition in which I could re-load Windows?  I want to kiss Windows good-bye but am having too many problems with Ubuntu to do that yet.

-Randy

---

### Post by Elfy on 2011-06-30
> **Alver said:**
> ...

> **rs321 said:**
> ...

When you need to reinstall over the top of an existing install. 

I shall assume that the partition you need to install over is /dev/sda5 for the moment. 

You need to check this - ```
sudo fdisk -l
``` in a terminal will list your partitions.

Do the Something Else/Advanced/Manual option when you get to the partition stage. 

Pick the partition - e.g sda5 

Edit the partition.

Format the partition

Mark the mountpoint as /

Save

Then proceed once more from the partition screen.

@rs321 - search for testdisk you miight be able to retrieve the partition table. [https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

---

### Post by rs321 on 2011-06-30
Folks,

I appreciate the prompt help and sound advice I've received here but there's one little thing that's seemed to elude those who have been kind enough to assist me, and that is that knowledge of Ubuntu is not innate.  I'm in the Absolute Beginner's section because I'm an absolute beginner.  It isn't that I'm not able to learn what i need to know; to the contrary I have been learning new things all my life and plan to continue to do so.  I have not, however, ever heard of some of the techniques and buzz-words used here and have not been able to find where to learn about them.  GUI has meant General User Interface in other programs but that doesn't seem to be the context in which it is used here.  GRUB, GNU, and a few others are things which I've never encountered but they are tossed-about freely here.  I've entered many lines of command but never in Ubuntu and don't know how to do that here.

Perhaps my time would be well spent compiling a list of commands and expressions for the absolute beginner (such as myself) and posting it somewhere it can be found.

Again, please do not think I'm unappreciative of the advice offered here and I've been able to benefit from a lot of it, but I think I'll take the time to figure out what is being said before I go any farther.

Thanks again,

-Randy

---

### Post by Elfy on 2011-06-30
If something has been told or referred to that you don't understand - ask :)

You might be a beginner and the forum might be abolsute beginners - different people have different views of beginner. 

No-one knows what you already know, there seems nothing untoward in the posts you've recieved.

I'm sure you'll get there - and don't also forget that all of the people helping you had to learn at some point. So not knowing is not new :)

---

