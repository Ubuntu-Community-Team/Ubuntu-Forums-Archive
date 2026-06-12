---
title: "HDMI no signal, driver issue?"
date: 2011-07-24
forum: New to Ubuntu
---

### Post by Witra on 2011-07-24
Hi, 

First of all, if this is on the wrong forum, please do go ahead and move. I just figured this'd be a fine place, since I am a complete beginner, and this feels like a simple issue.

Now then.. I'm running 11.04 on a asus 1215n(meaning the graphics chip is an NVidia Ion). 
I've been using ubuntu for about a day now, and today tried to hook it up to my tv via HDMI, but the tv is not getting a signal, at all. 
I tried updating drivers, but ended up screwing things up. Just now managed to undo my mistake. 

I found a few threads here and elsewhere describing the same thing, but either those were for old versions, had no answers or were too advanced for me. 

Now, I suppose there's something very simple I need to do to make this work, but could anyone help out as to what that might be? 

So.. any advice, folks?

---

### Post by relay_man on 2011-07-24
Did you connect the HDMI cable before or after you booted your machine?

Look at  System > Preferences > Monitors after you connect the cable and reboot.  You may need to make some adjustments there to get things to work.

---

### Post by androssofer on 2011-07-24
if you go to "additional drivers" and install the nvidia accelerated graphics driver.

once u get tht it will install the nvidia settings manager, then u can tweak settings in it... i have an asus eeebox 1501p running on HDMI and it runs a treat... had to tweak the overscan tho to get it to fit....

---

### Post by Witra on 2011-07-24
> **relay_man said:**
> Did you connect the HDMI cable before or after you booted your machine?

Look at  System > Preferences > Monitors after you connect the cable and reboot.  You may need to make some adjustments there to get things to work.
Both, and the tv doesn't show up in Monitors, I'm afraid.

> if you go to "additional drivers" and install the nvidia accelerated graphics driver.

once u get tht it will install the nvidia settings manager, then u can tweak settings in it... i have an asus eeebox 1501p running on HDMI and it runs a treat... had to tweak the overscan tho to get it to fit....
Unfortunately the NVIDIA X Server settings thing says "You do not appear to be using the NVIDIA Server X Driver. Please edit your X configuration file(just run 'nvidia-xconfig' as root), and restart the server."
And when I try to do that, I get
> Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Default Device" must have a Driver line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'


Any suggestions?

---

### Post by master_kernel on 2011-07-24
Unfortunately, it seems like there are no working drivers that anyone has found for this device:

[http://ubuntuforums.org/showthread.php?t=1798816](http://ubuntuforums.org/showthread.php?t=1798816)
[http://ubuntuforums.org/showthread.php?t=1649634](http://ubuntuforums.org/showthread.php?t=1649634)
[http://ubuntuforums.org/showthread.php?t=1639752](http://ubuntuforums.org/showthread.php?t=1639752)

If you really want to use your TV as output, you could always get a VGA to HDMI cable and set the resolution accordingly.

---

### Post by Witra on 2011-07-25
> **master_kernel said:**
> Unfortunately, it seems like there are no working drivers that anyone has found for this device:.
Well that does indeed suck..

---

### Post by utsuprainfra on 2011-09-22
VGA -> HDMI connector isn't a solution, IMHO.  Well, if I find one, and I intend to, I will share it.

---

