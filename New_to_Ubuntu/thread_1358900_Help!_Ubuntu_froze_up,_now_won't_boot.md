---
title: "Help! Ubuntu froze up, now won't boot"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by swarup on 2009-12-18
I've got a laptop set up with dual boot Gutsy/XP, and was working in Gutsy today doing an app install using Wine. In the middle of the install, Gutsy froze up. The only thing that worked was the screen's shutdown icon. So I clicked it, and selected to shut down the computer. It shut down fine. Now it boots fine into XP, but when at Grub I select Ubuntu, I get the first couple boot screens and then the screen goes blank and won't finish the boot. 

Can someone tell me how to fix this? I've got a lot of important data on this computer. Can't imagine something serious could have happened, but the computer won't boot. Thank you!

---

### Post by Yvan300 on 2009-12-18
To save yourself all the trouble, just boot up your live cd and copy your information. Then i would recommend using a newer version of ubuntu to do a fresh install.

---

### Post by Extract_Here on 2009-12-18
well this seems to be quite the problem. im not sure how to get it back up and running but if worse comes to worse. you can use an enclosure to plug your hardrive in another computer to retrieve the important files and then re-install and put them back on.

---

### Post by Extract_Here on 2009-12-18
use heron or juanty

---

### Post by swarup on 2009-12-18
Thanks for the suggestion re using the livecd to get the info. That should probably work.

As for the version, Gutsy is the LTS version-- is it less stable than the newer versions?

