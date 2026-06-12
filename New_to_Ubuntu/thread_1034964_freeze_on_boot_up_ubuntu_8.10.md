---
title: "freeze on boot up ubuntu 8.10"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by nojas on 2009-01-09
Hey, I just updated my ubuntu hardy to version 8.10 and when I log in using a standard gnome session my system freezes afterwards, I just get a blank screen. When I log in using the failsafe gnome option it works fine. I had the same problem in hardy and I hoped that with the update it would be fixed. 

My system config:
Amd Athlon 1800+
1gb memory
nvdia geforce2gts video card.


I hope someone had any ideas thanks

---

### Post by cmnorton on 2009-01-09
Can you boot with the live CD? If so, what are your graphics settings? If they are different and you can boot, then you may have to boot into recovery mode and run dpkg-reconfigure xserver-xorg and change your X settings.

---

### Post by nojas on 2009-01-12
Sorry for the late reply, wasn't at home this weekend. thanks for the suggestion, I didn't have a live cd, so i thought lets just change the settings and see.

ran the run dpkg-reconfigure xserver-xorg  code as suggested and changed the settings to using the kernel for support (that was the only x related option i could change the rest is about the keyboard settings. After the reboot, my image settings where set to low resolution and I got an error so I've reseted the x settings. so back at the beginning. any other suggestions? thanks!

---

