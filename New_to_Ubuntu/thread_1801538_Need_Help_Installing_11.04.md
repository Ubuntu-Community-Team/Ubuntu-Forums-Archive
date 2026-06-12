---
title: "Need Help Installing 11.04"
date: 2011-07-10
forum: New to Ubuntu
---

### Post by Mindswap1 on 2011-07-10
Hey Guys so yesterday I replaced my install of 11.04 with Fedora 15, because it was lagging, but now I miss Ubuntu :(. I want to install it back, the thing is I don't know how. I put in the install disc, and when it gives me the different options to install the only ones available are. 

1) Replace Windows 7 partition 

or 

2) Other (which makes me create partitions.) 

I just want to replace Fedora with Ubuntu, but the option to install side by side with Windows 7 is not there. And I don't want to create partitions, because I want to install if side by side with windows 7 so that it takes up half and half. Help please!

---

### Post by nick_goodfate on 2011-07-10
Choose the "Other" option and you will see your current partitions list. Just delete the partitions of fedora (NOT the ntfs ones) and use the freed up space to install Ubuntu.

---

### Post by seawolf167 on 2011-07-12
If you choose the 'other' option you can manually edit your partition table. Delete the existing ext entries as this is your Fedora install, then add a new partition for your Ubuntu install (or simply choose to overwrite in that partition). You can leave your swap space alone and reuse that. I suggest creating a separate /home partition while you are at it - it makes upgrading easier in the future.

When/if you are prompted about where to install grub, make sure you install it as the MBR, but do not overwrite the Windows partition boot record or you will have to get out your Windows cd and reinstall that boot record. Grub will then pick up your windows installation and point to the Windows loader.

If it doesn't, you can always have it check for other installations by entering the following commands

```
sudo apt-get install os-prober
sudo update-grub
```

---