I had a [similar thing]("http://ubuntuforums.org/showthread.php?t=452738") happen to me two years ago. But at that time, although it would not boot up, still it was coming to a terminal window-type prompt (root@swarup-laptop:~#). That time, someone told me to type there "e2fsck -y /dev/hda2". I tried it, and it fixed the problem. But that terminal window-type prompt was different from grub's command prompt. Today I tried typing the same command by typing "c" at the grub screen to get a command prompt (grub>), and it did not accept the command. Does anyone know how to adapt the terminology of the command I gave two years ago, so it will work at the grub command prompt?

---

### Post by joes7 on 2009-12-18
Re-install GRUB from the LIVECD

---

### Post by swarup on 2009-12-18
> **joes7 said:**
> Re-install GRUB from the LIVECD

Do you think the problem is with Grub? I do get the grub menu just fine, and it works fine for booting to XP as well as for at least initiating the boot to Gutsy. Do you think reinstalling Grub will make a difference?

---

### Post by themusicalduck on 2009-12-18
It might be worth runnning a live CD and using gparted to do a disk scan of the partition. It'll be under System > Administration, either gparted or Partition Editor on a newer version of Ubuntu. If something got corrupted then it might be able to fix it.

I think that is the same as what you did before -> I had a similar thing happen to me two years ago. But at that time, although it would not boot up, still it was coming to a terminal window-type prompt (root@swarup-laptop:~#). That time, someone told me to type there "e2fsck -y /dev/hda2" but this would be doing the same thing with a GUI from the live CD.

Gutsy isn't the current LTS version, Hardy Heron is and in April the new LTS will be Lucid Lynx.

---

### Post by jw5801 on 2009-12-18
> **swarup said:**
> I've got a laptop set up with dual boot Gutsy/XP, and was working in Gutsy today doing an app install using Wine. In the middle of the install, Gutsy froze up. The only thing that worked was the screen's shutdown icon. So I clicked it, and selected to shut down the computer. It shut down fine. Now it boots fine into XP, but when at Grub I select Ubuntu, I get the first couple boot screens and then the screen goes blank and won't finish the boot. 

Can someone tell me how to fix this? I've got a lot of important data on this computer. Can't imagine something serious could have happened, but the computer won't boot. Thank you!

Sounds a lot like your filesystem may have become corrupted.

> **swarup said:**
> Thanks for the suggestion re using the livecd to get the info. That should probably work.

As for the version, Gutsy is the LTS version-- is it less stable than the newer versions?

Gutsy isn't the LTS, Hardy is, although there will be a new LTS soon I believe. As it stands, I don't think Gutsy is supported any longer, so you won't be getting important security updates, so it might be time for an upgrade anyway.

> I had a [similar thing]("http://ubuntuforums.org/showthread.php?t=452738") happen to me two years ago. But at that time, although it would not boot up, still it was coming to a terminal window-type prompt (root@swarup-laptop:~#). That time, someone told me to type there "e2fsck -y /dev/hda2". I tried it, and it fixed the problem. But that terminal window-type prompt was different from grub's command prompt. Today I tried typing the same command by typing "c" at the grub screen to get a command prompt (grub>), and it did not accept the command. Does anyone know how to adapt the terminology of the command I gave two years ago, so it will work at the grub command prompt?

You need a running kernel and a shell for that command to work, which is very different to being at the grub prompt.

> **joes7 said:**
> Re-install GRUB from the LIVECD
Grub is obviously working correctly, why would you reinstall it?



The easiest solution is to boot into a LiveCD and grab everything you need from the hard drive, then (re)install. While you're installing, I'd recommend creating a separate partition for your /home directory, that way you can reinstall in future without losing any of your settings or data.

You can also try forcing a file system check on your root partition by running
```
e2fsck -f /dev/YOUR_PARTITION
``` as root (use sudo). Something like `fdisk -l' can be used to tell you which partition it is, if you're not sure.

---

### Post by swarup on 2009-12-19
@ themusicalduck: Thanks very much for the suggestion! I'll try it.

@ jw5801: Hiya! It's really great to hear from you. And so fast! Wow, thanks for coming on board. The reason I really want to save this install, at least for a little while longer, is that I have a special Hindi typing schema as well as extensive spellchecker set up there. And it is going to take me time to recreate that. So if I could just use it another few weeks even, and that as much as anything else to be able to study again just I got to the setup I've finally got.

So, I'll try what you suggested at the very end of your post. I guess if I do "fdisk -l" at the grub command prompt then, that should give me the partition id, right? I'll try it and see how it goes. Thanks again!

I'm so surprised to see such a corruption could have occurred during such routine use.

---

### Post by jw5801 on 2009-12-19
> **swarup said:**
> @ themusicalduck: Thanks very much for the suggestion! I'll try it.

@ jw5801: Hiya! It's really great to hear from you. And so fast! Wow, thanks for coming on board. The reason I really want to save this install, at least for a little while longer, is that I have a special Hindi typing schema as well as extensive spellchecker set up there. And it is going to take me time to recreate that. So if I could just use it another few weeks even, and that as much as anything else to be able to study again just I got to the setup I've finally got.

So, I'll try what you suggested at the very end of your post. I guess if I do "fdisk -l" at the grub command prompt then, that should give me the partition id, right? I'll try it and see how it goes. Thanks again!

I'm so surprised to see such a corruption could have occurred during such routine use.

Grub has no idea what fdisk or e2fsck are, same as it doesn't know what gnome or kde or xfce is. All you can do with grub (or at a grub prompt) is decide which partition contains the kernel, which kernel to load, and which partition to mount at /. You'll need to do all your diagnostics and testing from a LiveCD environment. If grub were the problem, we could debug it using itself, but we can't debug anything else using grub.

fdisk -l will give you a list of partitions somewhat like this:
```
Andornor ~ # fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         131     1052226   83  Linux
/dev/sda2             132        4831    37752750   83  Linux
/dev/sda3            4832       14593    78413265    5  Extended
/dev/sda5            4832       14332    76316751   83  Linux
/dev/sda6           14333       14593     2096451   82  Linux swap / Solaris
```

so you'll need to decipher which of the partitions listed on the left is your Ubuntu partition. I imagine you'll only have one Linux formatted partition however (unlike me), so it should be pretty obvious which one it is.

Filesystem corruption is just a first guess, and it doesn't have to be extensive, just in the wrong place and enough to kill an important file (/sbin/init for example). It's also not the only possibility (or even the most likely), but it's the easiest to check for first up. It's also generally more likely to be caused by hardware issues, than by software, so if it does turn out to be the cause, it's difficult to say if the hang caused the corruption, or if hardware issues caused the corruption which caused the hang you saw.

If fsck finds some corruption and is able to correct it so that your install is repaired, then you'll be able to continue on as normal, but if it finds some and can't repair it, you'll need to reinstall, and if there isn't any, then the problem may become a little more time consuming to track down, which might make reinstalling your quickest option anyway.

I'm not sure how one goes about installing new typing schema or where they get installed to, so I can't speak for that. But your custom dictionaries and all your user settings and the like will all be stored in your home folder, which is why I make the suggestion that you keep a separate partition for /home, so you can reinstall without disturbing any of your data or settings. You can migrate to this sort of setup and keep everything that's set in your /home/user now before you attempt a reinstall. pychocats have a [good tutorial](http://www.psychocats.net/ubuntu/separatehome) for how to do this, not sure how recently it was updated, but the steps haven't changed.

If you reinstall after doing that (with the partition manager in the installer told to use your new /home partition as /home without reformatting it or changing it at all), all you should have left to do is reinstall all the apps you use and do any extra Xorg or driver configuration you need to do. You may also need to reinstall your typing schema, depending on how you installed it, and where it installed to.

---

### Post by swarup on 2009-12-19
jw5801, you are amazing. You have saved me a third time. It's like they say a cat has nine lives-- well, you've given me an extra three.

I booted up to the livecd. Then I actually used gparted to identify the partition name of the Gutsy install. And executed the "e2fsck -f /dev/YOUR_PARTITION" command as you instructed. There must have been a lot of stuff that got screwed up by the OS freeze, because it must have taken 20 minutes to fix it all-- and must have asked 20 times whether I wanted such-and-such an item repaired. When it was done, I exited livecd, rebooted, and magic! Gutsy booted up just fine. Although after booting, the HDD kept on working and working like it was still trying to do something more. And not all the functions I needed in Gutsy were working. So I rebooted to the livecd-- two times more actually, each time running the "e2fsck -f /dev/YOUR_PARTITION" command, and each time finding more things that needed fixing. In the end, it seems everything has gotten repaired and the computer boots to Gutsy flawlessly, with the HDD quiet after the boot is complete, and with all the apps working properly.

I'd say for anyone else who may read this thread in the future-- if your Ubuntu install won't boot, try going to the livecd and executing the "e2fsck -f /dev/YOUR_PARTITION" command. It works wonders.

jw5801, thanks again for all your help! :)

---

