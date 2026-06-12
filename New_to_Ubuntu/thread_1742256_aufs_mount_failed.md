---
title: "aufs mount failed"
date: 2011-04-28
forum: New to Ubuntu
---

### Post by dwhite on 2011-04-28
i have made a bootable usb with 11.04, and get the following just after the splashcreen comes up:

```
(initramfs)mount: mounting aufs on /root failed: Invalid argument aufs mount failed
```I have been searching and have seen that this problem has been seen before but i see no fixes posted.  Any  ideas?

I've tried two different computers and get the same, have reformated the usb with the iso and get the same, have redownloaded the iso and reformated the usb and get the same


some info about my system on screenshot, however also tried on another machine so don't believe that is the problem, maybe i should try another usb drive?

---

### Post by trollger on 2011-04-28
It could be a bug in the usb installation script. Either use a different USB installation script(Unetbootin, Ubuntu Startup Creator) or you could probably just use a cd and forget about it.

It is verry unlikely that it is your proccesor or the usb drive/stick.

---

### Post by dwhite on 2011-04-28
> **trollger said:**
> Either use a different USB installation script(Unetbootin, Ubuntu Startup Creator) or you could probably just use a cd and forget about it.


good idea thanks, i didn't think of trying a different installer, i'll give it a try.

---

### Post by dwhite on 2011-04-28
ok, downloaded the 11.04 iso to my laptop running 10.10 used the "startup disk creator" to make the usb drive and now everything is working great.

Prior to that i had used a window based machine to download and install following the direction on the Ubuntu official site (which directs you to go to Pendrivelinux.com to get the installer)  I tried this four times and got the "aufs mount failed" problem every time (tried 4 different times using two different windows computers), so it appears it is the Pendrivelinux.com installer that is the problem.

thanks to trollger for suggesting this :)

---

