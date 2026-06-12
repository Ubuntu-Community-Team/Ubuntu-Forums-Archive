---
title: "After a restart, everything on my screen is GIANT SIZE!!!"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by redopinion on 2009-04-11
I downloaded some very simple updates to firefox, and after restarting my computer, everything on my screen was HUGE. It's like I just zoomed in on what was on my screen...I have to scroll left to righ while viewing web pages, and this is really starting to kill my eyes. I tried messing with font size and whatnot on my firefox preferences, I tried looking through the system preferences and I'm still looking at a giant EVERYTHING. Any help you guys could give would be great!!!

---

### Post by roccity1 on 2009-04-11
reboot your machine and hit esc to see the grub menu.In the menu choose the recovery option. When it boots through you will have a text installer go through it and you will get to a part where it will ask what you want to do. choose root shell. you will see a hash at the botttom of the screen and type, dpkg --reconfigure xorg-xserver or xserver-xorg. and it will reconfigure your xorg file and change the resolution for you.

---

