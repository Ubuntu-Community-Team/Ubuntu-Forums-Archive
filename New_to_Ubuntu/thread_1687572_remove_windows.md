---
title: "remove windows"
date: 2011-02-14
forum: New to Ubuntu
---

### Post by art_monu on 2011-02-14
Hello,
    I am using Ubuntu 10.04 LTS desktop edition. I have a corrupt copy of windows xp in one drive(partition). How can I remove windows from that drive and completely convert my computer into Ubuntu? Can I just format that drive? Please reply in detail..

---

### Post by mikewhatever on 2011-02-14
Is Ubuntu installed on a separate partition? If so, then yes, you can just format the Windows partition. If Ubuntu is installed 'inside Windows', then formatting Windows will also delete the Ubuntu files.

---

### Post by grahammechanical on 2011-02-14
Do you remember when you first installed Ubuntu? Did you not have to partition the hard disc? You had the choice of using the whole disc for Ubuntu or letting the installer partition the disc in two parts. The first part for Windows. The second part for Ubuntu, which would have included a small part for the Ubuntu swap partition. What do you think would have happened if you had chosen to use the whole disc?

You can repeat the installation again and choose to use the whole disc for Ubuntu. You will get rid of Windows and also all your data in your Ubuntu home folder. So, make a copy and store it somewhere off the disc.

You can simply format the Windows partition. That will get rid of Windows.

You make the ex-Windows partition smaller (perhaps 20GB) and install Ubuntu 11.04 in it (in a few weeks time). Then you can dual boot into two different Ubuntu installations.

You can use part of the free space to create a /home partition that will hold your home folder and keep it safe from re-installs. Over time, after you have migrated all your data to the /home partition,  you can enlarge and remove partitions but back up your data first and you may need to re-install so that GRUB and Ubuntu know what is where. Ubuntu needs to know where you home folder is. Otherwise you will break the installation.

For detailed instructions please send payment to .....

Look for tutorials.

Regards.

---

### Post by art_monu on 2011-02-14
thanks everyone... all the replies are really helpful.

---

