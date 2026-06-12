---
title: "Virtualizing Ubuntu, No Unity?"
date: 2011-05-30
forum: New to Ubuntu
---

### Post by _masterjonny on 2011-05-30
Hi,

I recently wanted to dual boot Ubuntu on my computer to separate work and play a bit easier, but I figured my computer just has too much non standard hardware that, from what I Google'd, isn't properly supported. Namely TRIM for my SSD, 3 * 580's, my G19 and an Aqua Computer Aquaero.

Anyway with Virtulization technology on CPU's, these days virtualizing is practically as good as running the real thing.

I've installed Ubuntu and I'm happy with it, however on the first login it told me that I couldn't run Unity because of my hardware. I've since installed the VirtualBox tools, which I assume contain the drivers needed, but I can't see the option to re enable unity again.

Can someone point me in the right direction? 

Cheers!

---

### Post by Paqman on 2011-05-30
> **_masterjonny said:**
> 
Namely TRIM for my SSD, 3 * 580's, my G19 and an Aqua Computer Aquaero.


TRIM is definitely supported, don't worry about that.

580's? Do you mean the graphics cards?
G19? The keyboard?
Your Aquaero fan controller does have some Linux software available for it, but it's from a 3rd party:
[http://breakbe.at/development/aquaero/](http://breakbe.at/development/aquaero/)

To get Unity working in VBox, you'll need the latest version of VBox (4.0) and you'll need to enable 3D hardware acceleration in the VBox settings. If you don't want to use Unity in 3D mode, download the package unity-2d, log out and select Unity 2D from the session menu at the bottom when you log back in.

---

### Post by grahammechanical on 2011-05-30
I also got that message about not having the right hardware and this was on a distribution upgrade from 10.10 to 11.04. This issue was solved by using Addition Drivers to download and install the recommended drivers. You will still need to do this in a virtual machine in my opinion.

Regards.

---

### Post by _masterjonny on 2011-05-30
I purposely name dropped the reasons I wasn't using Ubuntu natively in the hope someone would point out if it was possible or not :)

I enabled 3D acceleration in the VirtalBox settings, and Unity started working right away.

However now I have terrible frame lag when dragging Windows. I've tried un-installing and reinstalling the VirtualBox tools to no effect. I did notice that the few seconds between the script un-installing the tools, and reinstalling them the frame lag temporarily disappeared, hinting that the native drivers in Ubuntu may be a better way to go.

A bit of Googlin' around and I found this 

```
sudo apt-get install virtualbox-ose-guest-x11
```

Is that a different way of achieving the same result, or is that an alternate method I might have more luck with?

Currently I'm going with a Windows approach to fixing it, and reinstalling the VM but this time with the video acceleration enabled from the beginning, not post install. However I'm fairly sure the mantra of reinstalling fixes all isn't so applicable on Linux

---

