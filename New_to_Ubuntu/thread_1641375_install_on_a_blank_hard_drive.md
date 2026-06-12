---
title: "install on a blank hard drive?"
date: 2010-12-08
forum: New to Ubuntu
---

### Post by treverflume on 2010-12-08
Hi I am absolutely new and have never used Ubuntu or Linux. So I downloaded Ubuntu 10.10 ISO file and used Infra Recorder to burn the ISO file to a CD.  I had Windows xp professional on the computer I am trying to install Ubuntu on but deleted that partition using the xp setup CD. I think the hard drive is blank after I did that? not really sure :p Anyways I made sure the computer boots from the CD first and put it in. I get a message saying "non-system disk or disk error" "replace and strike any key when ready". If i strike a key it just comes up with the same message.  And I must have burned the ISO right because I used the "try it" feature on my main computer and it worked just fine. I'm unsure what to do and would appreciate any help given. THANKS!!:D


EDIT
thank you all so much!!! I stalled the ISO file onto a USB drive and it worked perfectly!

---

### Post by kesman on 2010-12-08
Maybe you have to hit some key to boot from CD? Review you BIOS settings again, and be careful during the boot process.

If the cd worked on another computer, then the CD-drive could be broken in the other computer you are trying to install it to, or then the BIOS settings still aren't right.

One solution could be installing it with a usb stick if you have one, try [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) to make a bootable Ubuntu stick and give it a try.

---

### Post by sikander3786 on 2010-12-09
> non-system disk or disk error

+1 to everything said by **kesman**.

This error surely has nothing to do with Ubuntu at all :-)

Re-check the Bios boot order and make sure CD-Drive is your first boot device. Make sure the CD/DVD Drive is in proper working condition and if not, try booting from USB (if Bios is capable of booting a USB drive).

---

### Post by C.S.Cameron on 2010-12-09
You might try checking the MD5SUM of your downloaded iso.

---

