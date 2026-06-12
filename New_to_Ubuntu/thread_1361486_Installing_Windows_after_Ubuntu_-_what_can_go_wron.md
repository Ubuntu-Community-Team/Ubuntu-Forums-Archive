---
title: "Installing Windows after Ubuntu - what can go wrong?"
date: 2009-12-22
forum: New to Ubuntu
---

### Post by Anuovis on 2009-12-22
I know that it is better to first install Windows and then Ubuntu. After some searching I found out that it is possible do dual boot the other way around, but one must restore the grub which Windows overwrites. There are tutorials to do this.

I am interested in risk by going this way. What else can go wrong? Can it affect only Windows, only Ubuntu or both? And in what ways?

Thank you.

---

### Post by James Dee on 2009-12-22
i did it in that way, first ubuntu and then windows, and I didn't have any problem.
follow this link to recover grub 2 via liveCD:
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by Gone fishing on 2009-12-22
Windows will over write the MBR so you wont have grub at startup and wont be able to boot anything but windows. However, this is all fixable. 

The basic processes would be:

. Start up on a live ubuntu CD and start gparted resize you ubuntu partition to make space for windows.
. Install windows into the created freespace
. Fix grub using an ubuntu live CD 

You could also use a custom boot loader like Gag if you wanted but you would still need to fix grub.

---

### Post by hariks0 on 2009-12-22
It will not affect both. Only the MBR will be replaced by windows boot loader instead of GRUB. I have recovered GRUB successfully after following a tutorial.

you should be able to reset Grub2 with Win here --> [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If it's borked your Grub2 installation totally, just re-install Grub2, it looks scary, but is a walk in the park, instead of scratching your head, trying different 'tweaks' --> [https://help.ubuntu.com/community/Gr...ing%20GRUB%202](https://help.ubuntu.com/community/Gr...ing%20GRUB%202)

---

### Post by sandy8925 on 2009-12-22
Just make sure you partition carefully.

---

### Post by Anuovis on 2009-12-22
Thank you for all the replies. No bad stories so far?

> **sandy8925 said:**
> Just make sure you partition carefully.
Could you explain what do you mean by this?

---

### Post by RyanVanDiemen on 2009-12-22
Hi, I have just done this couple of hrs ago. Had Vista + Ubuntu and decided to go back to XP... No problems whatsoever, however, I already had a partition for Windows (where Vista was installed) so just installed xp and installed grub to MBR afterwards. If you don`t have partition for Windows, you will need to edit the partitions -> Live CD and then run GParted and resize the partition. Anyway, if you need to edit paritions, I`d recommend to backup your data...

---

### Post by Anuovis on 2009-12-23
Thank you for all the replies. 
I tried installing Win XP and it went OK. Did not notice any problems at all.

---

### Post by RyanVanDiemen on 2009-12-23
good to hear :)

---

