---
title: "Upgrading to Intrepid and installing a new HDD"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by HittingSmoke on 2009-01-22
I just bought a shiny new 500 GB SATA drive to replace my aging pair of 80G IDE drives. Right now I have Ubuntu Hardy installed on the primary IDE drive with my home folder residing on the second disk.

I want to make a fresh Intrepid install on the 500GB and transfer the home folder from my Hardy install onto the new Home partition I will be creating on the 500.

Is it as simple as creating a home partition during installation then overwriting the home folder with my old one and rebooting or are there other steps I should know about?

---

### Post by logos34 on 2009-01-23
I would copy the /home partition to the 500 GB disk first (perhaps using Gparted ['move']("http://gparted.sourceforge.net/larry/move/move.htm") function--the exampleis for ntfs, but the principle is the same for ext3), then install 8.10 and specify the separate /home, as explained [here]("https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion").
Then either disconnect the 80 GB drive or else change the UUID (tune2fs -U random device) so there's no mixup.

hope that helps

good luck

---

### Post by HittingSmoke on 2009-01-23
> **logos34 said:**
> I would copy the /home partition to the 500 GB disk first (perhaps using Gparted ['move']("http://gparted.sourceforge.net/larry/move/move.htm") function--the exampleis for ntfs, but the principle is the same for ext3), then install 8.10 and specify the separate /home, as explained [here]("https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion").
Then either disconnect the 80 GB drive or else change the UUID (tune2fs -U random device) so there's no mixup.

hope that helps

good luck

Ok, I partitioned my drive using Gparted the way I wanted then booted to the Intrepid Live CD. I used the Live environment to copy my Home folder to the partition on the 500G I wanted to use for /home. The install went fine except it ended with an error message about a program crashing (ubi something). This was immediately after the progress bar for the copy system file dialog finished.

I hoped maybe the install finalized before it crashed since the progress bar appeared to reach 100% just before but when I rebooted then set my new drive to the primary boot device I get a no boot device error. Looking at the drive it appears to have the complete file system on the root partition. Is there a way to install GRUB on this to make sure it's not just an error with that?

*EDIT* ubiquiti is the program that crashed

---

### Post by Synt4xError on 2009-01-23
Have you installed only one time and got this error and haven't tried again?

And how did you install your drive?

---

### Post by HittingSmoke on 2009-01-23
> **Synt4xError said:**
> Have you installed only one time and got this error and haven't tried again?

And how did you install your drive?

Yes I only tried once so far, didn't have time for another go immediately.

The drive I just installed by mounting it in my case and attatching the cables...

---

### Post by Archmage on 2009-01-23
How I just did it.

Attach the SATA-HDD, change the booting order to CD, SATA-HDD, IDE-HDD, boot from the installer CD (I use the alternate CD, but Live-CD should also work), go till I'm in the partition screen, go to manual, make this partitions:

SATA-HDD
/ ext3, the size you need, 20 GB should be enough, but you can set this much higer just in case. But it shouldn't be more than 200 GB. Format this partition
Swap-Partition with your memory-size x 1.5 - with high memory you may not need it, but it is needed for hypernationg and susspending
/home ext3 with the rest of you free space. Format this partition

IDE-HDD
/home/[your username]/oldhdd DON'T FORMAT THIS PARTITION

Than go on with your install. After you did install, copy all the files (including hidden ones) from /home/[your username]/oldhdd/home/[your username]/ to /home[/your username]/

Than turn off the PC, remove the old IDE-HDD and use it as your backup. You may erease the entry in your fstab, if you want.

---

### Post by HittingSmoke on 2009-01-23
> **Archmage said:**
> How I just did it.

Attach the SATA-HDD, change the booting order to CD, SATA-HDD, IDE-HDD, boot from the installer CD (I use the alternate CD, but Live-CD should also work), go till I'm in the partition screen, go to manual, make this partitions:

SATA-HDD
/ ext3, the size you need, 20 GB should be enough, but you can set this much higer just in case. But it shouldn't be more than 200 GB. Format this partition
Swap-Partition with your memory-size x 1.5 - with high memory you may not need it, but it is needed for hypernationg and susspending
/home ext3 with the rest of you free space. Format this partition

IDE-HDD
/home/[your username]/oldhdd DON'T FORMAT THIS PARTITION

Than go on with your install. After you did install, copy all the files (including hidden ones) from /home/[your username]/oldhdd/home/[your username]/ to /home[/your username]/

Than turn off the PC, remove the old IDE-HDD and use it as your backup. You may erease the entry in your fstab, if you want.

Thats sort of what I did. But getting /home set up right wont be an issue if I cant get it to boot.

I just tried installing again using the Live CD except I didnt boot into the Live environment, I just chose the install option from the main menu.

It all went smooth and after the install I was left with the gnome desktop. After running for a couple of minutes I got the same crash report from ubiquiti and then the whole system locked up. I could get to bash with ctrl+alt+F1 but couldn't get back to X after that.

I did a reboot command in bash and on reboot I got the same message about inserting boot media. I've checked and double checked my BIOS and I know it's set up right. I even tried disabling the old drives and making the new one the only boot device, same message.

Does this mean GRUB isn't installing properly?

---

### Post by Archmage on 2009-01-23
> **HittingSmoke said:**
> Does this mean GRUB isn't installing properly?

Yes, I also think that something went wrong. Did you try installing with the IDE-HDD completly removed from the PC? (Or at least the IDE-cable pluged off?)

Or maybe you can only restore GRUB, but that may be a problem if it hasn't been installed proper in the first place.

---

### Post by HittingSmoke on 2009-01-23
> **Archmage said:**
> Yes, I also think that something went wrong. Did you try installing with the IDE-HDD completly removed from the PC? (Or at least the IDE-cable pluged off?)

Or maybe you can only restore GRUB, but that may be a problem if it hasn't been installed proper in the first place.

No I didn't try with the IDE drive completely disconnected, ill try that next.

---

### Post by HittingSmoke on 2009-01-23
I think several problems were going on.

I decided to try a guided install to see if that might work instead of manually setting partitions. I did a full disk guided install figuring a can repartition and move my home folder later. This time instead of going back to the Live environment after install it gave me a completed message and rebooted instead of getting a crash message from ubiquity.

It still wouldn't boot but I decided to mess with my SATA setting in the BIOS. Originally all my RAID setting were completely disabled and I had tried enabling them under JBOD to see if that might work but didnt on the manual install. I tried every possible setting that can support one drive and nothing worked at all on the manual install.

After running the guided install and returning all my RAID controller settings to disabled the system booted.

So my best guess is that there's a bug in the manual install that isnt setting up GRUB properly because of the ubiquity crash.

On the manual install I never got a completed message and like I said, it just went back to the live desktop. If I waited long enough I would get the ubiquity crash warning and shortly after the system would freeze.

When I did the guided install I got the completed message and right before that, the clean up progress bar would do it's thing. One of the messages in the clean up progress bar was "removing ubiquity" so I'm guessing that the crashing of that caused something not to be finalized with the install when done manually.

That's the best I can figure

---

### Post by logos34 on 2009-01-23
[edit--I just reread you posts, it probably won't help]

---

