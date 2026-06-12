---
title: "problem with screen resolution on nvidia card"
date: 2010-04-04
forum: New to Ubuntu
---

### Post by dagarshali on 2010-04-04
Hi have a ubuntu 64 bit karmic koala installed on ideapad Y450, which has a nivida geforce 110 card.

the laptop screen has a resolution of 1360x768. when i used the laptop alone, there isn't any problem. When i connect the dell lcd(1920 x 1080) via vga cable, the resolution doesn't get adjusted automatically. and when i manually pick the resolution, I get a pop up saying i need to fix some setting and upon clicking autofix, the screen becomes ok. 

when i revert back to laptop screen however, without restarting, i have the laptop screen now at 1920 x 1080.

How to fix this problem..?

Regards,
Vishwa

---

### Post by Sin@Sin-Sacrifice on 2010-04-04
System>Admin>NVIDIA X server settings

If it's not there, in a terminal ```
sudo apt-get install nvidia-settings
```

If that says already installed, in a terminal ```
nvidia-settings
```

---

