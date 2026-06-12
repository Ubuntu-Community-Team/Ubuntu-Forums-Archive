---
title: "FGLRX Issue"
date: 2010-05-29
forum: New to Ubuntu
---

### Post by allexkii on 2010-05-29
Ok guys,everything was working fine on Ubuntu 10.4 x86_64 untill I Attached my second monitor as extended desktop,my resolution changed to 800x600 on all monitors,and i couldnt change it back to 1920x1080 , so I decided to install FGLRX from Ati site ,when I installed it and rebooted system,everything was kinda laggy,I couldnt enable visual effects too,So I Uninstalled it,And after restarting When system startx i got "No Signal" On both monitors,what should i do ? :confused:

Alex.

---

### Post by scottiw2000 on 2010-05-31
Can you boot up in safe mode? Or boot to a text interface? If so, you could try telling the driver to reconfigure your xorg.conf file. At the terminal prompt type:

sudo aticonfig --initial

Then reboot and see what happens. If you install amdcccle (the catalyst configuration ui) you should be able to use it to configure your multiple monitors. It's under system->preferences.

Generally I've found the safest way to install the ati proprietary drivers is through Jockey (you can install jockey-gtk or jockey-kde through synaptic or the Ubuntu Software Centre).

---

### Post by psychoelf on 2010-05-31
Like stated above, use the driver pulled by jockey (Administration > Hardware Drivers).

I too tried the 10.4 catalyst from ATI's site and had boat loads of overheating and slowness.  The fglrx driver pulled by jockey is actually custom for Lucid Lynx and not the same as the one on ATI's site (wish I could remember the source where I found that, but oh well).

---

