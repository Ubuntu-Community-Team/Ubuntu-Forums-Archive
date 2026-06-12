---
title: "ATI Radeon 7500 P128 driver needed"
date: 2011-08-27
forum: New to Ubuntu
---

### Post by Autodave on 2011-08-27
I need a driver for an ATI Radeon 7500 series video card.  Where can I find that and how do I install it?
Thanks in advance!

---

### Post by mikebilak on 2011-08-28
Have you tried this site yet???
 
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by realzippy on 2011-08-28
edit:
see post #6

---

### Post by Mark Phelps on 2011-08-28
Do wish folks would do some research BEFORE telling others to use the Additional Hardware option ...

There are NO drivers for your ATI card beyond those already installed on your system.  ATI dropped Linux driver support for your card years ago and the only working drivers now are the default open-source drivers -- which are installed automatically when you install Ubuntu.

Don't go hunting around for other drivers  They won't work, they will trash your display, and you will then have a LOT of work ahead of you to remove them and replace them with the drivers you already have in place.

---

### Post by realzippy on 2011-08-28
If jockey offers a driver,it might work.I was not talking about the ATI download driver homepage,so calm down.
According to [this]("http://wiki.cchtml.com/index.php/9.4") list,it should work with fglrx,
this list might not be complete,that's why I used "If"..

Jockey never offers an ati driver for not supported cards,as ati homepage does.

---

### Post by realzippy on 2011-08-28
Update:
The radeon 7500 never was supported by any fglrx (catalyst) linux driver.
So additional driver gui won't offer also anything.
You have to stay with that already installed free ati driver,
although some modified versions may exist,eg. in xorgedgers ppa.

---

