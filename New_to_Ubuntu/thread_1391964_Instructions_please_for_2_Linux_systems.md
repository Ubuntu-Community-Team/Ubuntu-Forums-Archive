---
title: "Instructions please for 2 Linux systems"
date: 2010-01-27
forum: New to Ubuntu
---

### Post by oldfolks on 2010-01-27
I tried to find out how to load a second Linux distro but everything I read talks about if you want to load over windows. I do not have Windows on this computer only Ubuntu 9.10.
 I think I would load 2nd system up except when it came time to load bootloader that is where I'm lost. I also know NOTHING about "chainloading." so if some one could point me in right direction I would certainly like it . I am VERY new to Linux so your directions would have to be very direct and simple.

 Hope this is in right topic area but since I am an Absolute beginner I thought it was.
Thanks

---

### Post by chaanakya_chiraag on 2010-01-27
What second distro are you trying to install?  If it uses GRUB, then it should just add an entry to it.  If it uses LILO, it might install LILO over GRUB, but ALL options should remain (if the autoconfig works correctly of course)

---

### Post by oldfolks on 2010-01-27
I tried PCLinux but it would not see Ubuntu and so I did not know where to go from there. I would like to try to install Mandriva. Its a 4.3g dvd so it takes time so I sure would like to know BEFORE I go to the trouble. By the way PCLinux was with Grub.
 I really like Ubuntu as it seems to work better than any others I have tried as far as finding everything. But would like to learn more about different distros.
Thanks

---

### Post by chaanakya_chiraag on 2010-01-27
What exactly do you mean by "finding Ubuntu"?  The Ubuntu menu item in GRUB will only show up after you install.

---

### Post by oldfolks on 2010-01-27
It would not list it under other systems and when I installed it ONLY PCLinux was my choice to boot. SO I had to reinstall Ubuntu to use it.

---

### Post by oldos2er on 2010-01-27
Some distros do not automatically install grub entries for any OS already installed. You just need to manually add them to grub's menu list.

---

### Post by hhlp on 2010-01-27
see the part Adding Entries to Grub 2:

[http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

---

### Post by Gone fishing on 2010-01-27
Currently my box is running Ubuntu, Haiku, PC-BSD, and Windows 7 and I I have run Opensuse. The way I do it is using the GAG boot manager and installing grub onto the /boot or /root partition.

I did have a slight problem with Karmic as GAG didn't seem to like the ext4 file system and so I created a small ext3 /boot partition. I find GAG easier than messing about with grub. However the  update-grub2 does seem to be quite good at finding things and should find another Linux and Windows if not Haiku or PC-BSD.

So if you install the other Linux a be sure to install grub on its root partition if you run update-grub2 in karmic it should be found an appear on the boot menu.

---

