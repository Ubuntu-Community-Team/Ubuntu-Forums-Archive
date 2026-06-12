---
title: "How to restore the Graphics Interface"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by Trophy on 2009-07-07
I installed the Nvidia third party driver for my NVidia 7900 GS on my Ubuntu Jaunty. Each time i try it, the graphics interface will not load on boot and i am left at the prompt. I have tried a few different way based on the posts i have seen here but so far none work.

I am new to Ubuntu and have reinstalled it 4 times after ending up at the prompt not knowing how to get the graphics interface working again. 

Is there a way to reset to the generic drivers from the prompt or can you tell me what files do i need to backup in order to restore them should my next attempt at the driver installation fail.

---

### Post by SirBismuth on 2009-07-07
Are you using the proprietary drivers installed through System/Administration/Hardware Drivers, or did you download the drivers from Nvidia, and follow that installation procedure?.

Also try restarting your X server, maybe that will help?.  For 9.04, I installed the 185.XX drivers from Nvidia without a hassle, I have a 7600GT Gfx Card.

SB

---

### Post by Trophy on 2009-07-07
I first tried the System/Administration/Hardware Drivers which recommends the 180.xx for my 7900 GS cards (I have 2x in SLi) but black screen on boot.

I'll try the 185.xx from the Nvidia site but don't wont to have to re-intsall everything again so was hopeing to back up the config files so i could restore them in case.

Complete NewB here. how do i restart the x server? ):P

---

### Post by Sky Pixie on 2009-07-07
> **Trophy said:**
> Is there a way to reset to the generic drivers from the prompt or can you tell me what files do i need to backup in order to restore them should my next attempt at the driver installation fail.

Reconfigure xorg:
```
sudo dpkg-reconfigure xserver-xorg
```
Follow the instructions.

Backup the new xorg.conf file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf~
```

If you mess up, restore the default config file:
```
sudo cp /etc/X11/xorg.conf~ /etc/X11/xorg.conf
```

Have you tried manually inserting drivers and resolutions into xorg.conf?

---

### Post by Trophy on 2009-07-07
Ah, that sounds like what i need ... i'll give it a try tonight. I thought it might have been a resolution problem as many threads i have seen mention only being able to show max res of 800x600 but i didn't know which config file to edit ... i'll try adjust the res as well. 

Let you know in the morn? :KS

---

### Post by Trophy on 2009-07-08
Thanks Sky Pixie, that worked. I tried another way to install the driver but got to the same prompt after rebooting. Just did a restore and reboot and was back in. Thanks.

---

