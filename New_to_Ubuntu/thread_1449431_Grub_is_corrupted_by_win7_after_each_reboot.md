---
title: "Grub is corrupted by win7 after each reboot"
date: 2010-04-07
forum: New to Ubuntu
---

### Post by mbickell on 2010-04-07
I have recently installed a dual-boot with win7 (already installed) and ubuntu 9.10 (from a LiveCD). I am an ubuntu noob.

All was fine for a while, then Grub decided to become corrupted. I started my laptop (a Dell 1555) and the following was displayed:

Grub Loading.
the symbol 'b_sprinth' not found
Aborted. Press any key to exit.
  >>I pressed any key<<
Broadcom UNDI PXE-2.1 v11.0.9
Copyright...
Copyright...
All rights...
PXE-E61: Media Test failure, check cable
PXE-M0F: Exiting Broadcom PXE ROM
Operating system not found

I then booted off the LiveCD and found out how to reinstall my Grub2 from these forums. I used the Method 2 described in []("https://help.ubuntu.com/community/Grub2#Reinstalling GRUB 2") which fixed the problem and allowed me to get to the Grub menu and boot into win7. I thought my problems were solved - until I rebooted, and lo and behold I had the same problem again: Grub was again corrupted. 
I have done this several times now; once the error was not that the "symbol" b_sprinth could not be found, but another strange "symbol".
How can I protect my Grub from getting corrupted? I'm willing to reinstall ubuntu if necessary, but I'm not even sure if that will solve the problem.

I have searched the forums, but have not found a solution or a similar problem.

Just FYI: my ubuntu isn't even working anyway - before the above problem started, if I tried to boot into ubuntu, it would hang at the loading screen (the one with the bar moving from left to right). I could still press CTRL-ALT-F1 and get to the command line, but since I am a noob to ubuntu I couldn't do much from here except reboot (Although, this is where I updated the Grub after I reinstalled it, as instructed by the Method 2 I used to reinstall the Grub). I'm sure this is an unrelated problem, and I plan to create another thread for this later.

---

### Post by oldfred on 2010-04-08
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)
HP ProtectTools, Dell Recovery, and a few others write into MBR meierfra.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)
Dell Media direct issues with MBR
[http://ubuntuforums.org/showthread.php?t=923576](http://ubuntuforums.org/showthread.php?t=923576)

---

### Post by tavzz on 2010-04-11
hi bmickel,

i have the same problem like yours at the moment. im installing remix version bcoz im using acer netbook.

i hope we can solution soon bcoz i cany use my netbook.


help....anybody?

---

### Post by mbickell on 2010-04-12
I am pretty sure that the problem is with my Dell Datasafe Local Backup software on my laptop. The following two links convinced me:
[http://ubuntuforums.org/showthread.php?t=1447786]("http://ubuntuforums.org/showthread.php?t=1447786")
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR")
(Thank you to oldfred for the help)
I havent actually been able to fix it yet since for some reason I cant remove that software.
But this only works for Dells. After looking at the forums it seems that the problem is usually with some sort of recovery software (which writes stuff to the MBR and corrupts the Grub), so if you look for something like that on your acer it might fix the problem. So far I havent seen any reports of this problem with Acers though.

Let us know if you find anything.

---

