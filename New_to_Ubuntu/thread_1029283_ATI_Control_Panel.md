---
title: "ATI Control Panel"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by andjen on 2009-01-03
Hi guys. I'm new here so nothing too complicated please!

I've just successfully got Vista and Hardy to co-exist in a dual boot format. I was bringing Ubuntu up to date when I was informed that if I wanted I could get the latest ATI Control Panel to get the best from my graphics card (ATI Radeon Express 1250). This was followed by some warnings about the community not being able to control updates etc.

I chose to install it which was a bad call because now when Ubuntu boots I just get a message on my monitor in a little blue box which reads:
                     Out Of Range
                     H 53.7 Khz
                     V 60.0 Hz

Is there any way that I can get back into Ubuntu to remove the ATI Control Panel?

Andjen

---

### Post by blueridgedog on 2009-01-03
You may want to try 

sudo dpkg-reconfigure xserver-xorg

in a terminal.  You can get to a terminal by ctrl+ALT+F1

---

### Post by Skripka on 2009-01-03
> **andjen said:**
> Hi guys. I'm new here so nothing too complicated please!

I've just successfully got Vista and Hardy to co-exist in a dual boot format. I was bringing Ubuntu up to date when I was informed that if I wanted I could get the latest ATI Control Panel to get the best from my graphics card (ATI Radeon Express 1250). This was followed by some warnings about the community not being able to control updates etc.

I chose to install it which was a bad call because now when Ubuntu boots I just get a message on my monitor in a little blue box which reads:
                     Out Of Range
                     H 53.7 Khz
                     V 60.0 Hz

Is there any way that I can get back into Ubuntu to remove the ATI Control Panel?

Andjen

Reboot.  At GRUB, select "Recovery Mode"->Fix X Server

That should deactivate the ATi driver.

Be warned that the ATi has a LONG history of having their Latest and Greatest drivers being beta quality.

---

### Post by andjen on 2009-01-03
Thanks for your answers guys and sorry for the delay in getting back to you.

As usual, the advice on this forum is spot on and my problem is now solved. Thanks very much for your help.

Andjen

---

