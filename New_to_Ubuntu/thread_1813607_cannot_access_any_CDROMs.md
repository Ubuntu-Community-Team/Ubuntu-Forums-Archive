---
title: "cannot access any CDROMs"
date: 2011-07-28
forum: New to Ubuntu
---

### Post by Foobarz on 2011-07-28
Whenever I put a cd into my cd drive, it gives me this:

Could not display "cdda://sr0/".
Error: DBus error org.freedesktop.DBus.Error.ServiceUnknown: The name :1.389 was not provided by any .service files
Please select another viewer and try again.

And another thing: When I put music in, at least an audio cd is detected and mounted (there is that little arrow next to the cd). When I put my XP installation disc in, however, nothing is detected. And for both cases, there is no folder in /media or /cdrom. Is something wrong with my computer? Is something wrong with the way I understand this mounting stuff, since I'm used to drive letters, being Windowed all my life?

---

### Post by jerrrys on 2011-07-29
as far as i know windows cd cannot be read by linux,  maybe somehow with wind, but not your xp install disk.  that disk i would think is an .iso and can only be install at boot time.  at least thats the way i remember it.  havent ran windows in years,

---

### Post by Mark Phelps on 2011-07-29
If you're putting in your Windows XP installation disk to INSTALL it, that's NOT going to work because Linux can't run Windows apps from CD.

However, you SHOULD be able to see the contents of the disk regardless.

It's NOT that Linux can not read Windows CDs; it's just that Linux (generally) can't run programs (or use drivers) from Windows CDs.

---

### Post by Foobarz on 2011-07-30
Yeah I know, but I cant see the contents. JUST ONCE ONLY ONCE I got lucky and was able to see the contents of the disk, but now when I put the disc in, it never reads. What the heck?

---

### Post by anewguy on 2011-07-30
Does it spin up and then look like it does the "register" hit?

Perhaps you need to mount it - have you tried creating your own mount point and then trying to mount the device to that mount point?  If not, it's something we could try.

Dave ;)

---

### Post by Miljet on 2011-07-30
If your CDs work in another computer, you probably have a bad CD drive. Drive failure is more common than most people think. Or it could possibly be a dirty lens on the drive reader. In either case it is easier to just replace the drive, and they are dirt cheap now-a-days.

---

### Post by Foobarz on 2011-07-31
Yeah, so here is the problem. The CDROM has worked once on my Ubuntu, and never again (black magic). Any other CD works fine on my Ubuntu machine. If I shutdown and boot into Vista (SAME computer), the CD miraculously works. WHAT THE HECK? 

PS: Miljet, I dont think I can (easily) replace the cd drive on my laptop. . .

---

### Post by Miljet on 2011-07-31
I got the impression from your original post that you were having problems mounting/reading any CDs. If the drive works under Vista but not Ubuntu, that would certainly indicate that the problem is not the drive.

---

### Post by anewguy on 2011-08-01
> **Foobarz said:**
> ....Any other CD works fine on my Ubuntu machine. If I shutdown and boot into Vista (SAME computer), the CD miraculously works. WHAT THE HECK?....
I'm a little confused here - are you saying a single disk doesn't work?  If so, what is the disk and where was it recorded?

dave ;)

---

