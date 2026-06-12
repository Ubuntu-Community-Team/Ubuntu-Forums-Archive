---
title: "Screen Randomly Goes Black For Two Seconds"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by Penguin Guy on 2009-05-06
Not much to say; my screen randomly turns black now-and-again for about 2 seconds - there are no apparent side-effects.

This happens in both GNOME/Compiz and KDE/Kwm but only in Jaunty. My screen still receives signal because the indicator light is green. I have now switched to Linux Mint where things are working fine but I am leaving this here for other people who suffer from the same problem.

**Screen:** Dell 1905FP
**GPU:** Intel 829156/GV/910GL

---

### Post by tdreyer1 on 2009-05-06
Are you using compiz (any desktop effects)? If so, try turning them off & seeing if that changes the behavior. If not, try turning them on... What graphics card & monitor do you use?

---

### Post by Penguin Guy on 2009-05-06
> **tdreyer1 said:**
> Are you using compiz (any desktop effects)? If so, try turning them off & seeing if that changes the behaviour. If not, try turning them on... What graphics card & monitor do you use?
Don't know the answer to any of your questions - but I went to [COLOR="DimGray"]System -> Preferences -> Appearance -[Visual Effects][/COLOR] and none of the radio-buttons were checked - so I checked 'Normal' and then the screen went black twice and firefox froze for a while.

Well I suppose now we can be pretty sure it's compiz that's the problem?

---

### Post by Penguin Guy on 2009-05-07
Sorry; I try not to bump but this is really getting on my nerves - BUMP.

---

### Post by tdreyer1 on 2009-05-12
Sounds like it is likely. Have you tried setting it to "none"?

---

### Post by Penguin Guy on 2009-05-12
It worked fine in Intrepid so I don't see why it shouldn't work in Jaunty but I'll give it a try and see if I still get black screens - thanks!

---

### Post by Penguin Guy on 2009-05-12
Nope; it just went black again. It must be something else...

---

### Post by cerz on 2009-05-21
Having the same problem.  
Ubuntu 9.04.  No problem (that I can recall...) on 8.10, 8.04, 7.10, 7.04, or 6.06.
Using nVidia Corporation NV34 [GeForce FX 5200] according to Xorg.0.log.

Just turned off visual effects, waiting to see if that cures it, but doubtful since it didn't work for penguin guy.

Thanks

---

### Post by cerz on 2009-05-22
Effects are now set to none, and my screen also just went black.
The only (possibly) relevant log entry I could find was this undated entry in dkms_autoinstaller

nvidia (173.14.16): Already installed on this kernel.

But that may well have been from startup.

---

### Post by Didius Falco on 2009-05-22
When it goes black for 2 seconds, is it while you are actively using the system, or does it only happen when you aren't using the mouse and/or keyboard?

Regards,

Didius

---

### Post by lkraemer on 2009-05-22
OK, I just went through the same thing with my external LCD
MAG Innovision LT716S  700P Monitor.  Here are some troubleshooting
steps.

  When the screen goes BLACK:
1.  Turn power off Monitor for about 1 minute, and then power back on.
    You should see the displayed video for 2 seconds or until it goes
    BLACK again.
2.  Next try just unplugging the video cable from the Computer's port
    and plug it back in.  You should see the displayed video for 2 seconds
    or until it goes BLACK again.
3.  Notice what the Power LED on the monitor is doing.  It might stay
    GREEN or change colors, or start to rapidly blink.
4.  If #1 or #2 above bring the Displayed video back for a short period
    of time, your backlight is being turned off for some reason.
    Most likely a bad Power Supply Voltage, or Inverter Problem. 
5.  If you can't get the displayed video back, use a very powerful
    flashlight to shine at the display and see if you can detect any
    video being displayed.  If you can see some, then the backlight 
    circuit is defective.

Now proceed to [http://www.badcaps.net/forum](http://www.badcaps.net/forum) and start your adventure.
Search for your Brand of LCD, then add Model Number after you find
some details of your Brand.

REF:
[http://www.badcaps.net](http://www.badcaps.net)

My MAG Innovision LT716S  700P post:
[http://www.badcaps.net/forum/showthread.php?t=7130](http://www.badcaps.net/forum/showthread.php?t=7130)

I was lucky, and got mine repaired for less than $15.00.


What is the Brand, and Model number of your LCD Monitor?

lkraemer

---

### Post by Penguin Guy on 2009-05-23
I have switched to Arch Linux and am now no longer having any problems. For your information the indicator on my screen remained remained green for the two seconds.
lkraemer - there must be some misunderstanding, my screen only went black for two seconds then came back on, this would happen randomly about every 10-15mins. I am quite sure this is not a defect in my monitor because it only happens in Jaunty.

---

### Post by cerz on 2009-05-27
I'm sure this thread is dead... lost track of it over memorial day weekend. 

My screen blacks out when I am actively using the computer.  I am not sure if it continues to do so when I am not actively using it, as I don't watch movies or listen to music with the affected machine.  

It is not a monitor hardware issue, I had no problem under Intrepid and earlier releases.

---

