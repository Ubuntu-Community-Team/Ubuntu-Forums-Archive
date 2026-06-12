---
title: "no boot"
date: 2011-06-07
forum: New to Ubuntu
---

### Post by bjje on 2011-06-07
Sometimes on one of my natty machines, I will turn it on and get a white screen about half full of faces; ; ))
and it stays there. If I turn off and on again It boots up just fine.

Is it trying to tell me something?

---

### Post by ubudog on 2011-06-08
Does the same thing happen when you turn the computer off?  Have you enabled any graphics drivers in Additional Drivers?

---

### Post by jtarin on 2011-06-08
> **bjje said:**
> Sometimes on one of my natty machines, I will turn it on and get a white screen about half full of faces; ; ))
and it stays there. If I turn off and on again It boots up just fine.

Is it trying to tell me something?Yes you visit Facebook too often....it has burnt face-shaped pixels on your monitor. :P

---

### Post by bjje on 2011-06-09
Well sure, so  I changed all of my facebook icons to redirect me to ubuntu forums instead, and yes, I'm using nvidia for a geforce board. 
I don't see them on logout. It only happens sometimes when I first start the machine if it was off. Maybe there's a hotkey to proceed?

---

### Post by ubudog on 2011-06-09
If possible, could you take a picture of it when it happens and upload it here?

---

### Post by bjje on 2011-06-10
Usally looks like this

---

### Post by bjje on 2011-06-10
Well I'll try again

---

### Post by ubudog on 2011-06-10
Did this start happening after you installed restricted drivers?  Could you post your xorg.conf?  (/etc/X11/xorg.conf)

---

### Post by bjje on 2011-06-13
I installed ubuntu after I addaed the graphics card.

```

Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
EndSection

```

---

### Post by ubudog on 2011-06-13
What type of computer do you have?

---

### Post by bjje on 2011-06-13
I have several Dell Precision 340's with 2GB RAM and GEforce 6200 or similar graphics cards and only one shows this screen.  It seems to happen about every 5 bootups or so. Need to turn it off and every time then comes up fine.
Thanks

---

### Post by bjje on 2011-06-28
To update, I just saw the same exact screen on one of my other machines.

---

### Post by amjjawad on 2011-06-28
> **bjje said:**
> To update, I just saw the same exact screen on one of my other machines.

Your other machines have the same Hardware Specifications?

---

### Post by jtarin on 2011-06-28
> **bjje said:**
> Well I'll try again
In the lower left of the photo I see a dialog window....what is the message?

---

### Post by bjje on 2011-07-06
Sure, same machines Dell Precision 340, 2gB Ram, PNY Verto Geforce 6200. They are both fresh natty installs. I am not currently using unity on these machines.
I wrote PNY and sent the pic, but they say it's not them, at least so far.  On the second machine I only saw it once but totally identical. When I reboot, the smileys change a bit as it goes down.  Whenever I get that screen I am stuck, have to reboot and it's always fine. 
Sometimes, I get my login screen  with a way lower resolution and it goes to gnome like that. In order to get correct settings I can log out and in again, then it's fine. I guess sometimes the nvidia drivers don't load properly.

---

### Post by Perkins on 2011-07-06
Perhaps go into the BIOS settings and turn off any onboard video device and see if that fixes it.

---

### Post by bjje on 2011-07-07
Good idea, 
BTW, sorry, the dialog box was just an artifact of the screenshot not there on the mystery screen.

---

