---
title: "Operating System Not Found"
date: 2010-09-11
forum: New to Ubuntu
---

### Post by anguspodgorny on 2010-09-11
Hello All,


_INTRODUCTION_ (feel free to skip if you don't care)

I  will try to keep this as concise as possible. Quickly, it's great to  see a forum as civil as this. I have looked at a lot of software forums,  and people are quite harsh over electronic media. Thanks to all who  have set this up, and continue to make this accessible. Also, if I  perform any forum faux pas please alert me, so future posts can be  better.

 I am brand new to Ubuntu, so i apologize for my  ignorance, and I will make an effort to get up to speed as quickly as  possible. Also, I did search around for this topic and didn't recognize  an explicit answer to my problem. 


_PROBLEM_

I  just bought a Dell 14R(N4010) laptop, and installed Ubuntu 10.04  alongside Windows 7. Install went fine, and used Ubuntu for several  days. Then I booted into 7, it ran a disc check of some sort, and  continued working. Logged out, went home, tried to boot Ubuntu and got  basically nothing. I was able to get into bios and boot options menu,  but if I let it try to boot from the hard drive i would just get a blank  screen with flashing cursor(no input). After a ton of passed  diagnostics, Dell sent out a new hard drive. 

The second install was almost identical, except in that instead of blank cursor, this time i got

[B]no module name found
Aborted. Press any key to exit.

<<After pressing a key>>
Copyright (C) 1997-2008 Intel Cooperation
For Atheros PCIE Ethernet Controller v2.0.2.3(06/18/10)

Check Cable Connection!
PXE-M0F: Exiting Intel PXE ROM.
Operating System not found[/B]

So, I found only one place online with this specific error at [http://groups.google.com/group/iitdlug/browse_thread/thread/e239e6ba567211cd](http://groups.google.com/group/iitdlug/browse_thread/thread/e239e6ba567211cd), but it was for kubuntu, and there were three basic answers.

1)[ http://sidux.com/index.php?name=PNphpBB2&file=viewtopic&t=21496&highlight=]("http://sidux.com/index.php?name=PNphpBB2&file=viewtopic&t=21496&highlight=") which went over my head

2) "You can install Linux inside windows Or Windows inside Linux to avoid such 
 problem.", which seems undesirable

3) boot from external source, disc, usb etc. which also seems undeirable


_SELF DIAGNOSIS?_

Seems  that grub boot loader is being destroyed/moved by windows somehow. How  do I keep this from happening? As a side question, possibly for a  different thread/forum, if that is the case, why can't the windows  loader still boot into windows? 


[U]WHAT'S NEXT?
[/U]So, I have several solutions that seem relatively/very close.

