---
title: "Manual partitioning"
date: 2009-10-21
forum: New to Ubuntu
---

### Post by Loki57701 on 2009-10-21
I'm using 9.10 and wanted to do a fresh install and create a /home partition. After reading some guides online this is what I did:

"/"  30Gb primary

Swap 8Gb 

/home remaining-space Primary

There was a "beginning" and "end" option when creating the partitions and by default beginning was selected, since I created "/" first I'm hoping that means its bootable? Since there was no option to mark a partition as bootable from what I seen. Swap and /home were also marked as beginning.

The problem:
The installer finishes installing and then just goes crazy, I get all these weird flashing colors and symbols all over my screen, I cant even hold down the power button, I have to unplug and take out the battery to turn it off. So.. I must have done something wrong?

Any suggestions?

---

### Post by NightwishFan on 2009-10-21
Does the installer finish normally otherwise, or is the manual partitioning the problem?

Make sure you check the CD for errors before you install.

My disk setup is like this:
sda1: swap 2gb
sda2: / 30gb
sda3: /home 170gb

(Actually I use /mnt/data for sda3, as I like a clean home, and then I symbolic link my Documents Music to the /home, however that is just my preference, it is esentially the same thing)

---

### Post by Loki57701 on 2009-10-21
I installed from that disc using automatic partitioning and everything worked great so I'm guessing its the manual partitioning.

If I remember correctly my sda wasn't in order like yours for some reason. After I created my new partition table it (automatically) assigned me something like:

sda2 /
sda5 swap
sda6 /home

I don't know why. I didnt see an option to make it 1, 2 and 3 respectively. 

I'm still pretty new to this so I don't know what /mnt/data is, I've heard of symbolic links lol but I'm unsure on the specifics of how they work, sounds like shortcuts to me.

---

### Post by NightwishFan on 2009-10-21
I do not use extended partitions like the automatic partition scheme. You can do the partitioning entirely manually from both the live and alternate installers. If you run into problems, I would perhaps try the alternate installer. It is a bit different, but the questions are mostly the same.

My scheme is set to my preference, but having swap as /sda1 is not necessary.

**Suggestion:**
Perhaps boot the live CD desktop, and open System -> Administration -> Gparted. Pre-partition your disk from there, and when you install, simply mount and format the partitions using the manual option. (In live installer). After you modify the partition table, you should reboot before you try to install.

---

### Post by lavinog on 2009-10-21
> **Loki57701 said:**
> 
The problem:
The installer finishes installing and then just goes crazy, I get all these weird flashing colors and symbols all over my screen, I cant even hold down the power button, I have to unplug and take out the battery to turn it off. So.. I must have done something wrong?

Any suggestions?

That doesn't seem like a partitioning issue.

did you check the cd for defects prior to installation?
what video card do you have?

---

### Post by Loki57701 on 2009-10-21
I'll try the live CD option. Hopefully that works..

I choose ext4 as my format for all 3 partitions, there was an option for ext4(extended), should I have used that?

---

### Post by Loki57701 on 2009-10-21
I checked the disc for error and there were no problems. My video card is an nVidia 9800GS 512mb

---

### Post by lavinog on 2009-10-21
> **Loki57701 said:**
> I checked the disc for error and there were no problems. My video card is an nVidia 9800GS 512mb

What video driver are you using?

---

### Post by ikisham on 2009-10-21
Also if you're going to repartition and it offers an option to create an extended partition, I think it's a good idea. One can't have more than four primary partitions in the hd so the extended, which may encompass at least your root (/) partition and the swap partition and is counted as one primary partition will let you create more partitions in the future (if you want to install another system, even only to try, for example).

---

