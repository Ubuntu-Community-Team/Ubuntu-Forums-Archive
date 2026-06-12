---
title: "Lucid Splash Screen"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by fleamour on 2010-05-01
The splash screen for Lucid on my laptop is a horrible 2-bit black & white affair.  Can I restore/replace with Karmic's splash screen?  They were class & right resolution for my monitor.

---

### Post by teh603 on 2010-05-01
Short answer: No.

Long Answer: Lucid changed bootsplash from xsplash to Plymouth, for various reasons. The best official reason I heard is that designing themes for xsplash was a horrible trainwreck. There's also some unofficial speculation, particularly why the developers picked a splash that doesn't work with proprietary drivers. Plymouth is also a hard dependency for most of Ubuntu, so you can't just remove it without haxxing several pieces of key software.

---

### Post by fleamour on 2010-05-01
Thanks, nice to know the ins & outs.

---

### Post by 4Orbs on 2010-05-01
Surely there must be an easy way to just re-color the splash and make it one solid color?

---

### Post by The Thunder Chimp on 2010-05-01
If you're a real adventurer, and ready to do anything to get the splash screen beautiful you might want to download Karmic, and then upgrade from Karmic to Lucid. In the upgrade, don't forget to say that you want to keep your Karmic BootLoader.

---

### Post by 4Orbs on 2010-05-01
I don't need it to be beautiful... I simply don't want it to be ugly. It's a real slap in the face that I should be expected to accept the ratty image if I want to use the proprietary driver (which happens to work better than Nouveau driver).

---

### Post by Jose Catre-Vandis on 2010-05-01
I have the same problem - its a resolution issue. On first boot I had a nice small logo in the middle of the screen looking good - say about 2 inches wide. After installing the nvidia proprietory driver and rebooting, the same logo is now @ 5 inches wide and butt ugly - way to big for the resolution of the graphic.

How to get the original splash (if we call it that now?)  back?

---

### Post by 4Orbs on 2010-05-01
The only way to get the small, pretty logo back is to deactivate the proprietary driver. The developers have obviously demonstrated their opinion as to what they consider to be more important.

---

### Post by -humanaut- on 2010-05-01
You can install the Vesa driver and build it in to the Plymouth bootloader if your feeling inspired enough to dig into it. Won't affect the nvidia driver either I had it done on the Beta2 but haven't bothered again since the R.C.

---

### Post by -humanaut- on 2010-05-01
Here's how you do it.

you may use uvesafb to get a nice looking bootsplash. Just install "v86d" (universe), put something like
 

uvesafb mode_option=1280x1024-32@60 mtrr=3 scroll=ywrap
 in /etc/initramfs-tools/modules and run
 

sudo update-initramfs -u

There won't be kms with proprietary nvidia drivers.

---

### Post by zachHH on 2010-05-01
> I have the same problem - its a resolution issue. On first boot I had a nice small logo in the middle of the screen looking good - say about 2 inches wide. After installing the nvidia proprietory driver and rebooting, the same logo is now @ 5 inches wide and butt ugly - way to big for the resolution of the graphic.

I had the same problem, so after a quick google search I found this article written today [http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml]("http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml")

Apparently it works for some and not for others, and I couldn't get it it work, but it's worth a shot if the fuzzy image is really bothering you.

---

### Post by 4Orbs on 2010-05-01
Thanks for that, humanaut and zachhh. It turns out that all I needed was Startup Manager as per the link in zach's post to just blank the splash screen and once again I'm a happy guy. Beautiful.

EDIT: I might add this one little tip... if you use Startup Manager, when you set the resolution of the splash screen you should choose a resolution that is among those available as listed in your xorg.conf file.

---

### Post by -humanaut- on 2010-05-01
I was just browsing the Kubuntu Bug Reports and apparently there is a fix on the way its already in the (atleast Kubuntu) proposed-updates repo I'm assuming this will be a fix across all the *buntu's Just thought I would let you all know there should be a fix coming in the form of an update very soon.

---

### Post by 4Orbs on 2010-05-02
Great news. The splash screen is the only thing I dislike about 10.04... well, actually there is one more dislike, but that's up to the Wine developers to fix.

---

### Post by Jose Catre-Vandis on 2010-05-02
> **-humanaut- said:**
> I was just browsing the Kubuntu Bug Reports and apparently there is a fix on the way its already in the (atleast Kubuntu) proposed-updates repo I'm assuming this will be a fix across all the *buntu's Just thought I would let you all know there should be a fix coming in the form of an update very soon.

Thanks for the news and the tip humanaut, will hang on for the fix :)

---

### Post by wessexmario on 2010-06-08
I can't be the only one that does NOT WANT a splash screen.
I'm using two Nvidia cards and all I want is just a nice plain character based console during boot so I can see what's happening, to know whether I'm waiting forever because it's doing a series of fschk's, or whether some obscure module has issued a warning message. Hiding what's happing on the boot console with a fancy [abismal] graphic is of no use to me.

I wouldn't care so much, but the only configuration that I can get to work on my system also has a bug with the video drivers which completely locks my system up requiring a reboot using the reset button many times a day.

Who in their right minds made it mandatory to have a splash screen that cannot be uninstalled????
I can't believe that of all OS's, the Ubuntu developers deemed it desirable to force us to have a splash screen, and that being one that doesn't work with half the graphics cards out there.

The fact that NVIDIA isn't open source is NO EXCUSE, we were able to disable the splash graphics and use a text boot console and the latest Nvidia drivers with ALL the previous versions of Ubuntu, so WHY THE BACKWARDS STEP ???

How can I disable plymouth so that I can use the latest Nvidia drivers and have a text boot console in Lucid?

---