The first solution stated earlier in the problem (that went over my head),
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)  which seems like it may work and
[http://ubuntuforums.org/showthread.php?t=1569798](http://ubuntuforums.org/showthread.php?t=1569798) which seems like the closest.

Anyway,  i am a little gun shy after two epic failures. I am back to factory  install, a clean 7 install, and am willing to try again with a little  guidance. 

Thanks for everything,
Mike

---

### Post by Jakey_TheSnake on 2010-09-11
I'm dual booting them with no problem. The only time Windows should destroy the GRUB is if you do a fresh install after Ubuntu is already installed (because the Windows bootloader is ****). 

During your first install problem you could've booted it up with a live disk and repaired GRUB, the second looks like it was trying to do a network boot...

So at the end of the day I don't know what your previous problems were, it's hard to diagnose them now, but take confidence from the fact I run the two side by side with no problems whatsoever. All I can think for your first one is that Windows screwed up with the disk check (odd because I've let it run fdisk etc. before). 

Sorry for the lack of answers, just hopefully a confidence booster!

---

### Post by jtarin on 2010-09-11
From what I understand Dell has some front end hack to protect the system.This operation will not affect that or will Dell's hack affect this, but nevertheless....Install Ubuntu in it own partition and during install you will need to install Grub to the / (root) of that partition. Then you will use EasyBCD to edit your Windows Boot Manager to boot Windows and Linux. Link to EasyBCD is in my signature.[[COLOR="Red"]Link to EasyBCD tutorial[/COLOR]]("http://neosmart.net/forums/showthread.php?t=6350") (scroll down for illustrated Ubuntu/Windows7 install by forum member Ashoka). I've attached a pic of the place in the installation where you will set Grub to / know your partition before installing._DO NOT INSTALL GRUB2 TO MBR_

---

### Post by sandyd on 2010-09-11
> **anguspodgorny said:**
> Hello All,


_INTRODUCTION_ (feel free to skip if you don't care)

I  will try to keep this as concise as possible. Quickly, it's great to  see a forum as civil as this. I have looked at a lot of software forums,  and people are quite harsh over electronic media. Thanks to all who  have set this up, and continue to make this accessible. Also, if I  perform any forum faux pas please alert me, so future posts can be  better.

 I am brand new to Ubuntu, so i apologize for my  ignorance, and I will make an effort to get up to speed as quickly as  possible. Also, I did search around for this topic and didn't recognize  an explicit answer to my problem. 


_PROBLEM_

I  just bought a Dell 14R(N4010) laptop, and installed Ubuntu 10.04  alongside Windows 7. Install went fine, and used Ubuntu for several  days. Then I booted into 7, it ran a disc check of some sort, and  continued working. Logged out, went home, tried to boot Ubuntu and got  basically nothing. I was able to get into bios and boot options menu,  but if I let it try to boot from the hard drive i would just get a blank  screen with flashing cursor(no input). After a ton of passed  diagnostics, Dell sent out a new hard drive. 
[B]
you should have resized the partition from Control Panel -> Administrative Tools -> Computer Management -> Disk Management. Windows 7 hates when you touch its partitions, and so does vista.

[/B] The second install was almost identical, except in that instead of blank cursor, this time i got

no module name found
Aborted. Press any key to exit.

<<After pressing a key>>
Copyright (C) 1997-2008 Intel Cooperation
For Atheros PCIE Ethernet Controller v2.0.2.3(06/18/10)

Check Cable Connection!
PXE-M0F: Exiting Intel PXE ROM.
Operating System not found
[B]Try installing using the method below

[/B] So, I found only one place online with this specific error at [http://groups.google.com/group/iitdlug/browse_thread/thread/e239e6ba567211cd](http://groups.google.com/group/iitdlug/browse_thread/thread/e239e6ba567211cd), but it was for kubuntu, and there were three basic answers.

1)[ http://sidux.com/index.php?name=PNphpBB2&file=viewtopic&t=21496&highlight=]("http://sidux.com/index.php?name=PNphpBB2&file=viewtopic&t=21496&highlight=") which went over my head

2) "You can install Linux inside windows Or Windows inside Linux to avoid such 
 problem.", which seems undesirable

3) boot from external source, disc, usb etc. which also seems undeirable


_SELF DIAGNOSIS?_

Seems  that grub boot loader is being destroyed/moved by windows somehow. How  do I keep this from happening? As a side question, possibly for a  different thread/forum, if that is the case, why can't the windows  loader still boot into windows? 


[U]WHAT'S NEXT?
[/U]So, I have several solutions that seem relatively/very close.

The first solution stated earlier in the problem (that went over my head),
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)  which seems like it may work and
[http://ubuntuforums.org/showthread.php?t=1569798](http://ubuntuforums.org/showthread.php?t=1569798) which seems like the closest.

Anyway,  i am a little gun shy after two epic failures. I am back to factory  install, a clean 7 install, and am willing to try again with a little  guidance. 

Thanks for everything,
Mike
Alright. lets get this fixed...

First, do you have the windows 7 recovery disc?
If you do, stick it in, and restore windows. Alternatively, you can do [http://www.ehow.com/how_4836283_repair-mbr-windows.html](http://www.ehow.com/how_4836283_repair-mbr-windows.html)
Once windows is up and running, do this.
Go to Control Panel -> Administrative Tools -> Computer Management -> Disk Management.

At that that time, post a screenshot.

thnx

---

### Post by RJ12 on 2010-09-12
I bet it is the new Dell DataSafe program that is erasing GRUB...

Try Uninstalling these programs when you get it fixed,
 Dell DataSafe Local Backup
  Dell DataSafe Local Backup - Support Software

Also you should probably just need to install GRUB from the LiveCD
I don't remember how to do that, but someone else here can probably tell you.

---

### Post by oldfred on 2010-09-12
You can uninstall the offending Dell software. If it is new or different the grub folks are looking for the various win7 software that is corrupting grub. Known problem.

Grub team looking for info:
[http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html](http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html)
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)
[http://linux.slashdot.org/story/10/08/28/2112208/Some-Windows-Apps-Make-GRUB-2-Unbootable](http://linux.slashdot.org/story/10/08/28/2112208/Some-Windows-Apps-Make-GRUB-2-Unbootable)
In Windows 7, I had to remove Windows 7 DataSafe.
HP ProtectTools, Dell Recovery, and a few others write into MBR meierfra.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)
Dell Media direct or Uninstall Dell DataSafe issues with MBR
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)

---

### Post by anguspodgorny on 2010-09-18
Wow, thanks everybody for the input. I haven't tried anything yet, but should be giving some of these suggestions a whirl this weekend. I will let you know how it goes, and if I have any further questions. Thanks again for everything. 

Mike

---

### Post by anguspodgorny on 2010-09-19
Well, I finally have it up and running, and it certainly turned out to be the Dell DataSafe junk. Wow, what a simple fix for what turned out to be a huge headache for me. Oh well, now I know. Again, thanks to all for the help and I look forward to a long life with Linux, and continued participation in this forum.

Mike

---

### Post by jtarin on 2010-09-19
And your final solution was........?

---

### Post by anguspodgorny on 2010-09-19
I uninstalled the Dell DataSafe software that came with my machine. Seems it was writing where it shouldn't and destroying GRUB.

---

### Post by RJ12 on 2010-09-19
Glad I was able to help :)

It would be a big help to others though if you could mark this thread as solved using the "Thread Tools" button at the top of the first post
:)


Thanks!

---

