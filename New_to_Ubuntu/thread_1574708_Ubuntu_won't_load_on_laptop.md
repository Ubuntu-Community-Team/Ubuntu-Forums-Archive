---
title: "Ubuntu won't load on laptop"
date: 2010-09-14
forum: New to Ubuntu
---

### Post by Lemuel111 on 2010-09-14
I've been trying to get my laptop to start. I installed 10.04 but for some reason it won't load up. I just get to the Ubuntu screen with the dots with turn white but nothing happens. I have put the live CD in and tried rescue but I don't have the faintest idea what I am doing (rescue operations are listed). Can anyone help??

Thanks.

---

### Post by sandyd on 2010-09-14
> **Lemuel111 said:**
> I've been trying to get my laptop to start. I installed 10.04 but for some reason it won't load up. I just get to the Ubuntu screen with the dots with turn white but nothing happens. I have put the live CD in and tried rescue but I don't have the faintest idea what I am doing (rescue operations are listed). Can anyone help??

Thanks.
When you place the cd in, and as soon as the screen turns purple, press "esc".
Press F6

select nomodeset

---

### Post by Lemuel111 on 2010-09-14
I did the above, then selected boot from hard disk but still nothing.

---

### Post by sandyd on 2010-09-14
> **Lemuel111 said:**
> I did the above, then selected boot from hard disk but still nothing.
edit.
I didnt see that you had already installed ubuntu.
When you get to the grub menu (if it doesn't show up, keep on pressing the shift key)
press 'e'
add 'nomodeset' to the end of the kernel line (space in betweeen)

---

### Post by Lemuel111 on 2010-09-14
Sorry which is the grub menu and what is the best way to get to it?

Thanks.

---

### Post by Lemuel111 on 2010-09-14
I pressed ESC on start up, got a black screen with 'Check system. Then press F1 key.' and flashing cursor below it but I can't input any text. F1 then takes me into Sytem Setup but how do I do the 'e' from here?

Thanks.

---

### Post by wilee-nilee on 2010-09-14
> **Lemuel111 said:**
> I pressed ESC on start up, got a black screen with 'Check system. Then press F1 key.' and flashing cursor below it but I can't input any text. F1 then takes me into Sytem Setup but how do I do the 'e' from here?

Thanks.


It is the shift key hit it, and hold it down as soon as you hit the power button, this will bring up grub, hit e as instructed and use the arrows on the keyboard to get to the end of the kernel remove no splash and put in nomodset. You need a graphic card driver install probably, if this gets you in go to the check for drivers in the menu I forget the actual name. I'm on W7 now I forget program names at times.

I restarted it is additional drivers in system-admin, also do a update and upgrade. At least a update before checking the drivers.

---

### Post by sandyd on 2010-09-14
> **wilee-nilee said:**
> It is the shift key hit it, and hold it down as soon as you hit the power button, this will bring up grub, hit e as instructed and use the arrows on the keyboard to get to the end of the kernel remove no splash and put in nomodset. You need a graphic card driver install probably, if this gets you in go to the check for drivers in the menu I forget the actual name. I'm on W7 now I forget program names at times.

I restarted it is additional drivers in system-admin, also do a update and upgrade. At least a update before checking the drivers.
I keep on getting confused between grub1 and grub2....
why did they have to change the keys... *grumble*

---

### Post by Lemuel111 on 2010-09-14
I got into the grub menu thanks & did as suggested but there was no 'no splash' that I could see only 'quiet splash'. Do I remove this? I also have tried the recovery mode and it seems to have got stuck on the following:-

AC'97 1 access is not valid (0xffffffff), removing mixer.
ali mixer 1 creating error

Any suggestions?

Thanks.

---

### Post by wilee-nilee on 2010-09-14
> **sandyd said:**
> I keep on getting confused between grub1 and grub2....
why did they have to change the keys... *grumble*

I never touched grub-legacy I couldn't figure it out, I switched to grub2 in Jaunty I think.

@Thread starter removing the splash is just to see the text flash by and look for any errors, the main thing is adding the nomodset in there at the end of the kernel in that area where you see the splash comment. I believe to boot from the editing it is crtl-x.

Also if this doesn't work boot a live cd again and run this and post the graphic card.
```
lspci | grep VGA
```
Run this as well if you get in and have any problems.

I will be honest here I am just trying to get you in the OS and get some information on the graphics set up for the people who can actually help you, I have never had to load a graphics driver.

There might be a use for recovery here but really we just want to get into the OS to look for a driver prompt in the mentioned program or otherwise, and to run that command to identify the card if needed.

---

### Post by Lemuel111 on 2010-09-15
Right I have managed to get loaded via fail safe graphics in rescue mode. Then my screen size went down and a small display said 'xserver does not support size requested'. I had previously imputed data to increase the resolution of the screen. The rescue mode seems to have now deleted this & everything is back to normal apart from the fact I do not have full resolution. I typed in the lspci | grep VGA in terminal & this is the readout:-

01:00.0 VGA compatible controller: Trident Microsystems CyberBlade XPAi1 (rev 82)

Is this the monitor I need to get a driver for then and then I can increase the resolution size and it be compatible with xserver???

Thanks.

---

### Post by wilee-nilee on 2010-09-15
> **Lemuel111 said:**
> Right I have managed to get loaded via fail safe graphics in rescue mode. Then my screen size went down and a small display said 'xserver does not support size requested'. I had previously imputed data to increase the resolution of the screen. The rescue mode seems to have now deleted this & everything is back to normal apart from the fact I do not have full resolution. I typed in the lspci | grep VGA in terminal & this is the readout:-

**01:00.0 VGA compatible controller: Trident Microsystems CyberBlade XPAi1 (rev 82)**

Is this the monitor I need to get a driver for then and then I can increase the resolution size and it be compatible with xserver???

Thanks.

No this is the graphics card here is a google link to show others problems with this card. Also note in Lucid I believe there is no /etc/X11/xorg.conf, you have to make one if that is what is needed.
[https://encrypted.google.com/search?hl=en&q=Trident+Microsystems+CyberBlade+XPAi1+%28rev+82%29&aq=f&aqi=&aql=&oq=&gs_rfai=](https://encrypted.google.com/search?hl=en&q=Trident+Microsystems+CyberBlade+XPAi1+%28rev+82%29&aq=f&aqi=&aql=&oq=&gs_rfai=)

As far as your monitor goes it is really hard to tell if the card isn't the first problem, as I mentioned this is out of my general area of knowledge good luck.

---

