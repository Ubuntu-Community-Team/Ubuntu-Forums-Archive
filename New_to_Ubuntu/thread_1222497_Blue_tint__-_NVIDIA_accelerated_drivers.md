---
title: "Blue tint  - NVIDIA accelerated drivers"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by rlieving on 2009-07-25
I am a total Ubuntu newbie that just installed Jaunty 9.04 on a Dell Dimension 4300. 

---- computer specs
Graphics card: BODY { FONT-FAMILY:Verdana; FONT-SIZE:10pt } P { FONT-FAMILY:Verdana; FONT-SIZE:10pt } DIV { FONT-FAMILY:Verdana; FONT-SIZE:10pt } TD { FONT-FAMILY:Verdana; FONT-SIZE:10pt } 64MB, GEFORCE3TI
Processor: 1.7GB
Purchased: 11/8/2001
---
It works great with one exception (so far).  Whenever I enable the NVIDIA accelerated Graphics driver (for the advanced appearance effects) the screen gets a blue tint.  I can still see everything - the colors are just messed up.

I have a 64MB GEFORCE3TI card.  

Enabling the NVIDIA (v96) drivers in Administration > Hardware Drivers causes the blue tint .  Disabling the drivers (and a reboot) brings the normal coloring back.

Should I abandon hope?  Will a different card work better on this older machine?  

I'll take all suggestions.

---

### Post by jbrown96 on 2009-07-25
Install nvidia-settings ```
sudo apt-get install nvidia-settings
``` Then launch it with Alt+F2 then nvidia-settings. There is a section title X Server Color Correction. Then choose the Blue channel and you should be able to correct it.

---

### Post by rlieving on 2009-07-25
I followed all the instructions.  Thanks for those.

The problem with it is that modifying the blue settings has no effect at all on my machine.  I can't find the proper settings to do it by hand.  

I tried messing around with the Red and Green, as well as Brightness, Saturation and Hue.  Since there are nearly an infinite number of settings, I could fiddle all day and not the right settings.

Is there another way?  Does anyone know the exact settings?  Because, while the advanced graphics are really, really cool - the lack of blue is just too much sacrifice.

---

### Post by rlieving on 2009-07-28
Still haven't heard any good answers on this issue.  The suggestion by the other author does not work - the NVIDIA drivers are not displaying blue on my machine and there is nothing I have found to make it do so.

If you read this - I have a new request.  What is a good graphics card to work with Ubuntu?  I have read in other posts that NVIDIA works well.  

Fair enough - but my older NVIDIA card does *_**NOT**_* work, leaving me to wonder if it is the age of the card, the type of card, or the brand of card.

I have an 8 year old machine and I'll put in a different card.  I just don't want the same issue again if I buy a new NVIDIA graphics card.

---

### Post by nowfocus on 2009-11-13
This link solved it for me:  [http://blog.burlock.org/open-source/93-blue-tinthue-while-playing-videos](http://blog.burlock.org/open-source/93-blue-tinthue-while-playing-videos)

---

### Post by rlieving on 2009-11-14
Glad it worked for you.  Unfortunately, the blue problem is not limited to playing videos.  The blue problem affects everything.

And remember, it isn't that everything is blue tinted - it's that blue cannot be adjusted in the display. 

I've given up on this issue and blame it on the hardware, not the software.  The hardware is 8 years old and the monitor is newer.  The card may not seat right, etc...

But thanks for the tip anyway.

---

### Post by RedRat on 2009-11-14
This blue tint or hue problem might be caused by video. I found that when i played certain videos, can't remember which, I got the problem. It did NOT affect jpg or pictures or anything else, just video. The only solution was to run the Totem Video player and go to Edit> Preferences>Display and play with the sliders. Why this affects other video players is beyond me, but changing it in Totem helps.

Now if all of your screen, pictures, videos, even desktop has a blue tinge, I would suspect 1) the cable between your monitor and video card, 2) Video card.

---

### Post by AdamPond on 2009-12-07
> **nowfocus said:**
> This link solved it for me:  [http://blog.burlock.org/open-source/93-blue-tinthue-while-playing-videos](http://blog.burlock.org/open-source/93-blue-tinthue-while-playing-videos)

Thanks for this link. Fixed the problem for "Movie Player".

For VLC, I had to play with the equivalent setting.

Tools | Preferences | Video | Outout -> X11 Video Output (from default).

:popcorn:

---

### Post by Pilo on 2010-01-07
I'm suffering from the same problems with my video playback (other programs and the desktop are fine), as described in the link above it only crops up with xv.  x11, gl, vdpau all look normal.  An example of the blue tinted xv output is attached along with my lspci output.

---

### Post by RedRat on 2010-01-08
> **Pilo said:**
> I'm suffering from the same problems with my video playback (other programs and the desktop are fine), as described in the link above it only crops up with xv.  x11, gl, vdpau all look normal.  An example of the blue tinted xv output is attached along with my lspci output.
Try my solution using Totem Video Player that I describe above. Play with the Hue setting, you may have to push the slider all the way one direction or the other.

---

