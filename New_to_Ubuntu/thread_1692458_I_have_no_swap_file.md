---
title: "I have no swap file"
date: 2011-02-21
forum: New to Ubuntu
---

### Post by BananaPeal on 2011-02-21
Hello,

 I'm running a full install off USB and every once in awhile, firefox turns blue for a sec or so. I imagine it's something to do with saturating the usb link with read/writes... but I've already mounted the tmp folder to tmpfs as well as told firefox not to cache anything...

Could my absence of a swap space be causing this? My ram (4GB) never fills up and I query the tmpfs and it's usually empty during the course of a day too. So, seems to me like this is just side-effect of running from usb, does this sound reasonable, or could I mount more folders to ram to improve performance?

Look forward to your insights!

---

### Post by Keiran230 on 2011-02-21
You're correct about the USB bandwidth issue. Flash drives have a limited read and write speed which is kinda horrible (and writing is slower than reading).

Swap is not used unless RAM is full or nearly full. With 4 GB, you probably won't easily max that out. If you want to try adding a swap partition anyway, you can use the swapon and swapoff commands after creating one. GParted's the easiest way to create one, but there's a command-line way with mkfs.swap and fdisk too.

If Firefox is the only issue, it may be because of Firefox's size. Firefox 3.x is very large, which means there would be a lot of transferring from USB flash memory to RAM and back. Maybe another browser would work better, like Chromium, Galeon, Dillo or some other.

---

### Post by BananaPeal on 2011-02-21
Thanks for your reply.
 
I will try another browser.

---

