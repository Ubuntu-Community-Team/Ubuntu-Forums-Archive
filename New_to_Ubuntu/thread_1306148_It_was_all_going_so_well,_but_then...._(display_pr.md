---
title: "It was all going so well, but then.... (display problem)"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by catraeth on 2009-10-30
Hi all
New to this forum and to Linux.  Well, thought I would take the plunge and install the new Ubuntu 9.10 and it all went well - everything seemed to be working fine (including youtube on firefox etc) but then I tried to install an external monitor.  I couldn't get the resolution increased at all, so I thought okay, I'll leave it for now and tackle that later, so I shut down the external monitor.  But now my laptop monitor is throwing out intermittent garbage on the screen (which definitely wasn't there before).  I've tried a cold re-boot but it's still the same so I guess I've changed something inadvertently.  The display still works (I'm typing this on it) but if I minimise a window bits of it will be left on the desktop along with multi-coloured stripy garbage.  I considered reinstalling the whole thing again but maybe an expert can help me turn back the clock a little to how it was before?

The laptop is an aging but still good IBM T42 with an ATI card onboard I think.  It's never given any trouble.

So I guess I have two requests if that's not too cheeky:

Help me get my laptop display working as it was before I messed with it.

Help me get my external LCD display working correctly with better resolution.

Many thanks!

---

### Post by philinux on 2009-10-30
Have a look in System>admin>hardware drivers to see if you can activate a graphics card driver.

---

### Post by catraeth on 2009-10-30
Hi Philinux - I tried that just now but got the message that "No proprietary drivers are in use on this system"

---

### Post by catraeth on 2009-10-30
I have disabled 'visual effects' under 'appearance' and that seems to have got rid of the garbage for now.  I'd like to seek a full solution if possible though.

---

### Post by catraeth on 2009-10-30
I just had a crash report of a 'serious kernel crash'.  I was only running firefox.  Could this be connected to my display problems?

---

### Post by ikt on 2009-10-30
> **catraeth said:**
> I just had a crash report of a 'serious kernel crash'.  I was only running firefox.  Could this be connected to my display problems?

Did you report the bug?

If you did can you link to the launchpad bug report :)

---

### Post by Bölvaður on 2009-10-30
> **catraeth said:**
> I just had a crash report of a 'serious kernel crash'.  I was only running firefox.  Could this be connected to my display problems?
it's related to your problems, if it is display or not I cannot tell

what graphic card do you have?
you can find out by opening the terminal (applications &#8594; accessories &#8594; terminal) and type in ```
lspci | grep VGA
```
you can copy and paste by ctrl+shift+c and ctrl+shift+v in the terminal (ctrl+c is very old command for closing programs)

---

### Post by catraeth on 2009-10-30
> **Bölvaður said:**
> it's related to your problems, if it is display or not I cannot tell

what graphic card do you have?
you can find out by opening the terminal (applications &#8594; accessories &#8594; terminal) and type in ```
lspci | grep VGA
```you can copy and paste by ctrl+shift+c and ctrl+shift+v in the terminal (ctrl+c is very old command for closing programs)

Thanks for that - here's the card details:

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]

I'd be very grateful for any further help.  I did report the crash.

---

### Post by catraeth on 2009-10-30
Okay, I'm going to go for a clean re-install to see if that will fix it.  Thanks for your help.

---

### Post by shae on 2009-10-30
> **catraeth said:**
> Thanks for that - here's the card details:

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]

I'd be very grateful for any further help.  I did report the crash.

You probably should not use compiz with that video card.  It is only supported by the open source ATI drivers and those are very hit-or-miss with compiz.  I think that this is the source of your problem.

---

### Post by catraeth on 2009-10-30
I re-installed everything and now all's well again - took a while but as I'm only on day 1 of my Ubuntu/Linux journey it was no biggie.  Everything now works fine.  Sorry but I have no idea what compiz iz?

---

### Post by Absorbed on 2009-10-30
> **catraeth said:**
> I re-installed everything and now all's well again - took a while but as I'm only on day 1 of my Ubuntu/Linux journey it was no biggie.  Everything now works fine.  Sorry but I have no idea what compiz iz?

Compiz is the thing that gives you desktop effects, such as wobbley windows and when you minimize a window you get a little animation rather than the window just disappearing.

[http://www.youtube.com/watch?v=ZxfSwzhSn1c](http://www.youtube.com/watch?v=ZxfSwzhSn1c)

---

### Post by catraeth on 2009-10-31
> **Absorbed said:**
> Compiz is the thing that gives you desktop effects, such as wobbley windows and when you minimize a window you get a little animation rather than the window just disappearing.

[http://www.youtube.com/watch?v=ZxfSwzhSn1c](http://www.youtube.com/watch?v=ZxfSwzhSn1c)

Aha!  Many thanks for that...  I have soooo much to learn, but even though I'm only just scratching the surface, it's bye bye Windoze for me - I'm never going back.

---

### Post by Absorbed on 2009-10-31
> **catraeth said:**
> Aha!  Many thanks for that...  I have soooo much to learn, but even though I'm only just scratching the surface, it's bye bye Windoze for me - I'm never going back.

I still use windows for voice recognition software, but as far as I'm concerned ubuntu trumps windows everywhere else. Windows cannot match ubuntu's community, or the continual improvement of ubuntu itself.

---

