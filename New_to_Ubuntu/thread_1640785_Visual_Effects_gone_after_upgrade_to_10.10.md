---
title: "Visual Effects gone after upgrade to 10.10"
date: 2010-12-08
forum: New to Ubuntu
---

### Post by thereid on 2010-12-08
I had visual effects (wobbly windows) working fine in Hardy and Karmic, When I tried to upgrade directly to maverick, the install went bad, so I had to re-format the partition to install 10.10.
Now I can't get the effects to wok.  The only hardware change between the two was a RAM increase. (Now 2GB).

Video card info:
reid@reid-ThinkPad-R51:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
reid@reid-ThinkPad-R51:~$ 

It tells me there are no proprietary drivers for my system.

I bet this is an easy fix, but I'm a clueless noob.

Thanks for any help.

---

### Post by TeoBigusGeekus on 2010-12-08
See [this]("http://superuser.com/questions/192121/how-to-install-intel-82852-855gm-driver-on-ubuntu-10-10-maverick-meerkat") and [this]("http://askubuntu.com/questions/4658/how-to-install-intel-82852-855gm-driver").

---

### Post by thereid on 2010-12-08
reid@reid-ThinkPad-R51:~$ $ sudo add-apt-repository ppa:glasen/intel-driver $ sudo apt-get update && sudo apt-get upgrade
$: command not found
reid@reid-ThinkPad-R51:~$ 
?


reid@reid-ThinkPad-R51:~$ sudo apt-get install xserver-xorg-video-intel

Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-intel is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
reid@reid-ThinkPad-R51:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 90.2MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 143712 files and directories currently installed.)
Removing linux-headers-2.6.35-22-generic ...
Removing linux-headers-2.6.35-22 ...
reid@reid-ThinkPad-R51:~$


The other post you linked to suggests that I get rid on the Intel graphics card.  I'm not sure i can do that. I thought it was built in to the motherboard; not a discreet card...I will check.

Any other workarounds for enabling wobbly windows in 10.10 would be helpful.  Not a required function, I know; but it's one of my favorite features of Ubuntu.
Thanks

---

### Post by thereid on 2010-12-09
[COLOR=black]**Here is the other response:**[/COLOR]


I have the same card in my laptop. To the get the card working i changed the driver in /etc/X11/xorg.conf to intel
  Section "Device"
 Identifier "Configured Video Device"
 Driver  "intel"
EndSection
 and changed 
  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 
to 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.modeset=1"
 in /etc/default/grub
  run update-grub after making these changes & reboot.
 
**I found "X11" in the File manager, but i don't seem to have a file "xorg.conf"**

[B]I hate to be such a noob, but how do I do this?

[/B]

---

