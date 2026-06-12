---
title: "urgent help needed?"
date: 2009-09-25
forum: New to Ubuntu
---

### Post by nitishgarg91 on 2009-09-25
when i install ubuntu 9.04 inside windows using the CD of ubuntu, it prompts to restart. After restart it loads my Windows Xp only and not ubuntu.
It is written that ubuntu will start and it will take 10-15 min to install rather it opens my windows..
I have tried many times but nothing happens.
Help...

---

### Post by Cypher on 2009-09-25
I presume you are trying to install Ubuntu using WUBI, if so can you see if what's stated on [this page]("http://wubi-installer.org/faq.php") sounds about right?

---

### Post by nitishgarg91 on 2009-09-25
yes!!i m following the same method but as it says it will reboot the pc and then installation will continue for 10-15 mins, but when i m installing it boots my windows only..
Do i need to make some changes in the boot.ini file??
currently there is written 

C:\wubildr.mbr = "Ubuntu"

i have installed it in c drive..
help....

---

### Post by gdonwallace on 2009-09-25
Sounds like WUBI didn't write out the master boot record correctly.  That's really odd.  I would suggest uninstall / reinstall and see if that corrects it.  You can do this through the add/remove programs in windows.

Also, you can boot the LiveCD with Ubuntu and do the install through Ubuntu.  It will detect your hard drive and find that Windows is already installed; and ask you how much space you want to use to install Ubuntu.

---

### Post by nitishgarg91 on 2009-09-25
i have reinstalled many a times but in vain...
using the live CD as i get onto the main screen of ubuntu my pc just turns off abruptly...

should i try some previous version of ubuntu may be ubuntu 8.04..
help....:confused:

---

### Post by clive littlewood on 2009-09-25
Hi

I would check the integrity of the CD. If you burned from an ISO did you check the MD5sum.

If not sure I would try a new download and burn another CD.

Clive

---

### Post by nitishgarg91 on 2009-09-25
i m installing from the original CD of ubuntu that is supplied free...
one more question : 
should ubuntu be installed in the drive in which my other os in installed or is it not necessary..

---

### Post by buddhaPIMP on 2009-09-26
I've had problems with the live cd too - what worked for me was i DL'd Wubi  and took it from there, the setup is pretty straight forword, i just did this yesterday actually and now have a dual boot system with XP.

---

### Post by hansdown on 2009-09-26
Hi nitishgarg91.

You can choose to dual boot ubuntu and windows...

This how to is a bit old, but is still good advice.

[http://video.google.com/videoplay?docid=-2369893842637434537#](http://video.google.com/videoplay?docid=-2369893842637434537#)

Or you can do a wubi install.

[http://www.howtoforge.com/wubi_ubuntu_on_windows](http://www.howtoforge.com/wubi_ubuntu_on_windows)

---

