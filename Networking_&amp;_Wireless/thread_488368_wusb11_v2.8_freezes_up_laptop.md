---
title: "wusb11 v2.8 freezes up laptop"
date: 2007-06-30
forum: Networking &amp; Wireless
---

### Post by hcjc92 on 2007-06-30
Okay, I used 6.10 for quite a while, card worked great and I was really happy with it.
Wiped Ubuntu to use Gentoo, which I got sick of very quickly with all the compiling and what not.
Came back to Ubuntu to find Fiesty was the supported (well, not beta anymore) version.

I installed that, thinking it would be just like before, but better. I was mostly using my laptop at home with a LAN cable plugged into the back, and it was working great. When I went off to an internet cafe with my linksys wusb11 v2.8 (which, i believe has a prism chipset, atleast, thats what the windows drivers are labeled.) It worked for a while, and then froze up. This always happens after a while with the wireless card plugged in, sometimes after half an hour, sometimes after a day. I'm plugged into the router via an ethernet cable right now, and I'm on 5 days of uptime i believe. Now, this same thing would happen when i was using gentoo, and when it would happen on gentoo, after a reboot, when it was showing all the boot up stuff on screen, it would crash, and show a really debug message.

I asked about it then, and everyone said it was hardware, but if I use a dapper live cd, i don't get this problem, and a Fiesty live cd, I do get the problem.

Anyone have any idea how to fix this? Also, I was thinking of just trying to use ndiswrapper for the card, but the problem is that there's a kernel module for it, so ndiswrapper won't do it. Whats the module config file, so that I can make it not load the prism module on boot, and then try ndiswrapper to see if that fixes the freezing.

Thanks for any help, and I apologize for any messed up sentences, its 3:26 AM for me, not thinking my best at the moment.

---

### Post by hcjc92 on 2007-06-30
bump

and, well, it is infact an amtel chip set, using the at76_usb module, which i removed temporarily and used ndiswrapper, which didn't work at all.

---

### Post by hcjc92 on 2007-07-02
bump

no one knows whats wrong? :-(

---

