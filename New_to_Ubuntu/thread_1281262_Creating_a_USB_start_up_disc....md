---
title: "Creating a USB start up disc..."
date: 2009-10-03
forum: New to Ubuntu
---

### Post by OllieGab on 2009-10-03
I have used the Make USB Startup Disc function in 9.04 a few times without problems. However, the last couple of times, after downloading a **.iso** file to be used (Linus distros) I get an error message:
 "This is not a desktop install CD and thus cannot be used by this application."
I have not actually burned the iso file to a CD first but I shouldn't have to, should I? There is a "Other..." option so I assume that the application doesn't really care whether it sits on my harddrive or on a CD...or am I wrong?

Ollie

---

### Post by powel212 on 2009-10-03
> I have not actually burned the iso file to a CD first but I shouldn't have to, should I?

Nope. It doesn't matter.

But, if you are getting that message I am assuming the disc image you have is probably an alternate install disc as aposed to a live disc.

I have found the best way to create a USB startup disc is to put a live cd in the CD drive boot from it and use it to install to the to the flash drive.

I hope that helps.

Powel

---

### Post by Paqman on 2009-10-03
> **OllieGab said:**
> However, the last couple of times, after downloading a **.iso** file to be used (Linus distros) I get an error message:
 "This is not a desktop install CD and thus cannot be used by this application."

Are these .iso's Ubuntu? I'm not sure if that tool is able to use non-Ubuntu .iso's. You could try using [Unetbootin]("http://unetbootin.sourceforge.net/"), it does the same job and definitely works with a wide range of distros.

---

### Post by OllieGab on 2009-10-03
&#305; certainly thought I'd gone for the 'live CD' option when I downloaded...but I'll try your method now. 
Just to clarify what you were saying (I'm a bit of a newbie obviously!) : I'll burn the iso image to a CD, boot up using that CD and when it comes to install (and presumably it will ask where I'd like to install it) I'll just select my USB stick as the installation target. Is that how you meant?

Cheers

---

### Post by powel212 on 2009-10-03
> Just to clarify what you were saying (I'm a bit of a newbie obviously!) : I'll burn the iso image to a CD, boot up using that CD and when it comes to install (and presumably it will ask where I'd like to install it) I'll just select my USB stick as the installation target. Is that how you meant?

NO!

Burn it to disc

boot it as "use without any changes to my system".

once booted go to administration-create usb startup disc then point it to the usb flash drive.

Powel

---

