---
title: "I Installed Ubuntu on My SD Card By Mistake"
date: 2010-04-15
forum: New to Ubuntu
---

### Post by ChannelZ28 on 2010-04-15
i just wasnt paying attention and accidentally partitioned my sd card and installed the netbook remix on it, instead of my ssd. they are both 16gb, which was why i missed it.

now how do i unintall ubuntu so that i can reinstall it on my ssd and get all 16gb back on my sd card? i have some linux knowledge, but not much partitioning knowedge, this just seemed the right forum for a question like this.

---

### Post by e4uforums on 2010-04-15
Don't worry about uninstalling Ubuntu on your SD card, just go ahead and install Ubuntu on your SSD as you normally would.  Then, you can format your SD card to erase the Ubuntu installation and gain your storage space back.

---

### Post by Paqman on 2010-04-15
You'll need to boot up into the LiveCD or USB that you used to install Ubuntu. Go to System > Admin > Gparted, whicb is a partition editor.

Make sure none of the partitions are mounted, if you have a swap on the SD card you might need to right click on it and "swapoff". The just right click and "delete" for all the partitions. Easy peasy.

---

### Post by mikewhatever on 2010-04-15
Well, there is no uninstall button for OSs, so just format the card with Gparted. If there is useful data on the card, back it up first.

---

### Post by ChannelZ28 on 2010-04-15
thanks, that was pretty easy! took me a few minutes to figure out how to use gparted, but it was fairly simple. thanks!

---

### Post by e4uforums on 2010-04-15
Glad it's all working for you now.

Be sure to mark the thread as solved.  :P

---

### Post by Paqman on 2010-04-16
> **ChannelZ28 said:**
> thanks, that was pretty easy! took me a few minutes to figure out how to use gparted, but it was fairly simple. thanks!

Cool, it's well worth learning to use Gparted, it's an extremely useful tool.

---

### Post by aeiah on 2010-04-16
ps: if you have storage devices of the same size, its always a good idea to remove the ones you don't want to change before doing things like formatting or installing an OS :P

everyone makes mistakes when there's no easy way to tell them apart

---

