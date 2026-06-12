---
title: "Desktop is blank - mouse can go off the screen"
date: 2011-03-06
forum: New to Ubuntu
---

### Post by todd_k on 2011-03-06
I just installed v.10.10 for an HTPC.  I am using my 42" HDTV as a monitor via HDMI port.  Right now I'm using onboard video and have not installed my video card yet.  
When I booted Ubuntu for the first time, I get to the desktop but there isn't anything else these.  No bars, menus, options.  I am able to right click but I didn't have much luck there.
I tried the keyboard command to bring up gnome-panel but again, can't see it.  I am able to move my mouse off the screen so perhaps the menus I need are somewhere off-screen?
I rebooted a few times and always get the same panel.

---

### Post by Hedgehog1 on 2011-03-06
Your HDTX is in an 'overscan' mode where the top, bottom and sides are 'trimmed'.

You have two options:

(1) The TV may offer a 1-for-1 1920x1080 mode (mine does and I am typing this using that TV as the monitor).

(2) Your other choice is to set over scan compensation  This create a 'black frame' around your desktop so all the menus are visible.

Option 1 is best (check your TV manual or <if male> fool with the TV settings).

Option 2 has to be set in the setup screen your proprietary drivers installed.  You did not mention the brand of graphics card you are using.

***The Hedge***

:KS

---

### Post by todd_k on 2011-03-06
> **Hedgehog1 said:**
> Your HDTX is in an 'overscan' mode where the top, bottom and sides are 'trimmed'.

You have two options:

(1) The TV may offer a 1-for-1 1920x1080 mode (mine does and I am typing this using that TV as the monitor).

(2) Your other choice is to set over scan compensation  This create a 'black frame' around your desktop so all the menus are visible.

Option 1 is best (check your TV manual or <if male> fool with the TV settings).

Option 2 has to be set in the setup screen your proprietary drivers installed.  You did not mention the brand of graphics card you are using.

***The Hedge***

:KS


Thanks for the information.  Right now I'm using onboard video, the video card has not been installed yet.  I wanted to get the new machine up a running with as little extras as possible, then go back and install it once I have all my drivers and updates done.  
You don't happen to have a Sharp Aquos hdtv, do you?

---

### Post by Hedgehog1 on 2011-03-08
> **todd_k said:**
> Thanks for the information.  Right now I'm using onboard video, the video card has not been installed yet.  I wanted to get the new machine up a running with as little extras as possible, then go back and install it once I have all my drivers and updates done.  
You don't happen to have a Sharp Aquos hdtv, do you?

Samsung 8000.  Using a 55" LED LCD HDTV as a monitor is simply awesome!  At work I have a 17" monitor.  *It feels so small.*

Once you have your final video card selected, we can walk you through getting the adjustments right.

Will you be going ATI or NVidia?

***The Hedge*** 

*Sitting 8 feet away from his 55" monitor...*

---

### Post by alahnagr on 2011-03-08
Jumping in here - have same problem. Panasonic LED 32" TV/ HDMI (1920x1080) to a Nvidia ION graphics. What am I looking for in the TV Manual?

---

### Post by Hedgehog1 on 2011-03-08
First place to check is inUbuntu on the **NVidia** Setup Screen. You have an option (in the second to last - I think) window that sets 'overscan compenation'.  Mine is set to zero, with the TV set to 1:1 so I get a full 1920x1080.  Your TV may or may not get every pixel, so futz with that setting first.
 
I don't know where in the Panasonic manuak to check (sorry), but the overscan compensation should get you where you want to be.
 
***The Hedge***
**** 
:KS

---

### Post by alahnagr on 2011-03-10
Thanks "The Hedge" - I found what I needed to tell the TV Monitor to be a PC Monitor for a bit. I'll be futz-ing with it a bit to get it the way I want it, but at least I can see the panels and the info on the right/left of screen without guessing.

---

