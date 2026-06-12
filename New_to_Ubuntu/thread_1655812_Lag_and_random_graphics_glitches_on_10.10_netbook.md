---
title: "Lag and random graphics glitches on 10.10 netbook"
date: 2010-12-30
forum: New to Ubuntu
---

### Post by YagerX on 2010-12-30
I installed the netbook interface over the 10.10 (x64) desktop edition (using wubi) on my toshiba laptop to try out but random graphical glitches would appear (title bars of windows would have random "static") and the mouse would be almost unusuable (but only in programs, never over the desktop or launcher even when other programs are running in the background) as in the mouse stutters.

I have a intel core 2 duo p8600 2.4Ghz processor and a ati mobility radeon HD 3650. None of the above symptoms appear when using desktop mode.

I installed the netbook interface using 
sudo apt-get install ubuntu-netbook
Thanks in advance for any help

EDIT: I just checked top in terminal in netbook mode and it turns out xorg is using up to 94% of cpu while it only uses 11-25% when on desktop mode, I was thinking that the netbook mode was underclocking my cpu?

---

### Post by YagerX on 2011-01-05
Bump? I'll bump once more after this and if I can't find a solution, then I'll just give up and not use netbook mode...

---

### Post by kipp195 on 2011-01-14
I'm having the same problem om Kubuntu 10.10 desktop edition, after upgrading from 10.04. Some parts of the screen are randomly not updated, but when I switch to another desktop and back again it is fine again for a while. Also, it seems like scrolling up and down makes the screen update again.

---

