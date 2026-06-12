---
title: "Grub issues"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by GodlySoup on 2009-08-27
Problem! I was installing ubuntu on my girlfriend's hard drive while it was hooked into my computer, with my hard drive hooked in as well. Her hard drive works fine, but now, without hers hooked in, my hard drive is trying to start ubuntu and errors. I was sure that I was just installing it onto her hard drive when I installed it.

How do I uninstall jaunty, if that is the problem? What directory would it be in so I could just delete it? I'm running on a live cd right now.

I'm not sure what I should do. Please help.

GS

---

### Post by Shpongle on 2009-08-27
im guessing that the grub entry is messed up for your hard disk , maybe when installing on to your gf's hd the grub entry changed hers to be the primary hd and yours to be the secondary, just a thought , wish i could help more ,

although it shouldn't have been a problem,  maybe try reinstalling grub?,

what errors are you getting?

---

### Post by stalkier on 2009-08-27
Your GRUB is messed up. Try this [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) It says Windows but should work for you.

---

### Post by GodlySoup on 2009-08-27
It does the GRUB boot-up, so yes.
It says Error 17. Then stops loading.

Perhaps it would be better to tell you that I'm running Vista on my hard drive. I don't want my data ruined if I can manage it.

---

### Post by matchstich on 2009-08-27
had just had problems with grub error 15  perhaps one of these can help you

[http://ubuntuforums.org/search.php?searchid=63483688](http://ubuntuforums.org/search.php?searchid=63483688)

[http://ubuntuforums.org/showthread.php?t=224351&highlight=defrag](http://ubuntuforums.org/showthread.php?t=224351&highlight=defrag)

[http://members.iinet.net.au/~herman546/p15.html#How_to_get_GRUBs_Command_Line_to_investigate_a_computer](http://members.iinet.net.au/~herman546/p15.html#How_to_get_GRUBs_Command_Line_to_investigate_a_computer)


finally got mine to work again but am not sure how i did it.

---

### Post by GodlySoup on 2009-08-27
These solutions all seem to help only if I have Ubuntu installed on my hard drive. What I'm wondering is how to get rid of the GRUB all together. Is it the Boot folder in the C:\ drive? Perhaps it's stored somewhere else...

---

### Post by louieb on 2009-08-27
Is this widows only computer? Sounds like it. and you put another hard drive in and installed Ubuntu on the drive you just put in? 

> What directory would it be in so I could just delete it?  Not in any directory in windows. Its on the drive you put Ubuntu on. 

Sounds like when you installed Ubuntu the install change the MBR of your boot drive. 

If its window only and you have you window CD the easiest way to fix is boot the windows cd and go to recovery console and run **fixmbr**

If  you don't have a win CD other ways to restore win boot code to the MBR can be found here [IDBS Remove Replace Uninstal Grub]("http://members.iinet.net.au/%7Eherman546/p18.html")

---

### Post by raymondh on 2009-08-27
> **louieb said:**
> 

If  you don't have a win CD other ways to restore win boot code to the MBR can be found here [IDBS Remove Replace Uninstal Grub]("http://members.iinet.net.au/%7Eherman546/p18.html")

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

could be another option, albeit requiring the OP to download and burn a CD.

---

### Post by GodlySoup on 2009-08-27
> **louieb said:**
> If its window only and you have you window CD the easiest way to fix is boot the windows cd and go to recovery console and run **fixmbr** 

This console... do you mean the command prompt on the Widnows CD?

---

### Post by raymondh on 2009-08-27
> **GodlySoup said:**
> This console... do you mean the command prompt on the Widnows CD?

yes

in Vista and when you get a command prompt ... the wordings are

bootrec.exe/FixMbr

---

### Post by GodlySoup on 2009-08-27
Nvm. I googled the fix mbr thing and got it fixed. 

Thanks!

GS

---

