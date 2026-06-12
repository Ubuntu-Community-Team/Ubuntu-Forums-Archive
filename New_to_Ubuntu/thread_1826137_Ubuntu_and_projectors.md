---
title: "Ubuntu and projectors"
date: 2011-08-16
forum: New to Ubuntu
---

### Post by medusa93 on 2011-08-16
I have to make a presentation from my Laptop for a class. Usually I have been using WindowsXP Home and Microsoft Office. Recently I have installed Ubuntu using Wubi. 
Usually in Windows and screen projector, there is nothing I have to do (irrespective of the make of the projector) I just have to connect the RGB cable and it is ready for show-time. Is there something I need to know regarding settings in Ubuntu and screen projectors. Unfortunately I can test it only on the day of the class

---

### Post by androssofer on 2011-08-16
> **medusa93 said:**
> I have to make a presentation from my Laptop for a class. Usually I have been using WindowsXP Home and Microsoft Office. Recently I have installed Ubuntu using Wubi. 
Usually in Windows and screen projector, there is nothing I have to do (irrespective of the make of the projector) I just have to connect the RGB cable and it is ready for show-time. Is there something I need to know regarding settings in Ubuntu and screen projectors. Unfortunately I can test it only on the day of the class

found this for ya:

[https://shoaibmir.wordpress.com/2009/08/05/using-projecter-screen-with-ubuntu/](https://shoaibmir.wordpress.com/2009/08/05/using-projecter-screen-with-ubuntu/)

---

### Post by corncob on 2011-08-16
I plugged a projector into my laptop to teach a class with no problems.  It was a VGA connection though. The only thing that threw me was that the boot menu showed up on the projector screen but not the laptop.  You can go to System > Preferences > Monitors and adjust the resolutions separately.  Too bad you can't sneak into the room early and test it out.

---

### Post by JC Cheloven on 2011-08-16
I use regulary different beamers (there's one different in each classroom), connected to the vga output of my netbook. It is always fine, with the small precaution of pluging-in the beamer to the pc _before_ turning on the pc.

If you have any resolution issue, do as said: preferences->monitor settings should do it.
You may find interesting to watch [this video]("http://lubuntu.net/blog/lubuntu-screencast-lxpanel-2-panel-layout") also.

---

### Post by decoherence on 2011-08-16
If it doesn't 'just work' try hitting the video switch key combo on your laptop (for instance, Fn F8 on most Dell, iirc) and if that doesn't work try the 'auto adjust' button on the projector (assuming it has one.)

One of those things solved 80% of the projector problems I encountered when I was working at a school.

Good luck,

---

### Post by Paddy Landau on 2011-08-16
One small thing: WUBI is not stable. I personally would not want to rely on it.

---

### Post by medusa93 on 2011-08-16
Thanks all of you. I will keep you posted regarding how it worked out for me

---

### Post by medusa93 on 2011-08-17
I should title this post "solved with problems"
Accessed "Monitors" through the Unity launcher. When I choose "Show same image on all monitors" everything is as its supposed to be. The audience and I, both see the same stuff. 

 Problem occurs when I uncheck the "Show same image on all monitors". Then,

[LIST=1]
[*]The mouse cursor appears on the projector screen and not on the laptop screen
[*]The desktop is seen but not whatever else opens on the desktop e.g. Firefox, Nautlius browser etc open on the desktop is not seen on the projector screen. The projector screen just keeps showing the desktop background
[*]Impress opens up in slideshow on the projector screen whereas it is in outline mode on my screen. Impress remains at slide number one (in outline mode) whereas on the projector screen Impress has advanced to slide 15 on the slideshow
[*]Cannot choose anything with the mouse on the laptop. Have to pull out the RGB cable of the projector to be able to do that
[/LIST]
I had only limited time with the projector. It will be great if I can have access to slide notes which my audience cannot see. Since mouse cursor does not work on the laptop (only on the projector screen) I cannot do anything on the laptop if I uncheck "Show same image on all monitors"

---

### Post by HermanAB on 2011-08-17
Howdy,

The external screen/projector Plug and Pray is done upon login when Xorg starts up.  So log out, plug in the projector and then log in.  The projector should then work.

---

### Post by Paddy Landau on 2011-08-17
You should be able to drag windows from one screen to the other.

There is a way to change which is your "primary" screen, but unfortunately I don't remember how to do that.

---

### Post by realzippy on 2011-08-17
..maybe a little offtopic,but wanted to mention the tool "[disper]("http://willem.engen.nl/projects/disper/")"
which did a great job for me when using beamers..

---

### Post by corncob on 2011-08-17
> **medusa93 said:**
> 
 Problem occurs when I uncheck the "Show same image on all monitors". Then,

[*]The mouse cursor appears on the projector screen and not on the laptop 



My experience here is hooking up an external VGA monitor to my laptop to use as one big screen by unchecking "show same image..."   The computer might think the external monitor (the projector in your case) is in a different orientation, relative to your laptop screen, than you think.  Did you try moving the cursor off the screen to the left, right, top, and bottom and see if any of these brings it to the laptop screen?  You can also change  this by dragging the secondary monitor around in Preference > Monitors.

---

