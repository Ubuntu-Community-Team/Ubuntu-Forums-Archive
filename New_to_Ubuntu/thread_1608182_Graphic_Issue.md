---
title: "Graphic Issue"
date: 2010-10-28
forum: New to Ubuntu
---

### Post by raw157 on 2010-10-28
I'm trying to install Ubuntu on my latptop. When ever the screen to install it comes up, it's all distorted. The screen is all goofy looking, it's hard to explain. I can't install ubuntu because the resolution is all messed up, and I cannot get down to click Install now.

Ideas? Sorry for the pathetic explanation.

---

### Post by beew on 2010-10-28
I think you have a graphic card which requires a propietary driver and since it is not in the live usb/CD the graphic is all messed up. 

Find out what the graphic card is, if it is supported you can go ahead and install and then get the driver after you have installed Ubuntu. I encountered the same situation while installing Ubuntu in a computer that uses a nvidia graphic card. The graphic was all distorted and messed up during and after installation. Installing the driver afterwords solved the problem.

---

### Post by coffeecat on 2010-10-28
A couple of things.

What laptop - make and model? And what graphics chipset?

Also - can you take a digital photo of the 'goofy' screen and post that? Don't link from an image hosting site. Use the 'Manage Attachments' button below the message field to upload the jpeg so that we get a thumbnail. There's an image size limit, so you may have to resize your jpeg.

---

### Post by raw157 on 2010-10-28
It's an HP DV6000, integrated Nvidia graphics driver. 
I'll try and take a picture of it, but I'm not sure if i'll be able too. I can try and do it with a digital camera or something, but it'll look pretty shitty. 

I can't install the driver afterwords, because I can't see or read the screen because of the messed up graphics...

Could I boot into Windows 7, and do something from inside there?

---

### Post by coffeecat on 2010-10-28
> **raw157 said:**
> Could I boot into Windows 7, and do something from inside there?

No, but have you got a monitor you could plug the DV6000 laptop into? Because look what I've found:

[http://e0d.com/blog/hp-dv6000-ubuntu-10-410-10-display-installation-issues](http://e0d.com/blog/hp-dv6000-ubuntu-10-410-10-display-installation-issues)

---

### Post by raw157 on 2010-10-28
> **coffeecat said:**
> No, but have you got a monitor you could plug the DV6000 laptop into? Because look what I've found:

[http://e0d.com/blog/hp-dv6000-ubuntu-10-410-10-display-installation-issues](http://e0d.com/blog/hp-dv6000-ubuntu-10-410-10-display-installation-issues)


You my friend rock! As soon as I connect the other moniter, it cleared up the laptop display and i can now install.

Thank you, you sir :guitar:

---

### Post by coffeecat on 2010-10-28
If I read that link correctly, you have to install the proprietary nvidia driver to be able to use the laptop display by itself. But there's a small mistake in the link. There is no Perferences (sic) > Additional Drivers. There isn't a Preferences > Additional Drivers either. :p In Lucid/10.04 it's System > Administration > Hardware Drivers, and in Maverick/10.10 it's System > Administration > Additional Drivers.

One thing to note - the proprietary driver makes a mess of the Plymouth boot screen, so don't worry if you see that. As it's on screen for a few seconds only, that's a small price to pay but it's a pity. With the open source driver the Plymouth screen is quite elegant.

Good luck!

---

