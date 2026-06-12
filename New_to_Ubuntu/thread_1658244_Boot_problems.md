---
title: "Boot problems"
date: 2011-01-02
forum: New to Ubuntu
---

### Post by MHC on 2011-01-02
I've been learning to use Ubuntu 10.4 for a couple of months, then suddenly got a message that my boot file was full and I needed to do something about it. I had been working with some large .img files, and thought some might have got in there. So I had a look, saw some initrd.img files taking a lot of space, and thought I must have caused the problem so I should fix it by removing them and a couple of others! Not a good idea. Now I cannot even boot Ubuntu. A couple of questions:
1. How can I get the required boot file back so I can use Ubuntu again?
2. What caused the thing to fill up in the first place, and how can I stop that happening again?

---

### Post by blazemore on 2011-01-02
This will happen is you use a separate /boot partition, or if you have a very small (or very full) hard drive.

You deleted some files you probably shouldn't have. It's the equivalent of going into C:\Windows\System32 and deleting some big files.

Someone will shoot me down on this, but the easiest way IMO is to reinstall Ubuntu. Don't panic: you can still get at your files!
Just boot from the LiveCD, choose the option to Try Ubuntu.
Then you can access your Ubuntu partition from the Places menu.
Go to home/username and there are all your files.

Copy anything of value to your Windows partition or an external hard drive, and reinstall WITHOUT manually choosing a separate /boot partition. Just use the guided install, not manual, and choose to replace existing Linux system.

---

### Post by blazemore on 2011-01-02
This will happen is you use a separate /boot partition, or if you have a very small (or very full) hard drive.

You deleted some files you probably shouldn't have. It's the equivalent of going into C:\Windows\System32 and deleting some big files.

Someone will shoot me down on this, but the easiest way IMO is to reinstall Ubuntu. Don't panic: you can still get at your files!
Just boot from the LiveCD, choose the option to Try Ubuntu.
Then you can access your Ubuntu partition from the Places menu.
Go to home/username and there are all your files.

Copy anything of value to your Windows partition or an external hard drive, and reinstall WITHOUT manually choosing a separate /boot partition. Just use the guided install, not manual, and choose to replace existing Linux system.

---

### Post by blazemore on 2011-01-02
This will happen is you use a separate /boot partition, or if you have a very small (or very full) hard drive.

You deleted some files you probably shouldn't have. It's the equivalent of going into C:\Windows\System32 and deleting some big files.

Someone will shoot me down on this, but the easiest way IMO is to reinstall Ubuntu. Don't panic: you can still get at your files!
Just boot from the LiveCD, choose the option to Try Ubuntu.
Then you can access your Ubuntu partition from the Places menu.
Go to home/username and there are all your files.

Copy anything of value to your Windows partition or an external hard drive, and reinstall WITHOUT manually choosing a separate /boot partition. Just use the guided install, not manual, and choose to replace existing Linux system.

---

### Post by blazemore on 2011-01-02
This will happen is you use a separate /boot partition, or if you have a very small (or very full) hard drive.

You deleted some files you probably shouldn't have. It's the equivalent of going into C:\Windows\System32 and deleting some big files.

Someone will shoot me down on this, but the easiest way IMO is to reinstall Ubuntu. Don't panic: you can still get at your files!
Just boot from the LiveCD, choose the option to Try Ubuntu.
Then you can access your Ubuntu partition from the Places menu.
Go to home/username and there are all your files.

Copy anything of value to your Windows partition or an external hard drive, and reinstall WITHOUT manually choosing a separate /boot partition. Just use the guided install, not manual, and choose to replace existing Linux system.

---

### Post by blazemore on 2011-01-02
whoa what?

---

### Post by oldfred on 2011-01-02
Sometimes reinstall is quicker & easier, but we like to fix things even if it takes days or weeks.:)

You should be able to chroot into your system from a liveCD and reupdate it. If you have a separate /boot you have to mount that as part of the chroot and often instructions only mention it or leave it out as a /boot for desktops is not common.

drs305 has good chroot instructions for updating grub, which you probably do not have to do, but depending on what you deleted you may have to reinstall grub.

chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Once chrooted to update everything & reinstall the kernel:
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a
#

reinstall kernel:
sudo apt-get update
sudo apt-get install linux-image
sudo update-grub

sudo dpkg-reconfigure grub-pc

---

### Post by MHC on 2011-01-02
Thanks blazemore, that's helpful. A possible problem is that the CD I have is for 9.04 while I had 10.04 installed when I bought the PC. I guess it is no big deal going back to an older version. A simpler solution though, would be if I could just get the boot folder from the CD with the Try Ubuntu boot, and copy that over into the PC. Is that possible?

---

### Post by MHC on 2011-01-02
Thanks oldfred. Is the older version (9.04) on the CD going to be a problem with this approach?

---

### Post by oldfred on 2011-01-02
Not sure, I think it would work as you are just using the kernel from the liveCD to boot, but everything else is really using the install.

If you installed from 10.10, do you not have a liveCD of it. You may be able to just copy the kernel & initrd from 10.10, but would have to have the exact versions in grub to easily boot, otherwise you may be manually booting or editing grub menu lines for correct kernel & initrd versions.

---

