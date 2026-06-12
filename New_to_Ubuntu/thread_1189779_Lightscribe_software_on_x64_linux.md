---
title: "Lightscribe software on x64 linux"
date: 2009-06-17
forum: New to Ubuntu
---

### Post by Gp. on 2009-06-17
Hey,
I need this:
[http://www.lightscribe.com/downloadsection/linux/index.aspx?id=1372](http://www.lightscribe.com/downloadsection/linux/index.aspx?id=1372)

I got the .deb package, but it refuses to install. See screenshot.
Can I force a x86 program to install on x64?

---

### Post by 73ckn797 on 2009-06-17
You probably cannot force the install. i386 is 32bit software and would not work on 64bit, more than likely, unless it has been packaged with other necessary dependencies to make it work.

---

### Post by Gp. on 2009-06-17
So how am I gonna get this to work?

---

### Post by 73ckn797 on 2009-06-17
Install the 32bit Ubuntu.

I have not used the program and do not attempt to install 32bit software on a 64bit OS.

Running it in Windows using a virtual machine would work. Of course you would have to get the Windows version of the software.

---

### Post by mikechant on 2009-06-18
> I have not used the program and do not attempt to install 32bit software on a 64bit OS.

Actually it's quite common to install 32 bit packages on a 64 bit system - just a bit of messing about required.

This article includes some info about how to do it for a different package:
[http://mjhutchinson.com/journal/2006/11/05/install_iraf_on_ubuntu_edgy_amd64](http://mjhutchinson.com/journal/2006/11/05/install_iraf_on_ubuntu_edgy_amd64)
Look out for the dpkg --force-architecture -i command

I think it's quite likely that you'll get missing dependancies (32 bit libs) which you'll then have to also manually install with the dpkg --force-architecture -i command.


Additional:
I just found this ubuntu forum thread about installing lightscribe in an old 64-bit release (7.10) of Ubuntu:
[http://ubuntuforums.org/showthread.php?t=623251](http://ubuntuforums.org/showthread.php?t=623251)
Which led to this more up to date howto:
[http://howtopenguin.blogspot.com/2008/05/how-to-install-lightscribe-software-on.html](http://howtopenguin.blogspot.com/2008/05/how-to-install-lightscribe-software-on.html)
I would look at this first.

---

### Post by 73ckn797 on 2009-06-18
> **mikechant said:**
> Actually it's quite common to install 32 bit packages on a 64 bit system - just a bit of messing about required.

This article includes some info about how to do it for a different package:
[http://mjhutchinson.com/journal/2006/11/05/install_iraf_on_ubuntu_edgy_amd64](http://mjhutchinson.com/journal/2006/11/05/install_iraf_on_ubuntu_edgy_amd64)
Look out for the dpkg --force-architecture -i command

I think it's quite likely that you'll get missing dependancies (32 bit libs) which you'll then have to also manually install with the dpkg --force-architecture -i command.


Additional:
I just found this ubuntu forum thread about installing lightscribe in an old 64-bit release (7.10) of Ubuntu:
[http://ubuntuforums.org/showthread.php?t=623251](http://ubuntuforums.org/showthread.php?t=623251)
Which led to this more up to date howto:
[http://howtopenguin.blogspot.com/2008/05/how-to-install-lightscribe-software-on.html](http://howtopenguin.blogspot.com/2008/05/how-to-install-lightscribe-software-on.html)
I would look at this first.

Then I stand corrected. I know it has been done as alluded to in my earlier post in this thread but knew nothing about this particular situation. I will bow out from here.

---

### Post by FerN(SA) on 2009-06-25
Check this howto out:

[http://ubuntuforums.org/showthread.php?t=999532&highlight=lightscribe](http://ubuntuforums.org/showthread.php?t=999532&highlight=lightscribe)

---

