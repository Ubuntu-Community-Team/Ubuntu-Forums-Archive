---
title: "GParted Help"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by Son of MaxVK on 2009-07-26
Hi,

I am trying to install Ubuntu onto my computer that is also running Windows XP, the installation guide I found of this website it telling me to defrag my PC before I go to install Ubuntu fully. I have tried to install Ubuntu before but I never did install it, when I try to defrag my PC in XP it simply tells me it cannot start, I have also tried this in the command promt. My dad, MaxVK, has told me to boot Ubuntu from the CD and try Gparted but I have ran into a problem. There are six partitions showing on GParted, I think that one of them may be a partition set aside for Ubuntu the last time I tried to install it. 

[IMG]http://i137.photobucket.com/albums/q229/lordzak_999/Screenshot.png[/IMG]

Fat32 is the reinstall partition for Windows XP. I'm not sure what the others are. Any help would be greatly appreciated.

---

### Post by Liolikas on 2009-07-26
So use those etx3 partitions for ubuntu install one as / one as /home also you have swap already. When install select custom blabla to apply this.

---

### Post by theozzlives on 2009-07-26
> **Liolikas said:**
> So use those etx3 partitions for ubuntu install one as / one as /home also you have swap already. When install select custom blabla to apply this.

blabla?!

At the  partitioner you can select Manual (Advanced), right-click on sda2 and edit, select ext3 or 4, click format. Under mount point, select /. Do the same for sda5 except the mount point should be /home. Click forward and you should be off and running.

---

