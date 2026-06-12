---
title: "Cannot Enable Wireless Radio"
date: 2008-08-25
forum: Networking &amp; Wireless
---

### Post by bkmintie on 2008-08-25
Hello all, I have recently installed Hardy Heron on my old Inspiron 700m to have as a "beater" laptop in the living room.
However, I cannot get wireless to work.

I believe it has something to do with the physical switch not responding to FN+F2 command to enable wireless radio (as the LED won't light up)

---

### Post by itendo on 2008-11-01
from one 700m w/ hardy owner using it as an ubu beater in the living room to another, the fact that the LED does/not light up isnt too significant. I found that the button's functionality didnt really change the problems i was having. the intel b/g chipset can be finicky.

youll find the 700m has a lot of caveats within ubuntu. to go further with your problem though, i found that hard-lining it with an ethernet cable first, and setting up the connection to the network, then switching to wireless/roaming after worked. it seems a faulty method, but it worked. (make sure you make regular backups of your xorg.conf because when you manipulate some settings, ubuntu will be semi-prone to messing up your widescreen's settings.)

however, in the taskbar, under the networks settings (where the mobile networks should show up) there is a "roaming mode" switch you can enable under the right click menu of the icon.

---

