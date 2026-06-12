---
title: "removing multipule Ubuntu/Mythbuntu installs"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by nickm57 on 2010-03-04
Hi
I'm trying to remove multiple installs of ubuntu and mythbuntu. These were installed for testing now I do not want them. I want just my original install of Ubuntu along with the windows installs.
What seems to happen If remove(delete) the unwanted intall Grub goes into "grub recover" or something like that. Each new install takes command of the grub.
 How do remove the newer ones and return the grub to the Ubuntu and kernel version that I want to use?

thanks

---

### Post by byStanderone on 2010-03-04
...ok, take things one at a time, not sure of the grub version that you are using, tho if you are in karmic, that would be grub2 at the most.

- note down the kernels that you want to remove, then go to synaptic manager and do a complete remove of them...

- once you are through with synaptic, exit

- open terminal and sudo update-grub...then reboot

---

### Post by nickm57 on 2010-03-05
thanks
 that deals with the kernels, Yes i'm running 9.10.

But I have 3 other intalls of mythbuntu running on separate partitions. If I just delete these from the partition I lose the grub2 on booting. giving me "grub recover>" prompt.
How do I remove these installs completely and return control to the grub of the ubuntu install.
this is what my linux area looks like. It has 3 installs I do not want.
I have had to install (mythbuntu) again because I could not boot.

31 g extended /dev/sda1
            mythbuntu /dev/sda10
            swap        /dev/sda11
            5.6 file system /dev/sda12 (extra mythbuntu)
            swap        /dev/sda13
            swap      /dev/sda5
            Main Ubuntu /dev/sda6 (this is the one I want)
           swap /dev/sda7
           5.6 file system /dev/sda8
           swap /dev/sda9 (extra mythbuntu)

Windows /dev/sda2
Windows lite(tv) /dev/sda3
storage Disc /dev/4

---

### Post by byStanderone on 2010-03-05
...you were on the track when you removed myth, but since it is once again active...try if this will do the trick:

-boot from your karmic live cd

-mount your ubuntu karmic, as to your case it is:
 
 sudo mount /dev/sda6 /mnt

- reinstall grub2:

  sudo grub-install --root-directory=/mnt /dev/sda  (note: w/o 6)

-unmount the partition:

 sudo umount /mnt

- reboot

---

