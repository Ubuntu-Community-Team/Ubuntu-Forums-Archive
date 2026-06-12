---
title: "hi and help :)"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by tengteng on 2009-05-13
hi everybody.. 
im an ubuntu newbie and i just installed jaunty on an acer travelmate 3270 laptop 2 days ago.. dual booting with xp home.
i like jaunty very much so far and i would lke to ask for help on two problems that i have had re my install..
1. the laptop usually hangs during shutdown and the black screen with a blinking cursor and it says something about [  ] shutdown or something like that.. and
2. I get errors when i plug in my external usb hard drive (320 gig wd).  says something about unable to mount.. last night i did chkdsk on xp on the usb drive and it mounted ok but today its acting up again..
id really like to resolve these problems cos i like jaunty and wanna continue using it..
hope this post is ok.. i dont know much about tech talk..

thanks in advance!

---

### Post by HavocXphere on 2009-05-13
> **tengteng said:**
> 1. the laptop usually hangs during shutdown and the black screen with a blinking cursor and it says something about [  ] shutdown or something like that.. and
2. I get errors when i plug in my external usb hard drive (320 gig wd).  says something about unable to mount.. last night i did chkdsk on xp on the usb drive and it mounted ok but today its acting up again..
id really like to resolve these problems cos i like jaunty and wanna continue using it..
hope this post is ok.. i dont know much about tech talk..

thanks in advance!
You'll need to provide more detail on issue #1.

#2 is occurs when an NTFS drive is not disconnected properly (Safely remove device) or the computer crashes while it is in use. The drive is then flagged (not 100% correct technically but yeah) as not being cleanly removed and ubuntu doesn't want to touch it. The easiest way to resolve this is to boot into windows and shutdown again. Or you could force mount (just google this) it under ubuntu to force it being mounted even though its not "clean".

---

### Post by tengteng on 2009-05-13
thanks for the quick reply:)
re #1 i noticed that if i remove my usb mouse before i shutdown, the laptop usually turns off properly but still not 100% of the time.. if it hangs on shutdown i have to take off the battery to turn off the laptop cos my power button is kinda loose and i cant press it for 8 seconds to off it.. :)

---

### Post by tengteng on 2009-05-13
oh yeah regarding #2 i noticed that in computer/file system/media folder inside it are two folders with my external hard drive's name on it with the no read emblem on it.. is it related to why i cant mount the usb drive properly?

---

