---
title: "How to install video drivers?"
date: 2009-06-22
forum: New to Ubuntu
---

### Post by Rhythmdvl on 2009-06-22
I have an Asus P5KPL-CM motherboard with Intel GMA 3100 onboard video. 

My monitor’s native resolution is 1920 x 1200, but the highest setting I can choose is 1280 x 800 According to the Asus page, the board’s max resolution is 2048 x 1536. 

*Is* this a drivers issue? I also had to manually update/install the onboard LAN drivers – could this be the same? Everything else seems to work fine; should I update the BIOS? Should I be looking on Intel’s site? 

Thanks~

---

### Post by Pogeymanz on 2009-06-22
It is very likely a driver issue.

Do you have this package installed?
```
xserver-xorg-video-intel
```

You can check in Synaptic.

Assuming you do have that package, maybe you can do a google search to find out how to use a more up-to-date driver. Just google for "intel driver Jaunty" and you'll find plenty of guides on changing around the intel drivers. Unfortunately this may require you to update Xorg also, which has potential to get messy if it isn't a good guide.

---

