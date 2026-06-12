---
title: "dual monitors"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by allabouttowler on 2009-01-29
Hi, I'm a Ubuntu noob, switched from windows a few months ago and have so far really, really enjoyed the experience.

I'm having a problem now though that's really winding me up...

I'm trying to create an extended desktop environment onto an external (tv) display, in order to enjoy media files on a larger screen.

This is something that windows always made pretty straightforward either via s-video or VGA.

Having done some initial scouring it seems the problem may lie in a lack of support for some of the more intricate display settings of my intel video card...

Is it possible for me to do this through ubuntu at present or am I going to have to go back to a dual boot?

I'm keen to learn but at present my knowledge of the terminal and 'x' settings is very basic to say the least...

If there's anybody out there who would be prepared to sacrifice a little time to walking men thorough this as if i was a lost and lonely child it would be enormously appreciated!

Cheers!

---

### Post by allabouttowler on 2009-01-29
Oh, should probably add - when trying to connect through 'preferences - screen resolution' it shows my other monitor and will occasionally allow me to display my laptop display on it simultaneously.

Unfortunately the quality (even at highest res. setting) is woeully inadequate and trying to revert back to just the laptop's display invariably causes my machine to show just a black screen with a mouse cursor, on which I'm incapable of doing anything, requiring me to force a reboot...

---

### Post by jimmah6786 on 2009-01-29
> **allabouttowler said:**
> Oh, should probably add - when trying to connect through 'preferences - screen resolution' it shows my other monitor and will occasionally allow me to display my laptop display on it simultaneously.

Unfortunately the quality (even at highest res. setting) is woeully inadequate and trying to revert back to just the laptop's display invariably causes my machine to show just a black screen with a mouse cursor, on which I'm incapable of doing anything, requiring me to force a reboot...

What method are you using to connect to the TV? Also is it a newer TV, such as 720p or 1080p. We need to figure out its max resolution it can handle, from there we can figure out the frequency and configure your xorg accordingly. I know that old TVs ones that are lower than 480p have a resolution of 640x480 if you bought it in the US (NTSC not PAL). VGA cable should have no trouble with this nor should the S-Video. When you get into the higher resolutions, check google to see what an S-Video can handle.

Here is a link that got me going when I was doing something very similar with an external TV.
[http://www.ubuntugeek.com/dual-monitors-with-nvidia.html]("http://www.ubuntugeek.com/dual-monitors-with-nvidia.html")

Also try [http://ubuntuforums.org/showthread.php?t=221174]("http://ubuntuforums.org/showthread.php?t=221174")

Maybe try playing with your xorg(don't forget to back it up):
```
SubSection "Display"
            Virtual 2560 1024
      EndSubSection

```
Then from bash:
```

xrandr --output LVDS --mode 1440x900 --output TMDS-1 --mode 1280x1024 \ 
--right-of LVDS


```
Depending on the resolutions you need. 1440x900 primary, 1280x1024 secondary.

Even more: [http://intellinuxgraphics.org/dualhead.html]("http://intellinuxgraphics.org/dualhead.html")

If this is really confusing, post back your xorg...Located at(usually) /etc/X11/xorg

Hope this was helpful, 

Jim

---

### Post by allabouttowler on 2009-01-29
Hi, thanks very much for your help!

It's a brand spanking new Sharp HD LCD - can't give you the absolute specifics cos I'm actually at work at the moment.

I'll have a look at the links you've provided and a tinker tonight and if I can't get it up and running I'll get back to you with the info requested!

I can tell you though that in my test runs i've been trying to connect via s-video, though my (long enough for the task) VGA cable should be delivered today!

Also I'm in the UK, if that might have any bearing on possible resolutions...

Thanks again for your help, I'll drop back on later this evening (about 5 hours) to let you know how its gone... I'm sure you can't wait! ;-)

---

### Post by Axeonfluke on 2009-01-29
I'm going to monitor (no pun intended) this post because I'm having similar issues.  I often run a second monitor off my laptop while at home and occasionally plug into my LCD tv to show off when applicable. 

My recent change to Ubuntu, as of yesterday, has left me somewhat perplexed with how to manage my monitor settings.  I did figure out how to extend my desktop to a second monitor, however I am unable to drag windows onto it.  As I drag the window just stops at the edge but the cursor keeps on going.  

I created a new panel on the monitor but anything I open on it still pops up on the laptop screen.  Plus the resolutions seem a little off on mine as well.  

While you're at work I'm going to poke around and see if there is a better (or at least, more simplistic) set of software for monitor management.  Hopefully we can get this stuff resolved.

---

### Post by jimmah6786 on 2009-01-29
> **allabouttowler said:**
> Hi, thanks very much for your help!

It's a brand spanking new Sharp HD LCD - can't give you the absolute specifics cos I'm actually at work at the moment.

I'll have a look at the links you've provided and a tinker tonight and if I can't get it up and running I'll get back to you with the info requested!

I can tell you though that in my test runs i've been trying to connect via s-video, though my (long enough for the task) VGA cable should be delivered today!

Also I'm in the UK, if that might have any bearing on possible resolutions...

Thanks again for your help, I'll drop back on later this evening (about 5 hours) to let you know how its gone... I'm sure you can't wait! ;-)


Great, so it is a newer HD LCD. That will rule out the resolution being "out of bound" for the monitor(tv). So I want to reiterate that you have a Laptop and you want to extend the view over two monitors?

---

### Post by allabouttowler on 2009-01-29
Home from work!

yep it's a laptop (Toshiba Equium M50 164) running Hardy...

I've just plugged in using my VGA and It's seeing it in screen resolution, but now when I tell it to extend to it i'm getting nothing

---

### Post by allabouttowler on 2009-01-29
and sorry yes, my goal is to get it to extend over two monitors (prerably with the tv located above the laptop)

---

### Post by allabouttowler on 2009-01-29
Oh, and I'm also using the Awn dock via Compizfusion... a few sites i've landed on have told me that's a no-no if I want to do this... :-(

---

### Post by jimmah6786 on 2009-01-30
> **allabouttowler said:**
> Oh, and I'm also using the Awn dock via Compizfusion... a few sites i've landed on have told me that's a no-no if I want to do this... :-(

You could disable this from starting up (temporarly) to rule that out.

In regards to the extend, does your laptop have a button sequence you can press to enable the external VGA port on your laptop. I know there are usually 3 modes; Off, Clone/Mirror, and Extend. Lets rule that out first before we start looking deeper into Ubuntu.

---

### Post by alexc2 on 2009-01-30
Hi you guys! I followed this thread cause I'm also interested in getting this done. I have Hardy on a Dell Latitude X200 (PIII 800Mhz, 640Mb RAM, 60Gb H.D. wiht Intel graphic controller: "*Intel Extreme Graphics AGP*").
I do get my second monitor working but as a "mirror" of my laptop screen; I hit Fn+F8 (F8= CRT/LCD key) but I never get the "Extend" mode. Maybe in this model isn't supported. 
I'm going to follow the indications in: [http://intellinuxgraphics.org/dualhead.html](http://intellinuxgraphics.org/dualhead.html) to see if it helps, but If you guys came up with the solution, I'll owe you big time!

Greetings from Costa Rica.
AlexC2

---

