---
title: "remove syslinux pre-boot"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by vinchenzosaldevar on 2008-12-15
Syslinux Is Trying to take over my PC! 

i've been playing around today (unsucessfully) to install ubuntu on my new eeepc, using my existing laptop (dual boots xp and intrepid) to format and load the images onto my memory card. I tried lots of things but eventually gave up. attempted to reboot the pc into windows (to play games) instead of the regular boot menu i get syslinux 3.53 install boot screen and that's it. 

I really don't want to loose my existing installs or data but the rescue function built into syslinux does nothing (all 10 IO port probes come up clean). 

How do I remove syslinux without installing my system again from scratch?

---

### Post by caljohnsmith on 2008-12-15
If you can boot your Live CD, how about doing that, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd0,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
That should reinstall Grub to your MBR (Master Boot Record) so you can boot again. Let me know how it goes.

---

### Post by vinchenzosaldevar on 2008-12-15
Sorry for the delay I orriginally installed using wubi so had to download and burn a new iso... When i try to boot from optical drive it boots in to caldera DR-DOS 7.03 giving me a couple of options telling me whatever i try it will write through drives A & B. the last thing i want is to write through any drives at all. Now I'm stumped again.

Any Ideas?

---

### Post by caljohnsmith on 2008-12-15
Have you checked your BIOS settings to make sure the CD drive is first in the boot order? There should be some key you can press on start up to get into your BIOS, usually it's one of the function keys like F10, F12, etc. I would check that first.

---

### Post by vinchenzosaldevar on 2008-12-15
yes that was the first thing i did, if it goes to calendros or whatever when reading from disk and syslinux otherwise it has to be reading from disk before HD. it boots first from removeable media then from CD, then HD. I have a feeling the poor old thing might be jealous of the eee pc. last time it went wrong was just after i started looking at prices for one and now i actually have one it's sulking again.

---

### Post by vinchenzosaldevar on 2008-12-16
does anyone have any ideas?

---

