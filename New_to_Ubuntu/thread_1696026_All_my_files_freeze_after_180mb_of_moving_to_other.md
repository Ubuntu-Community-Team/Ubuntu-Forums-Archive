---
title: "All my files freeze after 180mb of moving to other HDD"
date: 2011-02-26
forum: New to Ubuntu
---

### Post by hopelessone on 2011-02-26
Hi,

I ran fcsk on both HDD's
i've got enough space on both
i checked permissions

Why do they freeze? What can I do to move those files?

Thanks

---

### Post by acrazyplayer on 2011-02-26
the same thing happened to me but in a different way, i tried moving files to a usb and it started out at 5 MB/s then kept going slower and slower until it would have took a insanely long time. I'm pretty sure it a bug in nautilus but im not 100% you can try a terminal to see if that works better.

just use the "mv" command like this "mv /home/*username here*/Downloads /home/*username here*/Desktop"

in that example I just copied the whole Downloads folder into my Desktop.

---

### Post by hopelessone on 2011-02-26
No. It's the same thing reaches 180mb and nautilus freezes...
have to reboot everytime...

IS the HDD on the way out? How can I tell? any other diagnostic programs i can run to test if its a broken HDD?

Many thanks...

---

### Post by hopelessone on 2011-02-26
Even ```
gksudo nautilus
```

Freezes at 180 mb

wtf doh...

---

### Post by owise1 on 2011-02-26
try launching nautilus from the command line and see if any error messages come up

---

### Post by samacaster on 2011-02-26
What is the SMART status of your HDD?

---

### Post by hopelessone on 2011-02-26
> What is the SMART status of your HDD?

Hi, how can check it?

The filesys is fragged 19% (from torrents) so i moved some files off it about 20gb and moved 1 file back it paused momentarily on 180mb but successfully transfered it over...

Might try to move all off and format and move back...

---

### Post by acrazyplayer on 2011-02-27
to view the SMART status just go to "system, administration, disk utility" and choose your disk and then in the top right side of the window you will see a couple things regarding SMART, that is assuming your HDD supports SMART and it is turned on in your BIOS. also you can benchmark your drive and see what that does during the read speed test. does that even fail? good luck

---

