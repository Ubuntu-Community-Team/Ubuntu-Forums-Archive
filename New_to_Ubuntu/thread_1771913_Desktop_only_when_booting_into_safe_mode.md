---
title: "Desktop only when booting into safe mode"
date: 2011-05-30
forum: New to Ubuntu
---

### Post by Protar972 on 2011-05-30
Wasn't really sure where to post this.

Fresh wipe and install of Ubuntu 10.10 on an older HP Pavilion ze4560us.

I can get a fully functioning desktop if I boot into the safe mode option available at login.

If I choose the regular login I get the multicolored desktop, start up sounds, and a cursor but no task bars and no right click menus. I can switch over to a shell and log in there but I'm not sure how to troubleshoot this.

Any help would be appreciated.   Updates were installed during install.


Todd

---

### Post by jtarin on 2011-05-30
Try creating another user and see if that makes a difference.

---

### Post by wildmanne39 on 2011-05-31
> **Protar972 said:**
> Wasn't really sure where to post this.

Fresh wipe and install of Ubuntu 10.10 on an older HP Pavilion ze4560us.

I can get a fully functioning desktop if I boot into the safe mode option available at login.

If I choose the regular login I get the multicolored desktop, start up sounds, and a cursor but no task bars and no right click menus. I can switch over to a shell and log in there but I'm not sure how to troubleshoot this.

Any help would be appreciated.   Updates were installed during install.


ToddHi, I have an old hp laptop and I have to use noacpi, or noapic then when I get to the desktop I install the drivers for my video card and that fixes it, I am assuming you have a nividia card? Sorry it took me a while to find this guide it will tell you how to add the noacpi to the kernel at startup.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Protar972 on 2011-05-31
Thanks for the link. I'll investigate it in more detail when I have a little time.

It looks to me like that is kind of a last resort fix so I'm a little hesitant but I suppose It wouldn't be a huge issue as this is a fresh install and would loose nothing if it all goes belly up.

It's a Mobility Radeon Chipset, if that matters much.

---

### Post by jtarin on 2011-05-31
ATI Mobility Radeon Chipset? What's the number?

---

