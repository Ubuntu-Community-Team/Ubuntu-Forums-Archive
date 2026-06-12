---
title: "Will the video issue ever be fixed for 9.10?"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by Wolowitz on 2009-11-06
I've a radeon x1650 pro vid card.  Am I ever going to be able to have 1680X1050 resolution in Karmic? What about the next release of Ubuntu?

---

### Post by ukripper on 2009-11-06
> **Wolowitz said:**
>   Am I ever going to be able to have 1680X1050 resolution in Karmic? 

Yes. Have you reported this as a bug on launchpad?

---

### Post by philinux on 2009-11-06
How about trying the linux driver from AMD the 1600 series is there.

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

---

### Post by Wolowitz on 2009-11-06
That's great to hear. 
Thanks!

---

### Post by Wolowitz on 2009-11-06
From [http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.9&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.9&lang=English)

It appears the driver I need is now in "legacy support". Which means that, 


**_AMD may periodically provide Windows XP and Windows Vista driver updates (for the products listed above) for critical fixes only.  No new features will be provided in future driver updates.  The Linux ATI Catalyst™ driver will only be supported in Linux distributions prior to February 2009 for the legacy products listed above._**

So no more drivers from ati? 
Can, will, someone else be able to write drivers for all these ati cards that are now in legacy support?
I'm sorry, I really don't understand all this.

---

### Post by diesch on 2009-11-06
Maybe it's just a configuration issue. Please attach your /var/log/Xorg.0.log.

---

### Post by Mark Phelps on 2009-11-06
> **Wolowitz said:**
> ... It appears the driver I need is now in "legacy support"... So no more drivers from ati? 
Unfortunately, that is correct.  AMD/ATI dropped support for your card (and mine) and LOTS of others back in May.
>  ... Can, will, someone else be able to write drivers for all these ati cards that are now in legacy support?
They already have. Canonical supplies open source drivers by default.  If you're able to boot into a graphical desktop, you're already using those drivers.
> I'm sorry, I really don't understand all this.
Appears you're not alone ...

Don't know why people are telling you to download ATI drivers because, with your card, there are no ATI drivers that will work with Ubuntu 9.04 or newer -- unless you want to go hacking around with the X-server.

---

### Post by chiefrocka on 2009-11-11
With a fresh install of Karmic, when I booted into it, the screen was all garbled. I.e. I couldn't see the login screen, and I could only make out the mouse (which looked like a big orange box).

This made me think that the opensource drivers that came with Ubuntu were not working correctly. Or that Karmic was not detecting my card correctly, and hence not installing the appropriate packages.

Does anyone know which packages I should have installed for the X1650 ati radeon? I'm kind of a newb when it comes to X. Doing some searches in Synaptic for 'ati' and 'radeon' showed me some packages that weren't already installed.

I installed those (I was using another video card to do this), and when I rebooted, everything looked ok except that scrolling any gui component was not refreshing the component correctly. I could scroll the bar, but would have to minimize and restore to actually see the scroll change. Am I missing a package? Is this a bug in the opensource driver? Where should I report it?

---

